# The world before React
Javascript gives us access to DOM APIs. The problem is, the DOMs on user devices are like an alien planet: we have no way of knowing what browsers they're using, in what network conditions, and what OS they're working on.


## JQuery
> As a tool is quite active in directly manipulating the user interface itself.

# Backbone 
## MVC pattern.
> Divides software applications into three interconnected components.

+ Model
  + Responsible for the data and business rules of aplication.
  + **Unware** of the View and Controller, ensuring the business logic is isolated from the user interface
+ View
  + Represents the UI of the application.
  + Display data from **_Model_** and send user commands to **_Controller_**.
  + Passive, waits for **_Model_** to provide data to display. Does not handle user interaction, delegates to **_Controller_**.
+ Controller
  + Interface between **_Model_** and **_View_**

### Challenges
#### Complex interactivity and state management
+ Struggle when it comes to managing complex user interfaces with many interactive elements
+ Separation between MVC components not accurately scoped in product code.
#### Two-way data binding
+ Lead to unintended side effects if not managed carefully. 
+ The view becomes out of sync with the model.

#### Tight coupling
+ Hard to change or refactor one without affecting the others.


## MVVM pattern.
> evolution of MVC, tailored for modern UI development platforms where data binding is a prominent feature.

+ Model
  + Same as MVC

+ View
  + Declaratively binds to the **_ViewModel_**, reflecting changes via data binding mechanisms.
  
+ ViewModel
  + Bridge Model and View.
  + Exposes data and commands for the View to bind to.
  + Handles user input via command patterns.
  + Contains the presentation logic and transforms data from the **_Model_** into a format can be easily displayed by **_View_**

| Criteria             | MVC                                                                                                  | MVVM                                                                                                                       |
|----------------------|------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| Primary purpose      | Primarily for web applications, separating user interface from logic                                 | Tailored for rich UI applications, especially with two-way data binding, like desktop or SPAs.                             |
| Components           | Model: data and business logic. View: user interface. Controller: manages user input,   update View. | Model: data and business logic. View: user interface elements. ViewModel: bridge between Model and View.                   |
| Data flow            | User input is managed by the Controller, which updates the Model and then the View.                  | The View binds directly to the ViewModel. Changes in the View are automatically reflected in the ViewModel and vice versa. |
| Decoupling           | View is often tightly coupled with the Controller.                                                   | High decoupling as ViewModel doesn’t know the specific View using it.                                                      |
| User interaction     | Handled by the Controller.                                                                           | Handled through data bindings and commands in the ViewModel                                                                |
| Platform Suitability | Common in web application development                                                                | Suited for platforms supporting robust data binding                                                                        |
