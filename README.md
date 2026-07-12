# Python Web Scraping and Dashboard Creation

This project built key skills in Python Requests web scraping, modular programming, data cleaning in pandas, data visualization with matplotlib and others, and dashboard creation with Python Shiny.

Please view my final result here, a visually striking, informative, and interactive dashboard of Pokemon card game tournament statistics built with the Python Shiny web application framework that showcases my skills in data presentation and analysis.

[Dashboard (links to Posit)](https://019cf8ca-d476-452b-cd6c-e8061766ff0e.share.connect.posit.cloud).

## Project Goals

As a longtime player of the mobile game Pokemon TCG Pocket, and a follower of the competitive tournament scene, I wanted to quantify the most successful cards and decks over the first 12 months of the game's life. While I could go on the Limitless TCG website and view the top decks within a certain time frame, I couldn't find any data that showed the competitive history of individual cards as well as comparing the success of cards across seasons. All the information was there on the Limitless TCG website, but no one had compiled it before. I decided to collect the data and analyze it to answer my questions.

## Explaining the Data

The data was collected with the Python Requests and Beautiful Soup libraries, gathering HTML from the Limitless TCG website.

<img src="/assets/Screenshot 2026-07-11 185618.png" width="500">

I converted the raw HTML into structured Panda data frames using Python loops and 'if' statements, accounting for errors and missing data.

<img src="/assets/Screenshot 2026-07-11 190417.png" width="500">

<br>
<br>

In raw form, the data consisted of three tables in a hierarchical structure with the following variables:

<table>
<tr>
<td valign="top">

### Table 1

* Deck Link
* Count
* Share
* Score
* Win %

</td>
<td valign="top">

### Table 2

* Player
* Tournament
* Date
* Placement
* Win-Loss Record
* Decklist Link
* Decklist

</td>

</td>
<td valign="top">

### Table 3

* Card 1
* Card 2
* Card 3
* ...
* Card 20
  
</td>

</tr>
</table>

Table 1 was an aggregation of deck archetypes. Table 2 was a list of individual tournament performances for a certain deck archetype. Table 3 was a complete decklist corresponding to a single player. Thus, these three tables formed a hierarchical structure with Table 2 derived from the 'Deck Link' variable of Table 1, and Table 3 derived from the 'Decklist Link' variable of Table 2.

All variables were strings when extracted from the raw HTML.

### Data Cleaning

I cleaned the data extensively using Pandas and built-in Python functions. For example, I separated the 'Placement' variable, which had the form "8th of 150", into two separate variables 'placement' and 'player_total' using regular expressions, and converted them to numeric data types.

<img src="/assets/Screenshot 2026-07-11 193921.png" width="500">

I also converted the 'date' variable into a date format using the Python datetime library.

In order to store Table 3, I represented it as a nested JSON object within Table 2, thus preserving the parent-child relationship of the data and allowing for simple data extraction.

<img src="/assets/Screenshot 2026-07-11 215854.png" width="400">

## Data Analysis

With the data cleaned and ready for use, I aggregated the data looking to answer certain questions, such as most successful cards of all time, highest ranking placement per card, and average placement per season. With the average placement per season metric, I was able to show the rise and fall, or the competitive history of each individual card. When it performed best relative to its peers, and when it performed worse. With this data, I was able to create charts such as the one below, using the Python library Plotly.

<img src="/assets/Screenshot 2026-07-11 221711.png" width="700">

Answering the question of the most successful cards of all time was the most difficult. In order to answer this, I had to decide on a way to measure success. Obviously winning 1st place in a tournament is the best sign of success, but placing 2nd, 4th, 10th, or even 64th, can be considered successful in tournaments consisting of 200+ players. Thus, in order to quantify the success of a card, I had to assign a weighted score to its placements and add them up, comparing each card to each other card.

<img src="/assets/Screenshot 2026-07-11 222218.png" width="700">

I also had to account for the length of time a card had been released. Cards that had been released for longer would automatically have higher scores because they had more opportunities to accumulate top finishes. To account for this, I also weighted the scores by how long they had been released for. With all these modifications, I was able to come up with a power-ranking metric that found the most successful cards in the history of the game.

<img src="/assets/Screenshot 2026-07-12 002831.png" width="500">

## Dashboard Creation

With metrics calculated and visualizations created, my last step was to create a dashboard. I chose to use Python Shiny because of its flexibility, allowing for multiple pages, custom selectors, and easy page layout adjustments.

For the dashboard, I created UI cards in Python Shiny, storing tables, charts, and information. For example, the code below creates a UI card with information for the top tournament placement for the selected card. Please see 'app.py' for the full dashboard code.

<img src="/assets/Screenshot 2026-07-12 003718.png" width="700">

I structured the dashboard in three pages:

Page 1: Individual Card Selection and Exploration. Each card can be selected individually and its statistics and history can be examined. The information includes average placement by season, top tournament finishes, both all time and by season, card art, and top partners, or the cards it is most often paired with.

Page 2: Most Dominant Cards. This page contains a visualization and a table that display the top scoring cards of all time. On this page, you can see the cards that won with the greatest frequency relative to their peers, marking them as the most dominant. In addition, an exciting animated visualization displays the progression of the most dominant cards. As more and more powerful cards are released, the card that holds the spot as Most Dominant continually changes, up until the first year of the game ended.

Page 3: Miscellaneous exploration. I chose to focus on one type of card in my individual card selection section, because there are simply too many cards to examine them all. On this page, curious explorers can look into any card that I didn't cover, getting general summary statistics on that card's performance.

<img src="/assets/Screenshot 2026-07-12 005102.png" width="800">
