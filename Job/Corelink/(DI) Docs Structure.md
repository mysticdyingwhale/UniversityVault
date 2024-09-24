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
