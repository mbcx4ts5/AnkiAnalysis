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
The page shows an overview of general statistics regarding reviews. A heatmap shows the number of reviews per day. Clicking on days and 
weeks on the heatmap will show the user daily and weekly statistics. The number of reviews is split up into reviews for learning/new cards,
young cards and mature cards. Also a count of the Due cards that were passed or flunked is provided as well as the Retention Rate and
True Retention Rate of the cards in order to give insight on my Japanese learning progress. Two pie charts both show the number of each
type of review I have done and the rating given to said reviews (including new cards).

### Review Count / Time
The page shows four graphs showing the number of reviews and time spent on each review per day and per month.

### Retention / True Retention
...

### Forecast
...

## Glossary
A glossary of key terms for this report

Review: The act of grading a card with one of four options "Again", "Hard", "Good", "Easy".
Lapse / Flunked Review: The act of answering "Again" to a review card.
Interval: The amount of time between an initial and future review.
Queue: The group that cards are placed in. "New" for unseen cards, "Due" for review cards, "Learning" for unseen but not yet learnt cards
and lapsed review cards.
Young Card: A review card with an interval less than 21 days.
Mature Card: A review card with an interval of 21 days or more.
Learning Review: Any review of a card that has not yet graduated graduated to the Due Queue.
Relearning Review: A review of a previously lapsed card.
Cram Review: A review that takes places outside the normal schedule.

## Citations
[1] https://docs.ankiweb.net/
[2] https://ankiweb.net/shared/info/1550984460
