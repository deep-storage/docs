# The 'deep' Higher Order Component

Wraps a react component, adding subscriptions to state changes and an optimised implementation of shouldComponentUpdate e.g.:

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

const storage = new DeepStorage({
    timer: 0
});

function resetTimer() {
    storage.setIn('timer')(0);
}

setInterval(function tick() {
    storage.updateIn('timer')(prev => prev + 1);
}, 1000);

const DeepTimerView = deep(storage, {timer: ['timer']})(TimerView);

ReactDOM.render((
    <DeepTimerView resetTimer={resetTimer}/>
), document.body);
```



