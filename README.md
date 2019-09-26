# AutoForm for Google App Script

[Script source code](https://script.google.com/d/1j2sCmpdtfmScueHcaxm2LtOk4ZJir_q5WEtGCYRjjYWQCpZZfD-GBwhr/edit?usp=sharing)
File > Make a copy, then modify and publish one yourself.

If you work on other platforms that uses JS, you can copy the whole autoForm function and it will just work.

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
        age: {type: Number},
        dob: {type: Date, label: 'Date of birth'}
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
`id` : (required) Name of the form to be created. Ex: 'myForm'

`action` : (required) A function which shall be called after form submission with a callback. Ex: `function(res){return res}`

`schema` : (required) A schema-like object that shares similiarity to meteor autoform library as explained in below section.

### Schema rules
A schema-object is an object of key:value pairs where the key represents the fieldName and the value represents the schema.
The list below shall demonstrate various examples of schema you can define:

    name: {type: String},
    age: {type: Number},
    birth: {type: Date},
    address: {type: String, label: 'Home Adress'},
    mobile: {type: Number, optional: true},
    gender: {type: String, autoform: {type: 'select', options: function(){return [
      {value: 'male', label: 'Male'}, {value: 'female', label: 'Female'}
    ]}}},
    occupation: {type: Number, optional: true, autoform: {
      type: 'select', options: function(name, doc){
        return ['student', 'freelance', 'professional'].map(function(val, index){
          return {value: index, label: val}
        })
      }
    }},
    work_experience: {type: Object},
    'work_experience.company': {type: String, label: 'Company Name'},
    'work_experience.years': {type: Number, label: 'Years of experience'},
    skills: {type: Array},
    'skills.$': {type: String},
    education: {type: Array},
    'education.$': {type: Object},
    'education.$.name': {type: String, label: 'School/University Name'},
    'education.$.date': {type: Date, label: 'Graduation date'},
    excluded: {type: String, exclude: true},
    just_info: {
      type: String,
      autoform: {type: 'hidden'},
      autoValue: function(name, doc){return name}
    },
    hidden_field: {
      type: String,
      autoform: {type: 'hidden'},
      autoValue: function(){return 'something'}
    }

## Further Dev

## Known Issues
