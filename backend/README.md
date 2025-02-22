# Backend - Full Stack Trivia API 

### Installing Dependencies for the Backend

1. **Python 3.7** - Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)


2. **Virtual Enviornment** - We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized. Instructions for setting up a virual enviornment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)


3. **PIP Dependencies** - Once you have your virtual environment setup and running, install dependencies by naviging to the `/backend` directory and running:
```bash
pip install -r requirements.txt
```
This will install all of the required packages we selected within the `requirements.txt` file.


4. **Key Dependencies**
 - [Flask](http://flask.pocoo.org/)  is a lightweight backend microservices framework. Flask is required to handle requests and responses.

 - [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py. 

 - [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests from our frontend server. 

### Database Setup
With Postgres running, restore a database using the trivia.psql file provided. From the backend folder in terminal run:
```bash
psql trivia < trivia.psql
```

### Running the server

From within the `./src` directory first ensure you are working using your created virtual environment.

To run the server, execute:

```bash
flask run --reload
```

The `--reload` flag will detect file changes and restart the server automatically.

## ToDo Tasks
These are the files you'd want to edit in the backend:

1. *./backend/flaskr/`__init__.py`*
2. *./backend/test_flaskr.py*


One note before you delve into your tasks: for each endpoint, you are expected to define the endpoint and response data. The frontend will be a plentiful resource because it is set up to expect certain endpoints and response data formats already. You should feel free to specify endpoints in your own way; if you do so, make sure to update the frontend or you will get some unexpected behavior. 

1. Use Flask-CORS to enable cross-domain requests and set response headers. 


2. Create an endpoint to handle GET requests for questions, including pagination (every 10 questions). This endpoint should return a list of questions, number of total questions, current category, categories. 


3. Create an endpoint to handle GET requests for all available categories. 


4. Create an endpoint to DELETE question using a question ID. 


5. Create an endpoint to POST a new question, which will require the question and answer text, category, and difficulty score. 


6. Create a POST endpoint to get questions based on category. 


7. Create a POST endpoint to get questions based on a search term. It should return any questions for whom the search term is a substring of the question. 


8. Create a POST endpoint to get questions to play the quiz. This endpoint should take category and previous question parameters and return a random questions within the given category, if provided, and that is not one of the previous questions. 


9. Create error handlers for all expected errors including 400, 404, 422 and 500. 



## Review Comment to the Students
```
This README is missing documentation of your endpoints. Below is an example for your endpoint to get all categories. Please use it as a reference for creating your documentation and resubmit your code. 

Endpoints
GET '/api/v1.0/categories'
GET ...
POST ...
DELETE ...

GET '/api/v1.0/categories'
- Fetches a dictionary of categories in which the keys are the ids and the value is the corresponding string of the category
- Request Arguments: None
- Returns: An object with a single key, categories, that contains a object of id: category_string key:value pairs. 
{'1' : "Science",
'2' : "Art",
'3' : "Geography",
'4' : "History",
'5' : "Entertainment",
'6' : "Sports"}

```


### GET '/categories'
```js
- Fetches a dictionary of categories in which the keys are the ids and the value is the corresponding string of the category
- Request Parameters: None
- Response Body:
  `categories`: object that contains all categories stored in database. 
{
    'categories': { '1' : "Science",
    '2' : "Art",
    '3' : "Geography",
    '4' : "History",
    '5' : "Entertainment",
    '6' : "Sports",
    '7' : "Literature",
    '8' : "Culture" }
}
```


### GET '/questions?page=1'
```js
- Fetches a paginated set of questions, a total number of questions, all categories and current category string. 
- Request Parameters: `page` : page number according to number of questions set per page and all questions store in database
- Response Body:
  `questions`: List of maximum 10 questions
  `total_questions`: number of all questions stored in database 
  `categories`: all categories stored in database
{
    'questions': [
      {
        "answer": "Apollo 13",
        "category": 5,
        "difficulty": 4,
        "id": 2,
        "question": "What movie earned Tom Hanks his third straight Oscar nomination, in 1996?"
      },
      {
        "answer": "Tom Cruise",
        "category": 5,
        "difficulty": 4,
        "id": 4,
        "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
      },
    ],
    'total_questions' : 100,
    'categories': { '1' : "Science",
    '2' : "Art",
    '3' : "Geography",
    '4' : "History",
    '5' : "Entertainment",
    '6' : "Sports",
    '7' : "Literature",
    '8' : "Culture" }
}
```

### GET '/categories/4/questions'
```js
- Fetches questions for a cateogry specified by id request parameter 
- Request Parameters: `id` : id of the category for which the questions are displayed
- Response Body:
  `current_category`: current category
  `questions`: all questions stored in database related to the current category
  `total_questions`: number of all questions stored in database related to the current category
{
  "current_category": {
    "id": 4,
    "type": "History"
  },
  "questions": [
    {
      "answer": "Maya Angelou",
      "category": 4,
      "difficulty": 2,
      "id": 5,
      "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
    },
    {
      "answer": "Muhammad Ali",
      "category": 4,
      "difficulty": 1,
      "id": 9,
      "question": "What boxer's original name is Cassius Clay?"
    },
  ],
  "total_questions": 5
}
```

### DELETE '/questions/5'
```js
- Deletes a specified question using the id of the question
- Request Parameters: id - id of the question to delete
- Response Body: 
  `question_deleted`: id of deleted question
  `total_questions`: number of remaining questions
{
  "question_deleted": 5,
  "total_questions": 22
}
```

### POST '/questions'
```js
- Create new question added to database
- Request Body:
  `answer`: answer statement
  `category`: category ID
  `difficulty`: difficulty level
  `question`: question statement
- Response Body: 
  `question_created`: object contains the new created Question
{
  "question_created": {
    "answer": "Joe Biden",
    "category": 4,
    "difficulty": 1,
    "id": 29,
    "question": "Who is the actual president of United States?"
  }
}
```

### POST '/questions'
```js
- Fetches questions based on `search term`
- Request Body:
  `search_term`: search term
- Response Body: 
  `questions`: object contains all questions found in database related to search term
{
  "questions": [
    {
      "answer": "George Washington Carver",
      "category": 4,
      "difficulty": 2,
      "id": 12,
      "question": "Who invented Peanut Butter?"
    },
    {
      "answer": "Alexander Fleming",
      "category": 1,
      "difficulty": 3,
      "id": 21,
      "question": "Who discovered penicillin?"
    },
  ],
  "total_questions": 5
}
```

### POST '/categories'
```js
- Create new category added to database
- Request Body:
  `type`: type of category statement
- Response Body: 
  `category_created`: object contains the new created Category
{
  "category_created": {
    "id": 9,
    "type": "Restauration"
  }
}
```

### POST '/quizzes'
```js
- Sends a post request in order to get the next question 
- Request Body: 
  `previous_questions`:  an array of question id's such as [1, 5] of previous questions answered
  `quiz_category`: object contains actual category's `type` and `id` selected for quiz
- Response Body:
  `question`: single new question object returned
{
  "question": {
    "answer": "George Washington Carver",
    "category": 4,
    "difficulty": 2,
    "id": 12,
    "question": "Who invented Peanut Butter?"
  }
}
```


## Testing
To run the tests, run
```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```

## Deployment N/A

## Authors
Udacity Team - Udacity's Student: MPOUDI André 

## Acknowledgements 
The awesome team at Udacity and all of the students, soon to be full stack extraordinaires! 