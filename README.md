# Python Web Scraping and Dashboard Creation

This project built key skills in Python Requests web scraping, modular programming, data cleaning in pandas, data visualization with matplotlib and others, and dashboard creation with Python Shiny.

Please view my final result here, a visually striking, informative, and interactive dashboard of Pokemon card game tournament statistics built with the Python Shiny web application framework that showcases my skills in data presentation and analysis.

[Dashboard (links to Posit)](https://019cf8ca-d476-452b-cd6c-e8061766ff0e.share.connect.posit.cloud).

## Explaining the Data

The data was collected with the Python Requests and Beautiful Soup libraries, gathering HTML from the Limitless TCG website.

<img src="/assets/Screenshot 2026-07-11 185618.png" width="500">

I converted the raw HTML into structured Panda data frames using Python loops and 'if' statements, accounting for errors and missing data.

<img src="/assets/Screenshot 2026-07-11 190417.png" width="500">

<br>
<br>

In raw form, the data consisted of two tables six variables:
* Deck
* Player
* Tournament
* Date
* Placement
* Win-Loss Record
* Decklist Link

<table>
<tr>
<td valign="top">

### Pros

- Fast
- Lightweight
- Open source
- Cross-platform
- Easy to use

</td>
<td valign="top">

### Cons

- Limited customization
- Learning curve
- No offline sync
- Few plugins
- Sparse documentation

</td>
</tr>
</table>


All variables were strings when parsed directly from the HTML. 'Decklist Link' consisted of a URL that linked to a decklist that would require further extraction.

### Data Cleaning

I cleaned the data extensively using Pandas and built-in Python functions. For example,



## Key Takeaways

* The key to good visualizations is not in choosing the fanciest chart, but in choosing meaningful data
* Choosing meaningful data often involves time spent planning and thinking through a data problem - then using data wrangling skills to get the data into its desired form
* Oftentimes, a simple table is just as effective as any graphic
* Game data like this is complicated, with endless edge cases and unexpected problems that have to be accounted for, scraping the data is not even half the battle
* Presentation matters - a color theme and clean visuals can go a long way

## Why This Matters

First, this project shows my ability to tell a story with data. With this dashboard I tell a complete story of the first year of Pokémon TCG Pocket. 
Tournament results, changes in the metagame overtime, nuances in deckbuilding, and overall power rankings are all represented. Many people responded to my storytelling ability when I 
shared this project with them, saying it was comprehensive, informative, interesting, and fun to look at. I can use these skills to clearly
tell business stories, pinpoint critical information, and handle difficult data questions for your business.

Secondly, this project shows my ability to adapt to using new tools. While I am well-versed in the industry standards of SQL, Python, Excel, and Tableau, I learned a new tool, Shiny, which I had never used before to complete this project. This shows that I can quickly adapt to new tools with which I have less experience.
