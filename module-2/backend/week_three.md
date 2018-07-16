## Week Three Recap

### Instructions
Fork this repository. Be sure to pull the latest changes to your local repo. Answer the questions to the best of your ability.

Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week.

Note: When you're done, submit a PR with a reflection in the comments about how this exercise went for you.

### Week 3 Questions

1. What is the entry at the command line to create a new rails app?
  rails new APPNAME -t -d='postgresql' --skip-spring --skip-turbolinks
2. What do Models generally inherit from in rails?
  the Application Record file
3. What do Controllers generally inherit from in a rails project?
  the Application Controller file
4. How would I create a route if I wanted to see a specific horse in my routes file assuming I'm sticking to standard conventions and that I didn't want other CRUD functionality?
  resources :horses, only: [:show]
5. What rake task is useful when looking at routes, and what information does it give you?
  rails/rake routes lets you see all existing RESTful routes
6. What is an example of a route helper? When would you use them?
  routes such as article_path(article) are a helpful way to access a url without typing the entire address
7. What's the difference between what `_url` and `_path` return when combined with a routes prefix?
  url contains the entirety of the filepath, whereas a path is much shorter
8. What are strong params and why are they necessary?
  Strong params ultimately enable which attributes can be accepted for the creation of an object using a private method
9. What role does `form_for` play in helping us create our forms?
  It enables both the labeling and creation of input fields in an HTML page
10. How does `form_for` know where to submit the user's input?
  Because it is rendered by the controller
11. Create a form using a `form_for` helper to create a new `Horse`.
  <%= form_for @horse do |f| %>
    <%= f.label :name %>
    <%= f.textfield :name %>
  <% end %>
12. Why do we want to validate our models?
  to confirm they contain the necessary attributes
13. What are the steps of the DNS lookup?
  - A Query is submitted
  - it is then transferred to the RNS (resolving name server)
  - then transferred to root server
  - then passed to top level domain server
  - then passed to authoritative name server
  - correct url returned to user

### Review Questions
14. How would you call the method `prance` from within the method `move` on a `Horse` instance?
class Horsey
  def prance
    'Bands'll make them prance'
  end

  def move
    prance
  end
end
15. Given the following hash:

```ruby
furniture = {table: {height: 3, color: "red"}, purchased: true}
```
What is the different between how you would return true vs returning 3?
  furniture[:purchased] = true
  furniture[:table][:height]
16. What is inheritance?
  The idea that classes can inherit attributes/methods from a superclass

### Self Assessment:
Choose One:
* I was able to answer most questions independently, but utilized outside resources for a few

Choose One:
* I feel comfortable with the content presented this week
