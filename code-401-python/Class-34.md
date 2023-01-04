# __Context API__

### __What is global state with React?__

### Role of the global state

In React, originally, the state is held and modified within the same React component. In most applications, different components may need to access and update the same state. This is achieved by introducing the global states in your app. The main purpose of the global state is to share a state among multiple components.

There are three ways this communication can happen:

1. With a child component
2. With a parent component
3. With a sibling component

---

### State traveling down
State traveling down through the hierarchy is best managed using the mutable state at the highest level to determine immutable properties that define the lower-level components. Even when these properties are updated, the lower-level component is updated rather than fully recreated.

As a result, the state tracked by the lower-level component will persist unless the component disappears (as could happen with conditional rendering). The following is how the change in a higher-level component is reflected in the lower-level components.

> React determines what has changed and updates only that part.

    import React, {Component} from 'react'; 
    import './App.css';

    class Clock extends Component { 
        constructor(props) {
            super(props);
            this.state = {offset: this.props.localOffset}; 
            this.alterOffset = this.alterOffset.bind(this);
        }
        alterOffset(event) { 
            event.preventDefault();
            if (event.target.name === 'plus1') {
                this.setState({offset: this.state.offset + 1}); 
                } 
            else if (event.target.name === 'minus1') {
                this.setState({offset: this.state.offset - 1}); 
                }
        }
        render() { 
            return <div>
                        <h2>The local time</h2>
                        <p>The time is now { this.props.universalTime +
                            this.state.offset }</p>
                        <p>for local time offset { this.state.offset }</p> 
                        <button onClick={ this.alterOffset }
                            name='minus1'>-1</button> 
                        <button onClick={ this.alterOffset }
                            name='plus1'>+1</button> 
                    </div>;
        }
    }
    class App extends Component { 
        constructor(props) {
            super(props);
            this.state = {time: 0};
            setInterval( () => this.setState({time: this.state.time + 1}),
                1000); 
        }
        render() { 
            return (
                <div>
                    <h1>I like clocks</h1>
                    <Clock universalTime={ this.state.time} localOffset={ 5 } /> 
                    <Clock universalTime={ this.state.time} localOffset={ 100 }
                        />
                    <Clock universalTime={ this.state.time} localOffset={ 200 }
                        /> 
                </div>
            );
        }
    }
    export default App;

---

### State traveling up

You need to pass down a callback function for a higher-level component to know the state. In the following version, we add a global state to count the total number of button presses and update this state with a callback function called pushed, which is called whenever a button is pushed.

Notice that the pushed App method is passed as a property (prop) to the Clock component, accessed as this.prop.callback. A new final line, number 18, in alterOffset calls it with this.props.callback().


    import React, {Component} from 'react'; 
    import './App.css';

    class Clock extends Component { 
        constructor(props) {
            super(props);
            this.state = {offset: this.props.localOffset}; 
            this.alterOffset = this.alterOffset.bind(this);
        }
        alterOffset(event) { 
            event.preventDefault();
            if (event.target.name === 'plus1') {
                this.setState({offset: this.state.offset + 1}); 
                } 
            else if (event.target.name === 'minus1') {
                this.setState({offset: this.state.offset - 1}); 
                }
            this.props.callback();
        }
        render() { 
            return <div>
                        <h2>The local time</h2>
                        <p>The time is now { this.props.universalTime +
                            this.state.offset }</p>
                        <p>for local time offset { this.state.offset }</p> 
                        <button onClick={ this.alterOffset }
                            name='minus1'>-1</button> 
                        <button onClick={ this.alterOffset }
                            name='plus1'>+1</button> 
                    </div>;
        }
    }
    class App extends Component { 
        constructor(props) {
            super(props);
            this.state = {time: 0, numPresses: 0};
            this.pushed = this.pushed.bind(this)
            setInterval( () => this.setState({time: this.state.time + 1}),
                1000); 
        }

        pushed() { this.setState({numPresses:this.state.numPresses+1}); }

        render() { 
            return (
                <div>
                    <h1>I like clocks</h1>
                    <Clock universalTime={ this.state.time} localOffset={ 5 } 
                        callback = {this.pushed}/> 
                    <Clock universalTime={ this.state.time} localOffset={ 100 }
                        callback = {this.pushed}/>
                    <Clock universalTime={ this.state.time} localOffset={ 200 }
                        callback = {this.pushed}/>
                    <p>{this.state.numPresses} button presses</p> 
                </div>
            );
        }
    }
    export default App;


### State traveling sideways
Various sub-components need to communicate updates between them. This can be achieved by passing state, using callback, up to a common parent component, and then passing it back down.

---

# Context
In a typical React application, data is passed top-down (parent to child) via props, but such usage can be cumbersome for certain types of props (e.g. locale preference, UI theme) that are required by many components within an application. Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.