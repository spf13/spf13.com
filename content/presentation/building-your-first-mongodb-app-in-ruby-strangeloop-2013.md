---
Description: An updated tutorial given at strageloop 2013 introduces the features
  of MongoDB by building a simple location-based application using MongoDB.
Keywords:
- MongoDB
- Presentations
- Ruby
Tags:
- mongodb
- Ruby
Title: Build your first MongoDB App in Ruby @ StrangeLoop 2013
Topics:
- MongoDB
- Presentations
date: 2013-09-23
---

An updated version of the [very popular workshop I gave at OSCON last year](presentation/building-your-first-mongodb-app-oscon-2012/).

This presentation was given at Strangeloop 2013 as a 3 hour interactive workshop.
<!--more-->
This tutorial will introduce the features of
[MongoDB](http://www.mongodb.org/ "MongoDB") by building a simple
location-based application using MongoDB. The tutorial will cover the
basics of MongoDB’s document model, query language, map-reduce framework
and deployment architecture.

The tutorial will be divided into 5 sections:

-   Data modeling with MongoDB: documents, collections and databases
-   Querying your data: simple queries, geospatial queries, and
    text-searching
-   Writes and updates: using MongoDB’s atomic update modifiers
-   Trending and analytics: Using mapreduce and MongoDB’s aggregation
    framework
-   Deploying the sample application

Besides the knowledge to start building their own applications with
MongoDB, attendees will finish the session with a working application
they use to check into locations around Portland from any HTML5 enabled
phone!

**TUTORIAL PREREQUISITES**<br>
Each attendee should have a running version of MongoDB. Preferably the latest stable release 2.4.6. 
You can dowload MongoDB at [http://www.mongodb.org/downloads](http://www.mongodb.org/downloads).

Instructions for installing MongoDB are
at [http://docs.mongodb.org/manual/installation/](http://docs.mongodb.org/manual/installation/).

Additionally we will be building an app in Ruby. Ruby 1.9.3+ is required for this. The current latest version of ruby is 2.0.0-p247.

There are many ways to install ruby, feel free to use your own solution if you have a preference. 
The following resources are also available:

-   For windows download
    the [http://rubyinstaller.org/](http://rubyinstaller.org/)
-   For OSX download [http://unfiniti.com/software/mac/jewelrybox/](http://unfiniti.com/software/mac/jewelrybox/)
-   For linux most users should know how to for their own distributions.

We will be using the following GEMs and they MUST BE installed ahead of time so you can be ahead of the game and safe in the event that the Internet isn’t accommodating.

-  bson 
-  bson_ext 
-  haml 
-  mongo
-  rack 
-  rack-protection 
-  rack shotgun 
-  sinatra 
-  tilt 

Prior ruby experience is NOT required for this, though you should be familiar with basic web programming in a similar language (javascript, php, perl, python, etc). 

We will NOT be using rails for this app.

{{% slideshare 26310189 %}}


## Transcript

1. Building your first MongoDB Application
2. Agenda Introduction to MongoDB MongoDB Fundamentals Running MongoDB Schema Design Ruby & Sinatra Crash Course Building Our First App
3. @spf13 Steve Francia AKA Chief Developer Advocate @ responsible for drivers, integrations, web & docs
4. Introduction to mongodb
5. What Is MongoDB?
6. * Document * Open source * High performance * Horizontally scalable * Full featured MongoDB is a ___________ database
7. * Not for .PDF & .DOC files * A document is essentially an associative array * Document == JSON object * Document == PHP Array * Document == Python Dict * Document == Ruby Hash * etc Document Database
8. * MongoDB is an open source project * On GitHub * Licensed under the AGPL * Commercial licenses available * Contributions welcome Open Source
9. * Written in C++ * Extensive use of memory-mapped files i.e. read-through write-through memory caching. * Runs nearly everywhere * Data serialized as BSON (fast parsing) * Full support for primary & secondary indexes * Document model = less work High Performance
10. Horizontally Scalable
11. * Ad Hoc queries * Real time aggregation * Rich query capabilities * Traditionally consistent * Geospatial features * Support for most programming languages * Flexible schema Full Featured
12. Depth of Functionality Scalability&Performance Memcached MongoDB RDBMS Database landscape
13. http://www.mongodb.org/downloads
14. What is a Record?
15. Key → Value * One-dimensional storage * Single value is a blob * Query on key only * No schema * Value cannot be updated, only replaced Key Blob
16. Relational * Two-dimensional storage (tuples) * Each field contains a single value * Query on any field * Very structured schema (table) * In-place updates * Normalization process requires many tables, joins, indexes, and poor data locality Primary Key
17. Document * N-dimensional storage * Each field can contain 0, 1, many, or embedded values * Query on any field & level * Flexible schema * Inline updates * * Embedding related data has optimal data locality, requires fewer indexes, has better performance _id
18. Running Mongodb
19. MongoD
20. Mongo Shell
21. user = { username: 'fred.jones', first_name: 'fred', last_name: 'jones', } Start with an object (or array, hash, dict, etc)
22. > db.users.insert(user) Insert the record No collection creation needed
23. > db.users.findOne() { "_id" : ObjectId("50804d0bd94ccab2da652599"), "username" : "fred.jones", "first_name" : "fred", "last_name" : "jones" } Querying for the user
24. * _id is the primary key in MongoDB * Automatically indexed * Automatically created as an ObjectId if not provided * Any unique immutable value could be used _id
25. * ObjectId is a special 12 byte value * Guaranteed to be unique across your cluster * ObjectId("50804d0bd94ccab2da652599") |-------------||---------||-----||----------| ts mac pid inc ObjectId
26. Schema Design
27. Tradational schema design Focuses on data storage
28. Document schema design Focuses on use
29. 4 Building blocks of Document Design
30. flexibility * Choices for schema design * Each record can have different fields * Field names consistent for programming * Common structure can be enforced by application * Easy to evolve as needed
31. Arrays * Each field can be: * Absent * Set to null * Set to a single value * Set to an array of many values * Query for any matching value * Can be indexed and each value in the array is in the index
32. embedded Documents * An acceptable value is a document * Nested documents provide structure * Query any field at any level * Can be indexed
33. * Object in your model * Associations with other entities entity Association Referencing (Relational) Embedding (Document) has_one embeds_one belongs_to embedded_in has_many embeds_many has_and_belongs_to_many MongoDB has both referencing and embedding for universal coverage
34. Exercise 1: Model a business card
35. Business Card
36. Contacts { “_id”: 2, “name”: “Steven Jobs”, “title”: “VP, New Product Development”, “company”: “Apple Computer”, “phone”: “408-996-1010”, “address_id”: 1 } Referencing Addresses { “_id”: 1, “street”: “10260 Bandley Dr”, “city”: “Cupertino”, “state”: “CA”, “zip_code”: ”95014”, “country”: “USA” }
37. Contacts { “_id”: 2, “name”: “Steven Jobs”, “title”: “VP, New Product Development”, “company”: “Apple Computer”, “address”: { “street”: “10260 Bandley Dr”, “city”: “Cupertino”, “state”: “CA”, “zip_code”: ”95014”, “country”: “USA” }, “phone”: “408-996-1010” } embedding
38. Exercise 2: Store a business card
39. Contacts db.contacts.insert( { “_id”: 2, “name”: “Steven Jobs”, “title”: “VP, New Product Development”, “company”: “Apple Computer”, “phone”: “408-996-1010”, “address_id”: 1 } ) Inserting with Reference Addresses db.addresses.insert( { “_id”: 1, “street”: “10260 Bandley Dr”, “city”: “Cupertino”, “state”: “CA”, “zip_code”: ”95014”, “country”: “USA” } )
40. Exercise 3: Retrieve a business card
41. Contacts c = db.contacts.findOne( { “name”: “Steven Jobs”, } ) Querying with Reference Addresses db.addresses.findOne( { “_id”: c.address_id, “street”: “10260 Bandley Dr”, “city”: “Cupertino”, “state”: “CA”, “zip_code”: ”95014”, “country”: “USA” } )
42. Building a MongoDB Application
43. MongoDB has native bindings for nearly all languages
44. Official Support for 12 languages Community drivers for tons more Drivers connect to mongo servers Drivers translate BSON into native types mongo shell is not a driver, but works like one in some ways Installed using typical means (npm, pecl, gem, pip) MongoDB drivers
45. Building an app in Ruby? Had to pick a language Sinatra is very minimal and approachable Wanted to focus on MongoDB interaction Ruby gems are awesome Works well on Windows, OS X & Linux Seemed like a good idea at the time
46. Ruby Crash Course
47. everything is an object 1.class 'a'.class :z.class class Foo end Foo.class Foo.new.class # => Fixnum # => String # => Symbol # => Class # => Foo
48. Structure Method Class Invocation def do_stuff(thing) thing.do_the_stuff end class TheThing def do_the_stuff puts "Stuff was done!" end end do_stuff(TheThing.new)
49. Strings name = 'World' # => "World" "Hello, #{name}" # => "Hello, World" 'Hello, #{name}' # => "Hello, #{name}"
50. Numbers 1 + 1 # => 2 1 + 1.1 # => 2.1 6 * 7 # => 42 6 ** 7 # => 279936 Math.sqrt(65536) # => 256.0 1.class # => Fixnum (2 ** 42).class # => Fixnum (2 ** 64).class # => Bignum 1.1.class # => Float
51. Arrays Array.new Array.new(3) [] a = [1,2,3] a[0] = 'one' a a[-1] a[1..2] # => [] # => [nil, nil, nil] # => [] # => [1, 2, 3] # => "one" # => ["one", 2, 3] # => 3 # => [2, 3]
52. Hashes Hash.new {} h = {1 => "one", 2 => "two"} h[1] h["1"] h[:one] = "einz" h[:one] h.keys h.values # => {} # => {} # => "one" # => nil # => "einz" # => "einz" # => [1, 2, :one] # => ["one", "two", "einz"]
53. Variables & Names CamelCased # Classes, modules with_underscores # methods, local variables @instance_variable @@class_variable $GLOBAL_VARIABLE
54. Control Structures if condition # ... elsif other_condition # ... end unless condition # ... end while # ... end
55. Sinatra is... not Rails not a framework a DSL for quickly creating web applications in Ruby with minimal effort
56. Hello World # myapp.rb require 'sinatra' get '/' do 'Hello world!' end
57. HTTP Actions In Sinatra, a route is an HTTP method paired with a URL-matching pattern. Each route is associated with a block: get '/' do .. show something .. end post '/' do .. create something .. end put '/' do .. replace something .. end delete '/' do .. annihilate something .. end
58. Routes Routes are matched in the order they are defined. The first route that matches the request is invoked. Route patterns may include named parameters, accessible via the params hash: get '/hello/:name' do # matches "GET /hello/foo" and "GET /hello/bar" # params[:name] is 'foo' or 'bar' "Hello #{params[:name]}!" end #You can also access named parameters via block parameters: get '/hello/:name' do |n| "Hello #{n}!" end
59. Splat Route patterns may also include splat (or wildcard) parameters, accessible via the params[:splat] array: get '/say/*/to/*' do # matches /say/hello/to/world params[:splat] # => ["hello", "world"] end get '/download/*.*' do # matches /download/path/to/file.xml params[:splat] # => ["path/to/file", "xml"] end
60. Building our App in Ruby
61. Introducing the milieu app
62. pre-populating our database
63. Download & Import the venues curl -L http://j.mp/StrangeLoopVenues | mongoimport -d milieu -c venues wget http://c.spf13.com/dl/StrangeLoopVenues.json mongoimport -d milieu -c venues StrangeLoopVenues.json Database Collection
64. Mongo Shell
65. Let’s look at the venues > use milieu switched to db milieu > db.venues.count() 50 Database
66. Let’s look at the venues > db.venues.findOne() { "_id" : ObjectId("52335163695c9d31c2000001"), "location" : { "address" : "1820 Market St", "distance" : 85, "postalCode" : "63103", "city" : "Saint Louis", "state" : "MO", "country" : "United States", "cc" : "US", "geo" : [ -90.20761747801353, 38.62893438211461 ] }, "name" : "St. Louis Union Station Hotel- A DoubleTree by Hilton", "contact" : { "phone" : "3146215262", "formattedPhone" : "(314) 621-5262", "url" : "http://www.stlunionstationhotel.com" }, "stats" : { "checkinsCount" : 0, "usersCount" : 0 } }
67. Creating a Geo index > db.venues.ensureIndex({ 'location.geo' : '2d'}) > db.venues.getIndexes() [ { "v" : 1, "key" : { "_id" : 1 }, "ns" : "milieu.venues", "name" : "_id_" }, { "v" : 1, "key" : { "location.geo" : "2d" }, "ns" : "milieu.venues", "name" : "location.geo_" } ]
68. Skeleton
69. Start with a skeleton /Users/steve/Code/milieu/app/ ▸ config/ ▸ helpers/ ▾ model/ mongodb.rb mongoModule.rb user.rb ▾ public/ ▸ bootstrap/ ▾ css/ styles.css ▸ images/ ▾ views/ footer.haml index.haml layout.haml login.haml navbar.haml register.haml user_dashboard.haml user_profile.haml venue.haml venues.haml app.rb config.ru Gemfile Rakefile README
70. Download & Install deps mkdir milieu cd milieu wget http://c.spf13.com/dl/GettingStarted.tgz tar zxvf GettingStarted.tgz bundle install Resolving dependencies... Using bson (1.9.2) Using bson_ext (1.9.2) Using googlestaticmap (1.1.4) Using tilt (1.4.1) Using haml (4.0.3) Using mongo (1.9.2) Using rack (1.5.2) Using rack-protection (1.5.0) Using shotgun (0.9) Using sinatra (1.4.3) Using bundler (1.3.5) Your bundle is complete! Use `bundle show [gemname]` to see where a bundled gem is installed.
71. Run app shotgun == Shotgun/WEBrick on http://127.0.0.1:9393/ [2013-09-13 21:25:43] INFO WEBrick 1.3.1 [2013-09-13 21:25:43] INFO ruby 2.0.0 (2013-06-27) [x86_64-darwin12.3.0] [2013-09-13 21:25:43] INFO WEBrick::HTTPServer#start: pid=85344 port=9393
72. Open Browser to localhost:9393
73. Preview --- error Screen
74. listing Venues
75. Connecting to MongoDB require 'mongo' require './model/mongoModule' require './model/user' # Connection code goes here CONNECTION = Mongo::Connection.new("localhost") DB = CONNECTION.db('milieu') # Alias to collections goes here USERS = DB['users'] VENUES = DB['venues'] CHECKINS = DB['checkins'] model/mongodb.rb
76. listing Venues get '/venues' do # Code to list all venues goes here @venues = VENUES.░░░░░ haml :venues end app.rb
77. listing Venues get '/venues' do # Code to list all venues goes here @venues = VENUES.find haml :venues end app.rb
78. listing Venues .container .content %h2 Venues %table.table.table-striped %thead %tr %th Name %th Address %th Longitude %th Latitude %tbody ~@venues.each do |venue| %tr %td %a{:href => '/venue/' << venue['_id'].to_s}= venue['name'] %td= venue['location']['address'] ? venue['location']['address'] : '&nbsp' %td= venue['location']['geo'][0].round(2) %td= venue['location']['geo'][1].round(2) views/venues.haml
79. listing Venueslocalhost:9393/venues
80. Paginating Venues get '/venues/?:page?' do @page = params.fetch('page', 1).to_i pp = 10 @venues = VENUES.find.░░░░░(░░░░).░░░░(░░░) @total_pages = (VENUES.░░░░░.to_i / pp).ceil haml :venues end app.rb # replaces the prior entry
81. Paginating Venues get '/venues/?:page?' do @page = params.fetch('page', 1).to_i pp = 10 @venues = VENUES.find.skip((@page - 1) * pp).limit(pp) @total_pages = (VENUES.count.to_i / pp).ceil haml :venues end app.rb # replaces the prior entry
82. .container .content %h2 Venues %table.table.table-striped %thead %tr %th Name %th Address %th Longitude %th Latitude %tbody ~@venues.each do |venue| %tr %td %a{:href => '/venue/' << venue['_id'].to_s}= venue['name'] %td= venue['location']['address'] ? venue['location']['address'] : '&nbsp' %td= venue['location']['geo'][0].round(2) %td= venue['location']['geo'][1].round(2) =pager('/venues') listing Venues views/venues.haml
83. paging through Venueslocalhost:9393/venues
84. Creating Users
85. Creating Users Users are a bit special in our app Not just data Special considerations for secure password handling Not complicated on MongoDB side, but slightly complicated on Ruby side
86. Creating Users class User attr_accessor :_id, :name, :email, :email_hash, :salt, :hashed_password, :collection, :updated_at def init_collection self.collection = 'users' end def password=(pass) self.salt = random_string(10) unless self.salt self.hashed_password = User.encrypt(pass, self.salt) end def save col = DB[self.collection] self.updated_at = Time.now col.save(self.to_hash) end end model/user.rb Inherited from MongoModule.rb
87. Creating Users post '/register' do u = User.new u.email = params[:email] u.password = params[:password] u.name = params[:name] if u.save() flash("User created") session[:user] = User.auth( params["email"], params["password"]) redirect '/user/' << session[:user].email.to_s << "/dashboard" else tmp = [] u.errors.each do |e| tmp << (e.join("<br/>")) end flash(tmp) redirect '/create' end end app.rb
88. Logging in part 1 configure do enable :sessions end before do unless session[:user] == nil @suser = session[:user] end end get '/user/:email/dashboard' do haml :user_dashboard end app.rb
89. Logging in part 2 post '/login' do if session[:user] = User.auth(params["email"], params["password"]) flash("Login successful") redirect "/user/" << session[:user].email << "/dashboard" else flash("Login failed - Try again") redirect '/login' end end app.rb
90. Logging in part 3 def self.auth(email, pass) u = USERS.find_one("email" => email.downcase) return nil if u.nil? return User.new(u) if User.encrypt( pass, u['salt']) == u['hashed_password'] nil end user.rb
91. User Dashboard .container .content .page-header -unless @suser == nil? %h2="Dashboard" %br %image{src: "http://www.gravatar.com/avatar/" << @suser.email_hash.to_s << '.png'} %h3= @suser.name.to_s -else redirect '/' %small %a{href: "/user/" << @suser.email.to_s << "/profile"} profile .container#main-topic-nav views/user_dashboard.haml
92. Dashboard localhost:9393/dashboard
93. Viewing Users
94. Finding a user get '/user/:email/profile' do u = USERS.░░░░░( ░░░░░ => ░░░░░.░░░░░) if u == nil return haml :profile_missing else @user = User.new(u) end haml :user_profile end app.rb
95. Finding a user get '/user/:email/profile' do u = USERS.find_one( "email" => params[:email].downcase) if u == nil return haml :profile_missing else @user = User.new(u) end haml :user_profile end app.rb
96. Creating an INdex > db.users.ensureIndex({email : 1}) > db.users.getIndexes() [ { "v" : 1, "key" : { "_id" : 1 }, "ns" : "milieu.users", "name" : "_id_" }, { "v" : 1, "key" : { "email" : 1 }, "ns" : "milieu.users", "name" : "email_1" } ]
97. A Venue
98. Showing a Venue get '/venue/:_id' do object_id = ░░░░░░░░░░░░░░ @venue = ░░░░░░░░░░( { ░░░░ => object_id }) haml :venue end app.rb
99. Showing a Venue get '/venue/:_id' do object_id = BSON::ObjectId.from_string(params[:_id]) @venue = VENUES.find_one( { :_id => object_id }) haml :venue end app.rb
100. Showing a Venue .row .col-md-4 %h2= @venue['name'].to_s %p =@venue['location']['address'].to_s %br= @venue['location']['city'].to_s + ' ' + @venue['location']['state'].to_s + ' ' + @venue['location']['postalCode'].to_s .col-md-8 %image{:src => '' << gmap_url(@venue, {:height => 300, :width => 450}) } views/venue.haml
101. A Venue localhost:9393/venue/{id}
102. Nearby VenueS
103. Nearby Venues get '/venue/:_id' do object_id = BSON::ObjectId.from_string(params[:_id]) @venue = VENUES.find_one({ :_id => object_id }) @nearby_venues = ░░░░░.░░░░░( {░░░░░ =>{░░░░░=>[ ░░░░░,░░░░░]}} ).░░░░░(4).░░░░░(1) haml :venue end app.rb
104. Nearby Venues get '/venue/:_id' do object_id = BSON::ObjectId.from_string(params[:_id]) @venue = VENUES.find_one({ :_id => object_id }) @nearby_venues = VENUES.find( { :'location.geo' => { ░░░░░ => [ ░░░░░,░░░░░] } }).░░░░░(4).░░░░░(1) haml :venue end app.rb
105. Nearby Venues get '/venue/:_id' do object_id = BSON::ObjectId.from_string(params[:_id]) @venue = VENUES.find_one({ :_id => object_id }) @nearby_venues = VENUES.find( { :'location.geo' => { ░░░░░ => [ ░░░░░,░░░░░] } }).limit(4).skip(1) haml :venue end app.rb
106. Nearby Venues get '/venue/:_id' do object_id = BSON::ObjectId.from_string(params[:_id]) @venue = VENUES.find_one({ :_id => object_id }) @nearby_venues = VENUES.find( { :'location.geo' => { :$near => [ @venue['location']['geo'][0], @venue['location']['geo'][1]] } }).limit(4).skip(1) haml :venue end app.rb
107. ... .row - @nearby_venues.each do |nearby| .col-md-3 %h2 %a{:href => '/venue/' + nearby['_id'].to_s}= nearby['name'].to_s %p =nearby['location']['address'].to_s %br= nearby['location']['city'].to_s + ' ' + nearby['location']['state'].to_s + ' ' + nearby['location']['postalCode'].to_s %a{:href => '/venue/' + nearby['_id'].to_s} %image{:src => '' << gmap_url(nearby, {:height => 150, :width => 150, :zoom => 17}) } views/venue.haml listing Nearby Venues
108. Nearby Venues localhost:9393/venue/{id}
109. Checking IN
110. Checking in get '/venue/:_id/checkin' do object_id = BSON::ObjectId.from_string(params[:_id]) @venue = VENUES.find_one({ :_id => object_id }) user = USERS. ░░░░░_and_░░░░░(░░░░░) if ░░░░░ ░░░░░ ░░░░░ ░░░░░ ░░░░░ else ░░░░░ ░░░░░ ░░░░░ ░░░░░ end flash('Thanks for checking in') redirect '/venue/' + params[:_id] end app.rb
111. Checking in get '/venue/:_id/checkin' do object_id = BSON::ObjectId.from_string(params[:_id]) @venue = VENUES.find_one({ :_id => object_id }) user = USERS.find_and_modify( :query => ░░░░░, :update => ░░░░░, :new => 1) if ░░░░░ ░░░░░ ░░░░░ ░░░░░ ░░░░░ else ░░░░░ ░░░░░ ░░░░░ ░░░░░ end flash('Thanks for checking in') redirect '/venue/' + params[:_id] end app.rb
112. Checking in get '/venue/:_id/checkin' do object_id = BSON::ObjectId.from_string(params[:_id]) @venue = VENUES.find_one({ :_id => object_id }) user = USERS.find_and_modify( :query => { :_id => @suser._id}, :update => {:$inc =>{ "venues." << object_id.to_s => 1 } }, :new => 1) if ░░░░░ ░░░░░ ░░░░░ ░░░░░ ░░░░░ else ░░░░░ ░░░░░ ░░░░░ ░░░░░ end flash('Thanks for checking in') redirect '/venue/' + params[:_id] end app.rb
113. Checking in get '/venue/:_id/checkin' do object_id = BSON::ObjectId.from_string(params[:_id]) @venue = VENUES.find_one({ :_id => object_id }) user = USERS.find_and_modify(:query => { :_id => @suser._id}, :update => {:$inc => { "venues." << object_id.to_s => 1 } }, :new => 1) if user['venues'][params[:_id]] == 1 VENUES.update(░░░░░) else VENUES.update(░░░░░) end flash('Thanks for checking in') redirect '/venue/' + params[:_id] end app.rb
114. Checking in get '/venue/:_id/checkin' do object_id = BSON::ObjectId.from_string(params[:_id]) @venue = VENUES.find_one({ :_id => object_id }) user = USERS.find_and_modify(:query => { :_id => @suser._id}, :update => {:$inc => { "venues." << object_id.to_s => 1 } }, :new => 1) if user['venues'][params[:_id]] == 1 VENUES.update({ :_id => @venue['_id']}, { :$inc => { :'stats.usersCount' => 1, :'stats.checkinsCount' => 1}}) else VENUES.update({ _id: @venue['_id']}, { :$inc => { :'stats.checkinsCount' => 1}}) end flash('Thanks for checking in') redirect '/venue/' + params[:_id] end app.rb
115. You’ve been here def user_times_at if logged_in? times = 'You have checked in here ' if !@suser.venues.nil? && !@suser.venues[params[:_id]].nil? times << @suser.venues[params[:_id]].to_s else times << '0' end times << ' times' else times = 'Please <a href='/login'>login</a> to join them.' end end helpers/milieu.rb
116. Checking In %p %a.btn.btn-primary.btn-large{:href => '/venue/' + @venue['_id'].to_s + '/checkin'} Check In Here %p =@venue['stats']['usersCount'].ceil.to_s + ' users have checked in here ' + @venue['stats']['checkinsCount'].ceil.to_s + ' times' %p=user_times_at views/venue.haml
117. A Venue localhost:9393/venue/{id}
118. What we’ve learned * Model data for MongoDB * Use MongoDB tools to import data * Create records from shell & ruby * Update records * Atomic updates * Create an index * Create a geo index * Query for data by matching * GeoQueries * Pagination * Single Document Transactions * Some ruby, sinatra, haml, etc
119. Next ?
120. It’s on Github
121. Some Ideas * Create interface to add venues * Connect to foursquare * Login w/twitter * Badges or Categories * Enable searching of venues * Tips / Reviews
122. Tweet if you liked it! Questions? http://spf13.com http://github.com/spf13 @spf13

## Related articles

-   [How I gave the most viewed presentation in the history of
    OSCON](http://spf13.com/presentation/building-your-first-mongodb-app-oscon-2012/)
-   [Big Data for the rest of us at NYC Strata
    2012](http://spf13.com/post/big-data-for-the-rest-of-us-at-nyc-strata-2012/)
-   [How I gave the most viewed presentation in the history of
    OSCON](http://spf13.com/post/how-i-gave-the-most-viewed-presentation-in-the-history-of-oscon/)
-   [Optimizing MongoDB Compound
    Indexes](http://emptysquare.net/blog/optimizing-mongodb-compound-indexes/)
-   [New features in the driver for MongoDB
    2.2](http://christiankvalheim.com/post/29753345741/new-features-in-the-driver-for-mongodb-2-2)

