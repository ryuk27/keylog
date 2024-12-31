# Node-Keylogger  

A simple Node.js Linux-only keylogger using events for keyboard input tracking.  

## Table of Contents  

1. [Features](#features)  
2. [Installation](#installation)  
3. [Usage](#usage)  
4. [Event Details](#event-details)  
5. [TODO](#todo)  

## Features  

- Minimal implementation without requiring additional modules.  
- Uses `fs.createReadStream` instead of `fs.open`.  

## Installation  

Install the package via npm:  
```bash
npm install node-keylogger
```
## Usage

- Import the library and set up event listeners:
```javascript
const Keyboard = require('node-keylogger');

// Replace 'event0' with the file corresponding to your keyboard in /dev/input/
const k = new Keyboard('event0');  

k.on('keyup', console.log);       // Logs key release events  
k.on('keydown', console.log);     // Logs key press events  
k.on('keypress', console.log);    // Logs key press and hold events  
k.on('error', console.error);     // Logs errors
```

## Event Details

- Each captured event provides the following details:
```javascript
{ 
  timeS: 1347572085,   // Timestamp (Seconds part)  
  timeMS: 741381,      // Timestamp (Microseconds part)  
  keyCode: 17,         // Keyboard key code  
  keyId: 'KEY_W',      // Key identifier (QWERTY layout)  
  type: 'keypress',    // Event type ('keyup', 'keydown', or 'keypress')  
  dev: 'event2'        // Device identifier  
}
```
## TODO
- Add support for Windows.
- Add support for macOS.
