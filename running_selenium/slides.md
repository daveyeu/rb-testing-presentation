!SLIDE

# Running Selenium #

### (on Snow Leopard) ###

!SLIDE commandline incremental

    $ gem install cucumber-rails -v0.2.3
    ...
    Successfully installed cucumber-0.6.2
    Successfully installed cucumber-rails-0.2.3
    ...

    $ gem install webrat -v0.7.0
    Successfully installed rack-test-0.5.3
    Successfully installed webrat-0.7.0
    2 gems installed

    $ gem install selenium-client
    Successfully installed selenium-client-1.2.18
    1 gem installed

!SLIDE subcontent bullets incremental

# Firefox 3.5.7 #

* Install 3.5.7
* 3.6.x borked
* May be fixed in the latest Selenium jar (2.0a2)
* Not included in webrat yet anyway

!SLIDE subcontent

# config/cucumber.yml #

    @@@ yaml
    default: -r features/support/env.rb   \
             -r features/step_definitions \
             -r features/support/plain.rb \
             ...

    selenium: -r features/support/env.rb      \
              -r features/step_definitions    \
              -r features/support/selenium.rb \
              ...

!SLIDE subcontent

# features/support/selenium.rb #

    @@@ ruby
    require "webrat/selenium/matchers"

    Webrat.configure do |config|
      config.mode = :selenium
      config.application_environment = :selenium
      config.selenium_browser_startup_timeout = 60
    end

    World(Webrat::Selenium::Matchers)

!SLIDE subcontent commandline

# plain vs. selenium #

    $ script/cucumber features/plain

    $ script/cucumber -p selenium features/selenium

!SLIDE

# Demo #
