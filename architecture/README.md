<p align="center">
  <img align="center" src="../img/BaraLogo.png" width="100%" alt="Bara" />
</p>
# Bara Architecture Overview

This spec document defines the way Bara work with stream of events, conditions, and actions.

## Table of Contents

- [Main](#main)
- [Stream](#stream)
- [Trigger](#trigger)
- [Event](#event)
- [Condition](#condition)
- [Actions](#action)

## Main

- A main is a Bara function which will do the registration of streams and trigger.
- A main function can be a Bara module to combine with other Bara module.

- This is the example main.js file implementation:

```javascript
import bara from "bara";
import StreamFile from "bara-stream-file";
import TriggerFileChange from "bara-trigger-file-change";
import TriggerCountFile from "bara-trigger-count-file";

const streams = [StreamFile("~/Data")];

const triggers = [TriggerFileChange, TriggerCountFile]);

const AwesomeFileService = bara("awesome-file-service", streams, triggers);

export default AwesomeFileService;
```

## Stream
- A Stream is the list of events emitted over the time of Bara process.
- A Stream can be registered to a Bara main module to listen on a specific event.
- A Stream does not take care of which trigger will consume the emitting event.
- A Stream only take care of one type of event with different payload.

Code usage example:

```javascript
import {registerStream, createEventType} from "bara";
import chokidar from "chokidar";

const events = {
  FILE_CREATED: createEventType("FILE_CREATED"),
  FILE_CHANGED: createEventType("FILE_CHANGED"),
};

const FileStream = createStream({
  id: "org.barajs.stream.file",
  name: "Bara Stream File",
  events: 
  method: {
    init: (emit, payload) => {
      // Define the location to watch files.
      const pathToWatch = payload;
    
      // Register file watcher.
      const watcher = chokidar(pathToWatch);
      
      // Emit event to the stream when a file is added.
      watcher
        .on('add', path => emit(events.FILE_CREATED, path));
        .on('change', path => emit(events.FILE_CHANGED, path));
    }
  }
});

export default FileStream;
```


  

## Event

An event is ...

## Condition

A condition is ...

## Action

An action is ...
