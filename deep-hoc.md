# React connect

connect_: \(storageProps, regularProps, otherStorages?\) =&gt; \(component\) =&gt; React.CompentType;_

Connect deep storage to a React component

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



