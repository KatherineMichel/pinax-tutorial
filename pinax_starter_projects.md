# Pinax Starter Projects

The Pinax starter project provides the Django project framework.

## Pinax Starter Project Code

The Pinax starter project code can be found in the Pinax GitHub organization account, in the individual branches of the [Pinax starter projects repo](https://github.com/pinax/pinax-starter-projects).

## Pinax Starter Project Descriptions

| Starter Project     | Description |
| ------------------- | ----------- |
| Project Zero        | The foundation for all other Pinax starter projects                              |
| Project Static      | A mocking and design tool                                                        |        
| Project Waitinglist | Includes pinax-waitinglist app to create a waitinglist website                   |  
| Project Blog        | Includes pinax-blog app to create a basic blog                                   | 
| Project Account     | Includes django-user-accounts app for user account management                    |
| Project Socialauth* | Includes social-auth-app-django for Twitter, Facebook, and Google authentication |
| Project Stripe      | Includes pinax-stripe app for payment acceptance                                 |
| Project Documents*  | Includes pinax-documents app to create a document library                        |
| Project Wiki*       | Includes pinax-wiki app to create a basic wiki                                   |
| Project Team Wiki*  | Includes pinax-wiki app and pinax-teams app to create a team wiki                |
| Project Company*    | Includes pinax-events app and pinax-news app to create a company website         | 

## Pinax Starter Project Packages and Inheritance

Pinax starter projects inherit from one another, meaning that a Pinax starter project includes the packages of a project it inherits from.

### Pinax Starter Projects, Django, and Templates

All Pinax starter projects inherit from pinax-project-zero, which includes Django 2.0 and pinax-templates app. 

|  Starter Project/App |  Django  | Templates |
| -------------------- | :------: | :-------: |
| All Starter Projects |     X    |     X     |  

### Additional Inheritance

In addition to inheriting from pinax-project-zero, all Pinax starter projects that include django-user-accounts app inherit from pinax-project-account. pinax-project-team-wiki inherits from pinax-project-wiki. pinax-project-company inherits from pinax-project-blog.

| Starter Project     |                Inherits From                |
| ------------------- | ------------------------------------------- | 
| Project Zero        | N/A                                         |
| Project Static      | Project Zero                                |        
| Project Waitinglist | Project Zero                                |  
| Project Blog        | Project Zero                                | 
| Project Account     | Project Zero                                |
| Project Socialauth* | Project Zero, Project Account               |
| Project Stripe      | Project Zero, Project Account               |
| Project Documents*  | Project Zero, Project Account               |
| Project Wiki*       | Project Zero, Project Account               |
| Project Team Wiki*  | Project Zero, Project Account, Project Wiki |
| Project Company*    | Project Zero, Project Blog                  |  

## Pinax Starter Projects and User Accounts

Several Pinax starter projects include django-user-accounts app, and one includes social-auth-app-django.

| Starter Project/App |  Django User Accounts  |  Social Auth App Django |
| ------------------- | :--------------------: | :---------------------: |
| Project Zero        |                        |                         |  
| Project Static      |                        |                         |  
| Project Waitinglist |                        |                         |  
| Project Blog        |                        |                         |  
| Project Account     |            X           |                         |  
| Project Socialauth* |            X           |            X            |  
| Project Stripe      |            X           |                         |  
| Project Documents*  |            X           |                         |  
| Project Wiki*       |            X           |                         |  
| Project Team Wiki*  |            X           |                         |  
| Project Company*    |                        |                         | 

## Pinax Starter Projects and Pinax App Functionality

All Pinax starter projects include one or more Pinax apps most relevant to the purpose of the project.

| Starter Project/App | Eventlog | Webanalytics | Waitinglist | Stripe | Blog  | Events |  News | Documents |  Wiki | Teams |
| ------------------- | :------: | :----------: | :---------: | :----: | :---: | :----: | :---: | :-------: | :---: | :---: |
| Project Zero        |          |              |             |        |       |        |       |           |       |       |  
| Project Static      |          |              |             |        |       |        |       |           |       |       |  
| Project Waitinglist |          |       X      |      X      |        |       |        |       |           |       |       |  
| Project Blog        |          |       X      |             |        |   X   |        |       |           |       |       |  
| Project Account     |     X    |       X      |             |        |       |        |       |           |       |       |  
| Project Socialauth* |     X    |       X      |             |        |       |        |       |           |       |       |  
| Project Stripe      |     X    |       X      |             |    X   |       |        |       |           |       |       |  
| Project Documents*  |     X    |       X      |             |        |       |        |       |     X     |       |       |  
| Project Wiki*       |     X    |       X      |             |        |       |        |       |           |   X   |       |  
| Project Team Wiki*  |     X    |       X      |             |        |       |        |       |           |   X   |   X   |  
| Project Company*    |          |       X      |             |        |       |    X   |   X   |           |       |       |   

## Text and Image Third Party Dependencies

Pinax relies on several third-party dependencies for text and image processing.

| Starter Project/App | Markdown | Pillow | Easy Thumbnails |
| ------------------- | :------: | :----: | :-------------: | 
| Project Zero        |          |        |                 |                      
| Project Static      |          |        |                 |                         
| Project Waitinglist |          |        |                 |   
| Project Blog        |    X     |   X    |                 | 
| Project Account     |          |        |                 |          
| Project Socialauth* |          |        |                 |   
| Project Stripe      |          |        |                 |
| Project Documents*  |          |        |                 |   
| Project Wiki*       |          |        |                 |   
| Project Team Wiki*  |          |   X    |         X       | 
| Project Company*    |    X     |   X    |                 | 

* Not included in a recent release. We can use assistance in updating these projects!
