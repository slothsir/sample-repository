# sample-repository
# WhatsApp Chat Decoder
A Python-based project that reads a WhatsApp chat export, converts the raw text into structured data, and performs basic analysis on the conversation.
This was one of my first practical Python projects, built to understand how file handling, string processing, lists, dictionaries, NumPy, and datetime can be used together to work with real-world data.

## What the Project Does
The project reads a WhatsApp `.txt` chat export and extracts information such as:
* Date
* Time
* Sender
* Message
The extracted messages are stored as dictionaries in a list, making the raw chat easier to analyze.
The final analysis includes:
* Total number of messages
* Number of messages sent by each participant
* Message percentage by participant
* Activity by hour
* Activity heatmap
* Frequently used words
* Fastest average replier
* Silent streaks
* Longest message
* Busiest day
* Busiest hour
* Rule-based personality archetypes

## Project Data
The project was tested on a WhatsApp group containing:
* 3,174 messages
* 6 participants
* 1 April 2024 to 30 May 2024
The final program produces a text-based report called **GROUP DNA**, summarizing the activity and communication patterns of the group.

## Libraries Used
### NumPy
NumPy was mainly used for creating and working with the activity matrix used for the hourly heatmap.
```python
import numpy as np

x = np.zeros((6, 24))
```
The matrix represents 6 participants across 24 hours of the day.

### datetime
The `datetime` module was used to convert the extracted date and time strings into datetime objects.
This was particularly useful for calculating:
* Response time
* Gaps between active days
* Silent streaks

```python
from datetime import datetime
```

## Problems I Faced

### 1. Parsing the WhatsApp chat
The first challenge was figuring out how to separate the date, time, sender, and message from each raw line.
Instead of immediately using `split()`, I experimented with string indexing and slicing to understand exactly how the WhatsApp export was structured.
This led to extracting specific sections of each line using indexes.

### 2. System messages
Not every line in the exported chat was an actual message.
There were system messages such as group creation and group description changes.
I had to identify these messages and remove them from the dataset so that the final count represented actual messages.
The initial parsed data contained 3,178 entries, which was reduced to the expected 3,174 messages after removing unwanted entries.

### 3. Different sender name lengths
Different participants had different name lengths, which made fixed string positions difficult to handle.
For example, extracting a sender with four characters required different slicing from extracting a sender with five or six characters.
I had to account for these differences while parsing the chat.

### 4. Debugging the parsed data
One of the first checks I performed was printing the first and last few parsed messages.
The first attempt produced incorrect results, so I went back and inspected the parsing logic before continuing with the analysis.
This helped me understand the importance of validating data before performing calculations on it.

### 5. Working with dates and response times
Calculating response times was more complicated than simply subtracting two strings.
I had to convert the date and time into `datetime` objects first and then calculate the difference between consecutive messages.
This allowed me to calculate the average response gap for different participants.

### 6. Finding silent streaks
Another challenge was determining how many consecutive days a participant was inactive.
I extracted the unique dates on which each participant sent a message, sorted those dates, and calculated the gaps between them.

### 7. Finding the longest message
Finding the longest message required comparing the length of messages one by one.
I initially encountered several errors while trying to implement this, which helped me understand indexing, list handling, and comparison logic better.

### 8. Finding if else for right purpose
Trying to solve errors related to loops and nested loops was tedious task  `if...:  else:`,  `for ..... in... :`,  `range(,)` . these required me to form more than 2 loops inside one to get online output

### 9. special maps and good looking graphs
Graph showing heat maps and using arrays to include all the information.
I initially found it easy to put all data but then after that properly presenting graph took a lot of time

## What I Learned
The main purpose of this project was not just to analyze a WhatsApp group.
It was to learn how to take **unstructured text data and turn it into something that can be processed and analyzed.**
While building it, I practiced:
* File handling
* Reading text files
* String slicing and processing
* Lists [in depth]
* Dictionaries
* Loops
* Conditional statements
* Functions
* NumPy arrays
* Date and time manipulation
* Basic data analysis
* loops

## Future Improvements
There are several things I would improve in a future version:
* Make the parser work with different WhatsApp export formats
* Remove the need to manually specify participant names
* Improve the message parsing logic
* Make the analysis more automated
* Add more statistical analysis
* Improve the visualization of the activity data
* Create a cleaner interface for uploading and analyzing a chat

## Project Structure
```text
WhatsApp-Chat-Decoder/
│
├── minor_project_1.ipynb
└── README.md
```

## Conclusion
This project was an experiment in applying Python to a real-world dataset rather than working only with predefined examples.
It also showed me that writing the code is only one part of programming. A large part of the process is debugging, testing assumptions, understanding the structure of the data, and figuring out why something does not work as expected.

