<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [Running The Demo Raincatcher Solution Locally](#running-the-demo-raincatcher-solution-locally)
  - [Overview](#overview)
  - [Requirements](#requirements)
    - [MongoDB](#mongodb)
    - [Ruby (Optional)](#ruby-optional)
  - [Clone All Of The Raincatcher Modules and Demo Apps](#clone-all-of-the-raincatcher-modules-and-demo-apps)
  - [Notes On Running Locally](#notes-on-running-locally)
    - [Using Drag & Drop Apps Locally](#using-drag-&-drop-apps-locally)
    - [Using A Local Service To Authenticate Users](#using-a-local-service-to-authenticate-users)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Running The Demo Raincatcher Solution Locally

## Overview

This guide presents the steps necessary to:

- Run the Raincatcher demo solution locally.
- Edit Raincatcher modules and have the results reflected in the demo solution.

## Requirements

There are some requirements to getting up and running locally with Raincatcher.

### RHMAP

The demo solution currently requires an instance of RHMAP and will not work properly without it. It can be a local or remote instance of RHMAP, but must be configured as outlined in the Raincatcher [Getting Started Guide](Getting-Started.md#running-the-raincatcher-demo-apps-in-rhmap). This allows the local *raincatcher-demo-cloud* app to access

- Forms
- Themes
- Drag & Drop App Config

### MongoDB

The *raincatcher-demo-cloud* app and *raincatcher-demo-auth* app requires a running MongoDB instance. See the [MongoDB Installation Guide](https://docs.mongodb.com/manual/installation/) for details on how to install MongoDB.

### Redis

The *raincatcher-demo-cloud* app requires a running instance of Redis. See the [Redis Quick Start Guide](https://redis.io/topics/quickstart) for details on how to insall Redis manually, or use your system's package manager.

### Ruby

In order to use the [Raincatcher CLI Tool](https://github.com/feedhenry-raincatcher/raincatcher-cli) to manage starting all of the demo apps, you will need to install [Ruby](https://www.ruby-lang.org/en/documentation/installation/).

## Install Raincatcher CLI & Clone Repositories

The [Raincatcher CLI Tool](https://github.com/feedhenry-raincatcher/raincatcher-cli) is a useful tool for getting set up with all of the Raincatcher modules and Demo Apps. Follow the steps in the README to clone, install, and link all of the Raincatcher modules.

## Configure Environment Variables

In order to communicate with RHMAP and the local authentication service, several environment variables need to be configured. You can find the values in RHMAP -> Projects -> _Project name given in step 2 of [Getting Started Guide](Getting-Started.md#running-the-raincatcher-demo-apps-in-rhmap)_ -> WFM Demo Cloud App -> Environment Variables -> System Environment Variables.

These environment variables should be placed in the `raincatcher-demo-cloud/Gruntfile.js` around line 50 (at the time of writing).

```javascript
{
  ...
  env: {
    local: {
      FH_APPNAME: "<FH_APPNAME value>",
      FH_DOMAIN: "<FH_DOMAIN value>",
      FH_ENV: "<FH_ENV value>",
      FH_INSTANCE: "<FH_INSTANCE value>",
      FH_MBAAS_ENV_ACCESS_KEY: "<FH_MBAAS_ENV_ACCESS_KEY value>",
      FH_MBAAS_HOST: "<FH_MBAAS_HOST value>",
      FH_MBAAS_PROTOCOL: "<FH_MBAAS_PROTOCOL value>",
      FH_WIDGET: "<FH_WIDGET value>",
      FH_APP_API_KEY: "<FH_APP_API_KEY value>",

      // This value can be found in `raincatcher-demo-cloud/Gruntfile.js`
      // in the FH_SERVICE_MAP environment variable
      WFM_AUTH_GUID: "iidn3tvprs62asdebat5m3eg"
    }
  }
  ...
}
```

## Run The Applications

```
wfm start
```
