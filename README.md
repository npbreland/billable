# billable: Billable Hours Tracker

**NOTE:** I built this with like 80% vibe coding and there are no tests. There is some input validation, but please don't use this in a client production environment.


A lightweight Linux command-line tool for tracking billable hours across multiple clients. Built in Python with SQLite for persistent storage.

## Key Features

- **Client Management**: Add and list clients
- **Billing Periods**: Start and end distinct billing periods for each client
- **Interactive Timer**: Real-time timer interface with live seconds ticking when active
- **Pause/Resume**: Toggle timer on/off with a single ENTER key press during work sessions
- **Time Reporting**: View accumulated hours (displayed as HH:MM:SS) for all clients and periods

## Core Workflow

1. Add a client: `billable add "Client Name"`
2. Start a billing period: `billable start "Client Name"`
3. Open interactive timer: `billable session "Client Name"`
   - Press ENTER to start/pause
   - Timer updates every second when running
   - Press CTRL+D to exit (auto-pauses if running)
4. End billing period: `billable end "Client Name"`
5. View totals: `billable list`
6. Adjust active period time with `billable adjust <client> [--add]|[--subtract] <HH:MM>`

## Technical Details

- **Storage**: SQLite database (`~/.billable_hours.db`)
- **Data Model**: Clients → Periods 
- **UI**: Terminal-based with ANSI escape codes for screen clearing and updates
- **Input Handling**: Non-blocking I/O for real-time display updates while monitoring for user input

## Design Philosophy

Quick and frictionless - designed to minimize interruption to your workflow. The interactive timer lets you stay in one view and toggle with a single keystroke, with visual feedback showing exactly how much time you've logged.
