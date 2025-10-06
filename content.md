# Ruby Class

<div class="alert alert-info">
  <ul>
    <li><a href="https://www.youtube.com/watch?v=8N0O9dynK0g">Video (with Benny)</a></li>
  </ul>
</div>

## Goals

By the end of this lesson, you'll be able to:

- Define a class and create instances (also called *objects*)
- Use `initialize` to set up object data
- Understand and use instance variables
- Define and call instance methods
- Use `attr_accessor` to read/write attributes

## Why It's Important

Up until now, you've been writing Ruby programs that use variables, arrays, and methods, but everything lives in the same space. As your programs grow, this can get messy. Classes let you group related data and behavior together into organized, reusable units. Instead of juggling multiple variables (`dog_name`, `dog_breed`, `dog_bark`), you can create one `Dog` object that knows its own name and how to bark.

This makes your code easier to:

- *Read* things that belong together live together.
- *Reuse*: you can make many objects from the same class blueprint.
- *Maintain*: changing one class doesn't break the rest of your program.

In short,  classes help you think about your code like you think about the real world, as objects with properties and actions.

## 1. What is a Class?

Essentially, it's a "blueprint" for creating objects.

Real-world analogy: a `Car` class defines what every car can do, but each car (object) has its own color or speed.

## 2. Defining a Simple Class

```ruby
class Dog
end
```
{: .repl }

## 3. Creating Objects (Instances)

We call `new` on the `Dog` class to create an instance of `Dog`.

```ruby
class Dog
end

fido = Dog.new
pp fido
```
{: .repl }

## 4. Adding Instance Variables and Methods

We use `@` to define an *instance variable* on the `Dog` class. You can also call these attributes.

There is a special method called `initialize` that gets called when creating new object. This is a common spot to set initial values for attributes.

```ruby
class Dog
  def initialize(name)
    @name = name
  end

  def bark
    puts "#{@name} says woof!"
  end
end

dog = Dog.new("Buddy")
dog.bark
```
{: .repl }

<!-- TODO: reader, writer, (getter/setter) -->
## 5. Using `attr_accessor`

We can also defined attributes using `attr_accessor`.

```ruby
class Dog

  attr_accessor :name

  def initialize(name)
    @name = name
  end

end

dog = Dog.new("Buddy")
puts dog.name
dog.name = "Rex"
puts dog.name
```
{: .repl }

<!-- TODO: quiz -->

<!-- TODO: move to project
Challenge: Create a Car class that stores a model and year, and prints a line like:

"My car is a 2020 Honda Civic."

🧠 Key Takeaways

class defines a blueprint.

@variable stores object state.

attr_accessor gives easy getter/setter access.

initialize runs automatically when you call .new. 
-->

## References
