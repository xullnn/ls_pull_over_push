## Ruby Foundations: More Topics

1. What's the definition of 'closure'?
  - why we call it 'closure'?
  - Is closure a unique concept in Ruby?

- answer
  - A closure is a **general programming concept** that allows programmers to save a "chunk of code" and execute it at a later time.
    - It's called a "closure" because it's said to bind its surrounding artifacts (ie, variables, methods, objects, etc) and build an "enclosure" around everything so that they can be referenced when the closure is later executed.
    - no.

2. Give a code example to show the use of a closure.

```ruby
module Cookable
  def melt; @melted = true; self; end
  def bake; @baked = true; self; end
  def boil; @boiled = true; self; end
  def steam; @steamed = true; self; end
end

class Eatable
  include Cookable
end

class Cheese < Eatable; end
class Chicken < Eatable; end
class Beef < Eatable; end

def make_a_dish(food)
  # buy(food)
  yield(food.new) if block_given?
  # clean_up_table
end

p make_a_dish(Cheese) { |food| food.melt }
p make_a_dish(Chicken) { |food| food.steam.bake }
p make_a_dish(Beef) { |food| food.boil.bake }
```

In the above code, the `make_a_dish()` method accepts the type of food, but it doesn't know or care about how to cook the food, so it give this part of autonomy later to the method caller, by accepting a chunk of code(block) at the calling time.

3. What's the 'binding' of a closure?

- answer
  - in order to be properly executed later, a closure will 'memorize' the needed artifacts around it during its creation. The closure may reference one or more of these artifacts when it is being executed later. All these information absorbed during closure's creation is called its binding.

4. Given the code below:

```ruby
[1, 2, 3, 4, 5].each.with_index(1) do |n, i|
  p n * i
end
```

output:

```
1
4
9
16
25
 => [1, 2, 3, 4, 5]
```

- answer

  - what's the initial receiver(caller)?
    - array `[1, 2, 3, 4, 5]`
  - how many methods did we call outside the block?
    - two: `each` and `with_index`
  - how many methods did we call inside the block?
    - two: `p` and `*`
  - did we pass any arguments to any outside-block methods?
    - yes: we pass one argument to the `with_index` method
  - how should we call `n` and `i` in `|n, i|`
    - respectively, what each of them represents?
    - what's the difference between 'argument' and 'parameter'

    - `n` and `i` in `|n, i|` called block parameters
    - inside the block, `n` represents each element in the caller, `i` represents the corresponding index in every iteration step.
    - `parameter` means the name of the real passed in value, like in `def a_method(x); end`, we would say we defined `a_method` which takes one parameter `x`; but when we call the method `a_method("a")`, the `"a"` can be called the argument passed in.
  - what's the return value of every iteration step, how the return values were used?
    - the return values of every block is `1, 4, 9, 16, 25`,
    non of them is used, means non of them affects the method's return value.
  - what's the final return value of the whole code expression
    - `[1, 2, 3, 4, 5]` the original caller.

5. What is the determinative factor that can decide the return value of a method(which optional accepts a block)?

- answer
  - it is the implementation of the method, or say how we initially defined the method. We could choose to let the block's return value affects the method's return value, we also could choose not to.

6. Can we pass a block to any methods?
  - yes. Syntactically, every method in Ruby accepts a block as an implicit argument.

7. Given this method definition:

```ruby
def a_method(a, b)
end
```

Which would raise exception by following expressions:

```ruby
#1
a_method(1,2)
#2
a_method(1,2) { puts "" }
#3
a_method(1) { puts "" }
#4
a_proc = Proc.new { puts "" }
a_method(1, a_proc)
#5
a_proc = Proc.new { puts "" }
a_method(1, 2, a_proc)
```

- Through the above code, can you tell what's the difference between block and proc?
  - use code example to further demonstrate your answer

- answer
  - first need to identify that the method requires exactly 2 arguments
  - second need to know block is not an object and every method in Ruby accepts a block as an implicit argument

  - `#3` will raise ArgumentError, since block is not an object but the method requires 2
  - `#5` will raise ArgumentError, since `Proc` object is an object, the method doesn't accept more than 2 args.

8. In what scenario a `LocalJumpError` will be raised?

- answer
  - we wrote `yield` inside a method definition
  - we call the method without giving a block

