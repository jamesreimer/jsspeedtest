Simple JavaScript Speed Test Class
==================================

While `console.time()` can be used to determine the speed of an operation, it has two inherent problems...

1. It lacks the ability to perform a truly accurate test, in that the results will vary each time the code is run.

2. The execution of `console.time()` itself can greatly add to the overall execution time.

This class provides a more efficient alternative, as well as providing a more accurate result by returning an average execution time based on a given number of repetitions.
