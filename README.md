# Pomodoro-Timer-A-Google-Chrome-Extension
This code is a Google Chrome extension script for a Pomodoro timer, providing features like starting, stopping, and resetting the timer through context menus. This script provides a functional Pomodoro timer using Chrome extension APIs, allowing users to control the timer through the browser's context menu and receive visual and notification feedback. Here is a breakdown of the code's functionality:
Global Variables:
seconds: Initializes the timer to 25 minutes (1500 seconds).
timerIsRunning: To track whether the timer is currently running.
Alarm Listener:
chrome.alarms.onAlarm.addListener((alarm) => {...}): This listens for alarm events. If the timer is running (timerIsRunning is true), it decrements the seconds counter.
Updates the badge text to show the remaining minutes (minBaki).
If seconds reaches 0, it stops the alarm, sends a notification, and resets the context menu title to "Start Timer".
Functions:
createAlarm(name): Creates a new alarm named name that triggers every second (1/60 minutes).
createNotification(message): Creates a notification with a given message, showing an icon and a title "Pomodoro Timer".
clearAlarm(name): Clears the alarm named name.
Context Menu Creation: 
Two context menu items are created:
start-timer: Starts or stops the timer.
reset-timer: Resets the timer.
Context Menu Click Listener:
chrome.contextMenus.onClicked.addListener(function(info, tab) {...}): Handles clicks on context menu items.
"reset-timer": Resets the timer to 0, updates the badge text to "R", sets the badge background color to green, sends a reset notification, and updates the menu item title to "Start Timer". Sets timerIsRunning to false.
"start-timer": If the timer is running, stops it, updates the badge text to "S", sets the badge background color to yellow, sends a stop notification, and updates the menu item title to "Start Timer". If the timer is not running, starts it, updates the badge background color to orange, sends a start notification, creates an alarm, and updates the menu item title to "Stop Timer".
Badge Background Color Initialization:
chrome.action.setBadgeBackgroundColor({ color: "orange" }, () => {...}): Sets the initial badge background color to orange.
Code Flow: 
Initialization: The badge background color is set to orange. Context menu items are created for starting and resetting the timer.
Starting the Timer: When the "Start Timer" menu item is clicked, the timer starts or stops based on its current state.
Running Timer: Every second, the alarm listener decrements the timer, updates the badge text, and checks if the time has elapsed.
Resetting the Timer: When the "Reset Timer" menu item is clicked, the timer resets, updates the badge text and color, and sends a reset notification.
