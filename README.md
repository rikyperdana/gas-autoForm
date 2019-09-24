# AutoForm for Google App Script

[Script source code](https://script.google.com/d/1j2sCmpdtfmScueHcaxm2LtOk4ZJir_q5WEtGCYRjjYWQCpZZfD-GBwhr/edit?usp=sharing)
File > Make a copy, then modify and publish one yourself

## Introduction
AutoForm is a remake of Meteor AutoForm like library that serves similiar purpose of generating a form which follow defined schemas.
You may take this project as a standalone boilerplate or copy some of it's parts to be included in your project or anything you see fit.
This project is composed of functions that returns Mithril virtual DOMs, therefore understanding MithrilJS first is suggested. The `autoForm` function itself only contains of less than 150 lines of code, intededly made simple so you can freely modify this function.

## Usage Example

    m(autoForm({
      id: 'testForm',
      action: console.log,
      schema: {
        name: {type: String},
        age: {type: Number}
      }
    }))
This code will generate a form with `name` field in text and `number` field in number

## Code structure
`Code.gs` : A server-side code which include `lodash`, `doGet`, and `include` function.

`Page.html`: An initial html file that contains cdns (from lodash, mithril, and bulma) and other client-sided scripts.

`Javascript.html`: Contains mithril instance that renders virtual doms for the page.

`autoForm`: Contains autoForm function that take options for generating the form.

## APIs
### Form options
`id` : Name of the form to be created

`action` : A function which shall be called after form submission with a callback. Ex: `function(res){return res}`

`schema` : A schema-like object that shares similiarity to meteor autoform library as explained in below section.

### Schema rules

## Further Dev

## Known Issues
