---
layout: post
title:  "ECDSA Node"
date:   2022-12-11 12:00:27 -0000
tags: blockchain cryptography react node
sitemap: false
description: >
  This project is an example of using a client and server to facilitate transfers between different addresses.
image: 
  path: /assets/img/blog/ecdsa-node@1x.jpg
  srcset:
    1920w: /assets/img/blog/ecdsa-node@1x.jpg
    960w:  /assets/img/blog/ecdsa-node@0,5x.jpg
    480w:  /assets/img/blog/ecdsa-node@0,25x.jpg
videoId: "https://user-images.githubusercontent.com/49920097/206914537-8491be30-90f3-4940-bc67-e5427cbdaadf.mp4"
repository: https://github.com/AxelWismer/ecdsa-node
---
## ECDSA Node

##### [Github repo]({{page.repository}})

This project is an example of using a client and server to facilitate transfers between different addresses. Since there is just a single server on the back-end handling transfers, this is clearly very centralized. We won't worry about distributed consensus for this project.

However, something that we would like to incorporate is Public Key Cryptography. By using Elliptic Curve Digital Signatures we can make it, so the server only allows transfers that have been signed for by the person who owns the associated address.

## Results
The application allows you to sign monetary transactions using the user's private key. Then, the server verifies that the signature is correct and extracts the address of the sender to modify the account balances.

{% include video.html id=page.videoId %}


### Cryptography module
For this project, a typescript cryptography module was created with the following functions:
```typescript
function hashMessage(message: string) : Uint8Array

async function signMessage(message: string, privateKey: Uint8Array) : Promise<[string, number]>

function getAddress(publicKey: Uint8Array): string

function recoverKey(message: string, signature: string, recoveryBit: number): Uint8Array

function authenticate(message: string, signature: string, recoveryBit: number): [boolean, string]
```

The objective of the module is to provide the UI and the server with the same cryptographic functions so that they can communicate securely.

## Get started

### Video instructions
For an overview of this project as well as getting started instructions, check out the following [video](https://www.loom.com/share/0d3c74890b8e44a5918c4cacb3f646c4):





### Client

The client folder contains a [react app](https://reactjs.org/) using [vite](https://vitejs.dev/). To get started, follow these steps:

1. Open up a terminal in the `/client` folder
2. Run `npm install` to install all the dependencies
3. Run `npm run dev` to start the application 
4. Now you should be able to visit the app at http://127.0.0.1:5173/

### Server

The server folder contains a node.js server using [express](https://expressjs.com/). To run the server, follow these steps:

1. Open a terminal within the `/server` folder 
2. Run `npm install` to install all the dependencies 
3. Run `node index` to start the server 

The application should connect to the default server port (3042) automatically! 

_Hint_ - Use [nodemon](https://www.npmjs.com/package/nodemon) instead of `node` to automatically restart the server on any changes.