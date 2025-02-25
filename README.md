
Here is the `Form.css` code to style your form component:

```css
.form-container {
  flex: 1;
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

textarea {
  width: 100%;
  height: 60px;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 5px;
  resize: none;
  font-size: 16px;
}

select {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 16px;
  background-color: white;
  cursor: pointer;
}

select[multiple] {
  height: 100px;
}

.buttons {
  display: flex;
  gap: 10px;
  margin-top: 10px;
}

button {
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  background-color: #007bff;
  color: white;
  font-size: 16px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

button:last-child {
  background-color: #dc3545;
}

button:last-child:hover {
  background-color: #a71d2a;
}
```

### **Explanation:**
- **Text areas** are styled for better readability.
- **Select inputs** have a consistent design, and the multi-select has a larger height.
- **Buttons** have hover effects and colors:
  - Blue for "Compare"
  - Red for "Refresh"

Would you like any specific styling changes?








Here’s a structured React project for your requirements. The project will have the following components:  

- `App.js`: The main component  
- `Navbar.js`: The sidebar navigation  
- `Form.js`: The form with text areas, a select dropdown, a multi-select dropdown, and buttons  
- `App.css`: Styles  

---

### **Project Structure**
```
/project-folder
  /src
    /components
      Navbar.js
      Form.js
    App.js
    App.css
    index.js
  package.json
```

---

### **1. Navbar.js**  
This component creates a sidebar with three categories, each containing three links.

```jsx
import React from "react";
import "./Navbar.css";

const Navbar = () => {
  return (
    <div className="sidebar">
      <h2>Categories</h2>
      <ul>
        <li>Category 1
          <ul>
            <li><a href="#">Link 1</a></li>
            <li><a href="#">Link 2</a></li>
            <li><a href="#">Link 3</a></li>
          </ul>
        </li>
        <li>Category 2
          <ul>
            <li><a href="#">Link 1</a></li>
            <li><a href="#">Link 2</a></li>
            <li><a href="#">Link 3</a></li>
          </ul>
        </li>
        <li>Category 3
          <ul>
            <li><a href="#">Link 1</a></li>
            <li><a href="#">Link 2</a></li>
            <li><a href="#">Link 3</a></li>
          </ul>
        </li>
      </ul>
    </div>
  );
};

export default Navbar;
```

---

### **2. Form.js**  
This component contains four text areas, a select dropdown, a multi-select dropdown, a compare button, and a refresh button.

```jsx
import React, { useState } from "react";
import "./Form.css";

const options = ["Option 1", "Option 2", "Option 3", "Option 4", "Option 5"];

const Form = () => {
  const [selectedOption, setSelectedOption] = useState("");
  const [multiSelectOptions, setMultiSelectOptions] = useState([]);
  const [remainingOptions, setRemainingOptions] = useState(options);

  const handleSelectChange = (e) => {
    const value = e.target.value;
    setSelectedOption(value);
    setMultiSelectOptions((prev) => [...prev, value]);
    setRemainingOptions(options.filter((opt) => ![...multiSelectOptions, value].includes(opt)));
  };

  const handleMultiSelectChange = (e) => {
    const selectedValues = Array.from(e.target.selectedOptions, (option) => option.value);
    setMultiSelectOptions(selectedValues);
    setRemainingOptions(options.filter((opt) => !selectedValues.includes(opt)));
  };

  const handleRefresh = () => {
    setSelectedOption("");
    setMultiSelectOptions([]);
    setRemainingOptions(options);
  };

  return (
    <div className="form-container">
      <textarea placeholder="Text Area 1"></textarea>
      <textarea placeholder="Text Area 2"></textarea>
      <textarea placeholder="Text Area 3"></textarea>
      <textarea placeholder="Text Area 4"></textarea>

      <select value={selectedOption} onChange={handleSelectChange}>
        <option value="">Select an option</option>
        {remainingOptions.map((opt) => (
          <option key={opt} value={opt}>{opt}</option>
        ))}
      </select>

      <select multiple value={multiSelectOptions} onChange={handleMultiSelectChange}>
        {multiSelectOptions.map((opt) => (
          <option key={opt} value={opt}>{opt}</option>
        ))}
      </select>

      <div className="buttons">
        <button>Compare</button>
        <button onClick={handleRefresh}>Refresh</button>
      </div>
    </div>
  );
};

export default Form;
```

---

### **3. App.js**  
This is the main app component, which includes the navbar and form.

```jsx
import React from "react";
import Navbar from "./components/Navbar";
import Form from "./components/Form";
import "./App.css";

const App = () => {
  return (
    <div>
      <header className="app-header">
        <h1>My App</h1>
      </header>
      <div className="app-container">
        <Navbar />
        <Form />
      </div>
    </div>
  );
};

export default App;
```

---

### **4. App.css**  
This file contains the styles for the app.

```css
body {
  margin: 0;
  font-family: Arial, sans-serif;
}

.app-header {
  background-color: red;
  color: white;
  padding: 15px;
  text-align: left;
  font-size: 24px;
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
}

.app-header::after {
  content: "";
  display: block;
  height: 5px;
  background-color: yellow;
}

.app-container {
  display: flex;
  margin-top: 70px;
}

.sidebar {
  width: 200px;
  background-color: #f4f4f4;
  padding: 15px;
  height: 100vh;
}

.sidebar ul {
  list-style: none;
  padding: 0;
}

.sidebar li {
  margin-bottom: 10px;
}

.sidebar a {
  text-decoration: none;
  color: black;
}

.form-container {
  flex: 1;
  padding: 20px;
}

textarea {
  width: 100%;
  height: 50px;
  margin-bottom: 10px;
}

select {
  width: 100%;
  margin-bottom: 10px;
}

.buttons {
  display: flex;
  gap: 10px;
}
```

---

### **How to Run the Project**
1. **Initialize React App**  
   ```sh
   npx create-react-app my-app
   cd my-app
   ```

2. **Replace `src` Folder**  
   Replace the files inside `src` with the ones above.

3. **Start the App**  
   ```sh
   npm start
   ```

---

### **Functionality Overview**
- The navbar has three categories with three links each.  
- The form has:
  - Four text areas  
  - A single select dropdown  
  - A multi-select dropdown that updates dynamically  
  - A **Compare** button (does nothing for now)  
  - A **Refresh** button that resets the form  

Would you like any modifications or additional functionality?