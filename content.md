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

We can define our own class using the `class` keyword, the name of the class (using PascalCase), and the `end` keyword. Here we are defining a `Dog` class.

```ruby
class Dog
end
```

## 3. Creating Objects (Instances)

Now that we have our `Dog` class, we will creat an *instance* of the `Dog` class (also called an object). We call `new` on the `Dog` class to create an instance of `Dog` (in this case `my_dog`).

```ruby
class Dog
end

my_dog = Dog.new
pp my_dog
```
{: .repl }

## 4. Adding Instance Variables and Methods

Our `Dog` class is a bit dull. Let's make sure our dogs have names. We'll use `@` to define an *instance variable* on the `Dog` class. You can also call these attributes.

There is a special method called `initialize` that gets called when creating new object. This is a common spot to set initial values for attributes. This is where we'll set the name of our dog.

```ruby
class Dog
  def initialize(name)
    @name = name
  end

  def bark
    "#{@name} says woof!"
  end
end

dog = Dog.new("Buddy")
pp dog.bark
```
{: .repl }

## 5. Using `attr_accessor`

Now we want to be able to set or get the value of `name` outside the `Dog` class. We can make our attributes accessible outside the class using `attr_accessor`.

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

<aside class="tip">
  Try changing the dog's name to something else.
</aside>

## 6. Using `attr_reader` and `attr_writer`

The class should control how it's data is accessed. There are some attributes we don't want to read AND write. We can restrict access to these attributes by using `attr_reader` and `attr_writer`. `attr_reader` limits access to *reading* the attribute. `attr_writer` limits access to *writing* the attribute value.

Let's apply this to our `Dog` class. Perhaps we don't want to allow users to change a dog's name, but we can change a dog's age.

```ruby
class Dog

  attr_reader :name
  attr_writer :favorite_food

  def initialize(name)
    @name = name
    @age = 0
  end

end

dog = Dog.new("Buddy")
puts dog.name

dog.age = 3
```
{: .repl }

<aside class="tip">
  Try changing the dog's name in the above code snippet and see what happens.
</aside>

<!-- TODO: go under the hood to see how this is creating getter/setter methods -->

## Quiz

- What does a Ruby class represent?
- A single, specific instance of data.
  - Not quite — that describes an *object*, not the class itself.
- A built-in Ruby method.
  - Nope! While classes contain methods, a class itself is not a method.
- A blueprint or template for creating objects.
  - Correct! A class defines the structure and behavior that its objects will share.
{: .choose_best #ruby_class_meaning title="What is a Ruby Class?" answer="3"}

- What does calling `Dog.new` do?
- It creates a new instance (object) of the Dog class.
  - Correct! The `.new` method calls `initialize` and returns a new `Dog` object.
- It defines a new method inside the class.
  - Not quite. `.new` creates objects, not methods.
- It prints the details of the class.
  - Nope! `.new` creates an object, but does not print anything by itself.
{: .choose_best #dog_new title="Creating Objects with .new" answer="1"}

## Wrap-Up

- `class` defines a blueprint.
- Use `@` for instance variables to store object state.
- `attr_accessor` gives easy getter/setter access.
- `initialize` method runs when you call `.new`.

## Project: Class

In this project, you will write Ruby programs that leverage Ruby Classes. This project includes automated tests, so click this link to get started <https://github.com/dpi-tta-projects/ruby-class/fork>, fork the repository and create a codespace.

<aside class="warning">
  In order to get credit for completing this project you'll need to open the assignment link from canvas to generate an access token.
</aside>

## References

- [Ruby Docs: Class](https://docs.ruby-lang.org/en/master/Class.html)
