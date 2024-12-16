API Reference
=============

`/search`
---------

**Method**: GET  
**Parameters**:  
- `query` (string): Search query for book title or author.  

**Example Request**:

.. code-block:: bash

   curl "http://127.0.0.1:5000/search?query=python"

**Response**:

.. code-block:: json

   [
       {
        "title": "Orwell's Nineteen eighty-four",
        "authors": ["Irving Howe, George Orwell"],
        "isbn": "9780155658110",
        "thumbnail": "https://covers.openlibrary.org/b/isbn/9780155658110-L.jpg"
       }
   ]

---

`/books`
--------

**Method**: GET  

**Example Request**:

.. code-block:: bash

   curl "http://127.0.0.1:5000/books"

**Response**:

.. code-block:: json

   [
       {
        "title": "Orwell's Nineteen eighty-four",
        "authors": ["Irving Howe, George Orwell"],
        "isbn": "9780155658110",
        "thumbnail": "https://covers.openlibrary.org/b/isbn/9780155658110-L.jpg"
       }
   ]