9. How to avoid this kind of situation?

- answer
  - add `if block_given?` or other appropriate conditional

10. How to implement a method can be called with or without giving a block? (Two ways)

- answer
  - use `&block` to capture the possibly passed in block
  - use `yield` accompanied with a proper conditional

11. Given these method definitions:

```ruby
#1
def method_one(arg)
  yield(arg)
end
#2
def method_two(&arg)
  &arg.call
end
#3
def method_three(&arg)
  arg.call('a')
end
#4
def method_four(arg)
  yield(arg, 1, 'a')
end
#5
def method_five(a, &arg)
  yield(a)
  arg.call
end
```

Which definition(s) are wrong, why?

- answer
  - the key is knowing the difference between `&arg` and `arg` when defining a method
  - bare `arg` in the argument list means this method explicitly requires 1 argument or say one object
  - `&arg` doesn't mean that, it means this method will capture the potentially passed in block, convert it into a proc, and assign that proc to `arg`, and block is not an object, so this method doesn't accept any object as its argument.

  - so accordingly
    - `#2` is wrong on syntactic level, inside the method definition we use `arg` without `&` to call out the captured-then-converted proc.
    - others are fine

12. Given this method:

```ruby
def method_five(a, &arg)
  yield(a)
  arg.call
end
```

What error will be raised for each expression
  - why?
  - how to fix?

```ruby
#1
method_five { puts 'Hello World.' }
#2
method_five('Hello') { |x| puts(x + ' World.') }
#3
a_proc = Proc.new { |x| puts(x + ' World.') }
method_five('Hello', a_proc)
```

- answer
  - `#1`: ArgumentError will be raised, because the method requires one argument but the calling expression didn't give any.
  - `#2`: NoMethodError will be raised
    - `yield(a)` will be fine
    - `arg.call` didn't pass any argument to the captured-then-converted proc `arg`, so the block parameters will be parsed to `nil`s, then we performed `x + ' World.'`, `x` is `nil` here, that's where the error was raised.
    - `#3`: ArgumentError will be raised, since the method only accepts one argument but we passed the proc object as the second argument.

13. Describe some scenarios that we may need block, better accompanied with code example.

  - answer
    - a typical scenario is when we need some 'before and after' operation on our program.
    - for example when we are dealing with `File` objects, we need to first open it then perform some processings, then close the file at the end. The 'open' and 'close' operations are the same steps would be performed every time, but the processing procedure might vary.

```ruby
File.open('../sample.txt', 'w') do |f|
  # do some processing about the file object `f`
end
```

  - though we only performed the file processing without writing the `open` and `close`, the `File::open` method actually did that for us, it's implemented in the method definition. Thus we can focus on the main purpose of processing file and no worry about forgetting close the file or bothering open the file every time.

14. Given this method definition:

```ruby
def a_method(&block)
  p block.class
end
```

What's the results of running these expressions:

```ruby
#1
a_method
#2
a_method { }
#3
proc_obj = Proc.new { p "In the proc." }
a_method(proc_obj)
```

- answer
  - `#1`: `Nil`
  - `#2`: `Proc`
  - `#3`: this will raise ArgumentError

15. What's the difference between:
- implicitly accept a block and `yield` in the method
- using `&something` to turn a block into a `Proc` and capture this proc by `something` in the method

- answer
  - if we use `yield`, by no means can we capture the passed in block by a variable, nor try converting it into a proc then pass it to another method. We can only pass arguments to the block and utilize the return value of the `yiled` call.
  - if we use `&something`, we can capture the passed in block and then instantiate a `Proc` object by using that block. This allows us to perform more operation, like pass the proc to another method.
  - but we should not say which one is better than the other, it all depends on the specific requirement. Sometimes `yield` is enough sometimes is not, choose the one which most meets the requirement.

16. What is "sandwich code", use code example to explain?

- answer
  - 'sandwich' describes the code which has a typical 3 layer structure, some 'before and after' code, and a mid layer code.
  - one example is the `File::open` method which takes a block to process the file object.
  - another application example is test method in minitest. There are two method `setup` and `teardown` which will be performed before and after every test method runs.

```ruby
require 'minitest/autorun'
require './some_file.rb'

class SampleTest < Minitest::Test
  def setup
    # setup steps
  end

  def teardown
    # teardown steps
  end

  def test_some
    # test something
  end
end
```

