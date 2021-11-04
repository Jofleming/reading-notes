# 301 Reading 9 - Functional Programming

## Functional Programming Concepts


Questions:

1. What is functional programming?
A programming paradigm/a style of building the structure/elements of computer programs. It treats computation as the evaluation of mathematical functions. Avoids changing-state and mutable data.

2. What is a pure function and how do we know if something is a pure function?
It returns the same result if given the same arguments and it does not cause any observable side effects.

3. What are the benefits of a pure function?
The code is easier to test, and there is no need to mock anything.

4. What is immutability?
It cannot be changed over time. In this context data is immutable when its state cannot change after it's created.

5. What is Referential transparency?
When a function yields the same result for the same input. In the reading it gives `pure functions + immutable data = referential transparency`


## Node JS Tutorial for Beginners #6 - Modules and require()


Questions:

1. What is a module?
A bit of code with a certain functionality. In the video he gives the example of having a module that counts, and then you can call upon that module when you want to count something. Like the components we have been making in React

2. What does the word ‘require’ do?
require is on the global object. You set a value equal to require, pass in a path to a module that is exporting something to reference/use it in another file. Like the import we have been doing in React.

3. How do we bring another module into the file the we are working in?
Exporting what you want from the module, setting a variable equal to require with the path passed into it, and then calling that module in the file.

4. What do we have to do to make a module available?
Export what you want to access in the initial module. 



[Back](README.md)