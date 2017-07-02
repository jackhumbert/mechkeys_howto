# How to develop your own custom keymap with QMK 

## Prerequisites
* Github.com account
* Development environment

## QMK

Log in to Github.com.

Fork the QMK repo, https://github.com/qmk/qmk_firmware , with the Fork button at the top right.

In your dev environment, locally clone your remote fork of the QMK repo:

```
git clone git@github.com:unxmaal/qmk_firmware.git
```

You need to set up a new 'remote', pointed to the original project. Name it 'upstream'.
```
git remote add upstream git@github.com:qmk/qmk_firmware.git
```

Fetch any branches and stuff from upstream, then pull.
```
    git fetch upstream
    git pull upstream master
```
Now your repo is in sync with the upstream. 

Create a new branch named after the feature you want to add. I like using my username too.
```
    git checkout -b unxmaal-spacecadet
```
Now make your changes. Typically, that could include copying the default keymap directory to a new directory, and naming it your username, or some feature.

Add and commit your changes.
```
    git add <file> <file>
    git commit -m "added new keymap with space cadet shift"
```
Push your change to your branch in your repo on Github.com
```
    git push origin unxmaal-spacecadet
```
Now, on github.com, look at YOUR repo. Be sure to pick your new feature branch from the dropdown. Click around and ensure everything looks nice. Now issue your pull request, by clicking New Pull Request.

Usually the defaults are fine; you're pulling your branch from your fork into their main repo on master branch.

In the description, explain what you did.

Click 'create pull request'. Then wait for the QMK guys to look over your stuff. Normally they'll accept additions to keymaps pretty quickly.

Good luck!