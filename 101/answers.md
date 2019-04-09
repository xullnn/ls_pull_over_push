## Programming Foundations

1. What is "snake case" and "camel case" in Ruby style guide? And what are they usually used for?

- snake case write things in lowercase and join words by underscore, for example `snake_case`, `a_method`
- camel case write things without any join notations but will capitalize every word, for example `CamelCase`, `SumNumbers`
- these two types of writing are both used for naming things like method name, variable name. In Ruby we conventionally use snake case to name method and variables.

2. In any programming language, in order to build conditional logic, we need boolean data type, booleans are represented by what objects in Ruby?

`true` and `false` objects.

3. What are logical operators used for? What are the possible return values of a comparison expression which contains logical operator(s)?

Logical operators(e.g `&&`, `||`) usually used for writing a conditional, a comparison expression which contains logical operator(s) normally return `true` or `false`.

4. In Ruby what are the only two objects that will be evaluated to `false`?

`false` and `nil`

5. What is integer division in programming? Give an example in irb.

Integer division is division in which the fractional part (remainder) is discarded.

```ruby
7 / 3
=> 2
2 / 3
=> 0
```

6. What're the return values of `"a123".to_i`, `"12a3".to_i`, `"123a".to_i` and `"abcd".to_i`? What's the pattern here?

- `"a123".to_i` returns `0`
- `"12a3".to_i` returns `12`
- `"123a".to_i` returns `123`
- `"abcd".to_i` returns `0`

`to_i` works like this:
- scan from the left to right of a string
- if the string starts with a non-digit char, return 0
- loop do
  - convert current char to integer
  - break if it encounters a non-digit char (other than 0-9)

7. When we use pseudo-code, what are the tow layers of problem are being separated? Why should we do this?

- logic layer
- implementation layer

Logic layer cares about the structure of the program in a high level, at this layer it is most important to focus on the relationships and interactions among different processes or sub processes, we should not consider to much about the implementation details at this level.

Implementation layer is the process in which we implement the components(processes) mapped out in the logic layer. At this layer we may want to consider things like which method to choose, wether the syntax is right etc.

With a previously settled logical structure, no matter it's represented by pseudo code or flow chart or just thoughts in mind, we ensure that we won't go into the wrong direction. But if we mix these two steps together, it's more likely that will happen.

8. What is procedural or imperative programming? What's declarative programming?

Briefly saying, procedural or imperative program expose more about the logical steps of the program, declarative programming is closer to high level method which may hide more implementation details. The former is lengthy but the procedures are visible, the latter is more descriptive or readable but needs previously defined high level functions.

procedural:(Computing)denoting high-level programming languages which can be used to solve problems without requiring the programmer to specify an exact procedure to be followed

9. When mapping out flowchart or pseudo code for a program, can the two types of programming(procedural and imperative) be mixed together? Why?

Yes. For some complicated programs, it's not appropriate to draw out every detail on the flowchart(work all in procedural style), overly crammed details may make the chart hard to read and understand. For some sub processes we can use a high level description to denote, then later we can draw another separated flowchart to map out the implementation details of this sub process. By doing this we can always keep things presented at the same level and grow our design systematically.

10. How many ways can you come up with to check if the input string get by `num = gets.chomp` can be completely converted to an integer?

- `num.to_i.to_s == num`
- `num.match(/[0-9]+/).string.size == num.size && !num.start_with?('0')`
- `!num.start_with?('0') && !num.match(/[^0-9]/)`
- `Integer(num)`

11. When defining a method, what aspects should be considered(think from naming, responsibility etc.)?

- case
- indentation
- descriptive name
- return value or print out message
- clear and single responsibility?
- code length
- mutate argument or not(side effects)

12. Use one sentence to describe the variable scope rule when using block in Ruby?

Variables initialized in an outer scope can be accessed in an inner scope, but not vice versa.

13. What is "variable shadowing" when invoking method with a block in Ruby, use example to explain.

When invoking method with block there exists same variable names inside and outside the block.

```ruby
n = 0
[1,2,3].map do |n|
  n += 1
end
```
14. What is the variable scope rule of method definition in Ruby(only talk about local variable)?

The only variables a method definition has access to must be passed into the method definition.

15. What is method definition and method invocation?

- Method definition is when we define a method using `def` keyword.
- Method invocation is when we call an existent method.

16. What's the final value of b? Explain why?

```ruby
a = "Hello World."
b = a
a = "Hi"

# b => ?
```

`b` is `"Hello world"`, the process is:
- string `"Hello World."` is assigned to local variable `a`
- `a` now is pointing to `"Hello World."` object
- `b = a` let `b` also pointing to `"Hello World."`
- `a = "Hi"` let `a` now pointing to another string `"Hi"`
- but `b` is still pointing to `"Hello World."`

