# REACT-little-things-beginners-need-to-know


##### ফাংশনাল কম্পোনেন্টে রিটার্নের পরে ব্র্যাকেট না দিলেও চলে, কিন্তু দেওয়াটা গুড প্র্যাকটিস ।
যেমন, নীচের কোড দুইটাই রান করবে
```javascript
// with parenthesis
function MyApp() {
  return (
    <ul>
      <li>1</li>
      <li>2</li>
      <li>3</li>
    </ul>
  )
}

//without parenthesis
function MyApp() {
  return 
    <ul>
      <li>1</li>
      <li>2</li>
      <li>3</li>
    </ul>
  
}
```
##### রিয়্যাক্ট ডম ডট রেন্ডারে চাইলে আমরা জেএসএক্স-ও লিখতে পারি। 
```javascript
import React from "react"
import ReactDOM from "react-dom"

ReactDOM.render(<h1>Hello World!</h1>, document.getElementById("root"))
```
##### 

```javascript
<h1>Hello {`${firstName} ${lastName}`}!</h1>
//or
<h1>Hello {firstName + " " + lastName}!</h1>
```

##### conditional rendering
```javascript

function App() {
  const date = new Date()
  const hours = date.getHours()
  let timeOfDay
  
  if (hours < 12) {
    timeOfDay = "morning"
  } else if (hours >= 12 && hours < 17) {
    timeOfDay = "afternoon"
  } else {
    timeOfDay = "night"
  }
  
  return (
    <h1>Good {timeOfDay}!</h1>
  )
}

ReactDOM.render(<App />, document.getElementById("root"))
```
##### inline style
```
<h1 style={{color: "#FF8C00", backgroundColor: "#FF2D00"}}>Good {timeOfDay}!</h1>
```
Another way to do this:
```
const styles = {
    color: "#FF8C00", 
    backgroundColor: "#FF2D00",
    fontSize: 200
  }
  
  return (
    <h1 style={styles}>Good {timeOfDay}!</h1>
  )
  ```
  200 is by default an integer and pixel in unit. if we have to use the unit, we need to put it as a string.
  ```
  const styles = {
    color: "#FF8C00", 
    backgroundColor: "#FF2D00",
    fontSize: "200px"
  }
  
  return (
    <h1 style={styles}>Good {timeOfDay}!</h1>
  )
  ```
  ##### dynamic styling
  ```
  function App() {
  const date = new Date()
  const hours = date.getHours()
  let timeOfDay
  const styles = {
    fontSize: 30
  }
  
  if (hours < 12) {
    timeOfDay = "morning"
    styles.color = "#04756F"
  } else if (hours >= 12 && hours < 17) {
    timeOfDay = "afternoon"
    styles.color = "#2E0927"
  } else {
    timeOfDay = "night"
    styles.color = "#D90000"
  }
  
  return (
    <h1 style={styles}>Good {timeOfDay}!</h1>
  )
}
```



##### how to pass props
```
 <ContactCard 
                name="Mr. Whiskerson" 
                imgUrl="http://placekitten.com/300/200" 
                phone="(212) 555-1234" 
                email="mr.whiskaz@catnap.meow"
 />
 //or
 contact={{name: "Mr. Whiskerson", imgUrl: "http://placekitten.com/300/200", phone: "(212) 555-1234", email: "mr.whiskaz@catnap.meow"}}
 //notice the double curly braces here ,one for object,one for jsx.
 ```
 

##### Displaying on condition
```javascript
<h3 style={{display: props.question ? "block" : "none"}}>Question: {props.question}</h3>
//or
 <h3 style={{display: !props.question && "none"}}>Question: {props.question}</h3>
 <h3 style={{color: !props.question && "#888888"}}>Answer: {props.punchLine}</h3>
```
##### saving the data
```
 const jokesData = [
    {
        id: 1,
        punchLine: "It’s hard to explain puns to kleptomaniacs because they always take things literally."
    },
    {
        id: 2,
        question: "What's the best thing about Switzerland?",
        punchLine: "I don't know, but the flag is a big plus!"
    },
    {
        id: 3,
        question: "Did you hear about the mathematician who's afraid of negative numbers?",
        punchLine: "He'll stop at nothing to avoid them!"
    },
    {
        id: 4,
        question: "Hear about the new restaurant called Karma?",
        punchLine: "There’s no menu: You get what you deserve."
    },
    {
        id: 5,
        question: "Did you hear about the actor who fell through the floorboards?",
        punchLine: "He was just going through a stage."
    },
    {
        id: 6,
        question: "Did you hear about the claustrophobic astronaut?",
        punchLine: "He just needed a little space."
    }
]

export default jokesData
```
and this is how to extract them:
```
 const jokeComponents = jokesData.map(joke => <Joke question={joke.question} punchLine={joke.punchLine} />)
 //dont forget to add key property while using map:
 const jokeComponents = jokesData.map(joke => <Joke key={joke.id} question={joke.question} punchLine={joke.punchLine} />)
```    

