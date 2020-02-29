# Array-Unique-Element-Count-Extension

In Solution 1, a tuple is used as a tool to inspect each element present in the array and compare it to the one prior to that. 

The first step in the process is creating a "sorted" version of the array by using the sorted(by: ) method present in Swift:

let sorted = self.sorted(by: <)

The sorted(by: ) method organizes the once shuffled array in ascending order as specificied by the "<" symbol in the method's predicate. 

Next, the "start" tuple is initialized with ".none" and "0" values:

let start: (Element?, Int) = (.none, 0)

These values are passed as the initial values to the reduce() method that is being called on the sorted version of the array.

The reduce() method combines the elements in the un-sorted and the sorted array and returns a new array with only unique values in it by returning a new tuple (currentElement) at each iteration and comparing it to the previous (previousResult) one:

let result = sorted.reduce(start){
    (previousResult, currentElement) in 
                 ... 

The variable "uniqueCount" is increased by one (+= 1) during each cycle if the current element is different (!=) than the previous one:

let result = sorted.reduce(start){
    (previousResult, currentElement) in 
    var uniqueCount = previousResult.1
    if(previousResult.0 != currentElent){
    uniqueCount += 1
    }
                 ...
    
Lastly, the method returns the new array that only contains unique values (currentElement) as well as the final count of the unique values (uniqueCount):

let result = sorted.reduce(start){
    (previousResult, currentElement) in 
    var uniqueCount = previousResult.1
    if(previousResult.0 != currentElent){
    uniqueCount += 1
    }
    return((currentElement, uniqueCount))
    }
