## Ruby Foundations: More Topics

1. What's the definition of 'closure'?
  - why we call it 'closure'?
  - Is closure a unique concept in Ruby?

2. How many ways are there in Ruby to implement closure?
  - give code examples to demonstrate these ways
  - give code examples to show the differences among these ways

3. What's the 'binding' of a closure?

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
- what's the initial receiver(caller)?
- how many methods did we call out of the block?
- how many methods did we call inside the block?
- did we pass any arguments to any outside-block methods?
- how should we call `n` and `i` in `|n, i|`
  - respectively, what each of them represents?
  - what's the difference between 'argument' and 'parameter'
- what's the return value of every iteration step, how the return values were used?
- what's the final return value of the whole code expression

5. What is the determinative factor that can decide the return value of a method(which optional accepts a block)?

6. Can we pass a block to any methods?

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

8. In what scenario a `LocalJumpError` will be raised?

9. How to avoid this kind of situation?

10. How to implement a method can be called with or without a followed block? (Two ways)

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

def method_five(a, &arg)
  yield(a)
  arg.call
end
```

Which definition(s) are wrong, why?

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

13. Describe some scenarios that we may need block, better accompanied with code example.

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
a_method(proc_obj) # => ArgumentError
```

15. What's the difference between:
- implicitly accept a block and `yield` in the method
- using `&something` to turn a block into a `Proc` and capture this proc by `something` in the method

16. What is "sandwich code", use code example to explain?

17. If we have a variable named `something`, now we don't know what this variable is pointing to, it might be:

- a string object
- a symbol object
- a proc object

Given this code expression:

```ruby
[1,2,3].each(&something)
```

How the `&` in `[1,2,3].each(&something)` will put in effort to make the code work? Use pseudo code to draw out the steps the `&` will try.

18. Given the code below:

```ruby
def a_method(x)
  x + 2
end
```

While iterating through array `[1, 2, 3]`, how to perform  `a_method` on every element by using the syntaxes below.
- add one line of code before the expression to make it work as we want.
- what is the return value of the expression?

```ruby
#1
[1,2,3].map(&obj)
```

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

---

20. What's the simplest reason to write tests?

21. What's the prerequisite code needed to create test class aided by minitest?

22. In order to make a test run automatically, how should we name the test method?

23. What is "SEAT Approach"?

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

Which 'SEAT' steps are included in the code? Which is absent?
  - indicate each step

25. What's the difference between `assert_equal` and `assert_same`?

26. What're the differences among proc, lambda and block, use code examples to explain.
