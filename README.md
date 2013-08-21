# Introduction

This repository contains a Homebrew formula for installing the Google App
Engine SDK with my custom patches. It will be kept up to date with the latest
SDK version that is known to be acceptable for Khan Academy development. It
does not conflict with existing installations of the mainline
`google-app-engine` formula, but only one of these can be `brew link`'d at a
time so you may want to `brew remove` it anyway.

Issues and pull requests gladly accepted, and feel free to steal these patches
for use in a non-Homebrew setup.

# Installation

    brew unlink google-app-engine
    brew tap dylanvee/gae_sdk
    brew install gae-sdk

# Included patches

**task-queue-hostnames.patch:** Fixes task queues on SDK version 1.8.x when
using Nginx as a reverse proxy. Works by assigning task queue requests with an
unrecognized Host header to the default instance instead of dropping them.

**watcher-skip-files.patch:** Modifies the mtime polling based file watcher to
be aware of the skip_files directives in your app.yaml.

# Potential future patches

**watcher-unlimited-files.patch** Don't limit the mtime polling based file
watcher to the current maximum of 10,000 files. Possibly also increase the
current polling interval of once per second.

**fsevents-file-watcher.patch** Restore and make corrections to the
FSEvents-based file watcher for Mac OS X. See the comment at the bottom of
google/appengine/tools/devappserver2/file_watcher.py.
