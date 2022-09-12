# React & Redux

# REMINDER: Each prompt is answerable in 5min. You'll have 25 minutes to respond to each of these questions. You must record your screen as well with this prompt on the foreground.

[Here is the link for the survey to be completed after.](https://forms.office.com/r/2ty04ksdbs)

# Prompt 1

1. What can you tell me about React?

2. How do you create and run a react app? What directory must you be in?

3. What are componenets? What must they always return?

4. What is JSX?

5. What are hooks? Give two examples of how and why we would use them.

# Prompt 2

1. What is the Virtual DOM?

2. Why use React over another library or framework?

3. What is state vs props?

4. What is redux?

5. What is a slice vs a store in redux?

# Prompt 3

Explain the following code. Line-by-line. **_NOTE_** Answer some of the comments.

```javascript
import { useRef, useState } from "react";
import { useDispatch } from "react-redux";
import { useNavigate } from "react-router";
import { nabnakClient } from "../../common/remote/nabnak-client";
import { loginStore } from "./loginSlice";

export default function Login() {
    const emailInput = useRef();
    const passwordInput = useRef();
    const [loginStatus, setLoginStatus] = useState();

    const dispatch = useDispatch();
    const navigate = useNavigate();

    async function login() {
        const body = {
            email: emailInput.current.value,
            password: passwordInput.current.value,
        };

        try {
            // What's happening with the below code. #Note: nabnakClient described below.
            const response = await nabnakClient.post("/auth", body);
            setLoginStatus(undefined);

            // What is the window.localStorage?
            window.localStorage.setItem("token", response.headers.authorization);
            dispatch(loginStore(response.data));
            navigate("/card");
        } catch (error) {
            // Why this?
            if (error.response.status === 404) {
                let loginFailed = `Email or Password was incorrect for email: ${body.email}`;
                setLoginStatus(loginFailed);
            }
        }
    }

    return (
        <>
            <label>Email:</label>
            <input id="loginEmail" placeholder="i.e Jester@mail.com" ref={emailInput} />
            <label>Password:</label>
            <input id="loginPassword" type="password" placeholder="i.e charlesIsCool!" ref={passwordInput} />
            <button onClick={login}>Login</button>
            {/*What's going on here? Why bother using this?*/}
            {loginStatus === undefined ? <p></p> : <p>{loginStatus}</p>}
        </>
    );
}
```

```javascript
import axios from "axios";

export const nabnakClient = axios.create({
    baseURL: "http://localhost:8080",
    headers: {
        Accept: "application/json",
        "Content-type": "application/json",
    },
});
```
