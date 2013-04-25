---
layout: post
title: "Test autocomplete in Rails"
date: 2013-04-25 10:28
comments: true
categories:
  - rails
  - capybara
  - rspec
  - jquery
  - autocomplete
---

Easy way to test autocomplete in RSpec request spec with Capybara

``` ruby

describe 'Description of the spec'
  it "should autocomplete user name", js: true do
    visit users_path
    auto_complete_field = 'user_name'
    fill_in auto_complete_field, with: 'Dimitar'
    page.execute_script %Q{ $('##{auto_complete_field}').trigger("keydown") }
    page.should have_content('Dimitar Kostov')
  end
end
```

<blockquote>Notice: You should use <a href="https://github.com/thoughtbot/capybara-webkit" target="_new">capybara-webkit</a> driver to enable JavaScript interaction.</blockquote>
