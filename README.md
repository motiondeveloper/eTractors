<!-- Links -->

[back to top ↑]: #aeeffectors

<div align="center">

# aeEffectors <!-- omit in toc -->

System for creating particle effectors in After Effects using expressions

**[Usage](#usage) | [Example](#example) | [Contact](#contact)**

</div>

## Overview

`aeEffectors` is a way to create 'effector' layers that can attract and repel other layers when they move within a specified distance.

It comes in the form of a JSON file that's imported into the project, and then referenced in expressions.

## Contents

- [Overview](#overview)
- [Contents](#contents)
- [Compatibility](#compatibility)
- [Usage](#usage)
  - [3. Create a new effector](#3-create-a-new-effector)
- [Example](#example)
- [License](#license)
- [Contact](#contact)

## Compatibility

This aeFunctions is compatible with After Effects versions >= 16.0.1 (CC2019) which use the new [Javascript engine](https://helpx.adobe.com/after-effects/using/expression-language-reference.html).

[Back To Top ↑]

## Usage

### 1. **Download and import `aeEffectors.jsx` into your After Effects project** <!-- omit in toc -->

Download the `aeEffectors.jsx` file from the master branch of this repository, and import it into your After Effects project.

### 2. **Add a reference to the library in your expression** <!-- omit in toc -->

> aeEffector is designed to be used on the 2D position property of a layer, and this is assumed by all of the following expressions.

To reference the library in an expression, you need to assign it to a variable. This is done via the line:

```javascript
const aeEffectors = footage('aeEffectors.jsx').sourceData;
```

> ⚠️ Since After Effects doesn't count footage items that are only referenced within expressions as used, it's recommended that you also place the `aeEffectors.jsx` file in any compositions where it is referenced.
>
> This will ensure After Effects includes the file when collecting assets or packaging into a Motion Graphics Template.

### 3. Create a new effector

This creates a new effector based on an effector layer, and the position of the current layer.

```javascript
const myEffector = aeEffector.createEffector(effectorLayer, particlePosition);
```



## Example

An example setup of an animation group with a couple of keyframes:

```javascript
// Import eKeys library
const eKeys = footage('eKeys.jsx').sourceData;

// Create an array of keyframes
const inKeys = [
  {
    keyTime: 1,
    keyValue: 0,
    easeIn: 0,
    easeOut: 66,
  },{
    keyTime: 2,
    keyValue: 250,
    easeIn: 90,
    easeOut: 0,
  }
];

// Create new animation group
const animIn = eKeys.AnimGroup(inKeys);

// Animate animation group
animIn(time);
```

[Back To Top ↑]

## License

This project is licensed under the terms of the MIT License.

[Back To Top ↑]

## Contact

Bugs, issues and feature requests can be submitted by filing an [issue](https://github.com/motiondeveloper/aeEffector/issues) on Github. For everything else, feel free to reach out to [@modeveloper](https://twitter.com/modeveloper) on twitter.

[Back To Top ↑]
