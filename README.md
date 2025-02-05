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

## Create and initialize project
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

## Create an initial title, header, and imports
    For this step the title and header will be in a markdown cell where the imports will be coded
    1. Within the wilcox_eda.ipynb notebook click the + Markdown button at the top of the window
    2. Add title and header
        Input:
        **Craig Wilcox: Exploratory Data Analysis Project**
        Purpose: Perform exploratory data analysis using tools in a Jupyter notebook
        Author: Craig Wilcox
        Date started: February 2 2025
    3. I created another markdown window and added the import names we would be using listed out
        This can be added to throughout the project
        Input:
        Imports required for this project
        1. pandas
        2. Iris Data set
    4. Click + Code button at the top of the window to create a python cell
    5. Insert code for import statements after inserting run the cell to check it runs properly and to import
        Insert:
        import pandas as pd
        import seaborn as sns
        import matplotlib
        print("Starting out with Jupyter.")
    6. Create another python cell to load data
        Insert:
        # Load the Iris dataset into pandas DataFrame
        iris_df: pd.DataFrame = sns.load_dataset('iris')

        # List column names
        iris_df.columns

        # Inspect first few rows of the DataFrame
        iris_df.head()
    7. At the top of the notebook window click Run All button and both python cell should run and populate a small graph

## Initial Data Inspection
Purpose is to take a look at the data to understand what we are working with and what in the future we can manipulate.
    1. Add another code cell and input below
        Insert:
        # Specify the number of rows to display
        iris_df.head(10)

        # Inspect the shape of the DataFrame with shape attribute
        # The shape is a tuple with count of rows and columns in the DataFrame
        iris_df.shape

        # Inspect the data types of the columns with dtypes attribute
        # The data types are returned as a pandas Series
        iris_df.dtypes

        # Inspect the data types of the columns with info() method
        iris_df.info()
    2. After running the results should display which will show 5 different columns or catagories with 150 data points in each of those columns

## Initial Descriptive statistics
    1. Add another code cell 
        input:
        # Inspect summary statistics for numerical columns
        iris_df.describe()
    2. After running the output should show count, mean, standard deviation, minimum, maximum, and quartiles
    3. There should be no errors in this data set but when used it can identify possible data integrity issues beyond that standard statiscical analysis.
## Initial Data Distribution for numerical and categorical columns
    1. Add a code cell
    2. For numerical columns input the following code to show histograms of all the columns
        # Inspect histograms for ALL numerical columns
        iris_df.hist()
        # Show all plots
        matplotlib.pyplot.show()
    3. Not used at this time but if you had only one column you wish to display below is an example
        # Inspect histogram by one numerical column
        iris_df['sepal_length'].hist()
    4. Add markdown cell to document observations
    5. Add another code cell for the categorical columns. The code below will show counts and display a graph of the counts
        # Inspect value counts by categorical column
        # Column name must be EXACT.
        # The value_counts() method is only available for Series objects.
        # The value_counts() method returns a pandas Series with the counts of unique values in the column.
        iris_df['species'].value_counts()
        # Inspect value counts for ALL categorical columns
        for col in iris_df.select_dtypes(include=['object', 'category']).columns:
            # Display count plot
            sns.countplot(x=col, data=iris_df)
            matplotlib.pyplot.title(f'Distribution of {col}')
            matplotlib.pyplot.show()
        # Show all plots
        matplotlib.pyplot.show()
    6. Add markdown cell to document initial observations
## Data Transformation and Feature Engineering
In this section there is an example of how you can change and manipulate the output of this data
    1. Create another code cell and input the following code
        # Feature Engineering
        # Renaming a column
        iris_df.rename(columns={'sepal_length': 'Sepal Length'}, inplace=True)
        # Adding a new column
        iris_df['Sepal Area'] = iris_df['Sepal Length'] * iris_df['sepal_width']
    2. This code will not display results for this cell when run as there is no input so add earlier code and see the difference in the graphs displayed
        # Inspect histograms for ALL numerical columns
        iris_df.hist()
        # Show all plots
        matplotlib.pyplot.show()
## Visualizations
This section will go through some exampls of visualization options
    1. Create new code cell and input below. This creates a grid of sctter plots for analysis
        # Feature Engineering
        # Renaming a column
        iris_df.rename(columns={'sepal_length': 'Sepal Length'}, inplace=True)

        # Adding a new column
        iris_df['Sepal Area'] = iris_df['Sepal Length'] * iris_df['sepal_width']

        # Create a pairplot of the Iris dataset
        # A pairplot is a grid of scatter plots for each pair of numerical columns in the dataset
        # The hue parameter is used to color the data points 
        # by species (a categorical column)
        sns.pairplot(iris_df, hue='species')

        # Show all plots
        matplotlib.pyplot.show()
    2. Create markdown cell to explain observations
    3. Create a new code cell and input code. this code adds another scatter plot based on specific parameters for more detail.
        # A scatter plot is a plot of two numerical variables.
        scatter_plt = sns.scatterplot(
            data=iris_df, x="Sepal Length", y="Sepal Area", hue="species")

        # Set axis labels using the Matplotlib Axes methods set_xlabel() and set_ylabel()
        scatter_plt.set_xlabel("Sepal Length (mm)")
        scatter_plt.set_ylabel("Sepal Area (mm squared)")   

        # Set the title using the Matplotlib Axes set_title() method
        scatter_plt.set_title("Chart 1. Iris Sepal Length vs. Sepal Area (by Species)")

        matplotlib.pyplot.show()
    4. Create markdown cell to explain observations
