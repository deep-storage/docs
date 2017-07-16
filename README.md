# Introduction to Deep Storage

Deep Storage provides observable state for reactive applications in JavaScript.

Key features of Deep Storage:

* Simple to use observable state management
* Optimised for use with React
* No global state

## The gist of Deep Storage

### 1. Create a new Deep Storage instance and initialise its state

Initialise DeepStorage with a regular JavaScript object

```
const storage = new DeepStorage({
    timer: 0
});
```

### 2. Create a view that responds to changes in state

The deep function wraps a regular React Component, passing in state from storage via props. In this case, it is taking the 'timer' property from storage and attaching it to a 'timer' prop. 

```
import {deep} from 'deep-storage/react';

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

const DeepTimerView = deep(storage, {timer: ['timer']})(TimerView);

ReactDOM.render((
    <DeepTimerView resetTimer={resetTimer}/>
), document.body);
```

### 3. Modify the State

All state changes go through storage so that subscribers are notified.

```
function resetTimer() {
    storage.setIn('timer')(0);
}

setInterval(function tick() {
    storage.updateIn('timer')(prev => prev + 1);
}, 1000);
```



