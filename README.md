# Angular 2.0 Workshops

### Clone repo:

```
git clone git@github.com:womanonrails/angular2-example-app.git
cd angular2-example-app
```

### Instal dependences:

```
npm install
npm start
```

### Prepare Rails

1. Gemset:
  - `.ruby-version`
  - `.ruby-gemset`

2. `gem install rails`
3. `rails new angular_api_app --api`
4. `cd angular_api_app`
5. Initial commit for Rails
6. Modify Rails inflections

  ```ruby
  # config/initializers/inflections.rb
  ActiveSupport::Inflector.inflections(:en) do |inflect|
    inflect.irregular 'hero', 'heroes'
  end
  ```

7. `rails g scaffold hero name:string:uniq`

8. Update migration

  ```ruby
  # db/migrate
  class CreateHeroes < ActiveRecord::Migration[5.0]
    def change
      create_table :heroes do |t|
        t.string :name, null: false

        t.timestamps
      end
      add_index :heroes, :name, unique: true
    end
  end
  ```

9. `rails db:migrate`

10. Prepare seeds

  ```ruby
  # db/seed.rb
  Hero.create([
    { name: 'Jason' },
    { name: 'Tim' },
    { name: 'Zach' },
    { name: 'Matt' },
  ])
  ```

11. `rails db:seed`
12. `rails server -p 3002`
13. `gem 'rack-cors'`
14. `bundle install`
15. Prepare Cors

  ```ruby
  # config/initializers/cors.rb
  # Be sure to restart your server when you modify this file.

  # Avoid CORS issues when API is called from the frontend app.
  # Handle Cross-Origin Resource Sharing (CORS) in order to accept cross-origin AJAX requests.

  # Read more: https://github.com/cyu/rack-cors

  Rails.application.config.middleware.insert_before 0, Rack::Cors do
    allow do
      origins '*'

      resource '*',
        headers: :any,
        methods: [:get, :post, :put, :patch, :delete, :options, :head]
    end
  end
  ```

### Back to Angular 2.0

Let's finished [this tutorial](https://angular.io/docs/ts/latest/tutorial/toh-pt6.html)


### Usefull links
  - [Prepared base Angular 2 app](https://github.com/angular/quickstart/blob/master/README.md)
  - [Connectig Angular 2 with Rails 5](https://www.angularonrails.com/angular-2-tour-heroes-tutorial-rails-backend/)
  - [Official Angular 2 tutorial](https://angular.io/docs/ts/latest/tutorial/toh-pt6.html)
