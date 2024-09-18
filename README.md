
# Concerts Database Management System
This Python project manages a concerts database with bands, venues, and concerts. It uses SQLite3 for database operations and raw SQL queries to interact with the data. The code demonstrates how to create tables, insert data, and perform various operations, such as retrie*ving bands that performed at specific venues, creating new concerts, and more.

## Features
**Bands Table**: Stores band information (name, hometown).
**Venues Table**: Stores venue information (title, city).
**Concerts Table**: Stores concert details, associating a band with a venue and date.
**Database Schema**
The database contains three tables:

### **bands**: Contains band names and hometowns.
**id**: Auto-incrementing primary key
**name**: Name of the band
**hometown**: Band's hometown
### **venues**: Contains venue titles and cities.
**id**: Auto-incrementing primary key
**title**: Title of the venue
**city**: City where the venue is located
### **concerts**: Stores the relationship between bands and venues, including the   **concert date**.
**id**: Auto-incrementing primary key
**band_id**: Foreign key referencing bands.id
**venue_id**: Foreign key referencing venues.id
**date**: Date of the concert
## **Classes**
Concert Class
This class provides methods to interact with concert-related data.

#### **band(concert_id)**: Returns the band playing in the concert.
**venue(concert_id)**: Returns the venue of the concert.
**hometown_show(concert_id)**: Returns True if the concert is in the band's hometown.
**introduction(concert_id)**: Returns a concert introduction string.
Venue Class
This class provides methods to interact with venue-related data.

#### **concerts(venue_id)**: Returns all concerts in the venue.
**bands(venue_id)**: Returns all bands that performed at the venue.
**concert_on(venue_id, date)**: Finds the first concert on a specific date at the venue.
**most_frequent_band(venue_id)**: Returns the band that has performed the most at the venue.
#### **Band Class**
This class provides methods to interact with band-related data.

**concerts(band_id)**: Returns all concerts played by the band.
**venues(band_id)**: Returns all venues where the band has performed.
play_in_venue(band_id, venue_id, date): Creates a new concert for the band at the venue.
**all_introductions(band_id)**: Returns all concert introduction strings for the band.
most_performances(): Returns the band that has played the most concerts.
Usage
**Create the database and tables**: The script will automatically create the necessary tables (bands, venues, and concerts) if they don't exist.

**Insert data**: You can insert bands, venues, and concerts using SQL queries. Example bands and venues are created in the script:

python
Copy code
cursor.execute("INSERT INTO bands (name, hometown) VALUES (?, ?)", ('H_Art the Band', 'Nairobi'))
cursor.execute("INSERT INTO bands (name, hometown) VALUES (?, ?)", ('Elani', 'Nairobi'))
cursor.execute("INSERT INTO venues (title, city) VALUES (?, ?)", ('Kenyatta International Convention Centre', 'Nairobi'))
cursor.execute("INSERT INTO venues (title, city) VALUES (?, ?)", ('Moi Stadium', 'Kisumu'))
Add concerts: Concerts are added by linking band IDs and venue IDs:

python
Copy code
cursor.execute("INSERT INTO concerts (band_id, venue_id, date) VALUES (?, ?, ?)", (band_id, venue_id, '2024-09-15'))
Run queries: Use the static methods provided by the Concert, Venue, and Band classes to retrieve or manipulate data.

Example
python
Copy code
# Get the introduction for a concert
introduction = Concert.introduction(concert_id)
print(introduction)

# Get all concerts at a venue
venue_concerts = Venue.concerts(kenyatta_id)
print(venue_concerts)

# Create a new concert
Band.play_in_venue(H_Art_the_Band_id, kenyatta_id, '2024-09-15')

# Find the band with the most performances
most_frequent_band = Band.most_performances()
print(most_frequent_band)
Setup
Install Python 3.x if not already installed.
Clone this repository.
Run the Python script to create the SQLite database (concerts.db).
bash
Copy code
python concerts.py
License
This project is licensed under the MIT License.

This README introduces the code, explains its functionality, and provides guidance on how to use it. Feel free to modify it based on the needs of your project.