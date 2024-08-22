# Lorcana League Project

This is a Google Scripts API project to create an easy-to-use, easy-to-access roster program for tracking players in a Disney Lorcana league.

## Disney Lorcana

*Disney Lorcana* is a new trading card game published by Ravensburger and featuring the Disney IP. While product has been hard-to-find, the Organized Play has been recieved well.

### Organized Play

Many TCGs are supported by and promoted alongside Organized Play. Local stores will host meetups where players of the TCG will come and play together. If you've ever heard of Friday Night Magic, that is the most widely supported form of Organized Play for the TCG *Magic the Gathering*. 

Organized Play comes in several forms. Most people know of the idea of a tournament, a meetup where players compete to win the most, either in a bracket, or usually with the Swiss organizing method. 

A more rare form of OP is to have a league. Players sign up, and for the duration of the league, they earn points by playing the game. Lorcana is one of these. 

### Lorcana League Rules

The Disney Lorcana league comes in the form of *seasons*, with each season consisting of three *rounds*, and each round consisting of 4 *weeks*. Each week, a registered player can come earn up to 10 points by playing matches against other league players, recieving 2 points for a win and 1 point per loss. 

Note: There are other ways to earn points, including 2 points for teaching someone how to play, 1 for wearing themed clothing, and 1 for using a themed deck. You even get a point for registering!

## Mission Statement

This project is intended to track the Lorcana League players and the points they win each week. As an additional requirement, we would like to track once a player has attended at least three weeks, as this allows the player to recieve a discount at the hosting store. Also, we must be able to output a weekly summary, as well as a season-wide ranking.

### The Data

The data we need to track includes the player's name, what day they registered, how many points they've earned each week, and whether the three week attendance threshold has not only been reached, but been migrated to their customer profile on the hosting store's point-of-sale system. We also need to track the seasons, their rounds, their weeks, and the dates there-of, keeping in mind that seasons can have an actual name. We also need to track how many points each player earned each week.

### Use Cases

#### 1. Registering a Player

*Requirements*: To register a player, all the user has to provide is the player's name. As the user types, it would be excellent to suggest names that are already registered, to help reduce user error. 

*Suggested Interface*: This functionality would have to consist of a text field and a *Register Player* button.

#### 2. Record a Player's Points 

*Requirements*: The user will need a way to record a player's points for a week. We should assume the points recording is for the current week according to the time-of-use, but allow the user to select a given week. If a player already has points, they should be allowed to both set and add to their amount, respecting the max amount of 10, which is the default number that we assume the player has earned that week. If the player needs to be registered, it should be easily doable. The player's point summary should also be shown, including the points earned this round, points earned this season, and points earned over the entirety of the player's participation. 

*Suggested Interface*: Use case 2 will require all of the functionality of use case 1, a week picker autoset to the current week, a set of value displays for points earned this round, this season, and all-time, as well as an integer-enforced text field for recording the amount of points earned this week. The text field should be autopopulated with the player's current points from the weekend, or 10 if no points have yet been earned this week. 

#### 3. Checking for Threshold Migration

*Requirements*: There should be a screen that shows the user which player's have crossed the threshold, but not yet been migrated to the store's point-of-sale system. The user should mark each player as the migration is made. 

*Suggested Interface*: A list of players, possibly indicating how many weeks they have attended, and a checkbox or button to mark the POS migration. Once the user marks the migration, the associated player should be removed from the list with a notification that the player has been migrated, or the checkbox should remain checked, or the button transitions to the word "Complete".

#### 4. Weekly Summary

*Requirements*: The user should be able to view a summary of the week, including the top 5 players, with ties broken by season points, lifetime points, then alphabetically, and their points earned, as well as some general information, including how many people attended, how many were newly registered, and the total points earned.

*Suggested Interface*: The first thing will be the week picker. This can be as simple as a selection box with a drop-down list including all weeks, with the current week auto-selected. The rest of the summary should auto-populate as soon as a week is chosen, displaying the season, the round, and the week, including the start and end dates of each. We should also display the number of attendees, the number of new registrations, and the total points earned. Finally, we should list the top 5 players this week, including their name, the date they registered, their points this week, and their points this round. The top 5 should be according to weekly score, then round score, then season score, then lifetime score, then alphabetically. 

#### 5. Round Summary

*Requirements*: The requirements for the round summary are similar to the weekly summary - describe the round, see how many people were active, how many were newly registered, the total points earned, and then list the top 10 players, round > season > lifetime > alphabetical.   

*Suggested Interface*: The round picker will be similar to the week picker, but populated with the rounds, the current round being auto-selected and the rest of the page reflecting the chosen round. We should describe the round by its season, start date, and end date. The display the number of active players, the number of new registrations, and the total points earned. Finally, list the top 10 players as organized in the requirements section, displaying their name, the date they registered, their points for each week, the points earned this round, and the points earned while they've been participating. 

#### 6. Season Summary

*Requirements*: Similar to the other summaries, the season summary should describe the season, show how many people were active, how many new registers, total points earned, then list the top 10 players, including the players name, the points the player earned each round, the points the player earned this season, and their rank in the league. 

*Suggested Interface*: A season picker, as expected, should be easy at this point. The season should be described by the season number, the season name, its start date, and its end date. Include how many participants, how many new participants, and how many points earned this season. List the top 10 players in the season, with their name, their date registered, thier season points, their lifetime points, and their ranking. Their should also be a text field and a button to start a new season.

#### 7. League Summary

*Requirements*: The league summary is a little different. We do not need to have a picker, but we do want to list the start date, the number of weeks we've had, the amount of players, the total points earned, the number of players who are past the threshold, the percentage of players past the threshold, the average points earned by players, 

*Suggested Interface*: There is no picker, just a display of all the stats mentioned above and a list of the top 10 players according to attendance.