##### how to check a check box
```
 <input type="checkbox" checked={props.item.completed}/>
```
##### class based component
```
class App extends React.Component {
    render() {
    //any type of display logic that's going to happen
        return (
            <div>
                <h1>Code goes here</h1>
            </div>
        )
    }
}
// like this:
class Greeting extends Component {
    render() {
        const date = new Date()
        const hours = date.getHours()
        let timeOfDay
        
        if (hours < 12) {
            timeOfDay = "morning"
        } else if (hours >= 12 && hours < 17) {
            timeOfDay = "afternoon"
        } else {
            timeOfDay = "night"
        }
        return (
            <h1>Good {timeOfDay} to you, sir or madam!</h1>
        )
    }
}
```
##### how to use function in a class
```
class App extends React.Component {
    
    yourMethodHere() {
        
    }
    
    render() {
        const style = this.yourMethodHere()
        return (
            <div>
                <h1>Code goes here</h1>
            </div>
        )
    }
}
```
##### How to use props
```

// function App(props) {
//     return (
//         <div>
//             <h1>{props.whatever}</h1>
//         </div>
//     )
// }

class App extends React.Component {
    
    yourMethodHere() {
        
    }
    
    render() {
        return (
            <div>
                <h1>{this.props.whatever}</h1>
            </div>
        )
    }
}

export default App
```
##### i can't change props, this is why state comes into play

##### state in class based component
```
class App extends React.Component {
    constructor() {
        super()
        this.state = {
            answer: "Yes"
        }
    }
    
    render() {
        return (
            <div>
                <h1>Is state important to know? </h1>
            </div>
        )
    }
}

export default App
```
##### how to send props from parent component to child component/s
```
class App extends React.Component {
    constructor() {
        super()
        this.state = {
            answer: "Yes"
        }
    }
    
    render() {
        return (
            <div>
                <h1>Is state important to know? {this.state.answer}</h1>
                <ChildComponent answer={this.state.answer}/>
            </div>
        )
    }
}

export default App
```
স্টেইট একবার চেইঞ্জ করা হলে সব চাইল্ড কমোনেন্টেও সেটার রিফ্লেকশন হয়,সো, আমাদের কে আর ম্যানুয়ালি নতুন করে প্রপ্স চেইঞ্জ করে পাঠানো লাগবে না 


##### কন্ডিশনাল রেন্ডারিং 
```
class App extends React.Component {
    constructor() {
        super()
        this.state = {
            isLoggedIn: false
        }
    }
    
    render() {
        let wordDisplay
        if (this.state.isLoggedIn) {
            wordDisplay = "in"
        } else {
            wordDisplay = "out"
        }
        return (
            <div>
                <h1>You are currently logged {wordDisplay}</h1>
            </div>
        )
    }
}
```
```
class App extends React.Component {
    constructor() {
        super()
        this.state = {
            count: 0
        }
        this.handleClick = this.handleClick.bind(this)
    }
    
    handleClick() {
    //this.setState({}) if we directly set it
        this.setState(prevState => {
            return {
                count: prevState.count + 1
            }
        })
    }
    
    render() {
        return (
            <div>
                <h1>{this.state.count}</h1>
                <button onClick={this.handleClick}>Change!</button>
                <ChildComponent count={this.state.count}/>
            </div>
        )
    }
}

```




```

function TodoItem(props) {
    return (
        <div className="todo-item">
            <input 
                type="checkbox" 
                checked={props.item.completed} 
                onChange={() => props.handleChange(props.item.id)}
            />
            <p>{props.item.text}</p>
        </div>
    )
}

export default TodoItem
//

class App extends React.Component {
    constructor() {
        super()
        this.state = {
            todos: todosData
        }
        this.handleChange = this.handleChange.bind(this)
    }
    
    handleChange(id) {
        this.setState(prevState => {
            const updatedTodos = prevState.todos.map(todo => {
               if (todo.id === id) {
                    return {
                        ...todo,
                        completed: !todo.completed
                    }
                }
            return {
                todos: updatedTodos
            }
        })
    }
    
    render() {
        const todoItems = this.state.todos.map(item => <TodoItem key={item.id} item={item} handleChange={this.handleChange}/>)
        
        return (
            <div className="todo-list">
                {todoItems}
            </div>
        )    
    }
}
```
