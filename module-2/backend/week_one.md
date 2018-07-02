## Week One - Module 2 Recap

Fork this respository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week (which is a TON!).

Note: When you're done, submit a PR.

### Week 1 Questions

1. List the five common HTTP verbs and what the purpose is of each verb.
  * GET - retrieves information in the form of a response from a server
  * POST - submits a form of information to a server to alter existing data
  * PUT - synonymous with 'update', changes existing data on a page in its entirety
  * PATCH - has roughly the same function as PUT, but only alters part of an existing dataset
  * DELETE - Removing an object/row from a database

2. What is Sinatra?
  * Sinatra is a coding software that is used in various applications

3. What is MVC?
  * MVC is a template for designing a program which has three primary components: The controller, the model, and the
  view. The controller will receive information from a web server and then decide how to return a response, choosing an
  appropriate model. Once the appropriate model is chosen, the model will temporarily take over and format the response to
  fit the request originally sent. After formatting, the model will send the data back to the Controller. The controller, in turn, passes the data off to the view, which decides how the data will be displayed or transformed. Finally, the controller is the component which ends the process by returning the appropriate view.

4. Why do we follow conventions when creating our actions/path names in our Sinatra routes?
  * We follow principles of REST in order to make our code more readable

5. What types of variables are accessible in our view templates without explicitly passing them?
  * Instance variables

6. Given the following block of code, how would I pass an instance variable `count` with a value of `1` to my `index.erb` template?
  * Version 1:
    - @count = 1  

  ```ruby
  get '/horses' do
    erb :index
  end
  ```

7. In the same code block, how would I pass a local variable `name` with a value of `Mr. Ed` to the view?
  * :locals => { :name => 'Mr. Ed'}

8. What's the purpose of ERB?
  * Embedded ruby is used to enable the use to ruby methods to alter the display of a view, as oppose to HTML

9. Why do I need a development AND test database?
  * The development database will be used for the actual program, but the test database will allow
  one to use smaller datasets of their choice without affecting the development database.

10. What is CRUD and why is it important?
  * CRUD - create, read, update, destroy/delete
  * CRUD is pivotal to a program as it encompasses the four basic functions an application should have

11. What does HTTP stand for?
  * HyperText Transefer Protocol - a stateless protocol

12. What are the two ways to interpolate Ruby in an ERB view template? What's the difference between these two ways?
  * <%= %>
  * "#{}"
  * The second way must be between the ends of the first  

13. What's an ORM? What does it do?
  * Object Relational Mappers are used to tie a database to classes, enabling the two to interact

14. What's the most commonly used ORM in ruby (Sinatra & Rails)?
  * SQL

15. Let's say we have an application with restaurants. There are seven verb + path combinations necessary to provide full CRUD functionality for our restaurant application. List each of the seven combinations, and explain what each is for.
  * A GET(food order) request is given to a CONTROLLER to view the index page
  * A GET verb is used to visit an individual dish's page to view details about the dish
  * A GET verb is used to take the user to a 'create order' page
  * A POST verb is placed in the orders/new.erb page of the app and sent back to the index, the order is added to the database
  * A GET verb is used to take the user to the Edit screen
  * A PUT verb is used to update the existing order and redirect the user back to the index
  * A DELETE verb is used to destroy the user's order and remove it from the database

16. What's a migration?
  * A migration is a layout of how data will be stored in a database that can be modified and seeded accordingly

17. When you create a migration, does it automatically modify your database?
  * No, one must format the migration before running rake db:migrate to ensure data is being interpreted correctly

18. How does a model relate to a database?
  * A model is the sole component which interacts with the database, extracting objects/data and altering them for the controller to then pass to the view.

19. What is the difference between `#new` and `#create`?
  * 'new' will create an instance of a row/object, but won't save it to the db, create will both generate a new instance and save it to the db.


### Review Questions:  
20. Given a CSV file (“films.csv”) with these headers [id, title, description], how would you load these into your database to create new instances of Film?
  rake db:create_migration NAME=create_films
class 980987209e8r7qw-create_films
  def change
    create_table :films do |t|
    t.integer       :id
    t.string        :title
    t.text          :description

    t.timestamps null: false
  end
end

  rake db:migrate

  CSV.foreach('./some_path.rb', headers: true, header-converters: true) do |row|
    Film.new(id: row[0],
            title: row[1],
            description: row[2])
  end

  rake db:seed

21. Given the following hash:
```
activities = {
  hiking: {cost: $0, supplies: ['hiking shoes', 'water', 'compass']},
  karaoke: {cost: $10, supplies: ['courage', 'microphone']},
  brunch: {cost: $35, supplies: ['mimosa flutes']},
  antiquing: {cost: $200, supplies: ['list of antique stores']}
}
```
How would I add 'granola bar' to things you should have when hiking?
  * activities[:hiking][:supplies] += ["granola bar"]

22. What are the 4 Principles of OOP? Give a one sentence explanation of each.
  * Encapsulation - the limitation of access to other files given to a class, to minimize breakage if an error occurs
  * Inheritance - an 'is a' relationship, where traits can be passed from a parent class to a child class
  (I had to look these two up)
  * Abstraction - the classes do not know the purpose of another close, and can only have a limited interaction. This is also used to express the intent of the class rather than its actual composition.
  * Polymorphism - achieving either a static(unchanging) or dynamic(via method_override) state to satisfy the requirements of the program.


### Self Assessment:
Choose One: (erase the others)
* I was able to answer most questions independently, but utilized outside resources for a few

Choose One:
* I feel comfortable with the content presented this week(I feel pretty good about understanding the material, but I just completed it10 on little-shop, and my syntax needs some work. I slipped up on the Friday code challenge because I overcomplicated the relationship between two tables, but conceptually it was not beyond my understanding - not to say that I understand every detail though!)
