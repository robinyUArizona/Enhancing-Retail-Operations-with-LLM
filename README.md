# Enhancing Retail Operations with LLM: A LangChain & Google PaLM Integration
### Problem Statement
AtliQ Tees is a t shirt store that sells Adidas, Nike, Van Heusen and Levi's t shirts . They maintain their inventory, sales and discounts data in MySQL database into 2 tables `t_shirts` and `discounts`. A store manager may have questions such as,
- How many white color Adidas t-shirts do we have left in the stock?
- How much sales our store will generate if we can sell all extra-small size t shirts after applying discounts?

### Solution
Built an LLM system based on Google Palm (PaLM2) within the Langchain framework that could interact with a MySQL database using the SQLDatabaseChain class. Users could ask questions in natural language, and the system generated answers by converting those questions into SQL queries and then executing those queries on the MySQL database.

To address the occasional failure of Google Palm LLM models in handling complex queries, the few-shot learning technique was employed.

Few-shot learning involved preparing a training dataset with sample questions and corresponding SQL queries. These training datasets were converted into embedding vectors using Hugging Face and stored in a vector database (ChromaDB). This setup was then paired with Google Palm LLM using a few-shot prompt template to create the SQL Database Chain. Finally, the UI was built using Streamlit.

**Tech Stack**: 
- Database: MySQL
- Embeddings: Hugging Face
- Vector Database: ChromaDB 
- LLM Framework: LangChain
- LLM: Google Palm LLM model 
- ML Framework: Few shot learning
- UI: Streamlit

### Overview of the project
![Project Overview](https://github.com/robinyUArizona/Enhancing-Retail-Operations-with-LLM/blob/main/Overview_project.jpg)


### Project Structure
- main.py: The main Streamlit application script.
- langchain_helper.py: This has all the langchain code
- requirements.txt: A list of required Python packages for the project.
- few_shots.py: Contains few shot prompts
- .env: Configuration file for storing your Google API key.



### Installation

1.Clone this repository to your local machine using:

```bash
  git clone https://github.com/robinyUArizona/Enhancing-Retail-Operations-with-LLM.git
```
2.Navigate to the project directory:

```bash
  cd Enhancing-Retail-Operations-with-LLM
```
3. Install the required dependencies using pip:

```bash
  pip install -r requirements.txt
```
4.Acquire an api key through makersuite.google.com and put it in .env file

```bash
  GOOGLE_API_KEY="your_api_key_here"
```
5. For database setup, run database/db_creation_atliq_t_shirts.sql in your MySQL workbench

## Usage

1. Run the Streamlit app by executing:
```bash
streamlit run main.py

```

2.The web app will open in your browser where you can ask questions

### Sample Questions
  - How many total t shirts are left in total in stock?
  - How many t-shirts do we have left for Nike in XS size and white color?
  - How much is the total price of the inventory for all S-size t-shirts?
  - How much sales amount will be generated if we sell all small size adidas shirts today after discounts?
  


### Outcome
![Alt text](https://github.com/robinyUArizona/Enhancing-Retail-Operations-with-LLM/blob/main/AtliQ_T_shirts.jpg)






