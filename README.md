#MavensMate

####PLEASE NOTE: this version of MavensMate is no longer being actively developed. We recommend using the Sublime Text version of MavensMate, which can be found here --> https://github.com/joeferraro/MavensMate-SublimeText

MavensMate is a TextMate bundle that aims to replicate the functionality of the Eclipse-based Force.com IDE.

* Create & Edit Salesforce.com projects with specific package metadata
* SVN & Git support
* Create & compile Apex Classes, Apex Trigger, Visualforce Pages, and Visualforce Components
* Compile and retrieve other Salesforce.com metadata
* Run Apex test methods and visualize test successes/failures & coverage
* Setup deployment connections & deploy Salesforce.com metadata to orgs
* Create "changesets" for easy deployment
* Headless Selenium testing via RSpec/Capybara
* Supports code completion for SObject fields & Apex primitive methods (alpha)
 
##Clean Install
(If you have installed XCode 4 via the App Store, you will need to install the <a href="https://github.com/kennethreitz/osx-gcc-installer">GCC development tools</a> before proceeding.)

```
$ sudo gem install builder
$ sudo gem install savon
$ sudo gem install rubyzip
```

To take advantage of headless Selenium tests:

```
$ sudo gem install rspec
$ sudo gem install capybara
$ sudo gem install selenium-webdriver
$ sudo gem install libwebsocket
```

```
$ mkdir -p ~/Library/Application\ Support/TextMate/Bundles
$ cd ~/Library/Application\ Support/TextMate/Bundles
$ git clone git://github.com/joeferraro/MavensMate.git "MavensMate.tmbundle"
$ osascript -e 'tell app "TextMate" to reload bundles'
```

Open TextMate, go to Preferences --> Advanced --> Shell Variables and add a Shell Variable called "FM_PROJECT_FOLDER" with the value being the location where you'd like your Salesforce.com projects to reside (for example: '/Users/joe/Projects') [*notice the absolute path*]

	/Users/username/development/projects

*FM_PROJECT_FOLDER is the only TextMate shell variable required by MavensMate*

<img src="http://wearemavens.com/images/mm/path3.png"/>

###RUBY GUIDE
####System Ruby (1.8.7)
To make MavensMate utilize your system Ruby, install the required gems directly into /Library/Ruby/Gems/1.8:

```
$ sudo gem install builder -i /Library/Ruby/Gems/1.8
$ sudo gem install savon --version 0.9.7 -i /Library/Ruby/Gems/1.8
$ sudo gem install rubyzip -i /Library/Ruby/Gems/1.8
```

####RVM - Ruby 1.8.7
```
$ gem install builder
$ gem install savon --version 0.9.7
$ gem install rubyzip
```

Your TextMate PATH shell variable should be enabled and should look something like this:

	/Users/your_username/.rvm/rubies/ruby-1.8.7-p352/bin:/usr/bin:/usr/sbin

Create a TextMate shell variable named GEM_PATH with the value:

	/Users/your_username/.rvm/gems/ruby-1.8.7-p352/


####RVM - Ruby 1.9+
```
$ gem install builder
$ gem install savon
$ gem install rubyzip
```

Your TextMate PATH shell variable should be enabled and should look something like this:

	/Users/your_username/.rvm/rubies/ruby-1.9.3-p0/bin:/usr/bin:/usr/sbin

Create a TextMate shell variable named GEM_PATH with the value:

	/Users/your_username/.rvm/gems/ruby-1.9.3-p0/

TextMate is not equipped to run Ruby 1.9.x out of box, so if you're committed to using Ruby 1.9.x, you'll need to make a slight modification to TextMate's plist.bundle:

```
$ git clone git://github.com/kballard/osx-plist.git
$ cd osx-plist/ext/plist
$ ruby extconf.rb && make
$ cp plist.bundle /Applications/TextMate.app/Contents/SharedSupport/Support/lib/osx/
```

###IMPORTANT
If you get a ruby "constantize" exception when running a MavensMate command, it's likely a gem dependency issue. Ensure you've installed rails, builder, savon, and rubyzip.

##Update

```
$ cd ~/Library/Application\ Support/TextMate/Bundles
$ rm -rf ~/Library/Application\ Support/TextMate/Bundles/MavensMate.tmbundle
$ git clone git://github.com/joeferraro/MavensMate.git "MavensMate.tmbundle"
$ osascript -e 'tell app "TextMate" to reload bundles'
```

##MavensMate Shortcut Keys (configurable)

Open MavensMate options:

	Control + Option + Command + M

Compile current metadata:

	Control + Option + Command + C

Deploy to server:

	Control + Option + Command + D	

Run RSpec Selenium test:

	Control + Option + Command + T

Run all RSpec Selenium tests in file:

	Control + Option + Command + Y

Code Completion (alpha):

	Shift + Tab (caret after dot for Sobject field completion #=> myAccount.<shift+tab here>)


##Some extra goodies

We recommend the following to augment MavensMate:

* ProjectPlus TextMate plugin >>> adds nifty SVN/Git icons to project folder/file icons <A HREF="http://ciaranwal.sh/projectplus">http://ciaranwal.sh/projectplus</A>


##Screencast

<a href="http://vimeo.com/mavens/review/33363307/c072a3df51">http://vimeo.com/mavens/review/33363307/c072a3df51</a>

##Screenshots

###Project Wizard
<img src="http://wearemavens.com/images/mm/project_wizard.png"/>
###Metadata Creation
<img src="http://wearemavens.com/images/mm/metadata.png"/>
###Apex Test Runner
<img src="http://wearemavens.com/images/mm/test2.png"/>
###Deployment Connections
<img src="http://wearemavens.com/images/mm/deployment_connections.png"/>
###Changesets (alpha)
<img src="http://wearemavens.com/images/mm/changesets.png"/>
###Code Completion (alpha)
<img src="http://wearemavens.com/images/mm/completion2.png"/>
###Options Dialog
<img src="http://wearemavens.com/images/mm/options.png"/>