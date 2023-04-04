## Quick Start

### Create simple signup form
The following code snippet renders a form for user signup with email and password fields. 

```jsx
import React from 'react'
import {Button, EmailSignupForm, FormControl} from "react-appwrite-auth-ui"

const EmailForm = () => {
  const [email, setEmail] = React.useState("")
  const [password, setPassword] = React.useState("")

  const onAuthSuccess = (response) => {
    console.log("error in signup" , error)
  }

  const onAuthError = (error) => {
    console.log('success in email signup', response)
  }

  return (
    <EmailSignupForm 
      email={email}
      password={password}
      onAuthError={onAuthError}
      onAuthSuccess={onAuthSuccess}
      >
        <FormControl 
          label='Email' 
          type='email'
          value={email}
          onChange={(e) => setEmail(e.target.value)}
          />

        <FormControl 
          label='Password' 
          type="password"
          value={password}
          onChange={(e) => setPassword(e.target.value)}
          />

        <Button type='submit'> Submit </Button>
    </EmailSignupForm>
  )
}

export default EmailForm
```

### Access authenticated user
The authenticated user can be accessed with react hook `useAuthenticatedUser` .

```jsx
import React from 'react'
import {useAuthenticatedUser } from "react-appwrite-auth-ui"

const GetAuthenticatedUser = () => {
  const {loading,error,user}= useAuthenticatedUser()

  if(loading) return <p>loading ⌚...</p>

  if(error) return <p>error while loading user 😭 </p>

  return  <p>Logged in with email id {user.email}</p>
}

export default GetAuthenticatedUser
```

### Signout authenticated user

The authenticated user can be signed out with `SignoutButton`

```jsx
import React from 'react'
import { SignoutButton } from 'react-appwrite-auth-ui'

const Signout = () => {
  const onAuthSuccess = (response) => {
    console.log("success in logging out" , response)
  }
  const onAuthError = (error) => {
    console.log("error in logging out" , error );
  }

  return (
    <div>
      <SignoutButton 
      onAuthSuccess={onAuthSuccess}
      onAuthError={onAuthError}
      />
    </div>
  )
}

export default Signout
```