# Deep Storage Forms

deep-storage-react forms simplify managing form state.

## Getting started

### Installation

Install deep storage and deep storage react

```
yarn add deep-storage deep-storage-react
```

## Create a validator

A validator is a class that has a validate method that receives an instance of the form being validated as well as the field that has changed. It must return an object with optional 'errors' and 'globalErrors' fields.

The errors field is an object who's keys are the names of the fields being validated and whose values are the error message associated with those keys e.g. { name: 'Name is required' }

The globalErrors is an array of strings that can be used to highlight errors that aren't related to a specific field.

```
// validates the name field on the form
class NameValidator {
  validate(form, field) {
    const data = form.data();
    const errors = {};
    if(!data.name || data.name.trim().length === 0) {
      errors.name = 'Name should not be empty'
    }
    return { errors };
  }
}
```

### Create a deep form

The deepForm method from 'deep-storage-react' is used to construct deep forms. It takes in a deep storage, a validator and an initial state of the form.

```
const storage = deepStorage();

const form = deepForm(storage.deep('form'), new NameValidator(), { name: '' });
```

### Create a react component that uses the form

deep-storage-react doesn't come with any pre-defined controls as they tend to be project specific. In order to connect a control to your deep form, you'll need to attach the following attributes:

#### onChange={form.changeEvent}

Sends change events back to the form to update the value of a field

#### onBlur={form.blurEvent}

Sends blur events back to the form so that it can track whether a field has been 'touched'. This is useful when you only want to show errors when a user leaves a field

#### value={form.fields\[fieldName\].value}

Connects the value of the form field to the value of the control. Note: if you don't initialise the value of the form, the field may not exist.

The following is an example of a connected input

```
// a form with a 'name' field
const NameForm = props => {
  const name = form.fields.name;
  return (
    <div>
      <input
        type="text"
        name="name"
        value={name.value}
        onChange={form.changeEvent}
        onBlur={form.blurEvent}/>
      {
        // only show an error on a field that has been touched and has an error
        name.touched && name.error
        ?
        (<div>{name.error}</div>)
        :
        null
      }
    </div>
  )
}

// connect the form to deep storage
const DeepNameForm = connect(
   { form }
)(NameForm);
```



