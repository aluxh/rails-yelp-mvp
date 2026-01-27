## NOTES

### Phase 1: Setting Up Models and Database

1. Create the models using the following command, and it will generate 2 files for each model:
    ```bash
    rails generate model <ModelName>
    ```
  - One file will be for the migration (to create the database table).
  - The other file will be for the model itself (to define the model's behavior and attributes).

2. After generating the models, run the migration to create the tables in the database:
    ```bash
    rails db:migrate
    ```

3. Add reference columns to establish relationships between models. For example, to add a reference from `posts` to `users`, you can generate a migration like this:
    ```bash
    rails generate migration AddUserRefToPosts user:references
    ```
  - Then run the migration again:
    ```bash
    rails db:migrate
    ```

4. If you have rspec created for testing the models, you can run the tests using:
    ```bash
    rspec
    ```
  - This will execute all the test cases defined in your spec files.

5. Edit the db seeds file (`db/seeds.rb`) to add initial data to your database. After editing, run the following command to seed the database:
    ```bash
    rails db:seed
    ```
  - This will populate your database with the data defined in the seeds file.

6. Configure the routes in `config/routes.rb` to define the endpoints for your application. For example:
    ```ruby
    resources :posts
    ```
  - This will create RESTful routes for the `posts` resource.

7. Generate controllers for your models using:
    ```bash
    rails generate controller <ControllerName>
    ```
  - This will create a controller file and associated view files.

8. Create views for your controllers in the `app/views/<controller_name>/` directory. You can create HTML files (e.g., `index.html.erb`, `show.html.erb`) to define how data is presented to the user.

### Phase 2: User Stories Implementation

Asking yourself what user stories will compose your application and which routes you will need is a very important step in your web-app building process. Routes should exactly mirror your product’s user stories. So, taking an example from an exercise, we want to build a restaurant review app. So let’s define our minimal product here:

- A visitor can see the list of all restaurants.
  - GET "restaurants"

- A visitor can add a new restaurant, and be redirected to the show view of that new restaurant.
  - GET "restaurants/new"
  - POST "restaurants"

- A visitor can see the details of a restaurant, with all the reviews related to the restaurant.
  - GET "restaurants/38"

- A visitor can add a new review to a restaurant
  - GET "restaurants/38/reviews/new"
  - POST "restaurants/38/reviews"

In our MVP, a visitor cannot update / delete any restaurant or review. This is the role of the admin (i.e. you) - as a developer you have the power to manipulate the DB from the rails console if you want to update / delete any record.

We know it’s a pretty basic MVP, but we just need you to understand that each route is the embodiment of a user-story. Don’t just blindly write 7 CRUD routes for every model in your app. It’s the best way to get confused by your own product and forget what your MVP really is.
