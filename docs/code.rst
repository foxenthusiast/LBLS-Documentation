Code Overview
=============

Core Functions
--------------

`getBookDetails(isbn)`

Fetches book data from the Open Library API based on ISBN. Prompts users to borrow, return, or add books, and updates Firebase with the current status.

**Parameters**:
- `isbn` (string): The ISBN number of the book.

**Example Execution**:

.. code-block:: python

   Enter ISBN number: 9781234567890

`saveToFirebase(isbn, title, authors, publishers, action)`

Updates the Firebase Realtime Database with book details and adjusts the total/borrowed copies based on user actions.

**Actions**:
- `borrow`: Increases the borrowed copies count.
- `return`: Decreases the borrowed copies count.
- `add`: Adds a new copy to the database.

---
