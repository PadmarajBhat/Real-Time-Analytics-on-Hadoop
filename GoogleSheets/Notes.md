* **number of create restriction** : I was automating sheet creation and updation to it and trial and error exceeded the number of create sheet you can call. 3200/day is the limit. I had around 1600 odd sheets to create and 2 attemps exhausted the number of creation.
  * solution was nothing more than rigorous testing through small data and at least once had to wait for a day.
  
* **time for macro run**: it is at max of 5 minutes. I had to parallelize the execution to reduce the time. The list, I was iterating, was broken to pieces. Those pieces were run in parallel through triggers.

* **segregation of tasks**: my one operation was to delete the old sheet, create the new one, fetch from db the latest value and move it to different folder because the spreadsheet by default creates in root directory. I split this one activity for an item to 5 different macros (only deletion macro (2 mins) , creating spread sheet (2 mins), copying to different volumn(~3 min) and deleting from root directory(~3 min). But these had to be scheduled/synced so that operations perform correctly. i.e. first delete macro has to trigger and then only create...so on
 * there is an issue too here: the results are segregated in different output and hence it has to be considered as one file or loaded on to memory.

* quick look at limitation : https://developers.google.com/apps-script/guides/services/quotas#current_limitations
  * source of big data problem :P

* **concurrency issue** : parallelism leads to race condition for resources and thus may slowdown couple based on availabity. I have split my triggers in different time.


* **async can help ?** : https://futurestud.io/tutorials/node-js-how-to-run-an-asynchronous-function-in-array-map
