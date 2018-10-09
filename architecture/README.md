# Bara Architecture Overview

This spec document defines the way Bara work with stream of events, conditions, and actions.

## Table of Contents

- [Main](#main)
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

## Event

An event is ...

## Condition

A condition is ...

## Action

An action is ...
