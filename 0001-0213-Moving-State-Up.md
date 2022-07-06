<!---
Current Directory : /in28Minutes/git/full-stack-with-react-and-spring-boot
-->

## Complete Code Example




### /frontend/todo-app/src/components/counter/Counter.css

```css
button {
    background-color: green;
    font-size : 16px;
    padding : 15px 30px;
    color : white;
    width : 100px;
}

.count {
    font-size : 50px;
    padding : 15px 30px;
}
```
---

### /frontend/todo-app/src/components/counter/Counter.jsx

```
import React, {Component} from 'react'
import PropTypes from 'prop-types'
import './Counter.css'

class Counter extends Component {

    constructor() {
        super(); //Error 1
        this.state = {
            counter : 0
        }
        this.increment = this.increment.bind(this);
    }
  
    render() {
        return (
          <div className="counter">
             <CounterButton by={1} incrementMethod={this.increment}/>
             <CounterButton by={5} incrementMethod={this.increment}/>
             <CounterButton by={10} incrementMethod={this.increment}/>
             <span className="count">{this.state.counter}</span> 
          </div>
        );
    }    

    increment(by) { 
        //console.log(`increment from child - ${by}`)
        this.setState({
             counter: this.state.counter + by
        });
    }
}

class CounterButton extends Component {
  //Define the initial state in a constructor
  //state => counter 0
  constructor() {
      super(); //Error 1
      this.state = {
          counter : 0
      }
      this.increment = this.increment.bind(this);
  }
  
  render()  {
  //render = () =>  {
    //const style = {fontSize : "50px", padding : "15px 30px"};
    return (
        <div className="counter">
            <button onClick={this.increment} >+{this.props.by}</button>
            {/*<span className="count" 
            >{this.state.counter}</span>*/}
        </div>
    )
  }
  
  increment() { //Update state - counter++
    //console.log('increment');
    //this.state.counter++; //Bad Practice
    this.setState({
        counter: this.state.counter + this.props.by
    });
    
    this.props.incrementMethod(this.props.by);
  }
}

CounterButton.defaultProps = {
    by : 1
}

CounterButton.propTypes = {
    by : PropTypes.number
}

export default Counter
```
---


### /frontend/todo-app/src/App.js

```js
import React, { Component } from 'react';
import FirstComponent from './components/learning-examples/FirstComponent'
import SecondComponent from './components/learning-examples/SecondComponent'
import ThirdComponent from './components/learning-examples/ThirdComponent'
import Counter from './components/counter/Counter'
import './App.css';

class App extends Component {
  render() {
    return (
      <div className="App">
         <Counter/>
      </div>
    );
  }
}

class LearningComponents extends Component {
  render() {
    return (
      <div className="LearningComponents">
         My Hello World
         <FirstComponent></FirstComponent>
         <SecondComponent></SecondComponent>
         <ThirdComponent></ThirdComponent>
      </div>
    );
  }
}

export default App;
```
---
