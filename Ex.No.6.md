# Ex06 BMI Calculator
## Date: 15/11/2025

## AIM
To create a BMI calculator using React Router 

## ALGORITHM
### STEP 1 State Initialization
Manage the current page (Home or Calculator) using React Router.

### STEP 2 User Input
Accept weight and height inputs from the user.

### STEP 3 BMI Calculation
Calculate the BMI based on user input.

### STEP 4 Categorization
Classify the BMI result into categories (Underweight, Normal weight, Overweight, Obesity).

### STEP 5 Navigation
Navigate between pages using React Router.

## PROGRAM
App.css
```
/* Full screen center alignment */
body, #root {
  height: 100vh;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(135deg, #4b7bec, #a55eea);
  font-family: "Poppins", sans-serif;
}

/* BMI Container */
.bmi-container {
  background: #ffffff;
  padding: 35px;
  width: 380px;
  border-radius: 15px;
  text-align: center;
  box-shadow: 0 10px 25px rgba(0,0,0,0.2);
  animation: fadeIn 0.5s ease-in-out;
}

/* Heading */
.bmi-container h1 {
  margin-bottom: 15px;
  color: #333;
  font-size: 28px;
  font-weight: 700;
}

/* Input fields */
input {
  width: 85%;
  padding: 12px;
  margin: 10px 0;
  border-radius: 8px;
  border: 2px solid #ddd;
  font-size: 16px;
  transition: 0.3s;
}

input:focus {
  border-color: #4b7bec;
  box-shadow: 0 0 5px rgba(75, 123, 236, 0.5);
}

/* Button */
button {
  width: 90%;
  padding: 12px;
  background: #20bf6b;
  border: none;
  color: white;
  font-size: 18px;
  border-radius: 8px;
  cursor: pointer;
  margin-top: 10px;
  transition: 0.3s;
}

button:hover {
  background: #1e9c5c;
}

/* Result Box */
.result {
  margin-top: 20px;
  padding: 15px;
  background: #f1f2f6;
  border-radius: 10px;
  font-size: 20px;
  box-shadow: inset 0 0 10px rgba(0,0,0,0.1);
}

.result h2 {
  color: #2d98da;
}

.result p {
  font-weight: bold;
  color: #3867d6;
}

/* Animation */
@keyframes fadeIn {
  from { opacity: 0; transform: scale(0.9); }
  to { opacity: 1; transform: scale(1); }
}
```

App.jsx
```
import React, { useState } from 'react';
import './App.css';

function App() {
  const [weight, setWeight] = useState('');
  const [height, setHeight] = useState('');
  const [bmi, setBmi] = useState(null);
  const [message, setMessage] = useState('');

  const calculateBMI = (e) => {
    e.preventDefault();

    if (!weight || !height) {
      alert('Please enter both weight and height.');
      return;
    }

    const heightInMeters = height / 100;
    const bmiValue = (weight / (heightInMeters * heightInMeters)).toFixed(2);

    setBmi(bmiValue);

    if (bmiValue < 18.5) setMessage('Underweight');
    else if (bmiValue >= 18.5 && bmiValue < 24.9) setMessage('Normal weight');
    else if (bmiValue >= 25 && bmiValue < 29.9) setMessage('Overweight');
    else setMessage('Obese');
  };

  return (
    <div className="bmi-container">
      <h1>BMI Calculator</h1>
      <form onSubmit={calculateBMI}>
        <input
          type="number"
          placeholder="Weight (kg)"
          value={weight}
          onChange={(e) => setWeight(e.target.value)}
        />
        <input
          type="number"
          placeholder="Height (cm)"
          value={height}
          onChange={(e) => setHeight(e.target.value)}
        />
        <button type="submit">Calculate</button>
      </form>

      {bmi && (
        <div className="result">
          <h2>Your BMI: {bmi}</h2>
          <p>Status: {message}</p>
        </div>
      )}
      <br></br>
      <h3 style={{ color: "#555", marginTop: "-10px" }}>Created by Muthulakshmi</h3>
    </div>
  );
}

export default App;

```

## OUTPUT

<img width="1919" height="991" alt="image" src="https://github.com/user-attachments/assets/eed1fe8c-9f29-4ca3-8824-93b51c5e66e6" />

## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
