## Week Two - Module 2 Recap

Fork or re-pull this respository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week (which is a TON - YOU are a web developer!!!).

Note: When you're done, submit a PR.


### Week 2 Questions

1. At a high level, what is ActiveRecord? What does it do/allow you to do?
  - ActiveRecord is an Object Relational Mapper, it helps to relate/arrange data between classes and the database

2. Assume you have the following model:

```ruby
class Team << ActiveRecord::Base
end
```

What are some methods you can call on `Team`? If these methods aren't defined in the class, how do you have access to them?
- Average, sum, find, find_by, all, joins, select, group, order; they all inherit from the ActiveRecord Base

3. Assume that in your database, a team has the following attributes: "id", "name", owner_id". How would you find the name of a team with an id of 4? Assuming your class only included the code from question 2, how could you find the owner of the same team?
  3A.) Team.where(id: 4).select(:name)/.name
  3B.) Owner.where(id: Team.find(4).owner_id)
4. Assume that you added a line to your `Team` class as follows:

```ruby
class Team << ActiveRecord::Base
  belongs_to :owner
end
```

Now how would you find the owner of the team with an id of 4?
Team.find(4).owner

5. In a database that's holding students and teachers, what will be the relationship between students and teachers? Draw the schema diagram.
Assuming many students have many teachers, and teachers have many students

class Teacher < ApplicationRecord
  has_many :student_teachers
  has_many :students, through: :student_teachers
end

class Student < ApplicationRecord
  has_many :student_teachers
  has_many :teachers, through: :student_teachers
end

Schema::Something.something-something
  create_table :students do
    t.string  :name
    t.age     :integer

    t.timestamps
  end


  create_table :teachers do  
    t.string    :name
    t.integer   :age

    t.timestamps
  end

  create_table :student_teachers do
    t.bigint :teacher_id
    t.bigint :student_id
    t.index ["teacher_id"], name: 'index_student_teachers_on_teacher_id'
    t.index ["student_id"], name: 'index_student_teachers_on_student_id'
  end

  add_foreign_key "student_teachers", "teachers"
  add_foreign_key "student_teachers", "students"
end

6. Define foreign key, primary key, and schema.
Foreign Key: this is a column held in a table that correlates to the unique id (primary key) of another table

Primary Key: All rows in a table have a unique primary key with which they can be called/found

Schema: How the tables as well as rows and columns thereof are arranged in a database

7. Describe the relationship between a foreign key on one table and a primary key on another table.
A foreign key on one table correlates to a primary key on another table: the two rows may be called from the other by utilizing this key.

8. What are the parts of an HTTP response?
The head (consisting of verb, path and protocol), and the body


### Optional Questions

1. Name your five favorite ActiveRecord methods (i.e. methods your models inherit from ActiveRecord) and describe what they do.
  - Where: easily my favorite and most useful method: seeks out rows of a table based on certain parameters

2. Name your three favorite ActiveRecord rake tasks and describe what they do.
  - rails g migration CreateTables name:string age:bigint body:text
  * This command is great for making new tables as well as specifying which columns it should have as well as the datatype stored therein.
  - rake db:migrate
  * Who could forget this timeless classic? Migrating the tables you created into the schema and enabling more data to be arranged as such
  - rails g migration AddTableToOtherTable table_1::references
  * Enables a column to be added on an existing table: add_reference :first_tables, :new_columns, foreign_key: true
  - rails g migration CreateJoinTable table_1:references table_2:references
  * enables a joint table to be created between two existing tables
  - rake db:{drop,create,migrate,seed}
  * Everyone's favorite four-in-one

3. What two columns does `t.timestamps null: false` create in our database?
  * created_at and updated_at

4. In a database that's holding schools and teachers, what will be the relationship between schools and teachers?
  Assuming a teacher can only belong to one school:
    class Teacher < ApplicationRecord
      belongs_to :school
    end

    class School < ApplicationRecord
      has_many :teachers
    end

5. In the same database, what will you need to do to create this relationship (draw a schema diagram)?
  create_table :teachers do
    t.string      :name
    t.integer     :school_id

    t.timestamps
  end

  create_table :schools do
    t.string      :name
    t.text        :location

    t.timestamps
  end

6. Give an example of when you might want to store information besides ids on a join table.
  Additional info could be stored in a join table for clarity

7. Describe and diagram the relationship between patients and doctors.
A patient can have many doctors, and a doctor could have many patients, this would be a many-to-many relationship

create_table :patients do
t.string      :name

t.timestamps
end

create_table :doctors do
t.string      :name

t.timestamps
end

create_table :doctor_patients do
t.integer     :patient_id
t.integer     :doctor_id
t.index["patient_id"], name: "index_doctor_patients_on_patient_id"
t.index["doctor_id"], name: "index_doctor_patients_on_doctor_id"
end

add_foreign_key "doctor_patients", "patients"
add_foreign_key "doctor_patients", "doctors"

8. Describe and diagram the relationship between museums and original_paintings.
  class Museum < ApplicationRecord
    has_many :paintings
  end

  class OriginalPainting < ApplicationRecord
    belongs_to :museum
  end

  This would be a one-to-many relationship, as an original painting could not be duplicated and remain original

9. What could you see in your code that would make you think you might want to create a partial?
  * Headers
  * Footers
  * Navbars

### Self Assessment:
Choose One:
* I was able to answer most questions independently, but utilized outside resources for a few

Choose One:
* I feel comfortable with the content presented this week (mostly - BUT IT'S SO MUCH I'M WORRIED IT WILL FALL OUT OF MY HEAD)
