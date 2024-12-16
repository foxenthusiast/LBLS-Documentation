Installation Guide
==================

Requirements
------------

To run this project, you need the following:

- Python 3.8+
- Flask
- Requests

Installation Steps
------------------

1. Check your Python version:

   .. code-block:: bash

      python --version

   Ensure it is Python 3.8 or higher.

2. Clone the repository:

   .. code-block:: bash

      git clone https://github.com/foxenthusiast/LBLS-Demo.git
      cd LBLS-Demo

3. Create a virtual environment (optional but recommended):

   .. code-block:: bash

      python -m venv venv
      source venv/bin/activate   # On macOS/Linux
      venv\Scripts\activate      # On Windows

4. Install dependencies:

   .. code-block:: bash

      pip install -r requirements.txt

5. (Optional) Install Sphinx for documentation:

   .. code-block:: bash

      pip install sphinx

6. Build the documentation (if required):

   If `make` is available:

   .. code-block:: bash

      make html

   If `make` is not available:

   .. code-block:: bash

      sphinx-build -b html docs/ docs/_build

7. Verify the setup:

   .. code-block:: bash

      python app.py

   This should start the Flask app on [http://127.0.0.1:5000/].
