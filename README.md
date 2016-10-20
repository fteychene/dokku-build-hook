# Dokku build hook

*Add hook for application to prepare build*

This plugin aim applications that requires to run some commands before build and offer a way to run these commands in dokku build lifecycle.

## Installation

```shell
# on 0.3.x
cd /var/lib/dokku/plugins
git clone https://github.com/fteychene/dokku-build-hook.git build-hook
dokku plugins-install

# on 0.4.x
dokku plugin:install https://github.com/fteychene/dokku-build-hook.git build-hook
```

## Usage

The plugin will search for scripts in application codebase to be executed on different phases of the build.

The scripts should be installed in a `hooks` directory in the project codebase and be name as the corresponding hook you want to trigger.

Hooks :
 - [x] pre-build : This script will be executed before the build of the project (Buildpack or Dockerfile based)


## Example

Add a script `hooks/pre_build` in a dokku project.
```bash
#!/usr/bin/env bash

echo "Run something before dokku build the project"
```

When deploying you app to dokku you should see the following instructions before build
```
-----> Checking for pre-build script
=====> Running pre-build script
Run something before dokku build the project
=====> End of pre-build script
```