```ruby
a = "Hello World."
b = a
a << "Hi"

# b => ?
```

`b` is `"Hello World.Hi"`, the process is:
- `a` and `b` first are all pointing to `"Hello World."`
- `a << "Hi"` first references the string `"Hello World."` and mutates it to `"Hello World.Hi"`
- this time the object to which `a` and `b` are pointing is changed, so `b` changed.

17. What does `_` mean in this code?

`h.each { |_, value| puts value }`

It denotes the key of each key/value pair, since it's not used in the block, so we use `_` to represent it.

18. What method is actually invoked by this expression `"Hello"[2,2]`? How does the method works and what is the return value?

This is same as `"Hello".slice(2,2)`, it return a 2 chars new string which starts from the char at index `2` -- the third char. In this case it returns `'ll'`

19. If we have a hash `hsh = { 'fruit' => 'apple', 'vegetable' => 'carrot' }`, what's the difference of the return value of the expressions below?

`hsh['dessert']` and `hsh.fetch('dessert')`

The former returns `nil` and the latter raise exception.

20. If we have an array `arr = [1, 3, 5]`, what's the difference of the return value of the expressions below?

`arr[3]` and `arr.fetch(3)`

The former returns `nil` and the latter raise exception.

21. How does `next` work in a loop? Use example to explain.

if `next` in a loop is executed, then the rest of the code inside the loop will not be execute. To put it another way, `next` let the program immediately enter the next loop.

```ruby
n = 0
loop do  
  n += 1
  next if n.even? # if current n is an even number then it will enter next loop execution
  puts "Loop number: #{n}"
  break if n > 7
end
```

22. Inspect the code below, specifically the line where `break` is at

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

The do the same thing. Although the two lines with `break` look like at different places but they are both executed after current loop's `counter += 1` and next loop's `puts chars[counter]`, they are in the same time slot and there's no other code in this time slot.

23. What're the 4 essential parts to form a looping in Ruby?

- a loop(`loop`, `while`, `until` ...)
- a counter
- a way to retrieve data
- a way to exit loop

24. What does PEDAC stand for?

- P Understand the Problem
- E Examples and Test cases
- DA Data structure and Algorithm
- C Code

25. Describe how does `select` work in Ruby? What's the return value of `[1, 2, 3].select { }` and `[1, 2, 3].select { 'false' }`? Why?

`select` iterate through the collection and collect elements based on the truthiness of the block's return value.

- `[1, 2, 3].select { }` returns `[]` because every empty block will return `nil` which will be evaluated as `false`
- `[1, 2, 3].select { 'false' }` returns `[1, 2, 3]` since `'false'` is a string which will be evaluated to `true` in every block execution step.

26. Describe how does `map` work in Ruby?

- go through element one by one
  - yield one element into the block at every iteration step
- use every block's return value to form a new array

27. What's the return value of `[1, 2, 3].each { |n| n * 2 }`?

`[1, 2, 3]`, `each` return the caller itself.

28. What's the return value of `[2, 5, 3, 4, 1].sort { |a, b| 0 }`, explain why?

It returns a new array same as the caller. Because `sort` order the elements based on the return value of the given block(-1, 0 ,1). Here the return value of every block execution is `0` which will be interpreted as "all elements are equal" by `sort`, so the original order will be kept.

29. What's the return value of `'abc' <=> 'abd'` Why?

It's `-1`. The first two chars of the two strings are same. But the third chars of them are `c` and `d`, in ASCII character table, `c`'s ordinal number is smaller than `d`'s, so it returns `-1` which mean `c` is smaller than `d`.

30. Consider the code below, what's the return value? Why?

```
arr_1 = ['a', 'b', 'c']
arr_2 = arr_1.dup

arr_1.object_id == arr_2.object_id
```

What about this? Why?

It returns `false`, cause they are not the same object, more specifically the outmost array container is not the same.

```
arr_1 = ['a', 'b', 'c']
arr_2 = arr_1.dup

counter = 0

arr_1.all? do |elem|
  elem.object_id == arr_2[counter].object_id
  counter += 1
end
```

This returns `true`. `dup` method only duplicate a collection's outmost "shell", the elements inside the new collection are shared with the original one.

31. What's the difference between `clone` and `dup`?

The difference between `dup` and `clone` is that `clone` preserves the frozen state of the object.

32. When invoking methods related to collection data types in Ruby, what should be aware of about the whole method call?

- the type of the caller
- the structure of the caller
- what method(s) are called
- how the called method(s) is implemented
- how many block parameters are there
  - what are they representing
- what's the return value of the block
- any side effects
