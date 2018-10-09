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


```javascript
import {createMain, registerStream, registerTrigger} from 'bara';
import StreamFile from 'bara-stream-file';
import TriggerFileChange from 'bara-trigger-file-change';
import TriggerCountFile from 'bara-trigger-count-file';

const streams = registerStream([StreamFile]);

const triggers = registerTrigger([TriggerOne, TriggerTwo]);

const AwesomeFileService = createMain('awesome-file-service', streams, triggers)

export default AwesomeFileService;

```


## Event

An event is ...

## Condition

A condition is ...

## Action

An action is ...
