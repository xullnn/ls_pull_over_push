## Object Oriented Programming

1. Describe "what is object in Ruby" in less than 30 words?

- In Ruby, objects can be think of as conceptual entities which have states(instance variables) and behaviors(methods), objects may have information exchanging with each other.

2. What are procedural programming and object-oriented programming?(this question is over the range of this course)
  - briefly describe what's the difference?
  - give examples about both of them, examples should be short, while showing some similarities and differences.

- procedural programming and OOP are both a type of programming paradigms.
  - precedural programming does things in [an imperative, step-by-step, logical fashion](https://launchschool.com/curriculum/courses/79f19170).
  - [Object-oriented programming](https://en.wikibooks.org/wiki/C%2B%2B_Programming/Programming_Languages/Paradigms#Object-oriented_programming) can be seen as an extension of procedural programming in which programs are made up of collections of individual units called objects that have a distinct purpose and function with limited or no dependencies on implementation.
- examples:

```ruby
bag = []
loop do
  batter = make_batter
  cake = bake_cake(batter)
  bag << cake
  break if bag.size == 5
end
```

```ruby
class Batter
end

class Cook
  attr_reader :bag

  def initialize
    @bag = []
  end

  def make_5_cakes
    while bag.size < 5
      bag << bake_cake
    end
  end

  private

  def bake(batter)
  end

  def bake_cake
    bake(Batter.new)
  end
end

Cook.new.make_5_cakes
```

3. Observe the example you just wrote, think of some of the pros and cons of OOP.

- pros
  - easier to understand in a conceptual level
  - individuality of objects make program more flexible
  - easier to manage interfaces
- cons
  - hard to observe program procedure in linear way
  - need to write more code
  - so flexible to come up with a best or good enough solution
  - may take more resources

4. In essence, OOP is just a programming paradigm, is there any other paradigms(y/n)?
- yes of course

5. Describe Encapsulation in 30 words.
- The behavior of deliberately hiding pieces of functionality(blocks of code) while exposing interfaces that the designer only want to expose. It's a form of data protection and interface management.

6. Describe Polymorphism in 30 words.
- In Ruby, Polymorphism describes the feature(implementation) that different receiver may return various values when we send same message to them.

7. Extract a key word(concept) from the definitions of Encapsulation and Polymorphism, this word should be one of the focusing points they all share.
- interface

8. What the `???` should be?
  - factory -- products, mould -- swords, blueprint -- buidings, ??? -- objects

- class

9. This type of relationship can be analogized to what relationship?
  - parent gives birth to child becomes parent gives birth to child becomes ...

- class and object

### Instance variable

10. Instance variables keep track of ??? and instance methods expose ??? for objects.
- states
- behaviors

11. What method will be called automatically every time you create a new object?
- initialize

12. Can an instance variable's lifespan be longer than the object which owns it?
  - can an instance variable keep existing after the the object which owns it 'died'?

- no, because instance variables are used to keep track of object's states
- no

13. What is the repsonsibility of an instance variable?

- instance variables are used to keep track of object's states

14. Uninitialized new instance variables can be referenced in an instance method, what is the return value?
  - is this the same with instance variables for Class?
  - is this the same with class variables?
  - give example(s) to demonstrate this

- `nil`
- yes
- no
- examples:

```ruby
class Dog
  class << Dog
    attr_reader :var
  end

  def print_instance_variable
    p @var
  end

  def print_class_instance_variable
    p self.class.var
  end

  def print_class_variable
    p @@var
  end
end

dog = Dog.new
dog.print_instance_variable
dog.print_class_instance_variable
dog.print_class_variable
```

### `to_s`, `puts`, `p`, string interpolation

15. Observe the code below, describe the relationships among `to_s`, `puts` and `p` in a reasonable way.
  - be aware of the difference between outputted message and return value

```ruby
class Dog
  attr_accessor :age
end
=> nil
dog = Dog.new
=> #<Dog:0x00007fca5d0a1c50>
dog.age = 4
=> 4

p dog
#<Dog:0x00007fca5d0a1c50 @age=4>
=> #<Dog:0x00007fca5d0a1c50 @age=4>

puts dog
#<Dog:0x00007fca5d0a1c50>
=> nil

p dog.to_s
"#<Dog:0x00007fca5d0a1c50>"
=> "#<Dog:0x00007fca5d0a1c50>"

dog.inspect
=> "#<Dog:0x00007fca5d0a1c50 @age=4>"

puts dog.inspect
#<Dog:0x00007fca5d0a1c50 @age=4>
=> nil

puts dog.to_s.inspect
"#<Dog:0x00007fca5d0a1c50>"
=> nil
```

- `to_s` can be understood as "string representation of ...", the return value is a string, the content of the string depends on how the object's class implements its own `to_s`.

- `inspect` also returns string. But vary from `to_s` it will return all information about an object, like instance variables which `to_s` usually does not. So we can think of `to_s` as a customized `inspect`

- both `to_s` and `inspect`'s return values are not the original objects, they are strings contains the information about objects

- `print` and `puts` both print out given object's string representation without any changing, then return `nil`.
  - difference is `puts` will append a new line character
  - if given object is not a string then `to_s` will first be called on the object

- `p`: For each object, directly writes `obj.inspect` followed by a newline to the program's standard output.
  - `p object` == `puts object.inspect` == `print(object.inspect + "\n")`

Look at the second example below, is `to_s` called before or after `.inspect` ? why

```ruby
"This is a #{dog}"
=> "This is a #<Dog:0x00007fcddb98e990>"

"This is a #{dog.inspect}"
=> "This is a #<Dog:0x00007fcddb98e990 @age=4>"
```

- `to_s` is called after `inspect`, because
  - if it first called `dog.to_s`, it will first returned a string that doesn't contain instance variable `@age`
  - then we call `inspect` on the previously returned **string**, the content would not have any change
  - so it must call `to_s` after `inspect` to show the full information of an object

16. Among `puts`, `p` and string interpolation, which ones will call `to_s`, if called, when?

- `puts` will call `to_s` if the given argument(s) is not a string
- `inspect` will not call `to_s` automatically but the return value is also string
- string interpolation will call `to_s` at the very end of its interior.

17. Would this code work out okay? Can you guess the message being outputted and what is the final return value?

```ruby
"#{
class Dog
  attr_accessor :name, :age
end

dog = Dog.new
dog.name = 'Babo'
dog.age = 3
puts "#{dog.name} is a #{dog.age} years old #{dog.class.name.downcase}"
}"
```

- it works.
- the printed out message would be `Babo is a 3 years old dog`
- the final return value is an empty string
  - the last line inside the whole string interpolation is `puts ...`, so the return value in the string interpolation is `nil`
  - so it's same as `"#{nil}"`, `nil` into a string interpolation will evaluate to nothing
  - so finally we get an emtpy string `""`

### Inheritance and mixin

18. When a class inherits from another class, what the two main things it can get from the superclass?
  - hint: an object can has its own () and ().

- states(attributes) and behaviors(methods)

19. Think of these words: lookup path, `super`, inherit, override. Choose one word to describe the directionality of these words.
  - (outward / inward / upward / downward)

- upward

20. Modules have two main features, what are they?

- holding reusable methods which can be mixed into other classes.
- namespacing: organize similar(or same type) classes into one module can facilitate management and avoid class name collision

21. Given this code, how to call `shine` method within the `show` method in `Face` class then print out `Shining`

```ruby
module Features
  def self.shine
    puts "Shining"
  end
end

class Face
  include Features
  def show
    # how?
  end
end

Face.new.show
```

```ruby
def show
  Features.shine
end
```

22. What is the output of the code?
  - what is the rule underlying?

```ruby
module Breathable
  def breathe_in
    puts 'Oxygen...'
  end

  def breathe_in
    puts 'Whatever...'
  end
end

class Creature
  include Breathable
end

class Plant < Creature
end

class Animal < Creature
end

class Human < Animal
end

Human.new.breathe_in
```

- the outputted message is `Whatever...`
  - human object didn't find `breathe_in` in its class
  - so it keep looking for it upwards following the inheritance chain
  - until it went into `class Creature` which included `module Breathable`
  - in `module Breathable`, the method lookup order is down to up, so the 'Whatever' one will override the 'Oxygen' one

### Assignment Branch Condition Size - ABC size

23. Based on the class definition:

```ruby
class Dog
  attr_reader :age
end
```

How many method calls are there in this method?

```ruby
def a_method
  if age < 5
  elsif age > 10
  elsif age % 10 == 0
  end
end
```
- after we wrote `attr_reader :age`, `age` or `self.age` would be a method call, so
  - `age` + 3
  - `<`, `>`, `%` and `==` are all fake operators + 4
- totally 7

What about this?

```ruby
def a_method
  age_value = age
  if age_value < 5
  elsif age_value > 10
  elsif age_value % 10 == 0
  end
end
```

- `age` was called once + 1
- `age_value` is a variable points to `age`'s value so it's not a method call
- `<`, `>`, `%` and `==` are all fake operators + 4
- totally 5

How many condition branches are there in the method?

```ruby
def a_method
  if age < 5
  elsif age > 10
  elsif age % 10 == 0
  end
end
```

- `if` + `elsif` + `elsif` = 3

How about this?

```ruby
def a_method
  if !(5..10).include?(age)
  elsif age % 10 == 0
  end
end
```

- `if` + `elsif` = 2

Count the exact number of Assignments, Branches and Conditions in `a_method`

```ruby
class Dog
  attr_reader :age

  def a_method
    if age > 10
      self.age = 9
    elsif age > 8
    elsif age > 7
    elsif age > 6
    elsif age > 5
    elsif age > 4
    elsif age > 3
    elsif age > 2
    elsif age > 1
    end
  end
end
```

Method call:
  - `age` + 10
  - `>` + 9

Assignment
  - `self.age = 9` + 1

Condition branches:
  - + 9

### Collaborator objects

24. Can an object be the state of another object?
  - give an example

- yes
- example

```ruby
class Person
end

class Dog
  attr_reader :name, :age, :owner

  def initialize(name, age)
    @name = name
    @age = age
    @owner = Person.new
  end
end

dog = Dog.new('Puppy', 2)
dog.name.is_a?(Object)
dog.age.is_a?(Object)
dog.owner.is_a?(Object)
```

### Exceptions

25. Look at the code below:

```ruby
class RustyError < StandardError; end

class Clown
  attr_accessor :balls
  def throw
    balls.each do |ball|
      puts "Throwing #{ball}. Catch me!"
      raise(ball, "Didn't catch it...") if ball == RustyError
    end
  end

  def play
    throw
  rescue StandardError => e
    puts e.message
  end
end

balls = [NameError, ArgumentError, RustyError, RuntimeError]
clown = Clown.new
clown.balls = balls
# clown.play
```

Before running the last line
  - how many exceptions will be raised
  - how many times the message `"Throwing ... . Catch me!"` will be printed out?
  - what is the last printed out message?
  - in `balls` array, which exception classes can be rescued by `rescue StandardError` if any of them is been raised? Why?

- only `RustyError` will be raised since we specified a condition `if ball == RustyError`
- 3 times.
- the last printed out message is `"Didn't catch it..."`, it's printed by `puts e.message` in `play` method's `rescue` branch
- all of them. Because all of them are descendant classes of `StandardError`, `rescue StandardError` will rescue `StandardError` and all of its descendant classes

### Reference constant

26. How to reference the constant `NUMBER` in `a_method` in this case?

```ruby
class A
  def a_method
  end
end

class B < A
end

class C < B
  NUMBER = 1
end
```

- `NUMBER` is first initialized in `class C`
- `class A` is at the upstream of `C` we cannot access a constant downwards

```ruby
class A
  def a_method
    C::NUMBER
  end
end
```

27. How to reference the constant `NUMBER` in `a_method` in this case?
  - come up with more than 5 ways, it doesn't have to be concise, just let it work

```ruby
class A
  NUMBER = 1
end

class B < A
end

class C < B
  def a_method
  end
end
```

- core rule
  - descendant class can access superclass's constant without specify first initialized place(class)
  - looking upward

```ruby
class C < B
  def a_method
    # 1: NUMBER; 2: C::NUMBER; 3: B::NUMBER; 4: A::NUMBER; 5: self.class::NUMBER
    # 6: self.class.superclass::NUMBER; 7: self.class.superclass.superclass::NUMBER
    # 8: C.superclass::NUMBER; 9: B.superclass::NUMBER ....
  end
end
```

28. How to reference the constant `NUMBER` in `a_method` in this case?

```ruby
module X
  NUMBER = 1
end

class A
end

class B < A
  def a_method
  end
end
```

- answer

```ruby
class B < A
  def a_method
    X::NUMBER
  end
end
```

29. How to reference the constant `NUMBER` in `a_method` in this case?

```ruby
module X
  NUMBER = 1
end

class A
  include module
end

class B < A
  def a_method
  end
end
```

- answer
  - easiest way is ignoring classes, get it directly from the module

```ruby
class B < A
  def a_method
    X::NUMBER
  end
end
```

30. How to reference the constant `NUMBER` in `a_method` in this case?

```ruby
module X
  class A
    NUMBER = 1
  end
end

class B
  def a_method
  end
end
```

- answer

```ruby
class B
  def a_method
    X::A::NUMBER
  end
end
```

31. Look at the code:

```ruby
module X
  class A
    NUMBER = 1
  end

  class B < A
  end
end

class C
  def a_method
  end
end
```

- how to reference `NUMBER` inside `a_method` from `class C` without referencing `class A`?

- answer

```ruby
class C
  def a_method
    X::B::NUMBER
  end
end
```

### Truthiness

32. What message will be printed out? Why?

```ruby
def count_things(num = 2)
  if 'false' || num / 0 > 1
    puts "Cloudy day!"
  else
    puts "Sunny day!"
  end
end

def calculate
  count_things
rescue ArgumentError, ZeroDivisionError
  puts "Windy day!"
end

calculate
```

- calling `count_things` without passing in argument will not raise exception since we specified default value for the argument while defining this method
- `'false' || num / 0 > 1` will not raise exception, because the short circuiting mechanism of Ruby
  - while using `||`, once a truthy value appears, the whole expression is surely to be truthy so the rest of the expression will be omitted
  - in this case `'false'` will first evaluated to true, so ruby never run `num / 0 > 1`
- no exceptions so program goes into the `if` branch in `count_things` method
- so the outputted message is `"Cloudy day!"`

### Others

33. What's the final returned value of `p Dog.new.age = 2`? Why?

```ruby
class Dog
  def age=(age)
    @age = age
    return 'I am a dog.'
    age += 100
  end
end

p Dog.new.age = 2
```

- whatever you do, the return value of a setter method in Ruby is always the original argument
- so the return value is 2

34. Can the code below work out ok?

```ruby
class Dog
  private
  attr_writer :age
end

Dog.new.age = 2
```

- no
  - private method `age=` cannot be used outside of the class definition

How about this?

```ruby
class Dog
  def set_age(age)
    dog = self
    dog.age = age
  end

  private
  attr_writer :age
end

Dog.new.set_age(2)
```

- no
  - though setter method is the only exception which accepts a reciever, but
    - the reciever must exactly be `self`
    - anyother variables pointing to current instance are not accepts even they are pointing to the same thing as `self`

Then how about this?

```ruby
class Dog
  def set_age(age)
    self.age = age
  end

  private
  attr_writer :age
end

Dog.new.set_age(2)
```

- why the first case failed?
- according to the last 2 cases, can you explain the rule of using private setter method?

 *Updated*

### Module and Multiple Inheritance

35. Give an example which can illustrate the use of mixin in Ruby core.

- A exmaple about `class String`, `class Hash`, `class Array` and `class Numeric`
- These classes are relating to the main data types that we use very often in Ruby.

If we check the ancestors for each of them:
```ruby
> [Array, Hash, String, Numeric].each { |main_type| p main_type.ancestors }
[Array, Enumerable, Object, Kernel, BasicObject]
[Hash, Enumerable, Object, Kernel, BasicObject]
[String, Comparable, Object, Kernel, BasicObject]
[Numeric, Comparable, Object, Kernel, BasicObject]
# => [Array, Hash, String, Numeric]
```

Tow things here need to be noticed:
- not all ancestors are classes
- their direct superclass is `class Object`

Actually `Enumerable`, `Comparable` and `Kernel` are modules, not classes. Modules are like pluggable packages that can enable specific classes to do many things. Once a class includes a module, its instances and its subclasses' instances are able to do things in this module.(graph may not showed complete, click link below to see full)

https://s3-ap-southeast-1.amazonaws.com/image-for-articles/image-bucket-1/core.jpg

![](https://s3-ap-southeast-1.amazonaws.com/image-for-articles/image-bucket-1/core.jpg)
*Kernel is included in `class Object`, this is not labelled in the graph.*

36. `class C` inherits from `class B` inherits from `class A` inherits from `class Object`. Is this multiple Inheritance?

- If not, give an example of multiple inheritance

- No. It's not. Multiple inheritance means one class directly inherits from many classes.
- exmaple:

```ruby
class A; end

class B; end

class C < A; end
class C < B; end
```

[here's a discussion on stack overflow](https://stackoverflow.com/questions/10254689/multiple-inheritance-in-ruby)

37. Using a code example to illustrate why sometimes single inheritance cannot meet the needs.

38. To solve the problem mentioned in previous question, what is the solution in Ruby, what mechanism does Ruby use to simulate(mimic) multiple inheritance, give code example to illustrate this.

- answer 37 and 38

Say we have these classes:
- `Animal`
- `Mammal`, `Fish`, `Bird`
- `Whale`, `Dog`, `Cat`, `Penguin`, `Woodpecker`

Their relationships can be represented by code:

```ruby
class Animal; end

class Mammal < Animal
end

class Fish < Animal
  # able to swim
end

class Bird < Animal
end

class Whale < Mammal
   # able to swim
end

class Dog < Mammal
  # able to swim
  # able to walk
end

class Cat < Mammal
  # able to walk
end

class Penguin < Bird
  # able to swim
  # able to walk
end

class Woodpecker < Bird
  # able to fly
end
```

Then we can visualize the relationships in thie graph(graph may not showed complete, click link below to see full)

https://s3-ap-southeast-1.amazonaws.com/image-for-articles/image-bucket-1/animals.jpg

![](https://s3-ap-southeast-1.amazonaws.com/image-for-articles/image-bucket-1/animals.jpg)

According to this graph we can see:
- we cannot include `Walkable` and `Swimmable` into `Mammal`, since one of the mammals `Cat` cannot swim, also `Whale` cannot walk
-  we cannot incldue `Flyable` into `Bird` because there is an exception `Penguin` cannot swim, it just walks...

When focusing on the classes which include 2 modules -- `Dog` and `Penguin` in this case
- `Dog` can swim and walk
  - but it cannot inherit from `class Fish` to enable itself to swim, because it is not fish
  - it cannot inherit from `class Mammal` to enable itself to walk since the existence of `Whale` disproves 'all mammals can walk'

- `Penguin` can swim and walk too
  - but it cannot inherit from `class Mammal` to enable itself to walk(same reason with Dog)
  - it cannot inherit from `class Fish` to enable itself to swim, because it is not fish

Even though Ruby allowed multiple inheritance, this problem cannot be solve. So we have to distribute different module to different classes as needed.
