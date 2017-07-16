# Going Deeper

Deep Storage aims to make it easy to have a single state tree but be able to see localised views of it.

```
const storage = new DeepStorage({
    companies: {
        'ccc1c7b8': {
            id: 'ccc1c7b8',
            name: 'Github'
        }
    },
    employees: {
        '92cfdbe4': {
            id: '92cfdbe4',
            name: 'Bob Barker',
            companyId: 'ccc1c7b8'             
        }
    }
});

const employeesStorage = storage.deep('employees');
const companiesStorage = storage.seep('companies');

const subscription = storage.subscription((path, newState, oldState) => {
    console.log(path, 'updated');
});
subscription.subscribeTo('employees');

// triggers the subscription above
employeeStorage.updateIn('92cfdbe4', name)(name => 'Bob Smith');
```

## Why is this useful?

In a typical React app, components will usually only need to react to part of the state tree. Deep Storage makes it easy to:

* Externalise state
* Only update the components that are affected by the part of the state that has updated
* Only trigger a single state update for a component when state changes
* Services built on top of the state tree only need to depend on the part of the tree they are responsible for





