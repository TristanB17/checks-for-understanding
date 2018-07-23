## Week Four Recap

### Instructions
Fork or re-pull this repository. Answer the questions to the best of your ability.

Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week.

Note: When you're done, submit a PR with a reflection in the comments about how this exercise went for you.

### Week 4 Questions

1. What is a cookie?
  - A text file that can be used to identify a user, stored on the client's computer and stores up to 4KB of data
2. What’s the difference between a session and a cookie?
  - Cookies are stored in the client's computer, sessions belong to the server
3. What’s a flash and when do you want to use flashes?
  - a flash is similar to a notification, you want to use it when there's been a change of state for the user (i.e. login, logout, failure to login etc)
4. Why do people say “HTTP is stateless”?
  - They are plain by default and have no special settings depending on the user
5. What’s authentication? Explain.
  - Authentication is verifying a user is who they say they are via a username and password
6. What’s the difference between authentication and authorization?
  - Authentication is ensuring the user is who they say they are, but authorization is the privilege to execute certain functions unavailable to the average user
7. What’s a before filter?
  - A before filter will carry out a method or set of methods prior to a controller class using a methods
8. How do we keep track of a user once they’ve logged in?
  - Via their login, which can limit their contributions to a website
9. When do you want to namespace a resource? When do you want to nest a resource? What's the differences between those two approaches?
  - namespacing is usually enabled to allow admins to have certain privileges
10. At a high level, what tools can you use to implement authorization? How would you use them?
  - Bcrypt at a basic level, clearance and sorcery at a higher level
11. What's an enum, and what advantages does it offer? What data type needs to be in your database to use an enum? Where do you declare an enum?
  it's a method used in a model used to delineate a role (user/admin)
12. What are some strategies you can use to keep your views DRY?
  - partials can often save some space when it comes to making a new or edit view page.

### Reviews Questions
13. Given the following array of hashes, how would I print an alphabetical list of holidays?
```ruby
[
 {holiday: {name: "St Patrick's Day", supplies: ["Corned Beef and Cabbage"]}},
 {holiday: {name: "Halloween", supplies: ["Candy", "Costume"]}},
 {holiday: {name: "Hanukkah", supplies: ["Menorah"]}}
]
```
  happy_holidays = holiday_hashes.reduce([]) do |sum, day|
    sum << day[:holiday][:name]
    sum
  end

  print happy_holidays.sort.join(", ")

14. How would you clean incoming data to ensure "$300" or "300.00" is stored as 300?
  Not gonna lie, totally used stack overflow for this one: "$300".gsub(/\D/,'').to_i //
  BUT this will not work for "$300.00" - so I just manunally would delete it in that case
  "$300.00".delete("$").to_i

### Self Assessment:
Choose One:
* I was able to answer most questions independently, but utilized outside resources for a few

Choose One:
* I feel comfortable with the content presented this week
