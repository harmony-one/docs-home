---
description: A web3-react toolkit for Harmony wallets
---

# Harmony-React

[Harmony-React](https://github.com/harmony-one/harmony-react) adds support for using OneWallet and MathWallet together with [web3-react](https://github.com/NoahZinsmeister/web3-react).

Harmony-React is not a fork of web3-react, but rather built on top of web3-react to ensure that the library can be upgraded whenever web3-react gets updated.

## Using Harmony-React

### Installation

Add `web3-react/core` and the wallets you want to use (OneWallet, MathWallet or both) to `package.json`:

```javascript
"@web3-react/core": "latest",
"@harmony-react/mathwallet-connector": "latest",
"@harmony-react/onewallet-connector": "latest",
```

Install using `yarn install` or `npm install`.

### Usage

Import packages:

```javascript
import { OneWalletConnector } from '@harmony-react/onewallet-connector'
import { MathWalletConnector } from '@harmony-react/mathwallet-connector'
```

Instantiate wallets:

```javascript
const onewallet = new OneWalletConnector({ chainId: 1 }) // 1 = Mainnet, 2 = Testnet
const mathwallet = new MathWalletConnector({ chainId: 1 })  // 1 = Mainnet, 2 = Testnet
```

Store the wallet references in a store or a suitable structure, e.g:

```javascript
    this.store = {
      ...
      web3context: null,
      connectorsByName: {
        OneWallet: onewallet,
        MathWallet: mathwallet,
      }
      ...
    }
```

For a more in-depth implementation example check [here](https://github.com/harmony-one/token-faucet-demo-dapp/blob/main/ui/src/stores/index.jsx).

Create a wallet connection/unlock modal (or other suitable UI element):

```javascript
import React from "react";
import {
  DialogContent,
  Dialog,
  Slide
} from '@material-ui/core';

import Unlock from './index.jsx';

export default function UnlockModal(props) {
  const { closeModal, modalOpen } = props
  const fullScreen = window.innerWidth < 450
  const Transition = React.forwardRef((props, ref) => <Slide direction="up" {...props} ref={ref} />)

  return (
    <Dialog open={ modalOpen } onClose={ closeModal } fullWidth={ true } maxWidth={ 'sm' } TransitionComponent={ Transition } fullScreen={ fullScreen }>
      <DialogContent>
        <Unlock closeModal={ closeModal } />
      </DialogContent>
    </Dialog>
  )
}
```

Implement the `Unlock` component:

```javascript
...
import { Web3ReactProvider, useWeb3React } from '@web3-react/core'
...

export default function Unlock({ closeModal }) {
  ...
  
  return (
    <div className={ classes.root }>
      <div className={ classes.closeIcon } onClick={ closeModal }><CloseIcon /></div>
      <div className={ classes.contentContainer }>
        <Web3ReactProvider getLibrary={ getLibrary }>
          <WalletComponent closeModal={ closeModal } />
        </Web3ReactProvider>
      </div>
    </div>
  )
}
```

And finally, implement the `WalletComponent`:

```javascript
export default function WalletComponent({ closeModal }) {
  const context = useWeb3React()
  const localContext = store.getStore('web3context')
  var localConnector = null;
  if (localContext) {
    localConnector = localContext.connector
  }
  
  const {
    connector,
    library,
    account,
    activate,
    deactivate,
    active,
    error
  } = context;

  var connectorsByName = store.getStore('connectorsByName')

  const [activatingConnector, setActivatingConnector] = React.useState()
  useEffect(() => {
    if (activatingConnector && activatingConnector === connector) {
      setActivatingConnector(undefined);
    }
  }, [activatingConnector, connector]);

  useEffect(() => {
    if (account && active && library) {
      store.setStore({ account: { address: account }, web3context: context })
      emitter.emit(CONNECTION_CONNECTED)
    }
  }, [account, active, closeModal, context, library]);

  const [hoveredConnectorButtons, setHoveredConnectorButtons] = React.useState(new Map());
  const updateHoveredConnectorButtons = (k,v) => {
    setHoveredConnectorButtons(new Map(hoveredConnectorButtons.set(k,v)));
  }

  // useEffect(() => {
  //   if (storeContext && storeContext.active && !active) {
  //     console.log("we are deactive: "+storeContext.account)
  //     store.setStore({ account: {}, web3context: null })
  //   }
  // }, [active, storeContext]);

  // handle logic to eagerly connect to the injected ethereum provider, if it exists and has granted access already
  // const triedEager = useEagerConnect();

  // handle logic to connect in reaction to certain events on the injected ethereum provider, if it exists
  // useInactiveListener(!triedEager || !!activatingConnector);
  const width = window.innerWidth

  return (
    <div style={{ display: 'flex', flexWrap: 'wrap', justifyContent: (width > 650 ? 'space-between' : 'center'), alignItems: 'center' }}>
      {Object.keys(connectorsByName).map(name => {
        const currentConnector = connectorsByName[name];
        const activating = currentConnector === activatingConnector;
        const connected = (currentConnector === connector||currentConnector === localConnector);
        const disabled =
           !!activatingConnector || !!error;

        var url;
        var display = (hovered && connected) ? 'Disconnect' : name;
        if (name === 'OneWallet') {
          url = HarmonyLogo
        } else if (name === 'MathWallet') {
          url = MathWalletLogo
        }

        return (
          // UI to generate list of wallets
        )
      }) }

      // UI to disconnect active wallet
  )
}
```

For full reference implementations of `Store`, `UnlockModal`, `Unlock`, and `WalletComponent`:

* `Store`: [https://github.com/harmony-one/token-faucet-demo-dapp/blob/main/ui/src/stores/index.jsx](https://github.com/harmony-one/token-faucet-demo-dapp/blob/main/ui/src/stores/index.jsx)
* `UnlockModal`: [https://github.com/harmony-one/token-faucet-demo-dapp/blob/main/ui/src/components/unlock/unlockModal.jsx](https://github.com/harmony-one/token-faucet-demo-dapp/blob/main/ui/src/components/unlock/unlockModal.jsx)
* `Unlock`: [https://github.com/harmony-one/token-faucet-demo-dapp/blob/main/ui/src/components/unlock/index.jsx](https://github.com/harmony-one/token-faucet-demo-dapp/blob/main/ui/src/components/unlock/index.jsx)
* `WalletComponent`: [https://github.com/harmony-one/token-faucet-demo-dapp/blob/main/ui/src/components/unlock/walletComponent.jsx](https://github.com/harmony-one/token-faucet-demo-dapp/blob/main/ui/src/components/unlock/walletComponent.jsx)
