name: inverse
layout: true
class: middle, inverse

---

# Modular code development

## [Radovan Bast](http://bast.fr)

### [NeIC](https://neic.nordforsk.org)/ [UiT The Arctic University of Norway](https://uit.no)

Text is free to share and remix under [CC-BY-SA-4.0](https://creativecommons.org/licenses/by-sa/4.0/).

Code examples: [MIT license](http://opensource.org/licenses/mit-license.html)

Credits: [Jonas Juselius](https://github.com/juselius),
         [Roberto Di Remigio](http://totaltrash.xyz),
         [Ole Martin Bjørndalen](https://github.com/olemb)

---

layout: false

## Simple vs. easy

<img src="img/development-speed.svg" style="width: 80%;"/>

---

## [The tar pit](http://shaffner.us/cs/papers/tarpit.pdf)

- Over time software tends to become harder and harder to reason about
- Small changes become harder to implement
- Bugs start appearing in unexpected places
- More time is spent debugging than developing
- Complexity strangles development because it does not scale well

(Slide adapted from [Complexity in software development by Jonas Juselius](https://github.com/scisoft/complexity))

---

## Modularity and composition

- Build complex behavior from simple components
- We can reason about the components and the composite
- Composition is key to managing complexity
- Modularity does not imply simplicity, but is enabled by it

<img src="img/knit_vs_lego.jpg" style="width: 100%;"/>

(Slide taken from [Complexity in software development by Jonas Juselius](https://github.com/scisoft/complexity))

---

## Purity

- Pure functions have no notion of state: They take input values and return
  values
- Given the same input, a pure function *always* returns the same value
- Function calls can be optimized away
- Pure function == data


<img src="img/bugbarrier.jpg" style="width: 40%;"/>

(Slide taken from [Complexity in software development by Jonas Juselius](https://github.com/scisoft/complexity))

---

## Example: pure vs. stateful

### a) pure

```python
# function which computes the body mass index
def get_bmi(mass_kg, height_m):
    return mass_kg/(height_m**2)

# compute the body mass index
bmi = get_bmi(mass_kg=90.0, height_m=1.91))
```

### b) stateful

```python
mass_kg = 90.0
height_m = 1.91
bmi = 0.0

# function which computes the body mass index
def get_bmi():
    global bmi
    bmi = mass_kg/(height_m**2)

# compute the body mass index
get_bmi()
```

---

## Pure functions are easier to

- Test
- Understand
- Reuse
- Parallelize
- Simplify
- Optimize
- Compose


### Examples

- Unix shell
- Mathematical functions

---

## Recommendations

- I/O is impure
- Keep I/O on the outside and connected
- Keep the inside of your code pure/stateless

<img src="img/good-vs-bad.svg" style="width: 100%;"/>

---

## Divide and conquer

- Split the code up
- Construct your program from parts:
  - functions
  - modules
  - packages (Python) or libraries (C or or C++ or Fortran)

## Abstract

- Rule of 3: if you need it 3rd time, abstract it into something more general

---

## Functions, functions, functions

- Build your code from functions
- Break your code down to more functions
  - if you have too many levels of indentation
  - if a function gets too long
  - if a function does more than one thing
  - if you find it hard to name a function

---

## Encapsulation

- Hide internals by language or by convention (header file in C/C++,
  public/private in Fortran, underscores in Python)
- "Python has no locked doors; it's a consenting adults language.
  If you open the door you're responsible for what you see." [R. Hettinger]
- Expose the "what", hide the "how"

## Import and export

- Import as little as possible
- Export as little as possible

---

## Simplicity and clarity before elegance before efficiency

### Avoid premature optimization

- Do not optimize
- If you have to optimize, optimize later
- If you have to optimize, measure, do not guess

### Simple is better than complex

- If you cannot understand or explain a function on a cold gray Monday morning before coffee, it is too complex. (Quote adapted from [Pieter Hintjens, Social Architecture, 2009](https://www.gitbook.com/book/hintjens/social-architecture/details))
- "Only God and I knew": https://twitter.com/farbodsaraf/status/1006215492607111168

---

## Conclusions

- Divide and isolate
- Introduce tests early
- Compose your code out of **pure functions**
- Prefer immutable data structures
- Do not overuse classes

---

## Discuss in a group

- What best practices can you recommend to arrive at well structured, modular
  code in your favourite programming language?
- What would you recommend your colleague who starts in the same programming language?
- How do you deal with code complexity in your projects?

### Write down your findings in a shared document

- Later we will discuss these together
- We can share and discuss our personal experiences

---

## Possible discussion points are below

Show how to structure a Python project:

- https://github.com/bast/somepackage

Become friends with these packages:

- https://docs.python.org/3/library/itertools.html
- https://docs.python.org/3/library/collections.html

---

## Main function vs. global scope

### a) main function

```python
def do_something(input):
    # ...
    return something

def main():
    result = do_something(2.0)
    print(result)

if __name__ == '__main__':
    main()
```

### b) global scope

```python
def do_something(input):
    # ...
    return something

result = do_something(2.0)
print(result)
```

---

## Implicit vs. named arguments

### a) implicit

```python
bmi = get_bmi(90.0, 1.91)
```

### b) named

```python
bmi = get_bmi(mass_kg=90.0, height_m=1.91)
```

---

## File I/O

### a) pass file name

```python
# parse_input1 function opens and reads the file
result = parse_input1(file_name)
```

### b) pass file handle

```python
with open(file_name, 'r') as f:
    # parse_input2 reads the file
    result = parse_input2(f)
```

### c) pass data

```python
with open(file_name, 'r') as f:
    input_lines = f.readlines()
    # parse_input3 does not know anything about the file
    result = parse_input3(input_lines)
```

---

## Loop vs. map/filter

### a) loop

```python
numbers = [1, 2, 3, 4, 5]

squares = []
for number in numbers:
    squares.append(number**2)

odds = []
for number in numbers:
    if number%2 == 1:
        odds.append(number)
```

### b) map and filter

```python
numbers = [1, 2, 3, 4, 5]

squares = map(lambda x: x**2, numbers)
odds = filter(lambda x: x%2 == 1, numbers)
```

---

### a) class

```python
class Pet:
    def __init__(self, name):
        self.name = name
        self.hunger = 0
    def go_for_a_walk(self):
        self.hunger += 1

my_dog = Pet('Pluto')
my_dog.go_for_a_walk()
print(my_dog.hunger)
```

### b) named tuple

```python
from collections import namedtuple

def go_for_a_walk(pet):
    new_hunger = pet.hunger + 1
    return pet._replace(hunger=new_hunger)

Pet = namedtuple('Pet', ['name', 'hunger'])

my_dog = Pet(name='Pluto', hunger=0)
my_dog = go_for_a_walk(my_dog)
print(my_dog.hunger)
```
