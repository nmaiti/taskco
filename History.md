
0.3.6 / 2014-11-04
===================
* Store-Redis#constructor: handles no password URLs

0.3.5 / 2014-10-14
===================
* Task#save: returns error rather than id for conflicting task

0.3.4 / 2014-07-08
===================
* Worker#work: makes when.js 3.3.0 compatible
* Mocha: better error debugging
* Build: upgrades when.js to 3.3.0

0.3.3 / 2014-05-29
===================
* Company#addFactory: uses "def" namespace when name is undefined


0.3.2 / 2014-03-11
===================
* Factory: fixes rids of race conditions in quickEntry
* Tasks: adds ability to pass existing id (via options.id) to create
* Factory: adds ability to use existing client to getNextId
* Task: adds ability to use existing client to save
* Monitor: moves {find, findId, findExists} to Tasks
* Dependencies: removes "async"


0.3.1 / 2013-11-19
===================
* Dispatcher: fix promise-related bug in halt
* Readme: reflects fact that time-to-live must be greater than 2 seconds
* Examples: better shutdown example


0.3.0 / 2013-11-19
===================
* Cleans up examples directory
* Add examples/shutdown
* Add Dispatcher.tidy with call on start and "terminating" event
* Fix bug where subscriber wasn't listening at start
* Add Scripts module and load scripts into factory
* Add additional Redis commands: hasScript, loadScript, evalSHA
* Rename timeToDie timeToLive
* Add Lua script for tidying post-crash
* All shutdown commands now return promises
* Factory.shutdown: fix bad call to team.off()
* Team.shutdown: fix undeclared done function, add priority to purgatory
* Add Dispatcher functions: halt, shutdown, requeueTask and states: halted, terminated
* Change sortedPop to return all information (breaks Dispatcher)
* Add graceful shutdown and license to Readme
* Add Team.shutdown function
* Add timeToDie to Company.shutdown, Factory.shutdown and Team.shutdown
* Separate sortedAdd from priorityAdd to stay true to Redis
* Add better description to Task process
* Add Broker.shutdown and Broker.destroyChannel
* Add Company.shutdown and Factory.shutdown


0.2.11 / 2013-11-04
===================
* Replaces "transport" language with "store" for appropriateness
* Replaces "job" references with "task" for consistency
* Adds Team tests
* Adds Procedures tests


0.2.10 / 2013-11-03
===================
* Factory: throws error when adding team w/insufficient connections
* Increases defaults connections to { min : 3, max : 10 }


0.2.9 / 2013-10-26
===================
* Attaches error to task upon failure


0.2.8 / 2013-10-24
===================
* Adds "parsePoolSettings" to Broker to allow additional pool parameters


0.2.7 / 2013-10-22
===================
* Tasks.getStatus no longer relies on Task.get
* Fixes erroneous call to self in Team.heartbeat
* Factory.getNextId now relies on Factory.execute


0.2.6 / 2013-10-22
===================
* Switches Broker.acquire to not use promises: promise now handled in Factory.execute
* Switches Factory.getClient calls to Factory.execute


0.2.5 / 2013-10-21
===================
* Hot fix of incorrect client usage in Monitor


0.2.4 / 2013-10-21
===================
* Updates retry example and adds remove example
* Created Task.remove function
* Adds StoreRedis.remove function and updates comments


0.2.3 / 2013-10-21
===================
* Adds task retry and example
* Wraps Task.finalize function in order to prep for failure retries
* Bug fix in Dispatcher (ignore instead of ignoreTask)
* Adds further overloading of Factory.execute
* Moves task cleanup logic from worker to task
* Moves team autostart to Factory.addTeam (prevents race conditions)


0.2.2 / 2013-10-18
===================
* Changed Dispatcher#broadcast(id, event) to (event, id)
* Binds appropriate Dispatcher functions in-module rather than out-of-module
* Switches sortedAdd/sortedPop order in order to fix LIFO problem
* Adds race condition example (demonstrates breaking)
* Cleans up remaining noop and done calls/declarations
* Adds extensive argument polymorphism: many fxn can accept client + factory
* Eliminates calls to "run" and Factory.run (was causing binding problems)
* Binds store-redis functions to self


0.2.1 / 2013-10-18
===================
* Adds "priority" feature and updates Readme
* Fixed another "subcriber" typo in Dispatcher.constructor


