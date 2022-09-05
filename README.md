<div id="top"></div>
<center>
  <h1 style="
  background: linear-gradient(89.97deg, #ae67fa 1.84%, #f49867 102.67%);
  background-clip: text;
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
  font-family: $font-family;
  font-size: 50px;
  line-height: 75px;
  font-weight: 800;
  "> v a l i d a t i o n s  -  f o r m s </h1>
</center>

## **Description**


```
It is a library that aims to help with form validation in an easy way :)
```

<p align="right"><a href="#top">volver arriba 🔼</a></p>

--------------------------------------------------------------------------------

## **Installation**

```bash
npm i -S validations-forms

OR

npm install --save validations-forms
```

<p align="right"><a href="#top">volver arriba 🔼</a></p>

--------------------------------------------------------------------------------

## **Getting Started**

> ### **Types Of Languages**
|  name                                                         |           Description               | Default value  |
| --------------------------------------------------------------|-------------------------------------|----------------|
| <img src ="https://img.shields.io/badge/ES-success">          | error messages in spanish language  |      ✅        |
| <img src ="https://img.shields.io/badge/EN-success">          | error messages in english language  |                |


> ### **Types Of Validations**

|  name                                                               |           Description                 |
| --------------------------------------------------------------------|---------------------------------------|
| <img src ="https://img.shields.io/badge/T-success">                 | Text data validation               |
| <img src ="https://img.shields.io/badge/R-success">                 | Required data validation           |
| <img src ="https://img.shields.io/badge/N-success">                 | Number data validation             |
| <img src ="https://img.shields.io/badge/TN-success">                | Text and number data validation    |
| <img src ="https://img.shields.io/badge/C-success">                 | Required data for combo            |
| <img src ="https://img.shields.io/badge/CURP-success">              | CURP data validation               |
| <img src ="https://img.shields.io/badge/DATE-success">              | Date data validation               |
| <img src ="https://img.shields.io/badge/EMAIL-success">             | Email data validation              |
| <img src ="https://img.shields.io/badge/RFC-success">               | RFC data validation                |
| <img src ="https://img.shields.io/badge/RFC_KEY_CODE-success">      | RFC KEY CODE data validation       |
| <img src ="https://img.shields.io/badge/POSTAL_CODE-success">       | POSTAL CODE data validation        |
| <img src ="https://img.shields.io/badge/SPECIAL_CHARACTER-success"> | Special character validation       |

> ### **Parameter description**

  <br/>
  <img src ="https://img.shields.io/badge/Required parameter-success">
  <br/>
  <img src ="https://img.shields.io/badge/Optional parameter-blue">

|  name                                                   |           Description                                    |
| --------------------------------------------------------|----------------------------------------------------------|
| <img src ="https://img.shields.io/badge/id-success">    | Input identifier                                         |
| <img src ="https://img.shields.io/badge/value-success"> | Value to validate                                        |
| <img src ="https://img.shields.io/badge/type-success">  | Type validation  `"ARRAY":["R","T"]` OR  `"STRING" : "T"`|
| <img src ="https://img.shields.io/badge/title-blue">    | Title of the entry to validate                           |
| <img src ="https://img.shields.io/badge/message-blue">  | personalized message                                     |
## **Usage**

> ### **Import / Require**

```javascript
// ES6+ example

import {
  singleValidation,
  multiValidation,
  multiValidationErrors,
} from "validations-forms";

```

```javascript
// ES5 example

const {
  singleValidation,
  multiValidation,
  multiValidationErrors,,
} = require("validations-forms");

```

```javascript
No ES+

const formValidatorInput = require("validations-forms");

formValidatorInput.singleValidation(DATA);
formValidatorInput.multiValidation(DATA);
formValidatorInput.multiValidationErrors(DATA);
```
<p align="right"><a href="#top">volver arriba 🔼</a></p>

--------------------------------------------------------------------------------

## **Usage**

### Example function _singleValidation_

```javascript
import { singleValidation } from "validations-forms";
```
#### a single validation on an input
```javascript
console.log(singleValidation({
  id    : "id_input",
  title : "input",
  type  : "T", // OR ["T"] <=== a single validation on an input
  value : "text",
}),"EN")
```
<img src ="https://img.shields.io/badge/successful-success">

```>>> { status: true }```
#### more than one validation on the same input
```javascript
console.log(singleValidation({
  id    : "id_input",
  title : "TITULO UNO",
  type  : [ "R", "T" ], // <=== more than one validation on the same input,
  value : "text",
}),"EN")
```

<img src ="https://img.shields.io/badge/successful-success">

```>>> { status: true }```

#### Errors
```javascript
console.log(singleValidation({
  id    : "id_input",
  title : "input",
  type  : [ "T" ],
  value : 345,
}),"EN")
```

<img src ="https://img.shields.io/badge/Error-red">

```
>>> {
  id      : "id_input"
  status  : false
  message : "The data input is not valid, please enter only letters"
}
```
```javascript
console.log(singleValidation({
  id: "id_input",
  title: "input",
  type: "R",
  value: "", // null OR undefined
}),"EN")
```

<img src ="https://img.shields.io/badge/Error-red">

```
>>> {
  id      : "id_input"
  status  : false
  message : "The data input is required"
}
```
### Example function _multiValidation_

```javascript
import { multiValidation } from "validations-forms";
```
#### Datas

```javascript
const DATA = [
   {
    id    : "id_input_one",
    title : "input_one",
    type  : ["R","T"],
    value : "texto",
  },
  {
    id    : "id_input_two",
    title : "input_two",
    type  : "N",
    value : 2323
  }
  { ... }

];

const DATA_ERRORS = [
  {
    id    : "id_input_one",
    title : "input_one",
    type  : ["R","T"],
    value : 3434,
  },
  {
    id    : "id_input_two",
    title : "input_two",
    type  : "T",
    value : 12345,
  },
  {
    id    : "id_input_three",
    title : "input_three",
    type  : ["R"],
    value : null,
  },
  {
    id    : "id_input_four",
    title : "input_four",
    type  : ["TN"],
    value : "123abcABC..*",
  },
  { ... }

];
```


```javascript
console.log(multiValidation(DATA,"EN"))
```

<img src ="https://img.shields.io/badge/successful-success">

``` >>> { status: true } ```

```javascript
console.log(multiValidation(DATA_ERRORS,"EN"))
```
<img src ="https://img.shields.io/badge/Error-red">

```
>>> {
  id      : "id_input_one"
  status  : false
  message : "The data input_one is not valid, please enter only letters"
}
```

### Example function multiValidationErrors

```javascript
import { multiValidationErrors } from "validations-forms";
```
#### Datas

```javascript
const DATA = [
   {
    id    : "id_input_one",
    title : "input_one",
    type  : ["R","T"],
    value : "texto",
  },
  {
    id    : "id_input_two",
    title : "input_two",
    type  : "N",
    value : 2323
  }
  { ... }

];

const DATA_ERRORS = [
  {
    id    : "id_input_one",
    title : "input_one",
    type  : ["R","T"],
    value : 3434,
  },
  {
    id    : "id_input_two",
    title : "input_two",
    type  : "T",
    value : 12345,
  },
  {
    id    : "id_input_three",
    title : "input_three",
    type  : ["R"],
    value : null,
  },
  {
    id    : "id_input_four",
    title : "input_four",
    type  : ["TN"],
    value : "123abcABC..*",
  },
  { ... }

];
```


```javascript
console.log(multiValidationErrors(DATA,"EN"))
```

<img src ="https://img.shields.io/badge/successful-success">

``` >>> { status: true } ```

```javascript
console.log(multiValidationErrors(DATA_ERRORS,"EN"))
```
<img src ="https://img.shields.io/badge/Error-red">

```
>>> {
  status : false,
  errors : [
    {
      id      : "id_input_one",
      status  : false
      message : "custom message",
    },
    {
      id      : "id_input_two",
      status  : false
      message : "The data input_two is not valid, please enter only letters",
    },
    {
      id      : "id_input_three",
      status  : false
      message : "The data input_three is required.",
    },
    {
      id      : "id_input_four",
      status  : false
      message : "The data input_four is not valid, please enter only letters and numbers",
    }
  ]
}
```

### Example function type language

**EN**
```javascript
console.log(singleValidation({
  id    : "id_input",
  title : "input",
  type  : [ "T" ],
  value : 345,
}),"EN") // <=== parameter language
```

<img src ="https://img.shields.io/badge/Error-red">

```
>>> {
  id      : "id_input"
  status  : false
  message : "The data input is not valid, please enter only letters"
}
```
**ES**
```javascript
console.log(singleValidation({
  id    : "id_input",
  title : "input",
  type  : [ "T" ],
  value : 345,
}),"ES") // <=== parameter language

 OR

console.log(singleValidation({
  id    : "id_input",
  title : "input",
  type  : [ "T" ],
  value : 345,
}))
```
### Example message custom

```javascript
console.log(singleValidation({
  id      : "id_input",
  title   : "input",
  type    : [ "T" ],
  message : "message custom example"
  value   : 345,
}),"EN") // <=== parameter language
```

<img src ="https://img.shields.io/badge/Error-red">

```
>>> {
  id      : "id_input"
  status  : false
  message : "message custom example"
}
```

<p align="right"><a href="#top">volver arriba 🔼</a></p>

## **Contributors**

<a href="https://github.com/ferch01992">
  <img src="https://avatars.githubusercontent.com/u/20364582?v=4" style="border-radius: 50% !important;" min-width="50px" max-width="50px" width="50px" height="50px"/>
</a>

<p align="right"><a href="#top">volver arriba 🔼</a></p>

## **License MIT**

```
MIT License

Copyright (c) 2021 Ferch01992

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

```

<p align="right"><a href="#top">volver arriba 🔼</a></p>
