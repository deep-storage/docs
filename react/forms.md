# Deep Storage Forms

deep-storage-react forms simplify managing form state.

```
// a form that captures a name
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

const storage = deepStorage();

const form = deepForm(storage.deep('form'), new NameValidator(), { name: '' });

const NameForm = props => {
  const name = form.fields.name;
  return (
    <div>
      <input
        type="text"
        name="name"
        value={name.value}
        onChange={form.changeEvent}/>
      {
        name.touched && name.error
        ?
        (<div>{name.error}</div>)
        :
        null
      }
    </div>
  )
}

const DeepNameForm = connect(
   { form }
)(NameForm);
```


