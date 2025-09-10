# Component 4: System Design Using UML Diagrams

This section presents the UML diagrams for the University Navigation App. Each diagram was selected to address different aspects of the system and together they accurately represent the functional requirements. Explanations are provided for each diagram.

---

## 1. Use Case Diagram

**Purpose**  
The use case diagram illustrates the external actors that interact with the system and the main functionalities they perform.

**Actors**  
- Student/Visitor – selects destinations and listens to directions.  
- Admin – uploads and manages route data.  

**Use Cases**  
- Select Destination  
- View Text Directions  
- Hear Voice Directions  
- Control Playback (Pause, Repeat, Stop)  
- Manage Routes (Admin only)  

**Notes**  
The use case diagram shows that students and visitors are the primary users of the system, while administrators are responsible for updating or managing the route database.

---

## 2. Activity Diagram (Get Directions)

**Purpose**  
The activity diagram shows the flow of actions when a user requests directions.

**Steps**  
1. The app opens and the main menu is displayed.  
2. The user selects a destination.  
3. The system checks if a route exists.  
4. If the route exists, the system loads the route, displays the steps, and initiates text-to-speech playback.  
5. If no route is found, the system shows an error message.  

**Notes**  
This diagram highlights the decision point (whether a route exists or not) and shows how the app supports user playback controls such as repeat or stop.

---

## 3. Class Diagram

**Purpose**  
The class diagram defines the static structure of the system, including its main classes, their attributes, methods, and relationships.

**Classes**  
- App: entry point of the system.  
- UI: handles the menu, destination selection, and displaying steps.  
- RouteManager: retrieves and calculates routes.  
- TTSService: converts text to speech.  
- Storage: loads and saves route data.  
- Route: represents a complete route.  
- Step: represents a single navigation instruction.  

**Relationships**  
- The App class uses UI, RouteManager, and TTSService.  
- RouteManager interacts with Storage and returns Route objects.  
- A Route is composed of one or more Steps.  

**Notes**  
This diagram focuses on the essential elements required to meet the system’s purpose. Optional classes such as Admin or Logger are excluded from the simplified version.

---

## 4. Sequence Diagram (Request Directions)

**Purpose**  
The sequence diagram shows how objects interact over time when a student selects a destination.

**Main Flow**  
1. The student selects a destination through the user interface.  
2. The user interface requests the route from the RouteManager.  
3. The RouteManager retrieves the route data from Storage.  
4. The route is returned to the user interface.  
5. The user interface passes the route steps to the TTSService.  
6. The TTSService outputs voice directions to the user.  

**Alternate Flow**  
If no route is found, the user interface displays an error message instead of proceeding to voice output.

---



**Notes**  
This diagram demonstrates that the application is fully contained on the student’s device, supporting offline functionality. Administrative updates are handled through occasional file imports, so no server is required in this version.

---

## Conclusion

The four UML diagrams presented (use case, activity, class, sequence) provide a complete and accurate design of the University Navigation App. Each diagram highlights a different perspective of the system, and together they address the functional requirements identified earlier in the assignment.
