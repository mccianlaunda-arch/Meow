PR01 — OPERATIONS WITH MONGODB
Running Steps
Start MongoDB Server.
Open MongoDB Compass or mongosh.
Open mongosh.
Run:
use test
Execute the following questions one by one.
Q1. Create a collection named employee.
db.createCollection("employee")
Q2. Insert a single employee record.
db.employee.insertOne({
    employee_id: 101,
    name: "Jhonny Stark",
    department: "CS",
    salary: 70000
})
Q3. Insert multiple employee records.
db.employee.insertMany([
    {
        employee_id: 102,
        name: "Peter Parker",
        department: "IT",
        salary: 55000
    },
    {
        employee_id: 103,
        name: "Steve Rogers",
        department: "Sales",
        salary: 60000
    }
])
Q4. Insert an employee document containing an array field.
db.employee.insertOne({
    employee_id: 104,
    name: "Priya Sharma",
    department: "Development",
    salary: 75000,
    skills: ["MongoDB", "Node.js", "React"]
})
Q5. Display all employee records.
db.employee.find()
Q6. Insert an employee document with nested fields.
db.employee.insertOne({
    employee_id: 105,
    name: "Ravi Kumar",
    department: "Design",
    salary: 50000,
    address: {
        street: "MG Road",
        city: "Pune",
        zipcode: 411001
    }
})
Q7. Find employees working in IT department.
db.employee.find({
    department: "IT"
})
Q8. Find employees having salary greater than ₹60,000.
db.employee.find({
    salary: { $gt: 60000 }
})
Q9. Find employees having the skill Python.
db.employee.find({
    skills: "Python"
})
Q10. Find employees whose city is Pune.
db.employee.find({
    "address.city": "Pune"
})
Q11. Find employees belonging to HR or Sales departments.
db.employee.find({
    department: { $in: ["HR", "Sales"] }
})
Q12. Add a skill using $push.
db.employee.updateOne(
    { employee_id: 101 },
    { $push: { skills: "Express.js" } }
)
Q13. Remove a skill using $pull.
db.employee.updateOne(
    { name: "Priya Sharma" },
    { $pull: { skills: "React" } }
)
Q14. Add a skill using $addToSet.
db.employee.updateOne(
    { employee_id: 104 },
    { $addToSet: { skills: "React" } }
)
Q15. Display employee ID, name, department and salary.
db.employee.find(
    {},
    {
        employee_id: 1,
        name: 1,
        department: 1,
        salary: 1
    }
)
Q16. Display employee ID, name and department excluding _id.
db.employee.find(
    {},
    {
        employee_id: 1,
        name: 1,
        department: 1,
        _id: 0
    }
)
Q17. Display employee records from CS department.
db.employee.find({
    department: "CS"
})
Q18. Update salary of CS employees to ₹50,000.
db.employee.update(
    { department: "CS" },
    { $set: { salary: 50000 } }
)
Q19. Update salary to ₹75,000 where employee_id > 104.
db.employee.update(
    { employee_id: { $gt: 104 } },
    { $set: { salary: 75000 } }
)
Q20. Delete any one employee record.
db.employee.deleteOne({
    employee_id: 101
})
Q21. Rename employee collection.
db.employee.renameCollection("employee_details")
PR02-A — PROPERTIES USING REACT COMPONENTS

The uploaded Practical No. 2 contains Class Component properties and Functional Component properties.

Q1. Demonstrating properties using Class Component
Steps
Open React project in VS Code.
Create ClassProps.js.
Create/update App.js.
Run npm start.
ClassProps.js
import React, { Component } from "react";

class Parent extends Component {
    render() {
        return (
            <div>
                <h1>
                    This is Parent Class {this.props.address}
                </h1>

                <Child
                    p_name="Parent Name"
                    p_age={50}
                />
            </div>
        );
    }
}

class Child extends Component {
    render() {
        return (
            <div>
                <h2>
                    {this.props.p_name}
                    <br></br>
                    {this.props.p_age}
                </h2>
            </div>
        );
    }
}

export { Parent, Child };
App.js
import "./App.css";
import { Parent, Child } from "./ClassProps";

