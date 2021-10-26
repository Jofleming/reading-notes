# 301 Reading 1: Introduction to React and Components

## Component-Based Architecture

Component-based architecture focuses on changing the design into functional or logical components which better represent well-defined communication interfaces containing methods, events, and properties. Provides a higher level of abstraction and divides the problem into sub-problems, each associated with component partitions.

The main goal of this is reusability. A component is supposed to encapsule functionality/behvior of a software element into a reusable binary unit.

A component is a modular and reusable set of well-defined functionality. It can have three different views:
Object-oriented view
Conventional view
Process-related view

Characteristics of Components:
Reusability
Replaceable
Not Context Specific
Extensible
Encapsulated
Independent

Advantages:
Ease of Deployment
Reduced Cost
Ease of Development
Reusable
Modification of Techincal Complexity
Reliability
System Maintenance and Evolution
Independent


## What is "Props" and how to use it in React?

Props is a special keyword in React that is used for passing data from on component to another. Data is passed one way, from parent to child. This data is read only. The parent should not be changed from a child component.

Steps:
1 Define an attribute and its value (data)
2 Pass it to child component(s) using Props
3 Render props data

Write react components similar to HTML. Attribute values use curly brackets though, component names are capitalized, and brackets are self closing.

```
<ChildComponent someAttribute={} attributeTwo={} />
```

Props are passed like arguments in a function to other components.


[Back](README.md)