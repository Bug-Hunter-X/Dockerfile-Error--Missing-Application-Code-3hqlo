# Dockerfile Bug: Missing Application Code

This repository demonstrates a common error in Dockerfiles: forgetting to copy the application code into the image.

The `Dockerfile` attempts to run a Python application, but it fails because the application code (`main.py`) is not copied into the image. The `Dockerfile-fixed` provides the corrected version.

## Steps to Reproduce

1.  Clone this repository.
2.  Build the original Dockerfile:
    ```bash
    docker build -t missing-app . 
    ```
3.  Attempt to run the image (it will fail):
    ```bash
    docker run missing-app
    ```
4.  Build the fixed Dockerfile:
    ```bash
    docker build -t fixed-app -f Dockerfile-fixed .
    ```
5.  Run the fixed image (it will successfully run a simple Python "Hello, world!"):
    ```bash
    docker run fixed-app
    ```

## Solution

The `Dockerfile-fixed` corrects the issue by adding a `COPY` instruction to copy the `main.py` file into the image before the `CMD` instruction.