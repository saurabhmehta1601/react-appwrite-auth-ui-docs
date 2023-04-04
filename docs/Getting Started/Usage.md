## Quick Start

### Create simple email signup form
The following code snippet renders a form for user signup with email and password fields. 

```jsx
import React from 'react'
import {Button, EmailSignupForm, FormControl, FormList} from "react-appwrite-auth-ui"

const MyForm = () => {
  const [email, setEmail] = React.useState("")
  const [password, setPassword] = React.useState("")

  const onAuthError = (error) => {
    console.log("error in signup" , error)
  }

  const onAuthSuccess = (response) => {
    console.log('success in email signup', response)
  }

  return (<EmailSignupForm 
      email={email}
      password={password}
      onAuthError={onAuthError}
      onAuthSuccess={onAuthSuccess}
      >
        <FormList>
        <FormControl 
          label='Email' 
          type='email'
          value={email}
          onChange={(e) => setEmail(e.target.value)}/>
        <FormControl 
          label='Password' 
          type="password"
          value={password}
          onChange={(e) => setPassword(e.target.value)}/>
        </FormList>
        <Button type='submit' className='u-margin-block-start-16' > Submit </Button>
      </EmailSignupForm>
  )
}

export default MyForm 
```

### Access authenticated user
The authenticated user can be accessed with react hook `useAuthenticatedUser` .

```jsx
import React from 'react'
import {useAuthenticatedUser } from "react-appwrite-auth-ui"

const MyAuthenticatedUser = () => {
  const {loading,error,user}= useAuthenticatedUser()

  if(loading) return <p>loading ⌚...</p>

  if(error) return <p>error while loading user 😭 </p>

  return  <p>Logged in with email id {user.email}</p>
}

export default MyAuthenticatedUser
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