0.2.0 / 2013-10-18
===================
MAJOR RENAMING: GOAL IS INTUITIVE, CONSISTENT FUNCTION NAMES
* Renamed "finish" event to "end"
* Procedure.andTeam now returns the team created
* Renames factory.client to getClient
* Renames "sub" to "subscriber" (and corresponding functions)
* Renames Dispatcher.digest to routeMessage
* Renames Dispatcher.dispatch to broadcast
* Renames Dispatcher{watch, ignore} to watchTask and ignoreTask
* Removes "done" references from Company
* Renames "localBind" to "bindLocal"
* Removes progress binding in Worker.work
* Renames "settings" variables to cxnSettings, and auth" to poolSettings


0.1.3 / 2013-10-17
===================
* Adds local vs global binding abilities


0.1.2 / 2013-10-17
===================
* Renamed complete event to success
* Fixes problem where expiration didn't work across processes
* Bug fixes in dispatcher
* Moves worker "complete" and "failure" to single "finished" event


0.1.1 / 2013-10-16
===================
* Adds task on/broadcast functionality
* Added publish to store-redis
* Added master/slave example
* Changes pubSub language to "sub" (publish clients are separate)
* Adds basic dispatch functions
* Allows for errors in store-redis.createConnection
* Adds pubSub to Broker, cleans up legacy code


0.1.0 / 2013-10-15
===================
 * Fixes auth connection string problem with store-redis
 * Refactors dispatcher and fixes memory leak in getNextTask
 * Cleans up console.log and whitespace
 * Switches Manager to Dispatcher (more appropriate name), binds delegate function
 * Initial refactoring of team/worker
 * Inserts missing variable in sequence call
 * Deleted unused functions from task/tasks
 * Better documentation for task.js
 * Refactoring of tasks
 * Utilizes pooled connections
 * Adds expiration to teams that don't check in
 * Fixes bug in Task defaults/options
 * Adds failure messages


0.0.5 / 2013-10-12
===================
* Fixes serialization in hashSet
* Fixes typos in Task.progress


0.0.4 / 2013-10-12
===================
* Adds error handling to Factory.quickEntry
* Removes required procedure for task creation
* Adds auto-serialization to StoreRedis


0.0.3 / 2013-10-12
===================
 * Adds string parsing to store-redis
 * Procedure has "andTeam" chaining
 * lacksTask now rejects with id vs error


0.0.2 / 2013-10-12
===================
 * Provides small redis url example and improves store-redis arguments
 * Improves broker auth race condition (hard to circumvent)
 * Extracts out Store layer functions (to allow different Stores)


0.0.1 / 2013-10-11
===================
 * Removes callback from Factory.reserveTaskId
 * Updates example for new form of quickEntry
 * Ensures that progress maxes out at 100
 * More extensive factory testing
 * Changes uid hash to not store type
 * Changes quickEntry to return task
 * Switches find to findExists in Factory.lacksTask
 * Fixes reference problem in Monitor.findExists
 * Adds Task.info
 * Fixed "this" vs "self" reference in Team.heartbeat
 * Fixed task with uid in Tasks.uidFunctions
 * Fixed error handling in Procedure constructor
 * Bug fixes in Monitor (incorrect findId call, missing proxy)
 * Reordered tasks in Factory to tie to reality better
 * Factory.addProcedure now actually returns procedure
 * Removed unused callback from Factory constructor
 * Enabled Company.addFactor to add settings without name
 * Renamed Factory.shortcut to Factory.quickEntry
 * Adds devDependencies for testing
 * Set up test directory structure
 * Adds complete and failure events to task
 * Consolidates complete/failure functions. Adds progress function.
 * Adds task activate and deactivate functions
 * Added metadata to task and wrapped options into it.
 * Moves Team creation to Team from Factory, adds "heartbeat" to team
 * Changes Team.process to Team.delegate
 * Small formatting fixes
 * Promisifies tasks
 * Promisifies task
 * Promisifies factory module
 * Formatting fixes
 * Adds task expiration (auto-removal)
 * Adds task completion/failure
 * Fixes some team serialization problems
 * Adds event handling to worker
 * Changes "job" to "task" (for consistency)
 * Changes "name" in manager to "type" (for consistency)
 * Adds initial support for custom events
 * Updates casing of title
 * Creates README
 * Adds TaskCo jpg
 * Begin separation of Tasks/Monitoring
 * Adds sketch diagram
 * Adds strict mode
 * irresponsibly large number of changes
 * increased formality to structure