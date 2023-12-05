# Running the Jupyter Server as Docker container
First, make sure that you installed [Docker](https://www.docker.com/).
```
$ git clone https://github.com/rexes-ND/dockerfiles
$ cd /dockerfiles/jupyter-venv
$ docker compose up --build
```

# Usage
## Browser
Go to `localhost:8888` and directory tree can be accessed.
Jupyter Notebook can be created too and is used to run Python code interactively.

## VS Code
1. Create new `ipynb` file.
2. Click on `Select Kernel` -> `Existing Jupyter Server...`.
3. Enter `http://localhost:8888?token=""` for URL.
4. Select `jupyter-venv` as Kernel.
5. Run Python code interactively
