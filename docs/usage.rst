Usage
==================

Running the Application
-----------------------

To start the Flask application, navigate to the project directory and run:

.. code-block:: bash

   python app.py

The app will be available at `http://127.0.0.1:5000/`.

Using the API
-------------

The API provides endpoints for searching and managing books in the database. Below are the available endpoints and their usage:

1. **Homepage (`/`)**  
   Access the homepage of the app:

   - **Method**: GET  
   - **Example**: Visit `http://127.0.0.1:5000/` in your browser.  

   This page serves as the entry point and gives an overview of the application.

2. **Search for Books (`/search`)**  
   Query books by title or author using the `query` parameter.

   - **Method**: GET  
   - **Parameters**:
      - `query` (string): Search term (book title or author).
   - **Example Request**:

     .. code-block:: bash

        curl "http://127.0.0.1:5000/search?query=python"

   - **Example Response**:

.. code-block:: json

   [
       {
           "title": "Learning Python",
           "authors": ["Mark Lutz"],
           "isbn": "9781449355739",
           "thumbnail": "https://covers.openlibrary.org/b/isbn/9781449355739-L.jpg"
       },
       {
           "title": "Python Crash Course",
           "authors": ["Eric Matthes"],
           "isbn": "9781593276034",
           "thumbnail": "https://covers.openlibrary.org/b/isbn/9781593276034-L.jpg"
       }
   ]

3. **View All Books (`/books`)**  
   Retrieve all books stored in the database.

   - **Method**: GET  
   - **Example Request**:

     .. code-block:: bash

        curl "http://127.0.0.1:5000/books"

   - **Example Response**:

.. code-block:: json

   [
       {
           "title": "Learning Python",
           "authors": ["Mark Lutz"],
           "isbn": "9781449355739",
           "totalCopies": 5,
           "borrowedCopies": 1,
           "thumbnail": "https://covers.openlibrary.org/b/isbn/9781449355739-L.jpg"
       }
   ]


Using `libraryMain.py`
----------------------

The `libraryMain.py` script provides a command-line interface for interacting with the application, allowing users to input ISBN numbers to fetch book details and manage inventory.

### Workflow

1. **Start the Script**:  
   Navigate to the project directory and run:

   .. code-block:: bash

      python libraryMain.py

2. **Input ISBN**:  
   The script will prompt you to enter an ISBN number:

   .. code-block:: text

      Enter ISBN number: 9781449355739

3. **Fetch Book Details**:  
   The script fetches book details from the Open Library API based on the ISBN provided and displays them:

   .. code-block:: text

      Title: Learning Python
      Authors: Mark Lutz
      Publishers: O'Reilly Media

4. **Perform an Action**:  
   You will be prompted to choose an action:

   - **Borrow**: Marks one copy of the book as borrowed.
   - **Return**: Marks one copy of the book as returned.
   - **Add**: Adds a new copy of the book to the inventory.

   Example interaction:

   .. code-block:: text

      Are you borrowing, returning, or adding this book? (borrow/return/add): borrow
      Borrowed a copy of the book.
      Book transaction recorded in the database.

5. **Store Data in Firebase**:  
   The script updates the book inventory in the Firebase Realtime Database under the book's unique ISBN.

### Script Details

- **Integration with Open Library**:  
  `libraryMain.py` fetches book details such as title, authors, and publishers from the Open Library API.

- **Firebase Database Management**:  
  The script updates inventory data (e.g., `totalCopies` and `borrowedCopies`) in Firebase. Example database entry:

.. code-block:: json

   [
       {
           "title": "Learning Python",
           "authors": ["Mark Lutz"],
           "isbn": "9781449355739",
           "totalCopies": 5,
           "borrowedCopies": 1,
           "thumbnail": "https://covers.openlibrary.org/b/isbn/9781449355739-L.jpg"
       }
   ]

  