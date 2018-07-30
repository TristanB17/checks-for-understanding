### Week 5 Questions

Re-pull from this respository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week (which is a TON!).

Note: When you're done, submit a PR.

### Week 5 Questions
1. How do we make flash messages display on a page?
  flash[:notice] = "some message" OR flash[:alert] = 'a different message'

2. Where is cart information/temporary information usually stored?
  In a session

3. What might be some reasons not to store a cart in our database? Are there any reasons why we would want to persist that information?
  Storage space in a database may be limited, and gratuitous data could prove detrimental to the speed/usability of the site

4. What is the purpose of the asset pipeline?
  It is to streamline asset compilation, as well as make an easier to navigate series of paths

5. Why do we precompile our assets?
  Because only html, css and javascript can be understood by browsers as raw code, but if it is precompiled, a browser
  can more easily understand the assets

6. What do each of the following tags do?

```ruby
<%= stylesheet_link_tag "application" %>
<%= javascript_include_tag "application" %>
<%= image_tag "rails.png" %>
```
1.) Enables access to a stylesheet(CSS)
2.) Enables access to javascript files
3.) references an existing image

7. What are some of the elements of a great read me? What are some of the benefits of taking the time to update a readme for our project?
  A good readme can go as far to guide projects very large in scale. Readmes can also address an existing issue and how they
  the code can solve or improve it.  

8. What are the top four accessibility issues that we as developers should be aware of?
  - literacy should not be assumed
  - hearing disabilities
  - blindness
  - using the site without a mouse (laptop)

9. `before_save` is an example of a what? Where in our Rails application would we find a `before_save`?
  - it is a callback, which should only be used as a 'codesmell', something that is a workaround to an existing problem and it
  is usually found in the models

10. Given the following object, how would we create a scope for all users who are active?

```ruby
User.create(name: "Happy", active: true)
```
- scope :user -> {where(active: true)}

11. What is the difference between a scope and a class method?
  A scope method is one which applies to a set of a certain class that meet a certain criteria,
  whereas a class method applies to the entire class

### Review Questions:  
12. Given the following hash:  

```ruby
{cart: {"17" => 4, "204" => 52, "29" => 22}}
```

  12a. How would you add item with id of 48 with a quantity of 4?
  session[:cart][48] = 4
  12b. How would you increase the quantity of item 29?  
  session[:cart][29] += 7
  12c. How would you find out how many items your user is thinking about purchasing?  
  session[:cart].values.sum

13. What is polymorphism? How does it relate to duck-typing? What are two ways you use this in everyday Rails applications?
    polymorphism is the ability for a method to have more than one application, and it relates to duck-typing as it
    will overwrite any code assigned to it
14. How would you clean the string "(630) 854-5483" to "630.854.5483"?  
    "(630) 854-5483".delete('(', ')', "-").squeeze.insert(3, "."), insert(7, ".")

### Self Assessment:
Choose One:
* I was able to answer a few questions independently, but relied heavily on outside resources

Choose One:
* I feel comfortable with the content presented this week

* I feel comfortable with the material, but I definitely need more practice
