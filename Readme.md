# backbone.js FormBuilder

## Project Goals

**FormBuilder** is a *backbone.js* extension that aims to make easier the task of rendering forms in a consistent way, as well as providing feedback to the user when necessary. Its main goals are:

* **Extensibility**: Will provide field builders for the most used ones, but can be extensible easily to support more of them.
* **Nice interface**: The Form Builder API should be nice to work with. Not too smart, not too dumb; should allow to change any aspect without much hassle.
* **Model bindings**: Will attach to the model, pre-populating its values when necessary.
* **Validation bindings**: Will bind to a model validation, rendering error messages in each field.
    * **Client side**: Will support the most common validations on the client side in order to return feedback to the user as fast as possible.
    * **Backend**: Will try to retrieve validations from the backend when provided in a standard format.

## Syntax

````javascript

form = new Backbone.FormBuilder({

  // The model instance to be bound to
  model:    model,

  // The success function that will be fired when the model can be saved
  success:  function(){
    Backbone.History.navigate('/models/' + this.model.get('id'));
  },

  // (optional): A function to be called if the model save fails
  error: function(){}
);

// This will attach a single text field to the form bound to the 'email'
// property. Will validate presence.
form.addField('email', {type: 'string', validates: 'presence'});

// This will attach a single password field to the form bound to the 'password'
// property. Will use a custom function to render the label value. Will
// validate presence.
form.addField('password', {
  type: 'password', validates: 'presence',
  label: function(){ I18n.t('user.password') }
});

// This will create a single text field without any validations.
form.addField('biography', {type: 'text'});

````

## Development

Backbone FormBuilder is still purely an **IDEA**. This means that still isn't developed at all.

## Contributions

Appreciated :D