The 'before and after' methods `setup` and `teardown` are not written into the `test_some` method, but they will be executed every time before and after `test_some` run. This can be seen as a form of sandwich code.

17. If we have a variable named `something`, now we don't know what this variable is pointing to, it might be:

- a string object
- a symbol object
- a proc object

Given this code expression:

```ruby
[1,2,3].each(&something)
```

How the `&` in `[1,2,3].each(&something)` will put in effort to make the code work? Use pseudo code to draw out the steps the `&` will try.

- answer
  - a general description is `&` will first try to convert `something` into a proc object, then further convert the proc to a block which can be used by the `each` method

```
first try converting `something` to a proc
  if `something` is already a proc, then keep it as it is
  else call `to_proc` on `something`
    if `something` can't be converted to a proc, raise exception
second convert the proc object into a block, then pass this block to the method invocation -- `each`
```

18. Given the code below:

```ruby
def a_method(x)
  x + 2
end
```

While iterating through array `[1, 2, 3]`, how to perform  `a_method` on every element by using the syntax below.
- add one line of code before the expression to make it work as we want.
- what is the return value of the expression?

```ruby
#1
[1,2,3].map(&obj)
```

- answer

```ruby
obj = method(:a_method)
```

return value is `[3, 4, 5]`

19. Do the two `&`s below behave the same?
  - if not, what's the difference?

```ruby
#1
[1,2,3].each(&something)
#2
def a_method(&something)
  something.call
end
```

- answer

They are different:
- for `[1,2,3].each(&something)` the `&` is trying to 1) converted `something` to a proc; 2) then to a block
  - the termination is block
  - the whole process is heading executing
- for `def a_method(&something)`, the `&` is trying to 1) capture a possibly passed block; 2) capture then convert the block to a proc; 3) then assign the newly created proc to `something`
  - the termination is use the passed in block to instantiate a proc object
  - the whole process is aiming defining method

---

20. What's the simplest reason to write tests?

  - to prevent regression

21. What's the prerequisite code needed to create test class aided by minitest?

- answer
  - first need to load Ruby's test library `require 'minitest/autorun'`
  - second need to load the file(s) which contain the program we want to test `require '../sample.rb'`
  - then need to create the test class which inherits from `Minitest::Test` for example `class CarTest < Minitest::Test; end`

22. In order to make a test run automatically, how should we name the test method?

- we can write the tests by naming every method starting with `test_`

23. What is "SEAT Approach"?

- answer

"SEAT" is the abbreviation of the general steps for a test.
- S: Setup
- E: Execution
- A: Assertion
- T: Teardown

24. Given the code below:

```ruby
require 'minitest/autorun'
require './car.rb'

class CarTest < Minitest::Test
  def test_engine_warm_up
    car = Car.new
    car.warm_up
    assert_equal true, car.warmed_up?
  end
end
```

Which 'SEAT' steps included in the code? Which is absent?
  - indicate each step

- answer
  - S: `car = Car.new`
  - E: `car.warm_up`
  - A: `assert_equal true, car.warmed_up?`
  - Teardown step is absent

25. What's the difference between `assert_equal` and `assert_same`?

- answer
  - `assert_equal` compares the expected object and the resulting object by using `==` method, it depends on how the class of the two objects defines the `==` method
  - `assert_same` compares the two on object level, means comparing whether they are same object

26. What're the differences among proc, lambda and block, use code examples to explain.

- answer
  - on object level
    - block is not an object, it's a syntax structure
    - proc is object, lambda is a special kind of `Proc`, but essentially they are both proc objects
  - on execution level
    - proc and block have a lenient arity rule
    - lambda has a rigorous arity rule

Object level:

```ruby
a_proc = proc {  }
p a_proc.class # => Proc
a_lambda = lambda {  }
p a_lambda.class # => Proc
a_block = { }
a_block.class #=> Hash
```

Execution(arity) level:

```ruby
[1, 2, 3].each { |x, y, z| p [x, y, z] }
# [1, nil, nil]
# [2, nil, nil]
# [3, nil, nil]
# => [1, 2, 3]

def a_method(x, y, z)
  yield(x, y, z, 1, 2, 3)
end

a_method('a', 'b', 'c') { |a| p a }
# "a"
# => "a"
a_proc = proc { |x, y, z| p [x, y, z] }
a_proc.call('a')
# ["a", nil, nil]
# => ["a", nil, nil]
a_proc = proc { |x| p x }
a_proc.call('a', 'b', 'c')
# "a"
# => "a"
```

