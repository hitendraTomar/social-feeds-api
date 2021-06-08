# README

## Required Environment / Minimum Setup

Ruby version is `3.0.1`.
Rails version is `6.1.3`.

Minimum setup required to run the app:

```shell
git clone https://github.com/hitendraTomar/social-feeds-api.git
cd social-feeds-api
bundle install

# NOTE: need to fill in the ENV values by below mentioned command. Need to setup below mentioned variables.
#  feed_base_url: https://takehome.io
#  database:
#    username: rails
#    password: rails
#    host: localhost

EDITOR=vim rails credentials:edit

# SetUp database
rails db:create db:migrate

# Start the rails server using
rails server
```

## Testing

Run the test suite to confirm if the setup is successful.

Make sure that the test database is prepared:

```shell
RAILS_ENV=test rails db:structure:load
```

Then run test suites:

```shell
rspec
```

## Details of Implementation
* Using `takehome.io` to fetch data for all three social media platforms: Facebook, Twitter, Instagram.
* If the response code is 200, then the response body getting parsed.
* In case the response code is not 200 for a request to a particular social network which indicates something went be wrong, then I am adding this value: `[{ error_message: 'Something went wrong.' }]`
* Connection timeouts are also handled explicitly and the error message in this case.
`[{ error_message: 'Connection timed out.' }]`
* You can change error messages by changing in the `en.yml` file.
