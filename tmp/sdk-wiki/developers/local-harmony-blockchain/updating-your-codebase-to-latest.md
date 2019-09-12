# Updating your codebase to latest

## Pre-requisites

Ensure that you have created your own local branch by following the harmony github cheatsheet.

New developers

{% hint style="info" %}
Ensure that you have committed and pushed your local changes before updating to the latest version.
{% endhint %}

## Updating your local code to the latest release

```text
cd /Users/johnwhitton/go/src/github.com/harmony-one/harmony
git status
git checkout master
git fetch upstream
git merge upstream/master
git push
```

