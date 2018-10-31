## Object Oriented Programming

1. Describe "what is object in Ruby" in less than 30 words?

2. What are procedural programming and object-oriented programming?
  - briefly describe what's the difference?
  - give examples about both of them, examples should be short, while showing some similarities and differences.

3. Observe the example you just wrote, think of some of the pros and cons of OOP.

4. In essence, OOP is just a programming paradigm, is there any other paradigms(y/n)?

5. Describe Encapsulation in 30 words.

6. Describe Polymorphism in 30 words.

7. Extract a key word(concept) from the definitions of Encapsulation and Polymorphism, this word should be one of the focusing points they all share.

8. What the `???` should be?
  - factory -- products, mould -- swords, blueprint -- buidings, ??? -- objects

9. This type of relationship can be analogized to what relationship?
  - parent gives birth to child becomes parent gives birth to child becomes ...

### Instance variable

10. Instance variables keep track of ??? and instance methods expose ??? for objects.

11. What method will be called automatically every time you create a new object?

12. Can an instance variable's lifespan be longer than the object which owns it?
  - can an instance variable keep existing after the the object which owns it 'died'?

13. What is the repsonsibility of an instance variable?

14. Uninitialized new instance variables can be referenced in an instance method, what is the return value?
  - is this the same with instance variables for Class?
  - is this the same with class variables?
  - give example(s) to demonstrate this

### `to_s`, `puts`, `p`, string interpolation

15. Observe the code below, describe the relationships amony `to_s`, `puts` and `p` in a reasonable way.
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

16. Look at the second example below, is `to_s` called before or after `.inspect` ? why

```ruby
"This is a #{dog}"
=> "This is a #<Dog:0x00007fcddb98e990>"

"This is a #{dog.inspect}"
=> "This is a #<Dog:0x00007fcddb98e990 @age=4>"
```

16. Among `puts`, `p` and string interpolation, which ones will call `to_s`, if called, when?

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

### Inheritance and mixin

18. When a class inherits from another class, what the two main things it can get from the superclass?
  - hint: an object can has its own () and ().

19. Think of these words: lookup path, `super`, inherit, override. Choose one word to describe the directionality of these words.
  - (outward / inward / upward / downward)

20. Modules have two main features, what are they?

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

How many branches are there in the method?

```ruby
def a_method
  if age < 5
  elsif age > 10
  elsif age % 10 == 0
  end
end
```

How about this?

```ruby
def a_method
  if !(5..10).include?(age)
  elsif age % 10 == 0
  end
end
```

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

### Collaborator objects

24. Can an object be the state of another object?
  - give an example

### Truthiness

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

### Others

32. What's the final returned value of `p Dog.new.age = 2`? Why?

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

33. Can the code below work out ok?

```ruby
class Dog
  private
  attr_writer :age
end

Dog.new.age = 2
```

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
