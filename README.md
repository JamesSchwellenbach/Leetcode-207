# Leetcode 207. Course Schedule (Medium)

# Problem

There are a total of numCourses courses you have to take, labeled from 0 to numCourses - 1. You are given an array prerequisites where prerequisites[i] = [ai, bi] indicates that you must take course bi first if you want to take course ai.

For example, the pair [0, 1], indicates that to take course 0 you have to first take course 1.
Return true if you can finish all courses. Otherwise, return false.

# Solution O(m + n) : n = numCourses, m = len(prerequisites) 

Create two lists of empty sets of size numCourses, one of these lists contains all the prereqs of class i, and the other has all the classes that class i is a prereq. also create a dict of all the classesLeftToTake, this is initially set to all ints, 0 to numCourses - 1. then create a queue of all classes that dont have any prereqs, these are all courses able to be taken, remove them from classesLeftToTake. Then loop while the queue still has indexes, pop off the next index and remove it as a prereq from all courses that have it as a prereq. If this reduces any of those courses to have 0 prereqs, then append it to the queue and remove it from classesLeftToTake. if classesLeftToTake is empty return True (you are able to take all the courses). If queue is empty, but there are still classesLeftToTake, then you are unable to take all courses, return False
