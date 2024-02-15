## Using of Fragments

```
import { Fragment } from "react";
function ListGroup() {
  const items = ["One", "Two", "Three", "Four", "Five"];
  return (
    <>
      <h1>List</h1>
      <ul className="list-group">
        {items.map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ul>
    </>
  );
}
export default ListGroup;
```

## Conditional Rendering

```
import { Fragment } from "react";
function ListGroup() {
  let items = ["One", "Two", "Three", "Four", "Five"];
  items = [];

  if (items.length === 0)
    return (
      <>
        <h1>List</h1>
        <p>No item found</p>
      </>
    );

  return (
    <>
      <h1>List</h1>
      <ul className="list-group">
        {items.map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ul>
    </>
  );
}
export default ListGroup;
```

Another method

```
import { Fragment } from "react";
function ListGroup() {
  let items = ["One", "Two", "Three", "Four", "Five"];
  items = [];

  return (
    <>
      <h1>List</h1>
      {items.length === 0 ? <p>No item found</p> : null}
      <ul className="list-group">
        {items.map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ul>
    </>
  );
}
export default ListGroup;
```

By using function

```
import { Fragment } from "react";
function ListGroup() {
  let items = ["One", "Two", "Three", "Four", "Five"];
  items = [];

  const getMessage = () => {
    return items.length === 0 ? <p>No item found</p> : null;
  };

  return (
    <>
      <h1>List</h1>
      {getMessage()}
      <ul className="list-group">
        {items.map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ul>
    </>
  );
}
export default ListGroup;
```

More precise method

```
import { Fragment } from "react";
function ListGroup() {
  let items = ["One", "Two", "Three", "Four", "Five"];
  items = [];

  return (
    <>
      <h1>List</h1>
      {items.length === 0 && <p>No item found</p>}
      <ul className="list-group">
        {items.map((item) => (
          <li key={item}>{item}</li>
        ))}
      </ul>
    </>
  );
}
export default ListGroup;
```

## Handling Events

To handle click events in a component

```
import { Fragment } from "react";
function ListGroup() {
  let items = ["One", "Two", "Three", "Four", "Five"];

  return (
    <>
      <h1>List</h1>
      {items.length === 0 && <p>No item found</p>}
      <ul className="list-group">
        {items.map((item, index) => (
          <li
            className="list-group-item"
            key={item}
            onClick={() => console.log(item, index)}
          >
            {item}
          </li>
        ))}
      </ul>
    </>
  );
}
export default ListGroup;
```

To handle typescript error: "Parameter 'event' implicitly has an 'any' type."

It occurs when typrscript compiler dowsn't know the type of the parameter.

It can be solved by type annotation

```
import { Fragment } from "react";
import { MouseEvent } from "react";

function ListGroup() {
  let items = ["One", "Two", "Three", "Four", "Five"];

  // Event handler - To handle click event
  const handleClick = (event: MouseEvent) => console.log(event);

  return (
    <>
      <h1>List</h1>
      {items.length === 0 && <p>No item found</p>}
      <ul className="list-group">
        {items.map((item, index) => (
          <li
            className="list-group-item"
            key={item}
            onClick={handleClick} // Here, we are just passing the reference instead of calling the function.
          >
            {item}
          </li>
        ))}
      </ul>
    </>
  );
}
export default ListGroup;
```