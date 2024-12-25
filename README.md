# Objective-C KVO Crash: Observer Not Removed

This repository demonstrates a common but subtle bug in Objective-C related to Key-Value Observing (KVO). The bug occurs when an observer is not removed before the observed object is deallocated, resulting in a crash.  The solution shows how to properly remove observers to prevent this issue.

## Bug
The `KVOCrashBug.m` file contains code that demonstrates the bug. A view controller observes a model object. If the view controller is deallocated before removing the observer, attempting to access the model object in the observer's method results in a crash. 

## Solution
The `KVOCrashSolution.m` file presents a corrected version of the code.  The key change is the removal of the observer in the view controller's `dealloc` method, preventing the crash.

## How to Reproduce
1. Clone this repository.
2. Open the project in Xcode.
3. Run the application.  Observe the crash in the original bug version and the fixed behavior in the solution.

## Lessons Learned
* Always remove KVO observers in the `dealloc` method of your observer class.
* Be meticulous about managing object lifetimes and their interdependencies to prevent similar memory management issues.