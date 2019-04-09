## Programming Foundations

1. What is "snake case" and "camel case" in Ruby style guide? And what are they usually used for?

2. In any programming language, in order to build conditional logic, we need boolean data type, booleans are represented by what objects in Ruby?

3. What are logical operators used for? What's the possible return values of a comparison expression which contains logical operator(s)?

4. In Ruby what are the only two objects that will be evaluated to `false`?

5. What is integer division in programming? Give an example in irb.

6. What's the return value of `"a123".to_i`, `"12a3".to_i`, `"123a".to_i` and `"abcd".to_i`? What's the pattern here?

7. When we use pseudo-code what are the tow layers of problem are being separated? Why should we do this?

8. What is procedural or imperative programming? What's declarative programming?

10. When mapping out flowchart or pseudo code for a program, can the two types of programming(procedural and imperative) be mixed together? Why?

11. How many ways can you come up with to check if the input string get by `num = gets.chomp` can be completely converted to an integer?

12. When defining a method, what aspects should be considered(think from naming, responsibility etc.)?

13. Use one sentence to describe the variable scope rule when using block in Ruby?

14. What is "variable shadowing" when invoking method with a block in Ruby, use example to explain.

15. What is the variable scope rule of method definition in Ruby(only talk about local variable)?

16. What is method definition and method invocation?

17. What's the final value of b? Explain why?

```ruby
a = "Hello World."
b = a
a = "Hi"

# b => ?
```

```ruby
a = "Hello World."
b = a
a << "Hi"

# b => ?
```

18. What does `_` mean in this code?

`h.each { |_, value| puts value }`

19. What method is actually invoked by this expression `"Hello"[2,2]`? How does the method works and what is the return value?

20. If we have a hash `hsh = { 'fruit' => 'apple', 'vegetable' => 'carrot' }`, what's the difference of the return value of the expressions below?

`hsh['dessert']` and `hsh.fetch('dessert')`

21. If we have an array `arr = [1, 3, 5]`, what's the difference of the return value of the expressions below?

`arr[3]` and `arr.fetch(3)`

22. How does `next` work in a loop? Use example to explain.

23. Inspect the code below, specifically the line where `break` is at

```ruby
chars = 'abcde'
counter = 0

loop do
  break if counter == chars.size
  puts chars[counter]
  counter += 1
end
```

```ruby
chars = 'abcde'
counter = 0

loop do
  puts chars[counter]
  counter += 1
  break if counter == chars.size
end
```

Will the two code snippet produce same output? Why?

24. What're the 4 essential parts to form a looping in Ruby?

25. What does PEDAC stand for?

26. Describe how does `select` work in Ruby? What's the return value of `[1, 2, 3].select { }` and `[1, 2, 3].select { 'false' }`? Why?

27. Describe how does `map` work in Ruby?

28. What's the return value of `[1, 2, 3].each { |n| n * 2 }`?

29. What's the return value of `[2, 5, 3, 4, 1].sort { |a, b| 0 }`, explain why?

30. What's the return value of `'abc' <=> 'abd'` Why?

31. Consider the code below, what's the return value? Why?

```
arr_1 = ['a', 'b', 'c']
arr_2 = arr_1.dup

arr_1.object_id == arr_2.object_id
```

What about this? Why?

```
arr_1 = ['a', 'b', 'c']
arr_2 = arr_1.dup

counter = 0

arr_1.all? do |elem|
  elem.object_id == arr_2[counter].object_id
  counter += 1
end
```

32. What's the difference between `clone` and `dup`?

32. When invoking methods related to collection data types in Ruby, what should be aware of about the whole method call?
