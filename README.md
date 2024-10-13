# 🤗 Hugging Face packaging using GitHub Container Registry

This repo shows how to create a container and package it with GitHub Actions. This repository gives you a good starting point for a Dockerfile, GitHub Actions workflow, and Python code.

The web application uses FastAPI with Hugging Face and exposes a single endpoint that you can interact with it. 

Fork this repository and run the GitHub Actions as-is so that you can register your own containerized application with no modifications needed.


## I. Installation 🦉

1. **Open on Codespaces and make sure you're on the right directory**

2. **Create and activate** a [**virtual environment**](https://docs.python.org/3/library/venv.html):
    ```bash
        python -m venv venv
        source venv/bin/activate
    ```
3. **Install all the requirements / librairies:**
    ```bash
        pip install -r requirements.txt
    ```

4. **Check if Docker is installed in your environment**
    ```bash
        which docker
   ```

5. If Docker is preinstalled that's great, you can skip to the next step. If not, follow this carefully:
    - From Codespaces tap on the search bar and look for `> Codespaces: Add Dev Container Configuration Files`
    - Click on `Modify your active environment` and choose this additional feature:  `Docker`.



## Running the FastAPI server locally

1. **Make sure `uvicorn` is well installed**
    ```bash
        which uvicorn
    ```

2. **Run the following command on CLI**
    ```bash
        cd webapp
        uvicorn --host 0.0.0.0 main:app
    ```

3. **Build the container:**
    ```bash
        cd ..
        docker build -t huggingface:local .
    ```

4. **Run the Docker image**
    ```bash
        docker run -i -p 8000:8000 huggingface:local
   ```


## CI/CD Packaging with GitHub Actions
The goal of using GitHub Actions is **to automate the process of building and deploying containerized applications**, particularly in the context of MLOps workflows. 

Instead of manually building, tagging, and pushing containers to a registry like Docker Hub, Azure, or AWS, automation ensures this process is streamlined and repeatable with minimal manual intervention. By setting up a workflow in GitHub Actions, the entire process — from building the container to publishing it to a registry — can be triggered with a single action, making deployment more efficient and reducing the risk of errors.

Check out the `main.yml` file in the `.github/workflows` directory for more details about the worflow.