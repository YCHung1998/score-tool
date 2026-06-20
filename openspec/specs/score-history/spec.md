## Purpose

Defines requirements for persisting session data, exporting and importing records, and resetting the application state.

## Requirements

### Requirement: Persist data across sessions
The system SHALL automatically save all roster, group, and match score data to localStorage so it survives page reloads without any user action.

#### Scenario: Data survives reload
- **WHEN** the user closes and reopens the app in the same browser
- **THEN** all players, groups, and match scores are restored to their previous state

### Requirement: Export records as text file
The system SHALL allow the user to download all current session data as a human-readable `.txt` file.

#### Scenario: Export produces txt file
- **WHEN** the user taps the export button
- **THEN** the browser downloads a `.txt` file containing all players, groups, match scores, and final rankings

#### Scenario: Exported file is human-readable
- **WHEN** the txt file is opened in any text editor
- **THEN** the content is structured and legible without requiring special software

### Requirement: Import records from text file
The system SHALL allow the user to upload a previously exported `.txt` file to restore a past session's data.

#### Scenario: Import restores session
- **WHEN** the user selects a valid exported txt file for import
- **THEN** the roster, groups, and match scores from the file are loaded into the app

#### Scenario: Invalid file rejected
- **WHEN** the user selects a file that is not a valid exported txt format
- **THEN** the system SHALL display an error and leave current data unchanged

### Requirement: Clear all records
The system SHALL allow the user to clear all match scores, roster, and group data, resetting the app to an empty state.

#### Scenario: Clear with confirmation
- **WHEN** the user initiates a clear action
- **THEN** the system SHALL display a confirmation prompt before deleting any data

#### Scenario: Data deleted after confirmation
- **WHEN** the user confirms the clear action
- **THEN** all players, groups, match scores, and history are removed from localStorage and the UI resets
