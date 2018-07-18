# Deep Storage React

deep-storage-react lets you connect React components to deep storage state. It also includes form handling built on top of deep storage.

The following code creates a link that is attached to deep storage. When a user clicks the link, the date is updated.

```
import * as React from 'react';
import { connect } from 'deep-storage-react';
import { deepStorage } from 'deep-storage';

const storage = deepStorage({
    date: new Date()
});

const DateView = props => (
    <a onClick={props.onClick}>{props.date.toISOString()}</a>
);

const DeepDateView = connect(
    {date: storage.deep('date')},
    {
        onClick: () => storage.updateIn('date')(new Date());
    }
)(DateView);

ReactDOM.render((
    <DeepDateView/>
), document.body);
```

## connect

_connect\(deepProps, ownProps?\)\(Component\)_

The connect method takes in 2 arguments. The first is a set of properties to pull out of a deep storage store and connect to the component. The second is a regular set of props to pass into the component.

The values in deepProps can either be a deep storage store or a 'factory' that returns a deep storage store. In the second case the object must have a property called 'storage'. This is useful for creating 'services' i.e. objects that have state backed by deep storage but have additional functionality attached. The service will get passed into the Component as a prop and the connect method will subscribe to any changes in the internal state.

```
class Authentication {
    constructor(storage) {
        this.storage = storage;
    }
    get isLoggedIn() { return !!this.storage.state.token; }
    logIn = async(username, password) => {
        // log in
        if(successful) {
            this.state.setIn('token', token);    
        } else {
            return false;
        }
    }
}

class App extends Component {
   render() {
       if(this.props.authentication.isLoggedIn()) {
           // render app
       } else {
           return (
              <div>
                  ... form fields
                  <button onClick={this.props.authentication.logIn}
              </div>
           )
       }
   }
}

const DeepApp = connect(
    {authentication},
)(App);
```

Deep storage has a helper property called 'props' that you can use to connect all of the state from storage

```
const storage = deepStorage({
    date: new Date()
});

const DateView = props => (
    <a>{props.date}</a>
);

const DeepDateView = connect(
    storage.props
)(DateView);
```



