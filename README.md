# AirBnB Clone – Phase 1: The Console

![Python](https://img.shields.io/badge/Python-3-3776AB?logo=python&logoColor=white)
![Storage](https://img.shields.io/badge/storage-JSON%20file-7aa2f7)
![ALX](https://img.shields.io/badge/ALX-Software%20Engineering-0f9d58)

First phase of the ALX/Holberton **AirBnB clone**: a backend data layer written in plain Python, a JSON file storage engine, and an interactive command interpreter built on the `cmd` module for creating, inspecting, updating and deleting objects. Later phases add MySQL storage, a REST API and a dynamic front end.

Project series: **v1 – console** · [v2 – MySQL and Flask](https://github.com/Blueskale/AirBnB_clone_v2) · [v3 – REST API](https://github.com/Blueskale/AirBnB_clone_v3) · [v4 – dynamic web](https://github.com/Blueskale/AirBnB_clone_v4)

## What it does

- `BaseModel` gives every object a UUID, `created_at`/`updated_at` timestamps, `save()` and `to_dict()` serialisation.
- Domain classes `User`, `State`, `City`, `Amenity`, `Place` and `Review` inherit from it.
- `FileStorage` serialises all objects to `file.json` and reloads them on start-up.
- `console.py` is a shell-like interpreter (prompt `(hbnb)`) that lets you create, show, list, count, update and destroy objects without writing Python.
- `web_static/` holds the first static HTML/CSS mock-ups of the site, validated with the W3C validator script included.

## Getting started

```bash
git clone https://github.com/Blueskale/AirBnB_clone.git
cd AirBnB_clone
./console.py
```

No third-party packages are required; Python 3 is enough.

## Using the console

The console works in **interactive** mode:

```
$ ./console.py
(hbnb) help

Documented commands (type help <topic>):
========================================
EOF  all  count  create  destroy  help  quit  show  update

(hbnb) create User
49faff9a-6318-451f-87b6-910505c55907
(hbnb) show User 49faff9a-6318-451f-87b6-910505c55907
[User] (49faff9a-6318-451f-87b6-910505c55907) {'id': '49faff9a-...', 'created_at': ..., 'updated_at': ...}
(hbnb) quit
```

and in **non-interactive** mode, where commands are piped in:

```
$ echo "create State" | ./console.py
(hbnb)
e37ebcd3-f8e1-4c1f-8095-7a019070b1fa
(hbnb)
```

Exit with `quit`, `EOF`, `Ctrl+D` or `Ctrl+C`.

### Commands

| Command | Usage | Description |
|---|---|---|
| `create` | `create <class>` | Creates an instance, saves it to `file.json` and prints its id |
| `show` | `show <class> <id>` or `<class>.show(<id>)` | Prints the string representation of an instance |
| `destroy` | `destroy <class> <id>` or `<class>.destroy(<id>)` | Deletes an instance and saves the change |
| `all` | `all`, `all <class>` or `<class>.all()` | Prints all instances, optionally filtered by class |
| `count` | `<class>.count()` | Prints the number of instances of a class |
| `update` | `update <class> <id> <attribute> "<value>"`, `<class>.update(<id>, <attribute>, <value>)` or `<class>.update(<id>, <dictionary>)` | Adds or updates an attribute and saves the change |
| `help` | `help` or `help <command>` | Describes a command |
| `quit`, `EOF` | – | Exits the console |

Valid classes: `BaseModel`, `User`, `State`, `City`, `Amenity`, `Place`, `Review`.

## Project structure

```
AirBnB_clone/
├── console.py                     # the command interpreter
├── models/
│   ├── base_model.py              # common attributes and methods
│   ├── user.py, state.py, city.py, amenity.py, place.py, review.py
│   ├── __init__.py                # the single FileStorage instance
│   └── engine/file_storage.py     # JSON serialisation and deserialisation
├── tests/                         # unittest suites for the console, models and storage
└── web_static/                    # static HTML/CSS prototypes (0-index.html … 8-index.html)
```

## Running the tests

```bash
python3 -m unittest discover tests
```

The suites also check PEP 8 style and need the `pep8` package (`pip install pep8`). Several console tests assert help texts from an earlier iteration of the interpreter and currently fail; they are kept for reference.

## Authors

- Princewill Mmadu – [GitHub](https://github.com/Blueskale)
- Stanley Chukwu