function App() {
    return (
        <div>
            <Parent address="qwerty" />
            <Child />
        </div>
    );
}

export default App;
Q2. Demonstrating properties using Functional Component
Function_name.js
import React from "react";

export let Car = (props) => {
    return (
        <h2>
            I am a {props.name} !!!
        </h2>
    );
};

export const Product = () => {
    return (
        <div>
            <h1>Product Details</h1>
            <Car name="prod_name" />
        </div>
    );
};
App.js
import { Product, Car } from "./Function_name";

function App() {
    return (
        <div>
            <Car name="Brezza" />
            <Product />
        </div>
    );
}

export default App;
PR02-B — USING STATES IN COMPONENTS

Your second uploaded Practical No. 2 is specifically Using States in Components.

Q3. Change message using State
Steps
Create Cls_state.js.
Update App.js.
Run npm start.
Click Click Here.
Cls_state.js
import React, { Component } from "react";

class Message extends Component {
    constructor() {
        super();

        this.state = {
            message: "Welcome Visitors"
        };
    }

    changeMessage() {
        this.setState({
            message: "Thank You for Visiting!"
        });
    }

    render() {
        return (
            <div>
                <h1>{this.state.message}</h1>

                <button onClick={() => this.changeMessage()}>
                    Click Here
                </button>
            </div>
        );
    }
}

export default Message;
App.js
import "./App.css";
import Message from "./Cls_state.js";

function App() {
    return (
        <div className="App">
            <Message />
        </div>
    );
}

export default App;
Q4. Create Counter using State
Classcounter.js
import React, { Component } from "react";

class Counter extends Component {
    constructor() {
        super();

        this.state = {
            count: 0
        };
    }

    increment() {
        this.setState((prevState) => ({
            count: prevState.count + 1
        }));

        console.log(this.state.count);
    }

    render() {
        return (
            <div>
                {this.state.count}
                <br></br>

                <button onClick={() => this.increment()}>
                    Increment
                </button>
            </div>
        );
    }
}

export default Counter;
App.js
import "./App.css";
import Counter from "./Classcounter.js";

function App() {
    return (
        <div className="App">
            <Counter />
        </div>
    );
}

export default App;
PR03 — FILE OPERATIONS IN NODE.JS

The uploaded Practical No. 3 contains synchronous and asynchronous file reading.

Q1. Read file synchronously
Steps
Create sample.txt.
Create Read.js.
Run:
node Read.js
sample.txt
Hello World!
This is a file named Sample text.
Read.js
const fs = require("fs");

const a = fs.readFileSync("./sample.txt", "utf-8");

console.log(a);
Q2. Read file asynchronously
Steps
Create Async.js.
Keep sample.txt in same folder.
Run:
node Async.js
Async.js
const fs = require("fs");

fs.readFile("./sample.txt", "utf-8", (error, data) => {
    if (error) {
        throw new Error("Error reading file!");
    }

    console.log(data);
});
PR04 — CREATING YOUR OWN NODE MODULE

The practical contains two EventEmitter programs.

Q1. Accept text, save it to text.txt and emit custom event
Steps
Create text.js.
Open terminal.
Run:
node text.js
Enter text.
text.txt will be created.
text.js
const fs = require("fs");
const readline = require("readline");
const EventEmitter = require("events");

const eventEmitter = new EventEmitter();

const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});

function handleInput(input) {
    eventEmitter.emit("textReady", input);
}

eventEmitter.on("textReady", (text) => {
    console.log(`Custom event fired: Text is ready - ${text}`);

    fs.writeFile("text.txt", text, (err) => {
        if (err) throw err;

        console.log("Text has been saved to text.txt");
        rl.close();
    });
});

rl.question("Enter some text: ", (text) => {
    handleInput(text);
});
Q2. Calculate factorial using custom event
Steps
Create factorial.js.
Run:
node factorial.js
Enter a number.
factorial.js
const readline = require("readline");
const EventEmitter = require("events");

const eventEmitter = new EventEmitter();

const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});

function calculateFactorial(num) {
    eventEmitter.emit("factorialEvent", num);
}

eventEmitter.on("factorialEvent", (num) => {
    let fact = 1;

    for (let i = 1; i <= num; i++) {
        fact *= i;
    }

    console.log(`Factorial of ${num} is ${fact}`);

    rl.close();
});

