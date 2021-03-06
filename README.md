[![NPM version](http://img.shields.io/npm/v/pisco-plugin-inquirer-emit.svg)](https://npmjs.org/package/pisco-plugin-inquire-emit)
[![Build Status](http://img.shields.io/travis/cellsjs/pisco-plugin-inquirer-emit.svg)](https://travis-ci.org/cellsjs/pisco-plugin-inquirer-emit)
[![licence](http://img.shields.io/npm/l/pisco-plugin-inquirer-emit.svg)](https://github.com/cellsjs/pisco-plugin-inquirer-emit/blob/master/package.json)

# Plugin inquirer-emit

This plugin helps to emit parameters just defining the inquire in your step configuration.

1. [check() hook](#check)
1. [emit() hook](#emit)

## Using this plugin

1. **Add dependency to package.json of your recipe**

```sh
npm install pisco-plugin-inquirer-emit --save
```

2. **Add the plugin in your step**

`recipe/steps/step-name/config.json`:

```json
"plugins": [ "inquirer-emit" ]
```

3. **Define a paramater called `emitPrompts` in your step**

Example `recipe/steps/step-name/config.json`:

```json
"emitPrompts": [ {
  "name": "param1",
  "type": "list",
  "message": "Choose one value",
  "choices": [
    "value1",
    "value2"
  ]
}, {
  "name": "param2",
  "type": "input"
} ]
```

## <a name="check"></a>check() hook

When a "emitPrompts" configuration has been defined, then inquire parameters.

Example:

```json
"emitPrompts": [ {
  "name": "param1",
  "type": "list",
  "message": "Choose one value",
  "choices": [
    "value1",
    "value2"
  ]
}, {
  "name": "param2",
  "type": "input"
} ]
```

This shows a message like this.

```sh
Inquiring 'emitPrompts' configuration...
```

## <a name="emit"></a>emit() hook

Emit all inquired parameters to rest of the flow. Parameters are going to be availables on this.params.

Example:

```json
"emitPrompts": [ {
  "name": "param1",
  "type": "list",
  "message": "Choose one value",
  "choices": [
    "value1",
    "value2"
  ]
}, {
  "name": "param2",
  "type": "input"
} ]
```

This will emit two paramaters `param1` and `param2`.

## Main Index:

- [Available Commands](#available-commands)
  - [Flows](#flows)
  - [Steps](#steps)
- [Plugins](#plugins)
  - [inquirer-emit](#inquirer-emit-inquire-and-emit-configuration)


## Available Commands:

### FLOWS

### STEPS

## PLUGINS

#### inquirer-emit (Inquire and emit configuration)
[[Index]](#main-index)

# Plugin inquirer-emit

This plugin helps to emit parameters just defining the inquire in your step configuration.

1. [check() hook](#check)
1. [inquirerEmit() addon](#emit)

## Using this plugin

1. **Add dependency to package.json of your recipe**

```sh
npm install pisco-plugin-inquirer-emit --save
```

2. **Add the plugin in your step**

`recipe/steps/step-name/config.json`:

```json
"plugins": [ "inquirer-emit" ]
```

3. **Define a paramater called `emitPrompts` in your step**

Example `recipe/steps/step-name/config.json`:

```json
"emitPrompts": [ {
  "name": "param1",
  "type": "list",
  "message": "Choose one value",
  "choices": [
    "value1",
    "value2"
  ]
}, {
  "name": "param2",
  "type": "input"
} ]
```

4. **Emit on your step the result of this.inquirerEmit()**

Example `recipe/steps/step-name/index.js`:

```javascript
module.exports = {
  emit() {
    return this.inquirerEmit();
  }
};
```

## <a name="check"></a>check() hook

When a "emitPrompts" configuration has been defined, then inquire parameters.

Example:

```json
"emitPrompts": [ {
  "name": "param1",
  "type": "list",
  "message": "Choose one value",
  "choices": [
    "value1",
    "value2"
  ]
}, {
  "name": "param2",
  "type": "input"
} ]
```

This shows a message like this.

```sh
Inquiring 'emitPrompts' configuration...
```

## <a name="emit"></a>inquirerEmit() addon

Return an object with all inquired parameters to rest of the flow. Parameters are going to be availables on this.params.

Example:

```json
"emitPrompts": [ {
  "name": "param1",
  "type": "list",
  "message": "Choose one value",
  "choices": [
    "value1",
    "value2"
  ]
}, {
  "name": "param2",
  "type": "input"
} ]
```

This will return an object with the two paramaters `param1` and `param2`.



