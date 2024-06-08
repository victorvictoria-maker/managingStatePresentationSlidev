---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# background: https://cover.sli.dev
# some information about your slides, markdown enabled
title: Welcome to Slidev
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply any unocss classes to the current slide
class: text-center
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
mdc: true
---

# Managing State Effectively in React

Reacting to Input with State.

Choosing the state structure.

---

# Reacting to Input with State

<br>

**Declarative UI:**

- In React, you define the UI as a function of state and props. Instead of manually manipulating the DOM, you describe the desired UI state, and React updates the DOM automatically when the state changes. This is known as a declarative approach.

<br>

**Advantages:**

- **Simplicity:** You describe what you want, and React handles how to achieve it.
- **Maintainability:** Declarative code is easier to read and maintain.
- **Consistency:** React ensures the UI is always consistent with the current state, reducing bugs and inconsistencies.

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

### Example: Counter Component

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

In the example above, the Counter component re-renders automatically whenever the state (count) changes.

<!-- # Welcome to Slideveloping

Presentation slides for developers

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div> -->

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

<!-- ## transition: fade-out -->

# Developing a Component:

1.  Identify Visual States: Determine the different states your component can be in (e.g., form states: typing, submitting, error).
2.  Determine Triggers: Identify what causes state changes (e.g., user actions like clicking a button or system events like loading an image).
3.  Use useState: Represent the state in memory using React's useState hook.
4.  Simplify State Variables: Remove non-essential state variables to keep the state minimal and efficient.
5.  Connect Event Handlers: Use event handlers to update the state.

<!-- # What is Slidev?

Slidev is a slides maker and presenter designed for developers, consist of the following features

- 📝 **Text-based** - focus on the content with Markdown, and then style them later
- 🎨 **Themable** - theme can be shared and used with npm packages
- 🧑‍💻 **Developer Friendly** - code highlighting, live coding with autocompletion
- 🤹 **Interactive** - embedding Vue components to enhance your expressions
- 🎥 **Recording** - built-in recording and camera view
- 📤 **Portable** - export into PDF, PPTX, PNGs, or even a hostable SPA
- 🛠 **Hackable** - anything possible on a webpage

<br>
<br>

