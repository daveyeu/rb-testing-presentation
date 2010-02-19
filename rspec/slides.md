!SLIDE

# RSpec #

!SLIDE

# BDD #

!SLIDE smaller

# What little I know... #

!SLIDE subcontent

# Avoid before(:all) #

    @@@ruby
	before :all do
	  @robot = Factory(:robot) // Polluting!!!
	end

!SLIDE subcontent

# Don't pollute your global binding #

    @@@ruby
    require "spec/spec_helper"

	// Don't do this.
    include RustyHelpers
    include PointyHelpers

    // Do this.
    describe KillerRobot do
      include RustyHelpers
      include PointyHelpers

!SLIDE subcontent

# Don't go too far with describe #

    @@@ruby
    describe KillerRobot do
      describe "#stab" do
        describe "when it has a knife" do
          describe "and it feels sleepy" do
            describe "and it gets woken up" do
              ...

!SLIDE subcontent

# Use factories #

    @@@ruby
    robot = Factory(:robot)

!SLIDE subcontent smaller

# Don't go mock crazy #

    @@@ruby
    proxy = mock(Processor)
    proxy.should_receive(:execute).with(1).and_return(true)
    proxy.should_receive(:success?).and_return(true)

    @robot.should_receive(:processor).and_return(proxy)
	@robot.should_receive(:save).and_return(true)

	@robot.kill

!SLIDE subcontent smaller

# Learn your matchers #

    @@@ruby
    lambda { do_something }.should change { count }.by(1)

    @robot.army.should include(@hal, @terminator)

    @robot.self_destruct.should raise_error(RuntimeError)

!SLIDE subcontent bullets smaller incremental

# When your tests get slow #

* Profile (spec --format profile <specs>)
* Look for network IO
* Spork
* Refactor
* Separate suites
* Distributed
* Fixtures

!SLIDE subcontent bullets

# Alternatives #

* test/unit (shoulda, matchy)
* bacon
* riot
* minitest
* [http://www.ruby-toolbox.com/](http://www.ruby-toolbox.com/)

!SLIDE smaller

# Learn one well so you can go fast #
