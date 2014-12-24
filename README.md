# OHHLA-WebScraper

This is a simple Web Scraper used to pull lyrics from the [Original Hip-Hop Lyrics Archive](http://ohhla.com/). The lyrics are left out of the github repo because of the extensive size of the archive (and thus the lyrics file). Feel free to clone the repo and run the scraper yourself, but be warned it might take a couple hours to go through all the pages. The OHHLA has a pretty extensive archive.

I intend to use the lyrics with a tweaked version of my Markov Babbler in order to create a Rap Generator. As of 23 Dec. 2014, the regular expressions, used to sanitize the lyrics, need to be improved before this Scraper can be fed to the Markov Model. The sanitization has currently been checked against all lyrics for artist whose names start with a '1'. I intend to hand-test the sanitization will all lyrics for all Artists whose name starts with an integer. There are older entries as well as newer entries to test the sanitization against and will have over 5000 lines of lyrics which it is tested with. I believe this will be a solid benchmark for the rest of the lyrics in the archive.

Finally, this is my *first ever* program written in Python. Please don't be too harsh judging it, but also **PLEASE** tell me how I butchered Python best practices so I can learn. I literally went from reading the docs to this program. Not a single small test program in between. I also think I did the whole Class/Module thing wrong and in order to execute my file I run 'import OHHLAScraper' which I also think is incorrect. I'm pretty sure any Python expert would cringe at this and re-write it differently. My bad.

-Andoni

## Using the Scraper

1. Download the source code (really just the OHHLAScraper.py file).
2. Start up your Python Command Line (V. 3.2 or higher is guaranteed. Haven't tested on older versions)
3. Execute `import OHHLAScraper`
4. Wait several hours while it compiles a new `lyrics.txt` file for you.

#### Trouble Shooting

Make sure you have the [lxml](http://lxml.de/) library downloaded. The rest of the needed imports are standard in Python3.

## Philosophy Towards Sanitization Rules

Some of you might be upset about what gets sanitized and what stays when going through and parsing the lyrics. There were some major executive calls that needed to be made. Remember, that all of this is intended to be used to feed a Markov Model with the intent of finding rhymes. As such, I excluded all parentheticals, choruses, outros, and the like from the Scraper. All of these sections of lyrics were, for the most part, a break in rhyme-scheme that did not flow with the consistent verses and would not feed nicely into a Markov Model. However, all of these are not to difficult to undo and tweak, in order to make the Scraper fit your own needs.

Some of the decisions cause the loss of rhymes for certain verses (When parentheticals indicated a background voice completing the rhyme), but on the larger picture it was necessary to lose these couple of rhymes in order to preserve the sanitization for the rest of the poorly formatted archive of lyrics.

**UPDATE** (24 Dec. 2014): Thanks to the wonderful and brilliant minds on Stack Overflow, I am now able to exclude Chorus blocks at the end of a page as well! Further, some playing around with alternations helped to clean up the Regular Expressions a ton. Finally, some inginuity and creativity managed to fix the Partial-Parentheses bug! Currently, there are no known bugs with the expressions currently implemented (There may be formatting issues I have yet to address, but of any formatting sanitizations that I have addressed, I currently believe my solutions are robust and bug-free).

If you have any questions or strong feelings towards excluding (or including) sanitizations of the lyrics, feel free to email me at [andoni@uchicago.edu](mailto:andoni@uchicago.edu).
