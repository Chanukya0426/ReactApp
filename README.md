Here's the **React code** and **CSS styling** in separate files.  

---

### **React Component (ConfigDriftValidator.js)**
```jsx
import React, { useState } from "react";
import "./ConfigDriftValidator.css"; // Import CSS file

const ConfigDriftValidator = () => {
  const [showModal, setShowModal] = useState(false);
  const [selectedOption, setSelectedOption] = useState("");
  const [multiSelectOptions, setMultiSelectOptions] = useState([]);
  const [availableOptions] = useState(["Option 1", "Option 2", "Option 3", "Option 4"]);

  const handleSelectChange = (e) => {
    setSelectedOption(e.target.value);
    setMultiSelectOptions(availableOptions.filter((opt) => opt !== e.target.value));
  };

  return (
    <div className="container">
      <h2>ConfigDrift Validator</h2>
      <button className="open-button" onClick={() => setShowModal(true)}>
        Open Validator
      </button>

      {showModal && (
        <div className="modal-overlay">
          <div className="modal">
            <h3>Config Validator</h3>

            <textarea placeholder="Text Area 1" className="textarea"></textarea>
            <textarea placeholder="Text Area 2" className="textarea"></textarea>
            <textarea placeholder="Text Area 3" className="textarea"></textarea>

            <label>Select an Option:</label>
            <select className="select" value={selectedOption} onChange={handleSelectChange}>
              <option value="">--Select--</option>
              {availableOptions.map((opt) => (
                <option key={opt} value={opt}>{opt}</option>
              ))}
            </select>

            <label>Multi-Select Options:</label>
            <select multiple className="select" value={multiSelectOptions}>
              {multiSelectOptions.map((opt) => (
                <option key={opt} value={opt}>{opt}</option>
              ))}
            </select>

            <div className="button-container">
              <button className="close-button" onClick={() => setShowModal(false)}>Close</button>
              <button className="submit-button" onClick={() => alert("Submitted!")}>Submit</button>
            </div>
          </div>
        </div>
      )}
    </div>
  );
};

export default ConfigDriftValidator;
```

---

### **CSS Styling (ConfigDriftValidator.css)**
```css
/* Container */
.container {
  text-align: center;
  padding: 20px;
}

/* Open Button */
.open-button {
  padding: 10px 15px;
  font-size: 16px;
  cursor: pointer;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
}

.open-button:hover {
  background-color: #0056b3;
}

/* Modal Overlay */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Modal Box */
.modal {
  background: white;
  padding: 20px;
  border-radius: 5px;
  text-align: center;
  width: 300px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

/* Textarea */
.textarea {
  width: 100%;
  height: 50px;
  margin: 5px 0;
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

/* Select Dropdowns */
.select {
  width: 100%;
  margin: 5px 0;
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

/* Button Container */
.button-container {
  display: flex;
  justify-content: space-between;
  margin-top: 10px;
}

/* Close and Submit Buttons */
.close-button, .submit-button {
  padding: 8px 12px;
  font-size: 14px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.close-button {
  background-color: red;
  color: white;
}

.close-button:hover {
  background-color: darkred;
}

.submit-button {
  background-color: green;
  color: white;
}

.submit-button:hover {
  background-color: darkgreen;
}
```

---

### **How to Use**
1. Save `ConfigDriftValidator.js` inside your React project (`src/components/`).
2. Save `ConfigDriftValidator.css` in the same folder.
3. Import and use the component in your main App file (`App.js`):
   ```jsx
   import React from "react";
   import ConfigDriftValidator from "./components/ConfigDriftValidator";

   function App() {
     return (
       <div>
         <ConfigDriftValidator />
       </div>
     );
   }

   export default App;
   ```
4. Run your project with `npm start` or `yarn start`.

This keeps your **React logic separate from styling**, making it modular and reusable. Let me know if you need any modifications!
