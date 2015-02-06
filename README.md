# simplement

Radically simple implementations of stuff

Why? Powerful libraries with complex API's, abstractions, and DSL's are great when you need them, but not when you don't (and at first you usually don't). Using these libraries is certainly preferable to rolling your own complex implementations, but simple V1 behavior is usually achievable in a relative few simple lines of code. That's what you'll find here. The simpler the better!

Implementations are listed by category like on [The Ruby Toolbox](https://www.ruby-toolbox.com/), with super simple code alternatives to the popular gems associated with those categories.

WARNING: Use the code provided here at your own risk. It is not guaranteed to work or even be safe. This project is intended for advanced users to find simple implementations that *might* be suitable for their needs, but which they alone are responsible for researching, discussing, and evaluating the suitability of the code for themselves. This is NOT intended for blind copy+paste into production by beginners.

## Contributing

Contributions are welcome (fork, branch, PR). Discussions are also welcome in [Issues](https://github.com/bonsaiben/simplement/issues). Right now implementations are mainly Ruby/Rails but I'm open to other language/framework implementations too.

## Table of Contents

- [Active Record Default Values](#active-record-default-values)
- [Pagination](#pagination)
- [Permalinks and Slugs](#permalinks-and-slugs)
- [Bootstrap and FontAwesome](#bootstrap-fontawesome)


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

Caveats: dead links if you later decide to change how slugs look

Libraries: [friendly_id](https://github.com/norman/friendly_id), [more...](https://www.ruby-toolbox.com/categories/rails_permalinks___slugs)


### Bootstrap and FontAwesome

```html
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.2/css/bootstrap.min.css">
<link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/font-awesome/4.3.0/css/font-awesome.min.css">
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.2/js/bootstrap.min.js"></script>
```

Caveats: requires network access

Libraries: [bootstrap-sass](https://github.com/twbs/bootstrap-sass), [twitter-bootstrap-rails](https://github.com/seyhunak/twitter-bootstrap-rails), [font-awesome-rails](https://github.com/bokmann/font-awesome-rails), [font-awesome-sass](https://github.com/FortAwesome/font-awesome-sass)
