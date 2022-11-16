# React Testing Library Sheat-sheet

## importance of testing

1. Catch Bugs
2. Increases the confidence of the application.
3. Speeds up QA time
4. Can serve as documentation

## Types of Testing

1. Unit Tests
   Testing Single unit (Component)

2. Integration Tests
   Testing interaction between components

3. End to End (E2E) Test
   semulate the userflow

## Test blocks

1. render the component we want to test

2. find elements we want to interact with

3. iteract with those elements

4. Assert that the results are as what we expected

## Query methods

1. getBy : Fails if not match or in more then one match, passes in one match, No await.
2. findBy : Fails if not match or in more then one match, passes in one match, support await.
3. queryBy : returns null if not match, passes in one match return array, Fails in more then one match, no await.
4. getAllBy : Fails if not match, passes and return array in one or more then one match, No await.
5. findAllBy : Fails if not match, return Array in or more then one match, support await.
6. queryAllBy : Passes and returns array in all situations, no await

## Priority

### Accessible by Everyone

1. getByRole
2. getByLabelText
3. getByPlaceHolderText
4. getByText

### Semantic Queries

1. getByAllText
2. getByTitle

### getByTestId

1. getByTestId

## How to write Test

first we need to import render and screen from react testing labrary, then render the component, get the element, and then the result expected  
example

### Unite test

```javascript
import { render, screen } from "@testing-library/react";
import Header from "../Header";

it("Test header", () => {
  render(<Header title="My header" />);
  const headingElement = screen.getByText(/my header/);
  expect(headingElement).toBeInTheDocument();
});
```

```javascript
import { render, screen } from "@testing-library/react";
import TodoFooter from "../TodoFooter";
import { BrowserRouter } from "react-router-dom";

const MockTodoFooter = ({ numberOfIncompleteTasks }) => {
  return (
    <BrowserRouter>
      <TodoFooter numberOfIncompleteTasks={numberOfIncompleteTasks} />
    </BrowserRouter>
  );
};

it("should render the correct amount of incompled tasks", async () => {
  // render the component we want to test
  render(<MockTodoFooter numberOfIncompleteTasks={5} />);

  // Find the element we want to interact with
  const paragraphElement = screen.getByTestId("para");
  // interact with emenets and assert thas the results are expected
  expect(paragraphElement).toBeInTheDocument(/5 tasks left/i);
});
```

## Add events to test type and Click

```javascript
const mockedSetTodos = jest.fn();
describe("Test AddTodo", () => {
  it("Should have empty input after clicking on the add button", async () => {
    render(<AddInput todos={[]} setTodos={mockedSetTodos} />);
    // get button and input
    const inputElement = screen.getByPlaceholderText(/add a new task here/i);
    const buttonElemnt = screen.getByRole("button", { name: /Add/ });
    // change to todo value / fill the input
    fireEvent.change(inputElement, {
      target: { value: "Learn React testing" },
    });
    // click to add button
    fireEvent.click(buttonElemnt);
    expect(inputElement.value).toBe("");
  });
});
```

### Integration test

you write in the parent component

```javascript
import { screen, render } from "react-testing-libary";
import Tod from "../Todo";
describe("Todo", () => {
  it("should add the task to the array of tasks", async () => {
    // the todo componenet  is already wrapped in BrouserRoute, because it contains Link router
    render(<MockTodo />);
    // Get Elements
    const inputElemnet = screen.getByPlaceholderText(/add a new task here.../i);
    const buttonElement = screen.getByRole("button", { name: /Add/i });
    // interact with the element
    fireEvent.change(inputElemnet, { target: { value: "This is a new Task" } });
    fireEvent.click(buttonElement);
    const divElement = screen.getByText(/This is a new Task/i);
    // assert that the result is what we have expected
    expect(divElement).toBeInTheDocument();
  });
});
```

check if the list is empty

```javascript
it("should not add task if the input is empty", async () => {
  render(<MockTodo />);
  addTask([""]);
  const tasksElements = screen.queryAllByTestId("task-container");
  expect(tasksElements.length).toBe(0);
});
```

Test Fitched data

```javascript
import { render, screen } from "@testing-library/react";
import { BrowserRouter } from "react-router-dom";
import FollowersList from "../FollowersList";

const MockFolllowersList = () => {
  return (
    <BrowserRouter>
      <FollowersList />
    </BrowserRouter>
  );
};

describe("FollowersList", () => {
  it("Should render follower items", async () => {
    render(<MockFolllowersList />);
    const followerDivElement = await screen.findByTestId(/follower-item-0/i);
    expect(followerDivElement).toBeInTheDocument();
  });
```
