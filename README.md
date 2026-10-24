# CS-360 Mobile Architecture and Programming

## Project Artifact

[Download the completed inventory app project](AliLaghariInventoryAppM7.zip)

This ZIP contains the Android Studio project, including the finalized UI and Java code developed for Project Three.

## App Requirements and User Needs

I developed an inventory app to help warehouse workers track items and maintain accurate stock quantities. The requirements included account creation and login, a persistent SQLite database, an inventory grid, adding and removing items, updating quantities, and optional SMS alerts when an item's quantity drops to zero. The app addresses the need to find inventory quickly, record stock changes, and identify items that need replenishment.

## Screens and User Centered Design

The app includes a login and account creation screen, an inventory screen, an add and edit item form, and an SMS notification settings screen. The inventory grid displays item names, SKUs, quantities, and actions. Search and quantity controls help users complete common tasks with fewer steps.

I used consistent colors, readable labels, input hints, and feedback messages to make the interface understandable. An out-of-stock text label communicates status alongside color, and a confirmation dialog helps prevent accidental deletion. Users can decline SMS permission and continue managing inventory. These choices supported the main tasks during emulator testing, although feedback from warehouse users would be needed to assess usability more fully.

## Coding Approach and Strategies

I developed the app incrementally, connecting the interface to database operations and testing features as I added them. I separated database access into DatabaseHelper and organized login, inventory, item entry, and notification settings into separate activities. SmsNotifier handles outgoing stock alerts.

I used descriptive names, comments, parameterized database queries, input validation, and background executors for database work and password hashing. These techniques made problems easier to isolate and kept the code organized. I can apply the same approach to future projects by dividing requirements into smaller features and checking each feature before combining it with others.

## Testing and Results

I tested the app using the Android Emulator. Testing covered account creation, successful and unsuccessful login attempts, adding and displaying inventory, editing items, increasing and decreasing quantities, deleting items, and retaining data after reopening the app. I also tested permission denial and confirmed that inventory updates continued when SMS alerts were disabled.

For the alert workflow, I reduced an item's quantity from one to zero and observed the generated outgoing stock message in the emulator's Messages app. This did not establish delivery through a real mobile carrier. Testing revealed a problem with relying only on the emulator's messaging feature declaration, which led me to investigate its SMS capability checks. Testing was important because working code also needed to produce the expected behavior under different user choices and device conditions.

## Innovation and Challenges

One challenge was determining why the app reported SMS as unavailable even though the emulator could receive a simulated message. I used diagnostic commands to inspect the emulator's reported features and SMS service. I then added a device capability fallback while retaining permission checks and error handling.

This experience taught me to investigate the cause of a failure instead of assuming that a successful build means every feature works. I also kept SMS failures separate from database updates so a messaging issue would not undo a saved inventory change.

## Component That Best Demonstrates My Skills

The SQLite inventory component best demonstrates my skills because it connects stored data to the interface through create, read, update, and delete operations. It also validates quantities, rejects duplicate SKUs, refreshes the grid after changes, and preserves data between sessions.

The login component strengthened this work by storing salted password hashes instead of plain-text passwords. Together, these components demonstrate how I translated requirements into a working application while considering data integrity, code organization, and user needs.
