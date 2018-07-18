# Introduction to Deep Storage

Deep Storage provides observable state for reactive applications in JavaScript.

Key features of Deep Storage:

* Simple to use observable state management
* Optimised for use with React
* No global state
* Simple way to manage shared state with or without a fully fledged flux pattern

## Examples

* [Real World Example](https://github.com/deep-storage/examples/tree/master/react-saas)
* [TodoMVC](https://github.com/deep-storage/examples/tree/master/react-todomvc)

## Installation

```
yarn add deep-storage

# for react bindings
yarn install deep-storage-react
```

## The gist of Deep Storage

### 1. Create a new Deep Storage instance and initialise its state

Initialise DeepStorage with a regular JavaScript object

```
import { deepStorage } from 'deep-storage';

const storage = deepStorage({
    timer: 0
});
```

### 2. Create a view that responds to changes in state

The deep function wraps a regular React Component, passing in state from storage via props. In this case, it is taking the 'timer' property from storage and attaching it to a 'timer' prop.

```
import {connect} from 'deep-storage-react';

class TimerView extends React.Component {
    render() {
        return (
            <button onClick={this.onReset.bind(this)}>
                Seconds passed: {this.props.timer}
            </button>
        );
    }
    onReset () {
        this.props.resetTimer();
    }
};

const DeepTimerView = connect({timer: storage.deep('timer')})(TimerView);

ReactDOM.render((
    <DeepTimerView resetTimer={resetTimer}/>
), document.body);
```

### 3. Modify the State

All state changes go through storage so that subscribers are notified.

```
function resetTimer() {
    storage.deep('timer').set(0);
}

setInterval(function tick() {
    storage.deep('timer').update(prev => prev + 1);
}, 1000);
```



