# Intention Revealing Methods

Methods are the core components of your code base.  A codebase without clean methods will be difficult to read and will be bug-prone.

## A. The problem

The problem occurs when you see very long methods, code with many if else branches, or code is heavily commented to explain what it does.  Here is the problem in the wild.

```ruby
if current_user && current_user.admitted_at < 1.week.ago
  # When user is admitted at least a week ago we show it's active projects and
  # admitted-only ones
  @active_projects = current_user.projects.active
  @promo_projects = Project.promo
else
  # If not admitted we show some featured projects, and set a marketing flash
  # message when user is new
  if current_user && current_user.created_at > 1.week.ago
    flash[:info] = 'Sign up for having your own projects, and see promo ones!'
  end
  @featured_projects = Project.active.featured
end
```

This may not seem like a poor method at first, but it is.  Imagine you are a senior developer trying to help a new developer improve this method.  Which parts of the method are unclear or difficult to parse out?  Is there functionality that does not belong in the method?  Are there ways to eliminate the code comments and instead have code naturally describes itself?

## B. The solution

The solution is to write methods under seven lines long, and extract components of a method into smaller and smaller methods.  Here are some good resources to learn about how to write cleaner methods.

1. [Martin Fowler on Intention Revealing Methods](https://martinfowler.com/bliki/FunctionLength.html)
2. [Intention Revealing Names Wiki](http://wiki.c2.com/?IntentionRevealingNames)
3. [RailsConf Simplifying Code](https://www.youtube.com/watch?v=ozWzehOEeuI)

Look at the railsconf video.  Tute gives four steps to getting to clean methods.  See what those four steps are, and then apply those steps to your code. 
<p class='util--hide'>View <a href='https://learn.co/lessons/intention-revealing-methods'>Intention Revealing Methods</a> on Learn.co and start learning to code for free.</p>
