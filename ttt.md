## Go through the funcs
---

### Square
---
- instantiates a value (x/o)
- returns a button with onSquareClick as click  func and value as rendered text
	- `onSquareClick` is just a placeholder name for a later derived function

### Board
---
- two `useState` vars
	- `xIsNext` - boolean -- is the next player an X? calculates value for square
	- `squares` - the `Array` of squares - instantiated as 9 empty array cells
- `isBoardFull` - bool for if every square value is not `null`

```jsx
function handleClick(i){
...
}
```
This function first checks if the  square already has a value
`if (squares [i] ...` and then calculates if there is a winner
`calculateWinner(squares)` if either of these are true with the logical `||` or operator
It returns nothing and quits
It then creates a full copy of the array 
	`const nextSquares = squares.slice();`
to then add either `X` or `O` depending on the `xIsNext` variable
Then sets `squares` to this new array `setSquares(nextSquares)`
then changes `setXIsNext(!xIsNext);`

