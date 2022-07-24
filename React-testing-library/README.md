# React Testing Library Sheat-sheet


## importance of testing 

1. Catch Bugs
2. Increases the confidence of the application.
3. Speeds up QA time 
4. Can serve as documentations

## Types of Testing

1. Unit Tests
Testing Single unit (Component)

2. Integration Tests
Testing interaction between components

3. End to End (E2E) Test
semulate the userflow 

## Test blocks

1. render the component we xant to test 

2. find elements we want to interact with

3. iteract with those elements 

4. Assert that the results are as expected

## Query methods

1. getBy : Fails if not match or in more then one match, passes in one match, No await.
2. findBy : Fails if not match or in more then one match, passes in one match, support await. 
2. queryBy : returns null if not match, passes in one match return array, Fails in more then one match, no await. 
1. getAllBy : Fails if not match, passes and return array in one or more then one match, No await. 
2. findAllBy : Fails if not match, return Array in or more then one match, support await.
2. queryAllBy : Passes and  returns array in all situations, no await 
