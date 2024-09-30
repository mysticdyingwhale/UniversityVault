# Structure

An important thing missing from the docs right now is a coherent and functional structure.

When going through it for the first time you can just follow down the pages, there's a lot of back and forth involved which confuses and causes people to miss important info.

Having separate sites for documentation seems unnecessary too. 

I understand the current cpp docs use Doxygen..

I think it makes sense to leave advanced setup/API documentation to the Doxygen site and moving the basic setup stuff to the new one.

A better, more standard structure that makes sense is:


- Getting Started
	- Client Installation
		- Prerequisites
		- Installing Corelink Client
		- Dependencies
		- Installing Dependencies (**NOT EXHAUSTIVE**)
	- Building Corelink (**NOT EXHAUSTIVE**)
		- Path Specifications
		- CMake Toolchain
	- Setup Examples (**NOT EXHAUSTIVE**)
		- CMake (mention again)
		- Visual Studio
		- XCode
		- Using Corelink 
	- Usage Example & Breakdown
		- Echo Client
		- Feature Breakdown
		- Understanding `async`
	- Unreal Engine Setup
	- Whatever else we need
	


This would be the Doxygen docs:

- API
	- Namespaces
		- Namespace List
		- Namespace Members
	- Classes
		- Class List
		- Class Hierarchy
		- Class Members
	- Files
		- File List
		- File Members
- Whatever else we need


- Architecture
	- Do we really need this to be first page? 
	- Half of it feels less like documentation and more like a blog post or article detailing the changes made to the client with the new version 


When I think about a NEW USER, someone who may not have much experience with C++ or setting up APIs or whatever it may be, their priority is to just get the thing running and understand how it works/how to use it. 

That should be what the first part of the docs focuses on. 

Think about WHO uses Corelink rather than the different POTENTIAL use cases for Corelink, and structure the docs for the majority use cases, while leaving the more advanced information accessible to those who need it. 


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

