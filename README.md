# Tyler-CSI-2300-Course-Project
1. Your project name, Tyler Birmingham
2. I am trying to build a To Do  Task Scheduling App That has a Very Simplistic View To not Overwhelm Users, I want to Build it Because I have problems with Other apps Where you have to pay for a month view and Have a view of soon to do Tasks. It will be Useful To Schedule Asignments, Mettings, etc It will allow you to see soon ToDo events at a Glance
3.
![image](https://github.com/user-attachments/assets/b98f8520-6a28-460f-958c-5043f1e9aae5).

4. Plan and estimate of effortCoding, Devloping, Impleting etc 100% effort By Me.
 
5.) updated uml diagram 
    classDiagram
    class ToDoApp {
        +void start(Stage)
        +static void main(String[])
    }
    
    class Application {
        +void start(Stage)
        +static void launch(String[])
    }
    
    class CalendarView {
        -BorderPane root
        -GridPane monthGrid
        -YearMonth currentMonth
        -Label monthLabel
        -EventManager eventManager
        -boolean showingThreeDayView
        -Button hamburgerButton
        -Stage primaryStage
        +CalendarView()
        +void showMonthView()
        -void updateMonthView()
        +void start(Stage)
    }
    
    class ThreeDayView {
        -EventManager eventManager
        -Stage primaryStage
        -Runnable backToMonthView
        -VBox root
        +ThreeDayView(EventManager, Stage, Runnable)
        +VBox createContent()
    }
    
    class EventManager {
        -List~Event~ events
        +void addEvent(Event)
        +void removeEvent(Event)
        +List~Event~ getEvents(LocalDate)
        +void editEvent(Event)
    }
    
    class Event {
        -String title
        -LocalTime time
        -LocalDate date
        -String description
        -LocalDateTime reminder
        +String getTitle()
        +LocalTime getTime()
        +LocalDate getDate()
        +String getDescription()
        +LocalDateTime getReminder()
        +String title()
        +Event(String, LocalDate, LocalTime, String)
    }
    
    class FormGUI {
        +static void show(LocalDate, List~Event~, Stage)
        +static void showAddTaskForm(EventManager, Stage, Runnable)
        -static void showAlert(String)
    }
    
    ToDoApp --|> Application : extends
    ToDoApp --> CalendarView : creates
    CalendarView *--> EventManager : creates and owns
    CalendarView --> ThreeDayView : creates
    CalendarView --> FormGUI : calls
    ThreeDayView --> EventManager : uses
    ThreeDayView --> FormGUI : calls
    FormGUI --> EventManager : uses
    EventManager o--> "0..*" Event : manages
    FormGUI ..> Event : creates
