## Exercise 1: Building a Button component

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

## Exercise 2: Showing an Alert

### App.tsx

```
import Button from "./components/Button";
import Alert from "./components/Alert";
import { useState } from "react";
function App() {
  const [alertVisible, setalertvisibile] = useState(false);
  return (
    <div>
      {alertVisible && (
        <Alert onClose={() => setalertvisibile(false)}>My Alert</Alert>
      )}
      <Button color="primary" onClick={() => setalertvisibile(true)}>
        My button
      </Button>
    </div>
  );
}

export default App;
```

### Alert.tsx

```
import { ReactNode } from "react";

interface Props {
  children: ReactNode;
  onClose: () => void;
}
const Alert = ({ children, onClose }: Props) => {
  return (
    <div className="alert alert-primary alert-dismissible">
      {children}
      <button
        type="button"
        className="btn-close"
        onClick={onClose}
        data-bs-dismiss="alert"
        aria-label="Close"
      ></button>
    </div>
  );
};

export default Alert;
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
