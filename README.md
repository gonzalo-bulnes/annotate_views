Annotate Views
==============

Provides information about variables used in Rails views as code comments.

    As a developer
    In order to avoid integration issues when renaming variables in views
    I want the presence of those variables to be properly tested with views and controllers specs

The issue
---------

Sometimes, the application growth requires several partials to be shared between views, or views to be shared among several controllers actions. The first case often requires to unify variable names (e.g. `@anonymous_user` and `@user` could be renamed `@user` in order to make possible the rendering of the `_anonymous_something.html.erb` and `_something.html.erb` partials into the `something/show.html.erb` view).

Variables renaming **must** be performed with caution (read _a proper integration tests suite_).
Such a tests suite may be difficult to maintain when views get larger. The purpose of this gem
is to generate useful information and, at your convenience, useful code to get that task done.

The tasks
----------

The annotations this gem generates for each view (including partials) list:

- the optional or required objects and attributes the view uses
- the controllers actions which renders the view

The gem provides checklists and generators to suggest or generate:

- views specs or examples to ensure that the defined variables are displayed
- controllers specs or examples to ensure the variables are properly created

A `--pedantic` option can also make sure that you test suite gets broken if any of those controller or view spec examples are missing.

The annotations format
----------------------

Not yet defined.

The API
-------

```bash
# Annotate all views
rake annotate:views:all
# ... or only some of them
rake annotate:views:list users/index.html.haml products/_description.html.haml
```

If you are using [RVM][rvm], don't forget to use `bundle exec` before Rake commands.

  [rvm]: http://rvm.io


```bash
# Generate the controllers specs
rails generate annotate_views:controllers:specs
# ... or only suggestions
rails generate annotate_views:controllers:specs --only-suggestions

# Do the same with the views specs
rails generate annotate_views:views:specs
rails generate annotate_views:views:specs --only-suggestions
```

Run `rails generate annotate_views --help` for more options.

Getting started
---------------

Add Annotate Views to your `Gemfile`:

```ruby
group :development do
  gem 'annotate_views', git: git@github.com:gonzalo-bulnes/annotate_views.git
end
```

Run `bundle install`. That's all! Let's annotate:

  rake annotate:views:all


Roadmap
-------

Following the [README Driven Development principles][1], this document was written before any code was. This _Roadmap_ section provides an overview of the already available features progress.

  [1]: http://tom.preston-werner.com/2010/08/23/readme-driven-development.html

For now, nothing was done. Remaining tasks are:

- Write down all the tasks that are required to get the gem working.
- Read them loudly.
