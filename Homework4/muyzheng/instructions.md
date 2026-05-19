# ECS 273: Visual Analytics | UC Davis | Spring 2026
## Homework 4: Make it full-stack

**Due: May 21, 2026**

---

## Overview

In Homework 3, you built an interactive frontend visualization system using React and D3. In Homework 4, you will extend that system into a full-stack web application. You can check the slides and examples provided in Coding Workshop #2.

Instead of reading stock data directly from frontend files, your application should now:

1. Import stock data into MongoDB.
2. Build backend API endpoints using FastAPI.
3. Fetch data from the backend in your React frontend.
4. Preserve the main visualizations from Homework 3.

---

## Data Requirements

Place your stock-related data inside: `server/data/`

The data should be the same data used in Homework 3:

```
data/
├── stockdata/   (results from Homework 1 Task 1, for the past 2 years.)
│   ├── CAT.csv
│   ├── CVX.csv
│   └── ...
├── stocknews/   (results from Homework 1 Task 2)
│   ├── AAPL/
│   ├── NVDA/
│   └── ...
└── tsne.csv
```

We have already put some of them for testing, but you should replace all of them with the data you retrieved from Homework 1 and 2.

> **5 points will be deducted if the folder structure is not followed.**

---

## Tasks and Grading

### 1. Database Design and Data Import [35 pts]

You will use MongoDB to store your stock data. Before running your backend, make sure your local MongoDB server is running.

Name your database: `stock_<abbr_of_your_name>`. This helps avoid database name conflicts during grading.

#### Requirements

You should design MongoDB collections for:

1. Stock price time-series data
2. Stock news data
3. t-SNE projection data

You may use the example schemas in `server/data_scheme.py`, or define your own.

#### Stock Price Data

You may store stock price data in either format:

1. Arrays for each attribute
2. Array of Records

Either format is acceptable.

#### News Data

Do not create one collection per stock. Instead, store all news articles in a single collection. To retrieve news related to a specific stock, use a filter on a designated key – such as `Stock` in the sample schema. This structure is more efficient for querying and indexing, especially as the number of stocks and articles grows.

#### t-SNE Data

Each row should represent one stock.

#### Expected Files

You should complete or modify: `server/data_scheme.py` and `server/import_data.py`

---

### 2. API Design [40 pts]

You will implement backend API endpoints using FastAPI. You may build on the examples in: `server/main.py`.

#### Requirements

Your API should:

- Retrieve data from MongoDB, not directly from CSV files.
- Return JSON responses.
- Handle invalid ticker symbols gracefully.
- Include clear endpoint names.
- Allow the frontend to request data dynamically.

---

### 3. Connect Frontend and Backend [25 pts]

Your React frontend should now fetch data from your FastAPI backend. The frontend should preserve the main Homework 3 visualizations:

1. Stock overview line chart
2. t-SNE scatter plot
3. News list

#### Requirements

The dropdown menu should fetch the stock list from the backend. When a stock is selected:

- The line chart should update using data from your stock ticker endpoint.
- The t-SNE plot should highlight the selected stock.
- The news list should update using data from your news ticker endpoint.

Your frontend should no longer rely only on local static CSV or JSON files.

---

## README Requirement

Include a `README.md` file explaining:

1. How to install dependencies for the client.
2. How to install dependencies for the server.
3. How to start MongoDB.
4. How to import the data.
5. How to run the FastAPI backend.
6. How to run the React frontend.
7. Any assumptions or known issues.