Time-Tracker
============

An iOS app with time tracking

###Step 1: Create the list view controller
- Either in Pomodoro or in a new app create a new list view controller
- Add it to the tab, or to the window's rootViewController inside of a navigation controller

###Step 2: Setting up a tableViewDatasource
- Create a new datasource object (ListTableViewDatasource subclass of NSObject)
- Add the tableViewDatasource protocol required methods (cellForRow, and numberOfRows)
- Add a datasource property to your list viewcontroller (strong)
- Initialize the datasource in the init method
- Add a tableview property to list viewcontroller
- Initialize the tableview and add it to the viewcontroller's view
- Set the datasource to your datasource property

###Step 3: Create a model and model controller
- See "Entries" for a sample project
- Create a Project class with necessary properties
- Create an Entry class with necessary properties
- Create a ProjectController singleton class (add the instanceType method)
  - The project controller should hold an array of Projects
  - You'll need an "AddProject" and "RemoveProject" method
  - Each project should hold an array of Entries
  - You'll need an "AddEntry" and "RemoveEntry" method
  - You'll need methods that convert the objects to and from dictionaries
    - (This allows you to store the model in NSUserDefaults)
- Now you can use the ProjectController for the row count and row value for the tableView
  - Use the project title for the cell label

###Step 4: Add a detail view controller
- Create a detail view controller with an XIB file
- Add a textField for the title
- Add a label to show the total time
- Add a tableview to show the list of entries
- Add a toolbar for an Add, Check In, Check Out, and Report button
- Add those objects as properties on the view
  - Wire them up
- Add a method for each button
  - Add
  - Clock In
  - Clock Out
  - Report

###Step 5: Add a datasource for the tableview
- Create a new datasource object (DetailTableViewDatasource subclass of NSObject)
- Add the tableViewDatasource protocol required methods  (cellForRow, and numberOfRows)
- Add a datasource property to your detail viewcontroller (strong)
- Initialize the datasource in the init method
- Add a tableview property to detail viewcontroller and wire it up
- Set the datasource to your datasource property

###Step 6: Return entries
- Add a public Project property to the detail view controller
- In the didSelectRow method in the ListViewController set the DetailViewController's Project property as the project in the ProjectController's project list at the index selected
- Add a public Project property to the detailTableViewDatasource
- In the viewDidLoad method of the detailViewController set the datasource's project property to self.property
- NumberOfRows should be equal to number of entries
- Set the cell's textLabel.text to the entry's start and end date
  - Feel free to format them if you'd like it to look pretty 
  - http://gtiapps.com/?p=1086

###Step 6: Add a Clock In method to the Project object
- Add a method "startNewEntry"
  - In that method create a new entry, and set the start time to now
  - Store that entry as a "currentEntry" property
- Add a method "endCurrentEntry"
  - In that method set the end time of "currentEntry to now
- Call those methods when the user selects clockIn or clockOut
  - Be sure to reload the tableview's data



