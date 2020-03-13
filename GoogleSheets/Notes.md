* **number of create restriction** : I was automating sheet creation and updation to it and trial and error exceeded the number of create sheet you can call. 3200/day is the limit. I had around 1600 odd sheets to create and 2 attemps exhausted the number of creation.
  * solution was nothing more than rigorous testing through small data and at least once had to wait for a day.
  
* **time for macro run**: it is at max of 5 minutes. I had to parallelize the execution to reduce the time. The list, I was iterating, was broken to pieces. Those pieces were run in parallel through triggers.

