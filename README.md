# Music Library System

A Python OOP lab implementing a `Song` class with instance attributes, class attributes, and class methods to manage and analyze a music library.

## The Scenario

You've just landed a role as a junior software engineer at MusicTech Innovations, a company that powers a popular music streaming service. Your first project involves designing a Python class that encapsulates the essential properties and behaviors of a song, making it easier for the team to manage and analyze the vast collection of tracks.

The `Song` class represents individual songs and maintains global insights — tracking the total number of songs, listing all unique artists and genres, and counting how many songs belong to each genre and artist.

## Setup

**Requirements:** Python 3.8+, pipenv

```bash
# Clone the repo
git clone https://github.com/iankinoti-cloud/music-library-system.git
cd music-library-system

# Install dependencies
pipenv install

# Run the tests
pipenv run pytest
```

Or with system Python:

```bash
pip install pytest
pytest
```

## Song Class

### Instance Attributes

| Attribute | Type   | Description          |
|-----------|--------|----------------------|
| `name`    | `str`  | Title of the song    |
| `artist`  | `str`  | Artist name          |
| `genre`   | `str`  | Genre of the song    |

### Class Attributes

| Attribute      | Type   | Description                                      |
|----------------|--------|--------------------------------------------------|
| `count`        | `int`  | Total number of Song objects created             |
| `genres`       | `list` | All unique genres across all songs               |
| `artists`      | `list` | All unique artists across all songs              |
| `genre_count`  | `dict` | Number of songs per genre `{"Rap": 5, "Pop": 3}`|
| `artist_count` | `dict` | Number of songs per artist `{"Beyonce": 17}`     |

### Class Methods

| Method                  | Description                                              |
|-------------------------|----------------------------------------------------------|
| `add_song_to_count()`   | Increments `count` by 1                                  |
| `add_to_genres(genre)`  | Appends genre to `genres` list if not already present    |
| `add_to_artists(artist)`| Appends artist to `artists` list if not already present  |
| `add_to_genre_count(genre)`  | Increments genre key in `genre_count` dict (or sets to 1)|
| `add_to_artist_count(artist)`| Increments artist key in `artist_count` dict (or sets to 1)|

## Usage

```python
from song import Song

# Create song objects
s1 = Song("99 Problems", "Jay Z", "Rap")
s2 = Song("Halo", "Beyonce", "Pop")
s3 = Song("Smells Like Teen Spirit", "Nirvana", "Rock")
s4 = Song("Lemonade", "Beyonce", "Pop")

# Total songs created
print(Song.count)          # 4

# All unique genres
print(Song.genres)         # ['Rap', 'Pop', 'Rock']

# All unique artists
print(Song.artists)        # ['Jay Z', 'Beyonce', 'Nirvana']

# Songs per genre
print(Song.genre_count)    # {'Rap': 1, 'Pop': 2, 'Rock': 1}

# Songs per artist
print(Song.artist_count)   # {'Jay Z': 1, 'Beyonce': 2, 'Nirvana': 1}
```

## Running Tests

```bash
pytest lib/testing/song_test.py -v
```

Expected output:

```
Class "Song" in song.py instantiates with a name, artist, and genre. PASSED
Class "Song" in song.py counts the total number of Song objects. PASSED
Class "Song" in song.py keeps track of all Song genres. PASSED
Class "Song" in song.py keeps track of all Song artists. PASSED
Class "Song" in song.py keeps count of Songs for each genre. PASSED
Class "Song" in song.py keeps count of Songs for each artist. PASSED

6 passed
```

## Project Structure

```
music-library-system/
├── lib/
│   ├── song.py               # Song class implementation
│   └── testing/
│       ├── conftest.py       # pytest configuration
│       └── song_test.py      # test suite (6 tests)
├── Pipfile
├── Pipfile.lock
├── pytest.ini
└── README.md
```

## License

This project is licensed under the terms found in [LICENSE.md](LICENSE.md).
