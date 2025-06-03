# Visit Scheduler Based on Time and Rank

This C++ program reads a CSV file containing information about various places (name, opening/closing time, and rank), then generates an optimal visit schedule based on available time, ranking, and constraints.

## Features

- Reads data from a CSV file (name, openingTime, closingTime, rank)
- Converts time from string to minutes for comparison
- Chooses next best place to visit based on:
  - Whether it's open
  - If it's not already visited
  - Rank and earliest availability
- Ensures at least 45 minutes is available before visiting a place
- Prints formatted schedule showing location and visit time range

## Input Format

The input file must be a CSV file with the following **exact format**:

```
name,openingTime,closingTime,rank
Museum,08:00,16:00,2
Cafe,10:00,18:00,3
Gallery,09:30,15:30,1
...
```

- **name**: Name of the place
- **openingTime** and **closingTime**: In `HH:MM` 24-hour format
- **rank**: Integer indicating visit priority (lower is higher priority)

 The header must be exactly: `name,openingTime,closingTime,rank`

## Output Format

For each visitable location, the output will be:

```
Location Museum
Visit from 08:00 until 09:00
---
Location Gallery
Visit from 09:00 until 10:00
---
```

## Compilation & Execution

### Compile

```bash
g++ -std=c++11 -o visit_scheduler 810101514-220701096.cpp
```

### Run

```bash
./visit_scheduler path_to_input_file.csv
```

## How It Works

- Time is handled in minutes from midnight to allow accurate comparison.
- Scheduler tries to visit as many high-ranked places as possible within available hours.
- Each visit lasts from 30 minutes to 1 hour.
- Preference is given to places already open, with earliest availability and best rank.

## Main Components

- `place_info` struct: Holds place name, opening/closing times, rank, and visitation status.
- `read_input_from_file()`: Parses CSV input file.
- `find_best_place()`: Decision logic for selecting the next visit.
- `print_output()`: Prints visit information in a readable format.

## Notes

- Start time is hardcoded at **07:30 AM**
- First visit starts at **08:00 AM**
- Visit duration logic adjusts dynamically based on place closing time
- Rank breaks ties; lower rank gets higher preference


