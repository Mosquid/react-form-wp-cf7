# React Form WP CF7 Wrapper

A wrapper for your React form component that allows you to send it t your WordPress CF7 REST API route.
Learn more from [my medium article](https://mosquid.medium.com/headless-wordpress-using-contact-form-7-rest-api-with-react-e73ef052af23).


### How to use

```js

import Cf7FormWrapper from "./cf7-form-wrapper"
import { useState } from "react"

function Form({ handler, isLoading, isSent, hasError }) {
  const [formState, setFormState] = useState({})

  const handleFieldChange = (field, e) => {
    setFormState({
      ...formState,
      [field]: e.target.value,
    })
  }

  const handleFormSubmit = (e) => {
    handler(e, formState)
  }

  return (
    <form onSubmit={handleFormSubmit}>
      <div>isLoading: {isLoading ? "Loading" : "false"}</div>
      <div>isSent: {isSent ? "Sent" : "false"}</div>
      <div>Error: {hasError || "null"}</div>

      <div>Enter your name:</div>
      <input onChange={(e) => handleFieldChange("your-name", e)} type="text" />
      <div>Enter your email:</div>
      <input onChange={(e) => handleFieldChange("your-email", e)} type="text" />
      <div>Enter your phone:</div>
      <input onChange={(e) => handleFieldChange("your-phone", e)} type="text" />
      <div>Enter your country:</div>
      <input onChange={(e) => handleFieldChange("country", e)} type="text" />
      <input type="submit" value="Send" />
    </form>
  )
}

function App() {
  return (
    <div className="App">
      <Cf7FormWrapper url="http://example.com">
        <Form />
      </Cf7FormWrapper>
    </div>
  )
}
```
