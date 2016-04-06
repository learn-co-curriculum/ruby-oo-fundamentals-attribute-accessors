# Macros and Abstraction

## Objectives

1. Learn the definition of a macro.
2. See how macros can abstract away the explicitly defined setter and getter methods in a Ruby class.

## What is a Macro?

A macro is any code that writes code for you. The implementation of macros is considered metaprogramming––the writing of programs that operate on other programs.

Implement macros to abstract away the manual, explicit definition of setter and getter methods in a Ruby class.

## Attribute Readers, Writers and Accessors

In object-oriented Ruby, there is a strong convention to have a setter and a getter method that pertain to the same attribute. For example, a `.name` getter and a `.name=` setter on our Person class. Because this pattern is so common, we find ourself making these manual setter and getter definitions again and again. As Rubyists, we are lazy, and this is a virtue. If we can achieve the same result with less code, we'll do it.

Check out the example below:

```ruby
class Person

  attr_reader :name
  attr_writer :name

end
```

The `attr_reader` macro, followed by the attribute name `:name`, *created a getter method for us*.

The `attr_writer` macro, followed by the attribute name `:name`, *created a setter method for us*.

We can now do the following, without explicitly defining a `.name` or `.name=` method ourselves:

```ruby
jay_z = Person.new
jay_z.name = "Shawn Carter"
jay_z.name
  => "Shawn Carter"
```

Let's compare a `Person` class that uses macros to one that uses explicit setter and getter methods:

#### Macros

```ruby
class Person
  attr_writer :name
  attr_reader :name

end
```

#### Explicit Method Definitions

```ruby
class Person

  def name=(name)
    @name = name
  end

  def name
    @name
  end
end
```

####Attribute Accessors
If we know that we are going to be reading and writing to the `name` attribute on our `Person` class, we can use another macro called an attribute accessor.

So this code:

```ruby
class Person
  attr_writer :name
  attr_reader :name

end
```

Can now be written like this:

```ruby
class Person
  attr_accessor :name

end
```
We now have access to reader and writer methods from one macro!

#### Using Macros is Usually Better

The usage of macros is preferred over the explicit definition of setter and getter methods, *unless you need to customize the implementation of a method*, like in our previous lesson when we defined `.name` as returning the first and last name variables combined.

To understand why, simply look at the code above. Which class would you rather write? The longer one, or the shorter one?

When opening up a class, `attr_accessor` and friends allow you to get a high level overview of the class right from the start.

As developers we spend more time reading rather than writing code, so it's important that the code we write be clear, concise and eloquent. We want to be kind to our future selves (when we come back to the programs we've written) and to other developers who will work with our code. 

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/ruby-oo-macros-readme' title='Macros and Abstraction'>Macros and Abstraction</a> on Learn.co and start learning to code for free.</p>

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/ruby-oo-macros-readme'>Object Accessors</a> on Learn.co and start learning to code for free.</p>
