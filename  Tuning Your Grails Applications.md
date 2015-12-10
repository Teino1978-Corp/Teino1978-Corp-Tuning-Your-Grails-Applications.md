# Tuning Your Grails Applications

## Profiling

### Server-side tools
- Spring Insight
- Profiler Plugin
- Hibernate logging
- P6Spy
- Hibernate Statistics
  - App Info & Hibernate Stats Plugins

### UI tools
- Chrome/Safari/IE developer tools
- Firebug (Firefox only)
- Opera Dragonfly (opera only)
- Google Speed Tracer (chrome only)
	- Spring Insight integration
- ySlow (Firefox only - requires Firebug)
- PageSpeed (Chrome & Firefox)

## Tuning

### Database performance
- Reduce the number of queries
	- Use appropriate fetch mode
	- Don't fetch data you don't need
- Tune your queries
	- Add appropriate indexes
	- Don't be afraid to change the model
- Beware large `hasMany` collections
	- Sets and lists always loaded when adding item
	- Bag implementation coming in Grails 2
	- Or use linking domain class (vis Spring Security Core plugin)
- Caching
	- Hibernate 2nd-level cache
	- Distributed cache/data grid
		- Terracotta
		- GemFire
- Alternative data store!

### Business login
- Caching
	- Spring Cache Plugin for service methods
- Go asynchronous
	- Ideal for long running tasks
	- Spring Events, Executor
	- Messaging: JMS, AMQP
- Fall back to Java
	- Limited applicability
	- Numerically intensive tasks?
- Groovy++?
	- One JAR
	- @Typed on class or method

### Network and UI
- Reduce view processing
	- Spring Cache plugin for views
- Reduce number of requests (latency)
	- Expires HTTP header
	- Bundle CSS & Javascript files
	- Image spriting
- Reduce amount of data transferred to browser (bandwidth)
	- Minify Javascript
	- Compress data
- Plugins
	- Performance UI, JAWR
	- Resources et al.

### Compressing page content
- Container-dependent
	- Tomcat has connector setting
	- For Jetty, add GzipFilter to your web.xml

### Resources plugin
- Modularise static content
- Bundle files of the same type
- Caching Resources plugin
	- Sets HTTP Expires header 1 year ahead
	- Gives static files a unique name
- Zipped Resources plugin
	- Gzips static content
	- Can exclude files by extension

### Rich UIs
- Browser does the work
- Minimal traffic
- GWT, Flex, etx.
- Data transfer
	- JSON
	- XML
	- GWT-RPC

## Summary
- Profile before you optimise!
- Several tools available for profiling
- Several plugins available for improving performance
- Many techniques apply to any web application
- Law of diminishing returns
	- At some point, further performance improvements aren't worth the required effort
- Resources will be in Grails 2.0

## Resources
- Spring Insight
	- http://www.springsource.com/developer/tcserver
- Grails Plugins
	- http://grails.org/plugin/profiler
	- http://grails.org/plugin/springcache
	- http://grails.org/plugin/resources