rl.question("Enter a number: ", (number) => {
    calculateFactorial(parseInt(number));
});

PR05 — SERVER USING EXPRESS & HTTP METHODS
Q1. Create a simple Node.js HTTP server
Steps
1. Open VS Code and create a folder named PR05 on your Desktop.
2. Open the PR05 folder in VS Code.
3. Create a new file named Server.js.
4. Copy and paste the following code into Server.js and save it.
Server.js
const http = require("http");

const hostname = "127.0.0.1";
const port = 4000;

const server = http.createServer((req, res) => {

    res.writeHead(200, {
        "Content-Type": "text/plain"
    });

    if (req.url === "/hello") {
        res.end("Hello World!\n");
    }
    else if (req.url === "/about") {
        res.end("This is the about page\n");
    }
    else {
        res.end("Node.js server!\n");
    }
});

server.listen(port, hostname, () => {
    console.log(
        `Server running at http://${hostname}:${port}/`
    );
});


5. Open the VS Code terminal using Terminal → New Terminal.
6. Run the following command:
node Server.js


7. Press Enter. The following output should appear:
Server running at http://127.0.0.1:4000/


8. Keep the server running.
9. Open the Extensions panel in VS Code.
10. Search for Thunder Client and click Install. Skip this step if it is already installed.
11. Click the Thunder Client icon in the VS Code sidebar.
12. Click New Request.
13. Select the GET method.
14. Enter the URL http://127.0.0.1:4000/hello in the URL field.
15. Click Send. The response should be:
Hello World!


16. Change the URL to http://127.0.0.1:4000/about and click Send. The response should be:
This is the about page


17. Change the URL to http://127.0.0.1:4000/ and click Send. The response should be:
Node.js server!

Q1 is completed.

Q2. Express API to display users from JSON
Steps
1. Open VS Code and create a folder named PR05_Express on your Desktop.
2. Open the PR05_Express folder in VS Code.
3. Open the terminal using Terminal → New Terminal.
4. Run the following command to initialize the Node.js project:
npm init -y


5. Install Express by running:
npm install express


6. In the Explorer panel, create a new file named users.json.
7. Copy and paste the following code into users.json and save it.
users.json
[
    {
        "id": 101,
        "name": "Alice",
        "age": 20
    },
    {
        "id": 102,
        "name": "Bob",
        "age": 22
    },
    {
        "id": 103,
        "name": "Charlie",
        "age": 21
    },
    {
        "id": 104,
        "name": "David",
        "age": 25
    }
]


8. Create another file named Users.js.
9. Copy and paste the following code into Users.js and save it.
Users.js
const fs = require("fs");
const express = require("express");

const app = express();
const port = 8000;

let users = JSON.parse(
    fs.readFileSync("./users.json")
);

app.get("/users", (req, res) => {
    res.json(users);
});

app.get("/users/:id", (req, res) => {

    let id = req.params.id * 1;

    const find_user = users.find(
        e1 => e1.id == id
    );

    if (!find_user) {
        return res.status(404).json({
            status: "FAILED",
            message: "could not find the user"
        });
    }

    res.status(200).json(find_user);
});

app.listen(port, () => {
    console.log(`Server running on port ${port}`);
});


10. In the VS Code terminal, run the following command:
node Users.js


11. Press Enter. The following output should appear:
Server running on port 8000


12. Keep the server running.
13. Open Thunder Client from the VS Code sidebar.
14. Click New Request.
15. Select the GET method.
16. Enter the URL http://127.0.0.1:8000/users.
17. Click Send. The response should display all four users stored in users.json.
18. Change the URL to http://127.0.0.1:8000/users/101.
19. Click Send. The response should display:
{
    "id": 101,
    "name": "Alice",
    "age": 20
}


20. Change the URL to http://127.0.0.1:8000/users/102 and click Send to display Bob's details.
21. To test an invalid user ID, enter http://127.0.0.1:8000/users/999.
22. Click Send. The response should display:
{
    "status": "FAILED",
    "message": "could not find the user"
}

23. Check that the response status is 404 Not Found.
Q2 is completed.
