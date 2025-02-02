# datafun-04-eda
My first Jupyter project

This repository holds a basic Jupyter project to learn and experiment. Follow the step by step instructions for what I did while creating and testing. This was created using macOS so all command or "Run:" prompts will be for macOS

## git add, commit, push
    Though not specifically listed when ran while creating and running this project commiting changes is required steps below
    1. git add .
    2. git commit -m "insert commit meesage here"
    3. git push -u origin main
        After initial push all other push commands are - git push

---

## Step one - Create and initialize project
    1. Create repository in GITHUB named datafun-04-eda
        a. Ensure you click to add readme.md
    2. Clone to local machine
        a. In VS code open terminal and run the following commands
            1. cd ~
            2. mkdir Projects (note this could be called something different on your local machine)
            3. cd Projects
            4. git clone https://github.com/s256657/datafun-04-eda (enter your own URL to your repository)
            5. cd datafun-04-eda
            code .
        This step brings the project down to local machine and opens in VS code
    3. Add .gitignore and requirements.txt
        a. Create new files and name them as shown
        b. Copy the both files from the repository and add into local computer
    4. Create and activate virtual environment
        a. To create virtual environment run: python3 -m venv .venv
            VS code should ask We noticed a new environment has been created. Do you want to select it for the workspace folder? Click Yes
        b. To activate virtual environment run: source .venv/bin/activate
    5. Activate and install dependencies
        a. run: python3 -m pip install --upgrade pip setuptools wheel
        b. run: python3 -m pip install -r requirements.txt
    6. Activate and run python script
        a. In the repository is demo_script.py
        b. Create folder and copy/paste demo script into file
        c. cmd+shift+P search and select "python select interpreter" then select the local .venv option
        d. Run: Source .venv/bin/activate
        e. Run: python3 demo_script.py
    7. Create a Jupyter notebook
        a. Click create new file in VS code and name demo_notebook.ipynb
        b. Within the newly created notebook in the top right there will be a kernel button - click kernel button
        c. Selevt the interpreter associated with .venv

------- To be continued
