# simplement

Radically simple implementations of stuff

Why? Powerful libraries with complex API's, abstractions, and DSL's are great when you need them, but not when you don't (and at first you usually don't). Using these such libraries is without a doubt preferable to rolling your own complex implementations, but simple V1 behavior is usually perfectly achievable in a relative few simple lines of code. That's what you'll find here. The simpler the better.

Implementations are listed by category like on [The Ruby Toolbox](https://www.ruby-toolbox.com/), with super simple code alternatives to the popular gems associated with those categories.

WARNING: Use the code provided here at your own risk. It is not guaranteed to work or even be safe. To that extent, this resource is intended for advanced users to find simple implementations which *might* be suitable for their needs, but which ultimately they alone are responsible for researching, discussing, and evaluating the suitability of the code for themselves. This is NOT intended for blind copy+paste into production by beginners.

## Table of Contents

- [Active Record Default Values](#active-record-default-values)
- [Pagination](#pagination)


## Implementations

### Active Record Default Values

```ruby
after_initialize :defaults, unless: :persisted?

def defaults
  self.number ||= 0.0
end
```

Discussion: [http://stackoverflow.com/questions/328525/how-can-i-set-default-values-in-activerecord](http://stackoverflow.com/questions/328525/how-can-i-set-default-values-in-activerecord)

Libraries: [https://www.ruby-toolbox.com/categories/Active_Record_Default_Values](https://www.ruby-toolbox.com/categories/Active_Record_Default_Values)

### Pagination

```ruby
@page = params[:page] || 0
@per_page = params[:per_page] || 20
scope = Post.published
@pages = scope.count / @per_page
@posts = scope.offset(@per_page * @page).limit(@per_page)
```

Libraries: [https://www.ruby-toolbox.com/categories/pagination](https://www.ruby-toolbox.com/categories/pagination)
