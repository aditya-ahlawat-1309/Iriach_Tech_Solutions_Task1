import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';


import 'bootstrap/dist/css/bootstrap.css';
import Counter from './components/counter';
import { useState } from "react";
import "./styles.css";

function App() {
  const [fields, setFields] = useState([{ value: null }]);

  function handleChange(i, event) {
    const values = [...fields];
    values[i].value = event.target.value;
    setFields(values);
  }

  function handleAdd() {
    const values = [...fields];
    values.push({ value: null });
    setFields(values);
  }

  function handleRemove(i) {
    const values = [...fields];
    values.splice(i, 1);
    setFields(values);
  }

  
  return (
    <div className="App">
      <h1>Section 1 : Task 1 - Interview Test</h1>

      <button className="btn btn-primary btn-sm m-3" type="button" onClick={() => handleAdd()}>+ </button>

      {fields.map((field, idx) => {
        return (
          <div key={`${field}-${idx}`}>
            <input
              type="text"
              placeholder="Enter Lecture No."
              value={field.value || ""}
              onChange={e => handleChange(idx, e)}
            />
            <button  className="btn btn-warning btn-sm m-3" type="button" onClick={() => handleRemove(idx)}>
              Save
            </button>

           
          </div>

          
        );
      })}
    </div>
  );
    
}

const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);

// ReactDOM.render(<Counter /> , document.getElementById("root"));
