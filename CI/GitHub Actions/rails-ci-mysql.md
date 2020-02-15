```yml
name: Rubocop & RSpec

on: [push]

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - name: Set up Ruby 2.5.1
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: 2.5.1

      - uses: actions/cache@v1
        with:
          path: vendor/bundle
          key: bundle-${{ hashFiles('**/Gemfile.lock') }}

      - name: Install libmysqlclient-dev
        run: sudo apt-get install -y libmysqlclient-dev

      - uses: borales/actions-yarn@v2.0.0
        with:
          cmd: install

      - name: Install bundler2
        run: gem install bundler

      - name: bundle install
        run: bundle install --jobs 4 --retry 3 --path vendor/bundle

      - name: Setup Database
        run: |
          cp config/database.yml.github-actions config/database.yml
          bin/rails db:create
          bin/rails db:schema:load
        env:
          RAILS_ENV: test
          MYSQL_ROOT_PASSWORD: root

      - name: Rubocop
        run: bundle exec rubocop

      - name: RSpec
        run: bundle exec rspec
        env:
          RAILS_ENV: test
          MYSQL_ROOT_PASSWORD: root
```

database.yml.github-actions
```yml
test:
  adapter: mysql2
  encoding: utf8mb4
  username: root
  password: <%= ENV.fetch('MYSQL_ROOT_PASSWORD', '') %>
  database: jobdraft_test
```
