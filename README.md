# Introduction

This repository contains a Homebrew formula for installing the Google App
Engine SDK with my custom patches. It will be kept up to date with the latest
SDK version that is known to be acceptable for Khan Academy development. It
does not conflict with existing installations of the mainline
`google-app-engine` formula, but only one of these can be `brew link`'d at a
time so you may want to `brew remove` it anyway.

This repository is strangely named, but Homebrew wants it that way. ("Tell me
why...")

# Installation

    brew unlink google-app-engine
    brew tap dylanvee/gae_sdk
    brew install gae-sdk
