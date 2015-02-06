# simplement

Radically simple implementations of stuff

Why? Powerful libraries with complex API's, abstractions, and DSL's are great when you need them, but not when you don't (and at first you usually don't). Using these libraries is certainly preferable to rolling your own complex implementations, but simple V1 behavior is usually achievable in a relative few simple lines of code. That's what you'll find here. The simpler the better!

Implementations are listed by category like on [The Ruby Toolbox](https://www.ruby-toolbox.com/), with super simple code alternatives to the popular gems associated with those categories.

WARNING: Use the code provided here at your own risk. It is not guaranteed to work or even be safe. This project is intended for advanced users to find simple implementations that *might* be suitable for their needs, but which they alone are responsible for researching, discussing, and evaluating the suitability of the code for themselves. This is NOT intended for blind copy+paste into production by beginners.


## Table of Contents

- [Active Record Default Values](#active-record-default-values)
- [Pagination](#pagination)
- [Permalinks and Slugs](#permalinks-and-slugs)


## Implementations

### Active Record Default Values

```ruby
after_initialize :defaults, unless: :persisted?

def defaults
  self.number ||= 0.0
end
```

Discussion: [http://stackoverflow.com/questions/328525/how-can-i-set-default-values-in-activerecord](http://stackoverflow.com/questions/328525/how-can-i-set-default-values-in-activerecord)

Libraries: [default_value_for](https://github.com/FooBarWidget/default_value_for), [more...](https://www.ruby-toolbox.com/categories/Active_Record_Default_Values)

### Pagination

```ruby
@page = params[:page] || 0
@per_page = params[:per_page] || 20
scope = Post.published
@pages = scope.count / @per_page
@posts = scope.offset(@per_page * @page).limit(@per_page)
```

Libraries: [kaminari](https://github.com/amatsuda/kaminari), [will_paginate](https://github.com/mislav/will_paginate), [more...](https://www.ruby-toolbox.com/categories/pagination)

### Permalinks and Slugs

```ruby
class Post < ActiveRecord::Base
  def to_param
    [id, title.delete(?').parameterize].join(?-)
  end
end

@post = Post.find(params[:id].to_s.split(?-).first)
```

Risks: dead links if you change the way permalinks/slugs are generated

Libraries: [friendly_id](https://github.com/norman/friendly_id), [more...](https://www.ruby-toolbox.com/categories/rails_permalinks___slugs)