Read more about [Why Slidev?](https://sli.dev/guide/why) -->

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

### Example

<br>

```jsx {all}{maxHeight:'500px'}
import { useState } from "react";

function LoginForm() {
  const [username, setUsername] = useState("");
  const [password, setPassword] = useState("");
  const [isSubmitting, setIsSubmitting] = useState(false);
  const [hasSubmitted, setHasSubmitted] = useState(false);

  const handleSubmit = (e) => {
    e.preventDefault();
    // Forgot to set isSubmitting to true

    // Simulate an API call
    setTimeout(() => {
      // Forgot to set isSubmitting back to false
      alert("Logged in!");
    }, 2000);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type='text'
        placeholder='Username'
        value={username}
        onChange={(e) => setUsername(e.target.value)}
      />
      <input
        type='password'
        placeholder='Password'
        value={password}
        onChange={(e) => setPassword(e.target.value)}
      />
      <button type='submit' disabled={isSubmitting}>
        {isSubmitting ? "Logging in..." : "Login"}
      </button>
    </form>
  );
}
```

<!--
Identify Visual States:
When developing a component, it's essential to identify the different visual states it can be in. For example, a form might have states like submitting, and error as we can see in the from here.

Determine Triggers:
Determine what triggers those state changes. Triggers can be user actions like clicking a link or button or system events like loading an image. In this example, a form submit is trigerring the state change.

Represent the State:
Represent the state in memory using React's useState hook. This allows you to keep track of the component's current state. Just like they are represneted.

Simplify State Variables:
Remove any non-essential state variables to keep the state minimal and efficient. For example, you might not need a hasSubmitted state as it's not crucial to your component's functionality.

Connect Event Handlers:
Connect the event handlers to set the state. This ensures that state changes in response to user actions or system events are properly managed.
-->

---

### Example: Better way to do it

<br>
<!-- 2-3|5 -->

```jsx {|all}{maxHeight:'500px'}
import { useState } from "react";

function LoginForm() {
  const [username, setUsername] = useState("");
  const [password, setPassword] = useState("");
  const [isSubmitting, setIsSubmitting] = useState(false);

  const handleSubmit = (e) => {
    e.preventDefault();
    setIsSubmitting(true);
    // Simulate an API call
    setTimeout(() => {
      setIsSubmitting(false);
      alert("Logged in!");
    }, 2000);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type='text'
        placeholder='Username'
        value={username}
        onChange={(e) => setUsername(e.target.value)}
      />
      <input
        type='password'
        placeholder='Password'
        value={password}
        onChange={(e) => setPassword(e.target.value)}
      />
      <button type='submit' disabled={isSubmitting}>
        {isSubmitting ? "Logging in..." : "Login"}
      </button>
    </form>
  );
}
```

<!--
Non-essential state variable - hasSubmitted has been removed. As the form is being submitted, the isSubmitting state is being used and called and also used to change the UI.
-->

---

# Choosing the state structure

<br>

- Properly structuring your state can significantly affect the ease of modifying and debugging your component.

- Make your state as simple as it can be.

- We would be looking at 5 principles to follow:

  1. Group related state.
  2. Avoid contradictions in state.
  3. Avoid redundant state.
  4. Avoid duplication in state.
  5. Avoid deeply nested state.

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

## Group related states.

If you always update two or more state variables together, consider merging them into a single state variable.

<br>

```jsx
const [firstName, setFirstName] = useState("");
const [lastName, setLastName] = useState("");
const [middleName, setMiddleName] = useState("");
const [age, setAge] = useState(0);

const handleFirstNameChange = (e) => {
  setFirstName(e.target.value);
};

const handleLastNameChange = (e) => {
  setLastName(e.target.value);
};

const handleMiddleNameChange = (e) => {
  setMiddleName(e.target.value);
};

const handleAgeChange = (e) => {
  setAge(e.target.value);
};
```

<!--
For example, you can combine all these data into user state - probaly an object.  If some two state variables always change together, it might be a good idea to unify them into a single state variable.

Another case where you’ll group data into an object or an array is when you don’t know how many pieces of state you’ll need. For example, it’s helpful when you have a form where the user can add custom fields.
-->

---

## Avoid Contradictions in State.

Avoid maintaining state variables that can contradict each other.

<br>

```jsx
// Instead of
const [isUserLoggedIn, setIsUserLoggedIn] = useState(false);
const [user, setUser] = useState(null);

// Use derived state
const isUserLoggedIn = user !== null;
```

<!--
When the state is structured in a way that several pieces of state may contradict and “disagree” with each other, you leave room for mistakes.

Try to avoid this.

Example - Instead of maintaining separate isUserLoggedIn and user state variables that can get out of sync, You can derive isUserLoggedIn from user.

 Another example is isSending and isSent state in a form. If you forget to call setIsSent and setIsSending together after the function runs, you may end up in a situation where both isSending and isSent are true at the same time.
-->

---

## Avoid redundant state.

Do not store information in the state if it can be derived from existing state or props.

```jsx
// Instead of
const [firstName, setFirstName] = useState("");
const [lastName, setLastName] = useState("");
const [fullName, setFullName] = useState(`${firstName} ${lastName}`);

// Use derived state
const fullName = `${firstName} ${lastName}`;
```

<br>

Don’t put props into state unless you specifically want to prevent updates.

```jsx {all}{maxHeight:'400px'}
function Message({ messageColor }) {
  const [color, setColor] = useState(messageColor);

  // Incorrect: Storing props in state without necessity
  return <div style={{ color }}>{messageColor}</div>;
}

// Better Approach: Avoiding redundant state
function Message({ messageColor }) {
  const color = messageColor; // Using prop directly

  return <div style={{ color }}>{messageColor}</div>;
}
```

<!--
Redundance is the presence of duplicate or unnecessary code segments that serve the same purpose.

If you can calculate some information from the component’s props or its existing state variables during rendering, you should not put that information into that component’s state.

Having fullName, lastName and fullNmae when you can get fullname from both.

For example 2,

By avoiding redundant state, you ensure that your components are more predictable and easier to work with. This practice reduces the chances of bugs related to state synchronization and keeps your code clean and efficient.
-->

---

## Avoid Duplication in State.

Reduce duplication by keeping data in a single place.

```jsx {all}{maxHeight:'400px'}
import React, { useState } from "react";

function UserProfile() {
  const [firstName, setFirstName] = useState("");
  const [lastName, setLastName] = useState("");
  const [fullName, setFullName] = useState("");

  const handleNameChange = (e) => {
    const { name, value } = e.target;
    if (name === "firstName") {
      setFirstName(value);
      setFullName(`${value} ${lastName}`);
    } else if (name === "lastName") {
      setLastName(value);
      setFullName(`${firstName} ${value}`);
    }
  };

  return (
    <div>
      <input
        type='text'
        name='firstName'
        placeholder='First Name'
        value={firstName}
        onChange={handleNameChange}
      />
      <input
        type='text'
        name='lastName'
        placeholder='Last Name'
        value={lastName}
        onChange={handleNameChange}
      />
      <p>Full Name: {fullName}</p>
    </div>
  );
}
```

<!--
When the same data is duplicated between multiple state variables or within nested objects, it becomes difficult to keep them in sync.

In this example, firstName, lastName, and fullName are stored as separate state variables.
Every time the user updates their first or last name, the component must update fullName to keep the state in sync.
This duplication increases the complexity and potential for bugs if the state variables get out of sync.
-->

---

## A better approach.

<br>

```jsx {all}{maxHeight:'400px'}
import { useState } from "react";

function UserProfile() {
  const [name, setName] = useState({ firstName: "", lastName: "" });

  const handleNameChange = (e) => {
    const { name, value } = e.target;
    setName((prevState) => ({
      ...prevState,
      [name]: value,
    }));
  };

  return (
    <div>
      <input
        type='text'
        name='firstName'
        placeholder='First Name'
        value={name.firstName}
        onChange={handleNameChange}
      />
      <input
        type='text'
        name='lastName'
        placeholder='Last Name'
        value={name.lastName}
        onChange={handleNameChange}
      />
      <p>
        Full Name: {name.firstName} {name.lastName}
      </p>
    </div>
  );
}
```

<!--
In this improved example, firstName and lastName are grouped into a single name state object.
This reduces duplication because the full name can be derived directly from the name object.
The state update logic is simplified, ensuring that firstName and lastName are always in sync.
This approach reduces the complexity of state management, making the code easier to maintain and less prone to bugs.
-->

---

## Avoid Deeply Nested State.

If updating nested state is complex, consider flattening it.

<br>

```jsx
// Instead of deeply nested state
const [user, setUser] = useState({
  profile: {
    name: "",
    age: 0,
  },
  settings: {
    theme: "light",
    notifications: true,
  },
});

// Flattened state
const [name, setName] = useState("");
const [age, setAge] = useState(0);
const [theme, setTheme] = useState("light");
const [notifications, setNotifications] = useState(true);
```

---

# CONCLUSION

<br>

By following best practices for structuring state, you can create components that are easier to maintain, debug, and enhance. Remember to:

- Define UI declaratively based on state and props.
- Identify and manage different visual states of your components.
- Simplify state structure to avoid contradictions, redundancy, and duplication.
- By mastering these concepts, you can build robust and scalable React applications.

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
