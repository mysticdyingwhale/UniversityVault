# Structure

An important thing missing from the docs right now is a coherent and functional structure.

When going through it for the first time you can just follow down the pages, there's a lot of back and forth involved which confuses and causes people to miss important info.


Documentation outline


1. What is corelink cpp client?

2. How do you install corelink client?
	2.1 Install dependencies
	2.2 Clone Corelink from gitlab
	2.3 Optionally compile corelink

3. How do you use corelink
	3.1 Route 1: Include corelink directly in your project as source code.
		Describe steps on how to point your project/ compiler to corelink include and src directories
	3.2 Route 2: Include corelink as a dynamically linked library.
		Describe steps on how to compile corelink. In this case, corelink becomes a third-party dependency for your project.

	Ensure that all the paths to bin/ lib/ are available at runtime -> add bin/ lib/ paths to %PATH% var or $PATH

4. Describe steps on how to include third-party dependency directories (include, bin, lib).

5. Links to examples


Non-blocking functions for babies

foo() -> non-blocking means that you will not receive something immediately but after the operation is done. 

To capture the results of that operation you will need to specify a function for the library to call you which is called a **hook**. And your function is called a **callback** function.

