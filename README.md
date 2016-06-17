#MSProject Project Task Retrieve

  This handler retrieves a single task's id based on a name and parent information.

#Parameters

[Project Id]  - The id of the project to retrieve data from.

[Name]  - Name of the task to retrieve.

[Has Parent?] - True if attempting to retrieve a top level comment.

[Parent Name]  - Name of the Parent task (If necessary).

[Parent Id]  - Id of the Parent task (If necessary).

#Results

[Task Id]  - The task id for the task that matched the inputted parameters.

#Sample Configuration

Project Id:                   db521c56-44ab-422d-9abd-29d8d359043a

Name:                         Searchable Name

Has Parent?:                  True

Parent Name:                  Top Level Task

Parent Id:                    5e4aa3ed-f55e-4c63-818f-b84bab4822a1

#Detailed Description

This handler makes a REST call to Microsoft Project Online to the Project
Server API to retrieve a task given a variety of parameters. After authenticating
against the Project Server using the inputted username and password. After the
whole list of tasks is returned, the handler starts by parsing down the list to
tasks that match the inputted name. Each task in that pared down list then makes
another REST call to search the parent information for each task to see if it 
matches the parameters. If more than one task matches all of the inputted
parameters, an error is thrown and a manual search for the task id will need
to be done. If a single task is found, the id will be returned in the handler
results. Any errors that occur during this process will be caught and re-raised
by the handler.
