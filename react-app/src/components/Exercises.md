## Exercise: Building a Button component

### App.tsx

```
import Button from "./components/Button";
function App() {
  return (
    <div>
      <Button color="primary" onClick={() => console.log("Clicked")}>
        My button
      </Button>
    </div>
  );
}

export default App;
```

### Button.tsx

```
import React from "react";
interface Props {
  children: string;
  color?: string; //optional property of this props
  onClick: () => void;
}
const Button = ({ children, color, onClick }: Props) => {
  return (
    <button className={"btn btn-" + color} onClick={onClick}>
      {children}
    </button>
  );
};

export default Button;
```
