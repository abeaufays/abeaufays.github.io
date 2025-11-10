---
layout: post
title: Functional Core, Imperative Shell
---

# Functional Core, Imperative Shell

## Introduction

[Story telling: I was developping a new part of application earlier this year.]  
In 3 parts:

- **Application**: orchestration between different modules
- **Domain**: expressing the business logic
- **Data**: defining the way data is persisted

The question became, when should we persist the data ?

The most straightforward way to do this would be to let the domain handle data persistence as part of it's action.

```python
# in application
def application(id):
    with open_transaction():
        domain_action()
        other_action()
    log_stuff()

# in domain
def domain_action(id):
    # get the object
    thing = data.get_thing(id)
    # do the thing
    thing.apply_whatever_business_logic()
    # persist in database
    data.save(thing)
```

## TL;DR

I now believe a better way to approach this is to make the domain part functional, and let the application layer handle data persistence.

```python
# in application
def application(id):
    with open_transaction():
        thing = data.get_thing(id)

        thing = domain_action(thing)
        thing = other_action(thing)

        data.save(thing)
    log_stuff()

# in domain
def domain_action(id):
    # do the thing
    thing = apply_whatever_business_logic(thing)
    return thing
```

## What is it about ?

### Functional

#### What's functional programming

The first time I heard about functional programming was in a conference.  
[Speak about theory of functional programming and how intro can be super confusing]

#### What ?

- Avoid side effects
- Lightweight

### Core

- Importance of isolating business rules
  - Mention DDD
-

### Imperative

### Shell

## Practical benefits

- Makes your domain focus on business logic
- Easy tests
- Makes it easy to experiment with code in a repl / notebook
