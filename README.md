# Analysis of Anki Review Statistics Using Power BI 
This project is designed to show various statistics and data based on the flashcard reviewing application, Anki.
The project consists of a dashboard produced in Power BI which visualises review data, displaying review key statistics such as a detailed
breakdown of the number of reviews, card retention rates, card maturity and review intervals, time spent reviewing material in the
application and a forecast of future material yet to be reviewed.
The aim of this project was to explore review trends and insights for the purpose of self improvement when using the application, as well as to further my skills in
data analysis and DAX.

## About Anki
Anki is an open source flashcard programme that allows the user to create, share and review flashcards. The application also schedules
when to display cards to the user in a optimal way so as to minimise the chance that the user forgets the content of the card. The flash
card app allows the user to grade the difficulty of the card (Again, Hard, Good, Easy) which affects when the card is next shown to the user.
The user can also set a number of new, unseen cards to add to their daily reviews.

### Anki Queues
Cards are divided into three queues. The "New" Queue contains unseen cards, the number of which is set by the user. The "Due" Queue contains
previously seen cards that need to be reviewed. Finally the "Learning" Queue contains cards that Anki thinks the user doesn't know, which
includes cards that the user pressed "Again" whilst reviewing (known as a lapse) and cards from the "New" queue that have not yet graduated
into the Review Queue. The functionality of these queues and the requirements for new and lapsed cards to graduate from the Learning Queue
can be set by the user

### Card Maturity
If the user passes the card (i.e. rates the card as anything but Again), the interval between when the card gets scheduled for review grows.
If the card's interval reaches 21 days or greater, the card is referred to as "Mature". Otherwise, the card is referred to as "Young".

For more information on how Anki schedules reviews, please see the Anki Manual [1].

## Project Overview
The data visualised here consists of data obtained from my personal usage of Anki from January 2025 to July 2025. The deck is a modified
version of the publicly available "JLPT-N5-N1 Japanese Vocabulary" deck available here [2]. In summary, the cards in this deck have a
Japanese word or phrase on one side and an English definition on the back. The goal is to try to recall the English definition when given the
Japanese word. All data on cards and reviews is kept in an SQL databse which was exported for the purpose of this project. The Power BI
dashboard is split into 4 sections in order to efficiently visualise the data.

### Daily Overview
The first page shows an overview of general statistics regarding reviews. A heatmap shows the number of reviews per day. Clicking on days and 
weeks on the heatmap will show the user daily and weekly statistics. The number of reviews is split up into reviews for learning/new cards,
young cards and mature cards. Also a count of the Due cards that were passed or flunked is provided as well as the Retention Rate and
True Retention Rate of the cards in order to give insight on my Japanese learning progress. Two pie charts both show the number of each
type of review I have done and the rating given to said reviews (including new cards).

### Review Count / Time
The second page shows four graphs showing the number of reviews and time spent on each review per day and per month. The columns are split by type of card type of card reviewed. This shows how time spent on reviews, total reviews and the type of reviews changes with time in order to gauge progress.

### Again Rate / True Retention
The third page shows graphs pertaining to the rate at which I pressed Again on cards whilst reviewing and True Retention, the Again Rate of cards in the Due Queue. The first graph shows again rate and true retention on reviews per month. The second section contains three graphs showing a count for good and again presses for learning, young and mature cards. Note that the bar chart for learning cards also includes initial answers for cards in the New Queue. Percentage pass rates are also provided for each group. Finally the graph at the bottom shows again rate and true retention for each day spent reviewing. These graphs allow the user to check how my retention changes with time and how my pass/fail rate splits across different types of cards and shows that retention gets higher as cards mature.

### Forecast
The fourth page shows various metrics forecasting reviews in the future. The first graph shows the forecasted number of mature and young cards to be reviewed each day for the next 30 days assuming now new cards are added. The second graph is a histogram of the ratio of the new interval / old review for each review. Numbers greater than 1 indicate reviews where the interval increase (due to a pass), whilst numbers less than 1 represent reviews where the interval decreased after review (due to a lapse). The graph at the bottom shows the current intervals of every card currently to be reviewed. This data gives insight into when future reviews could take place as well as overall performance (high intervals = many successive passes of the card).

## How the Data was Obtained
Data is from my personal Anki usage. To obtain this data, I first exported the data as a .apkg in Anki's PC application. The file can be treated as a zip file which contains an SQL databse. Using software such as DB Browser for SQLite [3], one can view the data in the databse and export to various .csv files which can then be imported by Power BI. If you are an Anki user, feel free to clone this reprository or download the Power BI file and import your own exported data. (Please note, Anki allows users to change when a new day rolls over in Preferences. Please make sure that the day rolls over at the correct hour by checking the Config table in the model. By default, new days start at 4.00am).

If you need help with the Anki's database structure, a detailed breakdown of the columns can be found here [4].

##

## Glossary
A glossary of key terms for this report

Review: The act of grading a card with one of four options "Again", "Hard", "Good", "Easy".

Lapse / Flunked Review: The act of answering "Again" to a review card.

Interval: The amount of time between an initial and future review (in days for due cards, seconds for learning cards and new cards).

Queue: The group that cards are placed in. "New" for unseen cards, "Due" for review cards, "Learning" for unseen but not yet learnt cards and lapsed review cards.

Young Card: A review card with an interval less than 21 days.

Mature Card: A review card with an interval of 21 days or more.

Learning Review: Any review of a card that has not yet graduated graduated to the Due Queue.

Relearning Review: A review of a previously lapsed card.

Cram Review: A review that takes places outside the normal schedule.

## Citations
[1] https://docs.ankiweb.net/

[2] https://ankiweb.net/shared/info/1550984460

[3] https://sqlitebrowser.org/

[4] https://github.com/ankidroid/Anki-Android/wiki/Database-Structure
