# AirportDatabaseSearch
This program is a tkinter-based graphical user interface designed to interact with the airport.db database. The project is organized into several packages, each serving a specific role in the application.

Project Structure-

p2app.views
This package defines the tkinter-based graphical user interface (GUI) for viewing and editing information from the airport.db database. All necessary functionality for the GUI is already implemented, so no modifications are needed in this package.

p2app.engine
This package is where you'll implement the functionality to communicate with the airport.db database. The GUI interacts with this package through events, delegating database operations and receiving results.
p2app.events

Provides tools for communication between p2app.views and p2app.engine using events. The existing functionality handles event propagation and response handling, ensuring effective communication between the GUI and database engine.
project2.py

The program separates concerns by keeping the GUI unaware of the database implementation details. This design ensures modularity and allows independent development of the GUI and database engine components.

Communication Protocol-
Events serve as the communication protocol between the GUI (p2app.views) and the database engine (p2app.engine). When user actions require database operations, the GUI sends events to the engine, which then processes them and returns appropriate events containing results or status updates.


Event Handling-

Events are handled according to predefined protocols for various application and data-related tasks. The following table outlines some key events and their corresponding handling:

Situation	Event sent by p2app.views	Event(s) sent back by p2app.engine
Application-level events		
User quits the application:

Event sent by p2app.views: QuitInitiatedEvent
Event(s) sent back by p2app.engine: EndApplicationEvent
User opens a database file:

Event sent by p2app.views: OpenDatabaseEvent
Events sent back by p2app.engine:
DatabaseOpenedEvent when opened successfully
DatabaseOpenFailedEvent when opening fails with an error message
User closes the currently-open database file:

Event sent by p2app.views: CloseDatabaseEvent
Event sent back by p2app.engine: DatabaseClosedEvent
Continent-related events

User searches for continents:

Event sent by p2app.views: StartContinentSearchEvent
Event(s) sent back by p2app.engine: ContinentSearchResultEvent(s)
User loads a continent for editing:

Event sent by p2app.views: LoadContinentEvent
Event sent back by p2app.engine: ContinentLoadedEvent
User saves a new or modified continent:

Event sent by p2app.views: SaveNewContinentEvent or SaveContinentEvent
Events sent back by p2app.engine:
ContinentSavedEvent when saved successfully
SaveContinentFailedEvent with an error message when saving fails
Country-related events

User searches for countries:

Event sent by p2app.views: StartCountrySearchEvent
Event(s) sent back by p2app.engine: CountrySearchResultEvent(s)
User loads a country for editing:

Event sent by p2app.views: LoadCountryEvent
Event sent back by p2app.engine: CountryLoadedEvent
User saves a new or modified country:

Event sent by p2app.views: SaveNewCountryEvent or SaveCountryEvent
Events sent back by p2app.engine:
CountrySavedEvent when saved successfully
SaveCountryFailedEvent with an error message when saving fails
Region-related events

User searches for regions:

Event sent by p2app.views: StartRegionSearchEvent
Event(s) sent back by p2app.engine: RegionSearchResultEvent(s)
User loads a region for editing:

Event sent by p2app.views: LoadRegionEvent
Event sent back by p2app.engine: RegionLoadedEvent
User saves a new or modified region:

Event sent by p2app.views: SaveNewRegionEvent or SaveRegionEvent
Events sent back by p2app.engine:
RegionSavedEvent when saved successfully
SaveRegionFailedEvent with an error message when saving fails
