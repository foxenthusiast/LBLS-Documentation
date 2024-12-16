# LBLS - LibraryBookLookupSystem

LBLS-Demo is a project built using Flask, which allows you to manage and search for books through an API. The project includes features like fetching book information from a Firebase database and displaying book data through a website.

## Features

- **Search functionality**: Allows users to search for books by title or author.
- **Book information**: Displays detailed information about books, including a thumbnail image, all from OpenLibrary.
- **Guaranteed inconvenience**: Will be an utter drag, incredibly slow and painful. But we love him really!

## Table of Contents

- [Installation Guide](#installation-guide)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Code Details](#code-details)
- [License](#license)

---

## Installation Guide

### Requirements

- Python 3.8+
- Flask
- Requests

### Install Dependencies

To get started with the project, you need to install the necessary dependencies. You can either clone the repository and install the dependencies using `pip` or create a virtual environment for it.

1. **Clone the repository**:

    ```bash
    git clone https://github.com/foxenthusiast/LBLS-Demo.git
    cd LBLS-Demo
    ```

2. **Install dependencies**:

    ```bash
    pip install -r requirements.txt
    ```

3. (Optional) **Install Sphinx for documentation**:

    If you want to generate and view the project documentation locally:

    ```bash
    pip install sphinx
    ```

    You can then build the documentation using:

    ```bash
    make html
    ```

---

## Usage

### Running the Flask App

To run the Flask application, execute the following command:

```bash
python app.py
```

By default, the app will be available at [http://127.0.0.1:5000/](http://127.0.0.1:5000/).

### API Endpoints

- **GET `/`**: Displays the homepage of the app.
- **GET `/search`**: Search for books by title or author. Example:

    ```bash
    curl "http://127.0.0.1:5000/search?query=python"
    ```

- **GET `/books`**: Retrieve all books in the database. Example:

    ```bash
    curl "http://127.0.0.1:5000/books"
    ```

The above endpoints return data in JSON format with book details like title, authors, and ISBN.

---

## API Endpoints

### `/search`

**Method**: GET  
**Query Parameter**: `query` (string) - The search query (book title or author).  

**Example Request**:

```bash
GET /search?query=python
```

**Response**:

```json
[
    {
        "title": "Orwell's Nineteen eighty-four",
        "authors": ["Irving Howe, George Orwell"],
        "isbn": "9780155658110",
        "thumbnail": "https://covers.openlibrary.org/b/isbn/9780155658110-L.jpg"
    },
    ...
]
```

---

### `/books`

**Method**: GET  

**Example Request**:

```bash
GET /books
```

**Response**:

```json
[
    {
        "title": "Orwell's Nineteen eighty-four",
        "authors": ["Irving Howe, George Orwell"],
        "isbn": "9780155658110",
        "thumbnail": "https://covers.openlibrary.org/b/isbn/9780155658110-L.jpg"
    },
    ...
]
```

---

## Code Details

### Core Functionality

**libraryMain.py** includes the functionality to fetch book details using an ISBN, prompt users to borrow, return, or add books, and save the book's status to Firebase.

#### Main Functions

- **`getBookDetails(isbn)`**: Fetches book data from Open Library API based on ISBN and allows users to borrow, return, or add copies of the book.
- **`saveToFirebase(isbn, title, authors, publishers, action)`**: Updates the Firebase Realtime Database with the current status of the book.

#### Example Usage

```bash
Enter ISBN number: 9780155658110
```

The program will fetch book details, prompt you to take an action, and update Firebase accordingly.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
