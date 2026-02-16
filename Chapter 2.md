# 🌟 JavaScript Execution Context 

*(Namaste JavaScript – Behind the Scenes of JS Engine)*

![Image](https://media.licdn.com/dms/image/v2/D4E12AQEojyVOipOL1w/article-cover_image-shrink_720_1280/article-cover_image-shrink_720_1280/0/1707323060304?e=2147483647\&t=L7hbfEut17y5ucTWs9WOLFPz9MlYxSR8mE_6iOXAavY\&v=beta)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2ACuL8xsqLb1GhpuHgmDKk0A.png)

![Image](https://media.licdn.com/dms/image/v2/D5612AQGLiPuwCz7lHQ/article-cover_image-shrink_720_1280/article-cover_image-shrink_720_1280/0/1697821748372?e=2147483647\&t=ZpwgzrPzsrTv8A7F5DgXnTSGTp2J5pmY2YhCTq6JMuM\&v=beta)

![Image](https://binovarghese.com/img/2022/execution-context-1.jpg)

---

## 🔥 Big Picture (Why This Matters)

When you run a JavaScript program:

* **A LOT happens behind the scenes**
* JS Engine manages memory, execution, function calls, and control flow
* All of this is powered by **Execution Contexts** and the **Call Stack**

> ⚠️ Without understanding this, JavaScript will always feel “magical” and confusing.

---

## 🧠 Core Reminder

> **Everything in JavaScript happens inside an Execution Context**

* No JS code can run without it
* Execution Context = **Environment where code executes**

---

## 🚀 What Happens When a JS Program Runs?

✅ **A Global Execution Context (GEC) is created**

This Global Execution Context:

* Represents the entire JS program
* Is created **first**
* Is pushed into the **Call Stack**

---

## 📦 Structure of an Execution Context

Every Execution Context has **2 components**:

### 1️⃣ Memory Component

*(Variable Environment)*

* Stores:

  * Variables
  * Functions
* Stored as **key–value pairs**

---

### 2️⃣ Code Component

*(Thread of Execution)*

* Executes code **line by line**
* Only **one line at a time**

---

## 🔁 Execution Context is Created in **2 Phases**

### 🟡 Phase 1: Memory Creation Phase

*(VERY IMPORTANT)*

During this phase:

* JavaScript **scans the entire code**
* Allocates memory to:

  * Variables → `undefined`
  * Functions → **entire function code**

📌 Nothing is executed yet

---

### 🟢 Phase 2: Code Execution Phase

* JavaScript again goes **line by line**
* Assigns actual values
* Executes calculations
* Invokes functions

---

## 📘 Example Code (Used in Explanation)

```js
var n = 2;

function square(num) {
  var ans = num * num;
  return ans;
}

var square2 = square(n);
var square4 = square(4);
```

---

## 🧩 Phase 1: Global Memory Creation

Memory allocated like this:

| Identifier | Value Stored  |
| ---------- | ------------- |
| n          | undefined     |
| square     | function code |
| square2    | undefined     |
| square4    | undefined     |

📌 **Key Insight**

* `undefined` is a **placeholder**
* Functions are stored **completely**

---

## ▶️ Phase 2: Global Code Execution

### Step 1: `n = 2`

* `undefined` → `2`

---

### Step 2: Function Definition

* Nothing executes
* JS skips function body

---

### Step 3: `square(n)` → Function Invocation

⚠️ **Important Rule**

> Whenever a function is invoked, a **NEW Execution Context** is created

---

## 🧠 Function Execution Context (square)

### 🔹 Again, TWO PHASES happen

---

### 🟡 Phase 1: Memory Creation (Function Context)

Memory inside function:

| Identifier | Value     |
| ---------- | --------- |
| num        | undefined |
| ans        | undefined |

📌 Parameters are treated like variables

---

### 🟢 Phase 2: Code Execution (Function Context)

1️⃣ Argument passed

* `n = 2` → `num = 2`

2️⃣ Calculation

* `num * num = 4`
* `ans = 4`

3️⃣ Return statement

* `return ans`

📌 Control goes **back to the place where function was called**

---

## 🔄 Returning to Global Context

* Returned value `4`
* Assigned to `square2`

```js
square2 = 4;
```

✅ Function Execution Context is **deleted**

---

## 🔁 Second Function Call: `square(4)`

Same steps repeat:

* New Execution Context created
* `num = 4`
* `ans = 16`
* Returned value replaces `square4`

```js
square4 = 16;
```

Execution Context deleted again

---

## 📦 Final Global Memory State

| Variable | Value |
| -------- | ----- |
| n        | 2     |
| square2  | 4     |
| square4  | 16    |

<img width="1063" height="532" alt="image" src="https://github.com/user-attachments/assets/3ae38708-fff3-4f61-8c48-c5ceefda8016" />

---

## 🧠 How Does JS Manage All This?

👉 **CALL STACK**

---

## 🧱 Call Stack Explained

![Image](https://felixgerschau.com/static/79486d91b22a7c1b4044fce88a4cae20/5a190/js-event-loop-explained.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2ArJ2Gwch8CiATB_4MJzm-6g.png)

![Image](https://blog.openreplay.com/images/explaining-javascript-s-execution-context-and-stack/images/mFQtgsb.png)

### 📌 What is Call Stack?

* A **stack data structure**
* Manages:

  * Execution Context creation
  * Execution Context deletion
  * Order of execution

---

## 🔄 Call Stack Working

### Step-by-step:

1️⃣ Program starts

* Global Execution Context pushed

2️⃣ Function invoked

* New Execution Context pushed

3️⃣ Function finishes

* Execution Context popped

4️⃣ Control returns to previous context

5️⃣ After program ends

* Call Stack becomes empty

---

## 🏷️ Other Names of Call Stack

Call Stack is also known as:

* Execution Context Stack
* Program Stack
* Runtime Stack
* Control Stack
* Machine Stack

📌 **All mean the SAME thing**

---

## 🎯 Final Golden Rules (Interview Gold)

* JavaScript is **synchronous & single-threaded**
* Execution Contexts are created & destroyed dynamically
* Call Stack maintains execution order
* Functions create **new execution contexts**
* `undefined` is assigned during memory creation phase

---

## 🧠 One-Line Summary

> **JavaScript executes code using Execution Contexts, manages them using the Call Stack, and runs everything in two phases: Memory Creation and Code Execution.**

---
