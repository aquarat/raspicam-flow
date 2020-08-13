# raspicam-flow

raspicam-flow is a set of NodeRed flows that make it easy to drive the Raspberry Pi HQ Camera module from a web browser.

A friend lent me a telescope and I really wanted to try it out with my Raspberry Pi HQ Camera module. Unfortunately there didn't seem to be a lot of options for long exposure web-based interfaces for the Pi HQ Camera... so I threw this together.

Some notes:
 - This is rough around the edges.
 - It has only been configured and tested with the HQ Camera module.
 - Only some flags from the raspistill utility are exposed.
 - Video recording functionality hasn't been "implemented".

## Installation
You'll need to install NodeRed, either in the host OS or via Docker. If you go the docker route you'll need to follow various guides to allow camera access from within the container.

Once NodeRed is installed, add the following external packages:

 - node-red-dashboard
 - node-red-node-base64

You'll also need to add the following configuration to settings.js:

    contextStorage: {
       default: "file",
       memoryOnly: { module: 'memory' },
       file: { module: 'localfilesystem' },
    },

The above configuration makes the default context storage persistent via disk. This is used for dashboard/UI settings. It also adds a second context store which is memory-only (volatile). The memoryOnly store is used for caching JPEGs.

## Screenshots
<p align="center">
  <img src="https://github.com/aquarat/raspicam-flow/blob/master/screenshot-browser.png?raw=true" alt="The web browser view."/>
  <br/>
  <img src="https://github.com/aquarat/raspicam-flow/blob/master/images/screenshot-flow.png?raw=true" alt="The flow."/>
</p>
