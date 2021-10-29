# lavacoffee
> A lightweight and rich-featured lavalink wrapper for node.js

> Install and grab some coffee ☕

[![NPM Version](https://img.shields.io/npm/v/lavacoffee.svg?maxAge=3600)](https://www.npmjs.com/package/lavacoffee)
[![NPM Downloads](https://img.shields.io/npm/dt/lavacoffee.svg?maxAge=3600)](https://www.npmjs.com/package/lavacoffee)

# Table Of Contents
- [Features](#features)
- [Installation](#installation)
- [Documentation](#documentation)
- [Getting Lavalink](#getting-lavalink)
- [Test](#test)
- [Examples](#examples)
  - [Init](#init)
  - [Nodes](#nodes)
  - [Voice Updates](#voice-updates)
  - [Events](#events)
  - [Players](#players)
    - [Creating](#creating)
    - [Getting](#getting)
    - [Replaying](#replaying)

# Features
- Easy-to-use
- Lightweight and performant

# Installation
> NPM (Stable) => npm install lavacoffee

> Github (Dev) => npm install XzFirzal/lavacoffee#main

# Documentation
> https://xzfirzal.github.io/lavacoffee

# Getting Lavalink
Download the latest binaries from the [CI Server (Dev)](https://ci.fredboat.com/repository/download/Lavalink_Build?guest=1&branch=refs/heads/dev)

Put an [application.yml](https://github.com/freyacodes/Lavalink/blob/master/LavalinkServer/application.yml.example) in your working directory.

Run with `java -jar Lavalink.jar`

Docker images are available on the [Docker hub](https://hub.docker.com/r/fredboat/lavalink/).

# Test
[Test Bot](https://github.com/XzFirzal/lavacoffee/blob/main/test/index.ts)
> npm run test

# Examples
### Init
```ts
// Importing lava instance constructor
import { CoffeeLava } from "lavacoffee"

// Construct the lava instance
const lava = new CoffeeLava(lavaOptions)

// Init the lava instance
lava.init(clientID)
```

### Nodes
```ts
// Adding a node
lava.add(nodeOptions)

// More nodes
lava.add(nodeOptions1)
lava.add(nodeOptions2)
...
```

### Voice Updates
```ts
// Payload can be voice state update payload or voice server update payload
lava.updateVoiceData(payload)
```

### Events
> [LavaEvents](https://xzfirzal.github.io/lavacoffee/interfaces/LavaEvents.html)

## Players 
### Creating
```ts
// THis will create a new player or get an existing if exist
const player = lava.create(playerOptions)

// Connect to voice channel
player.options.voiceID = voiceChannelID
player.connect()

// Adding tracks
player.queue.add(tracks)

// Play
player.play()
...
```

### Getting
```ts
// Use this if you only want to get a player without creating it
const player = lava.get(guildID)

if (!player) return

// Getting queue
const queue = player.queue

// Getting current track
const track = player.queue.current
...
```

### Replaying
```ts
/**
 * When player is disconnected from node
 * it will automatically move to another node
 * then replay the track on current position
 * you can disable this behaviour with setting
 * `autoReplay` to false in LavaOptions
 */

// Replay events

// When successfully replayed
lava.on("playerReplay", player => { ... })

// When there's an error while replaying
lava.on("replayError", (player, error) => { ... })
...
```