As the code showed above, proc and block don't enforce we to pass the right number of arguments.

But for lambda:

```ruby
a_lambda = lambda { |x, y, z| p [x, y, z] }
a_lambda.call('x')
# => ArgumentError: wrong number of arguments
```

27. What's the return value of every `counter.call`, why?

```ruby
def make_counter
  n = 3
  pr = Proc.new { n = n + 1 }
  n = 0
  pr
end

n = 5
counter = make_counter
counter.call
counter.call
counter.call
```

- answer

Line by line:
  - `n = 5` initialized a new local variable `n` on top level, assigned by 5
  - `counter = make_counter` call `make_counter` method then assign the return value to a new top level local variable `counter`
    - inside the `make_counter` method
      - first initialized a new method local variable `n`, assigned 3 to it
      - second instantiated a new proc object which involves the `n` variable
      - then updated the method local variable `n` to `0`
      - finally return the proc object
  - first the top level `n` and the method local variable `n` are in different scopes, and we never passed top level `n` to the method call, so we can ignore the top level `n`
  - second the method local variable `n` was assigned twice, before and after the proc was created.
    - according to how a closure behaves in Ruby, the proc will grasp the updated `n` (`n = 0`) as part of its binding
    - so if this proc object is executed later, the `n` will start from `0`
  - third the return value of `make_counter` is a proc object, we assigned it to top level local variable `counter`, when we later calling `counter.call` we are not invoking `make_counter` again, we just call `call` method on the same proc, so the update steps inside `make_counter` will not effect the proc binding afterwards

So before the first `counter.call`, the `n` relating to the binding of the proc is `0`, then:
  - first `counter.call` will perform `n = n + 1` so the return value is `1`, also the `n` has updated to `1`
  - second `2`
  - third `3`

28. If I have a Gemfile for a project, and I specified the versions of minitest that are compatible with my project, by writing `gem 'minitest', '~> 5.10'`.

- What's the meaning of the second argument `'~> 5.10'`?
- What about `'~> 5.1.1'`

- answer
  - `'~> 5.10'` means the version number should `>= 5.10` but `< 6.0`  
  - `'~> 5.1.1'` means the version number should `>= 5.1.1` but `< 5.2.0`

> Most of the version specifiers, like `>= 1.0`, are self-explanatory. The specifier `~>` has a special meaning, best shown by example. `~> 2.0.3` is identical to `>= 2.0.3` and `< 2.1`. `~> 2.1` is identical to `>= 2.1` and `< 3.0`. `~> 2.2.beta` will match prerelease versions like `2.2.beta.12`.

29. Briefly describe the relationships among

- Your local operating system
- Ruby
- Rubygems
- RVM and Rbenv
- Bundler
- Rake

- answer
  - level 1: among all the stuff listed above, the local operating system(call OS) is at the highest level.
  - level 2: Ruby is a programming language that is originally carried by MacOS, we can inspect this by running `/usr/bin/ruby -v`, this will get `ruby 2.3.7p456 (2018-03-28 revision 63024) [universal.x86_64-darwin17]`, this is the system-carried Ruby version installation
  - level 1.5: I prefer to put the RVM or Rbenv at the level between 1 and 2. because they are both Ruby version manager that deviate from the system-carried Ruby.
    - they can install and manage multiple versions of Ruby and RubyGems
    - it can also determines what version of Ruby we are using
  - level 3: RubyGems, they are packages of code that we can download, install and execute in our Ruby project or terminal. We talk about RubyGems under the context of Ruby. They can be thought of as external libraries we can import.
    - we use directives start with `gem` to manipulate the different gems
    - we don't have to install RubyGems, it's carried by modern Rubies
  - level 4: Bundler and Rake, they are both RubyGems
    - rake is originally carried by modern Rubies, it's a tool that can automate many tasks on Ruby development.
    - bundler is a gem, but it can manage the versions of gem for a project, it is a little recursive. We use bundler to handle the various dependencies in our project, it ensures we would run the correct version of different gems in different projects.
