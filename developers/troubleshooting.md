# Troubleshooting

**Command:** ./bin/wallet -p local balances  
**Error:** error while loading shared libraries: libbls384\_256.so: cannot open shared object file: No such file or directory  
**Try:**

```text
cd /Users/johnwhitton/go/src/github.com/harmony-one/harmony
source ./scripts/setup_bls_build_flags.sh
```

