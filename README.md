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
```
