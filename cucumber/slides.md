!SLIDE

# Cucumber? #

!SLIDE

# Integration testing with stories #

!SLIDE subcontent

# test/integration #

    @@@ ruby
    def test_signup_new_person
      get "/signup"
      assert_response :success
      assert_template "signup/index"

      post "/signup",
           :name => "bob",
           :password => "secret"
      assert_response :redirect
      follow_redirect!
      assert_response :success
      assert_template "ledger/index"
    end

!SLIDE subcontent

# features #

    @@@ cucumber
    Feature: Search courses
      Scenario: Search by topic
        Given there are 240 courses
        And there are 2 courses A001, B205
        When I search for "biology"
        Then I should see the following courses:
          | Course code |
          | A001        |
          | B205        |
