# REACT-little-things-beginners-need-to-know


##### ফাংশনাল কম্পোনেন্টে রিটার্নের পরে ব্র্যাকেট না দিল্ব চলে, কিন্তু দেওয়াটা গুড প্র্যাকটিস ।
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
