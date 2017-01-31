# Deploying Software with Git Hooks

Using the Git hooks "post-update" you can deploy your software with ease. Make sure to read about the Git hooks documentation and how scripts work. 

#### Notices

 * It is assumed that you know how to setup a simple git repo on your server to push to.
 * The origin `local` in these examples is simply pointing to the local filesystem's git repos.

## Example

The example below shows you a simple example of running a build script when the master branch is updated.

```
#!/etc/bin/env bash
set -e

BRANCH=$(basename $1)
if [[ -z $BRANCH || $BRANCH != "master"]]; then
  exit 0
fi

echo "Master updated, let's build!"
cd /projects/the-project
git --git-dir=.git pull local master
./build-bin

exit 0
```

## Restarting Services

In the cases where you are running services that need to be restarted once you push you can simply execute an additional script that has sudo access. You can look up how to assign sudo access to a particular program/script on the "interwebs".

```
#!/usr/bin/env bash
set -e

BRANCH=$(basename $1)
if [[ -z $BRANCH || $BRANCH != "staging" && $BRANCH != "production" ]]; then
  exit 0
fi

echo "$BRANCH updated, lets build!"
cd  /projects/the-project-$BRANCH

git --git-dir=.git pull local $BRANCH

echo "NodeJS Version"
node --version
echo "NPM Version"
npm --version
echo "Installing node modules..."
npm install
echo "Building..."
npm run build
echo "Restarting service..."
sudo scripts/restart-$BRANCH

exit 0
```

This previous example shows a funky setup where there are two instances of it running. One in production and one in staging.
