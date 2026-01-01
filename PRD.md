# Overview

This repository hosts a claude code plugin which allows on to use the Haskell Language Server (HLS) LSP with
claude code.

# Goal

This plugin should allow claude to use HLS on a given haskell project. It should be able to check if HLS is availble, if it is working,
and if it can analyze the given code (maybe a simple "completions available here" or "call hierarchy" test). It should offer guided
troubleshooting if things don't appear to be working. 

The plugin should work on Linux, Windows and MacOS. It should not offer to install HLS or Haskell tools - the user is responsible for that. It should
also expect an existing Cabal or Stack directory.

## Supporting Documentation

The plugin should ship with the following documentation, which can help the user:

* @hls-docs.xml - HLS documentation
* @ghc-user.xml - GHC user guide
* @cabal-docs.xml - Cabal documentation

# Testing / Iteration

When developing this plugin, execute claude (with --plugin-dir and a prompt) in order to test the plugin.

# Development Documentation

The following documenation will be useful when developing this plugin, but should NOT be shipped:

* @plugins.html - Claude Code Plugins - Describes how to add LSP servers to a plugin
* @plugins-reference.html - Claude Code Plugin Reference - Complete technical reference for Claude Code plugin system, including schemas, CLI commands, and component specifications.
* @settings.html - Claude Code Settings - Reference for all claude code settings, JSON format, etc. Most importantly , how to make use of a plugin.
* @claude-code.xml - Claude Code Repo - Includes plugin examples in the `plugins` directory