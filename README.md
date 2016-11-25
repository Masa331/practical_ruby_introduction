# Practical introduction to Ruby

1. Basics
2. Syntax
3. Classes & Modules
4. Standard & Core library
5. Metaprogramming
6. Exceptions
7. Managing Ruby versions
8. Rubygems
8. irb, pry, debugger
10. Tests in ruby ecosystem
11. Where to start

## 1 - Basics

- Ruby vs. Ruby on Rails & Ondra thinks Ruby is magic

- Dynamicly typed, interpreted
- Everything is an object and has methods

## 2 - Syntax

- http://web.stanford.edu/%7Eouster/cgi-bin/cs142-spring12/slides/ruby.pdf
- https://learnxinyminutes.com/docs/ruby/

- Newline is statement separator - semicolon is optional
- whitespace independent(unlike python for example)
- the goal is readability
- Rubocop - Ruby style guide - https://github.com/bbatsov/ruby-style-guide

```
  local_variable = 'something' # accessible only from same scope(method, block, class, ..)
  @instance_variable = 'something else' # accessible from everywhere in the same instance
  @@class variable = 'something totally else' # don't use this
  $global_variable = 'bla bla' # DON'T USE THIS

  DEFAULT_DISCOUNT = 0 # constant
```

```
  "something", 'something else' # String
  1 # Integer
  [1, 2] # Array
  { key1: "value 1", key2: "value 2" } # Hash = key, value, similar to objects in Javascript or dicts in Python
  { "key1" => "value 1", "key2" => "value 2" }
  :success # Symbol
```

```
  1 + 1 # it's a method - can be redefined - think invoice + invoice
  1 != 2

  def +(invoice)
    ...
  end

  !
  true && false
```

```
  nil
```


```
  def name
    "Premek Donat" # last method statement result is implicitl value returned by method(no return needed)
  end
```

```
  name = "Premek"

  if name # truthiness only 'nil' or 'false' will go to else branch
    puts "name is #{name}"
  else
    puts 'no name given'
  end

  puts 'true' if result
```

```
# positional arguments
def name_with_age(name, age)
  puts "The name is #{name} and age is #{age}"
end

name_with_age('Tomas Novak', 31)
name_with_age 'Tomas Novak', 31 # equivalent

# keyword arguments
def name_with_age(name:, age:)
  puts "The name is #{name} and age is #{age}"
end

name_with_age(age: 31, name: 'Tomas Novak')
```

- method documentation - `#strip`, `::new`, `.new`

### Blocks

- working with collections
- logger, benchmark
- iteration with each

```
  ['Premek', 'Petr', 'Zbynek', 'Ruda', 'Patrik', 'Ondra'].each { |name| puts name }

  ['Premek', 'Petr', 'Zbynek', 'Ruda', 'Patrik', 'Ondra'].select do |name|
    name.start_with?('P')
  end
  # => ['Premek', 'Petr', 'Patrik']
```

- https://ruby-doc.org/core-2.2.0/Array.html

## 3 - Classes & Modules

- classes can be instantiated via `#new` method
- modules = namespacing, sharing behaviour, utils - modules can't be instantiated

```
class Invoice
  ...
end

module Confirmable
  ...
end

class SalesInvoice < Invoice # inheritance
  include Confirmable
  include ...
end

class PurchaseInvoice < Invoice
  include Confirmable
end

class Retail
  include Confirmable

  def initialize(document_id, buyer)
    ...
  end

  def self.last_id
    ...
  end

  def buyer
    ...
  end
end

retail1 = Retail.new('2016000001', alax)
Retail.ancestors # => [SalesInvoice, Confirmable, Invoice, Object, Kernel, BasicObject]
```

- ancestors chain
- monkey patching, reopening classes

```
class Car
  def color
    "blue"
  end
end

class Car
  def color
    "green"
  end
end
```
## 4 - Standard & Core library

- the goal is to provide good, easy, and readable starting point for developer - Array has 50 methods vs 6 in Python
- select & detect - aliases

- core vs. standard
- version differences - #positive? on Number

- http://ruby-lang.org/
- http://ruby-doc.org/core-2.3.3/
- http://ruby-doc.org/stdlib-2.3.3/

- http://ruby-doc.org/stdlib-2.3.3/libdoc/csv/rdoc/CSV.html
- https://ruby-doc.org/core-2.2.0/Array.html

## 5 - Metaprogramming

- don't do it if you don't have to

- **classes reopening and method redefinition - monkeypatching**

- #send()
- dynamic code eval
- dynamic method definition
- method_missing
- const_missing

## 6 - Exceptions

```
  def some_method
    ...
  rescue StandardError => e
    e.backtrace
  end
```

- rescue only StandardError and it's descendants
- https://ruby-doc.org/core-2.1.1/Exception.html

## 7 - Managing Ruby versions

- currently Ruby 2.3
- ruby in system packages is outdated
- RVM, rbenv
- brightbox - https://www.brightbox.com/docs/ruby/ubuntu/

## 8 - Rubygems

- rubygems.org
- bundler - bundler.io - Gemfile & Gemfile.lock
- gemspec - gem dependencies - popelka - gems from github
- `gem install nokogiri`, `gem list`
- `require 'nokogiri'`
- `bundle`, `bundle show nokogiri`


## 9 - irb, pry, debugger

- repl
- pry ls command
- http://pryrepl.org/
- require 'pry'; binding.pry

## 10 - tests

- dynamic langugae needs tests because there is no compiler which otherwise detects mistakes
- easy refactoring
- tdd - write test -> see it failing -> implement -> refactor

- default tetsing library in ruby vs RSpec

```
RSpec.describe String do
  describe '#strip' do
    it 'removes leading and trailing whitespace' do
      expect('  ahoj  '.strip).to eq('ahoj')
    end
  end
end
```

## 11. Where to start

- http://tryruby.org/levels/1/challenges/0
- https://www.railstutorial.org/

- http://rubykoans.com/
- https://www.codecademy.com/learn/ruby
- https://www.codeschool.com/learn/ruby
