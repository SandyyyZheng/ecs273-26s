This is a straightforward markdown conversion, no need for the docx skill. Here it is:

---

## Data Requirements

In the `data` folder, there is a demo file (`demo.json`). In place of that, you will place your stock-related data **(20 stocks)** here. The structure should follow this organization:

```
data/
├── demo.json         (demo file; not used in final submission)
├── stockdata/        (results from HW1 Task 1, for the past 2 years.)
│   ├── CAT.csv
│   ├── CVX.csv
│   └── …
├── stocknews/        (results from HW1 Task 2)
│   ├── AAPL/
│   ├── NVDA/
│   └── …
└── tsne.csv          (stores the two-dimensional t-SNE projection of the latent representations from HW2. It has two columns, each representing one of the two-dimensional coordinates for each stock for the past two years.)
```

## Layout

The layout is defined in `App.tsx` (or `App.jsx` in the JS version), where we will use [Tailwind CSS](https://tailwindcss.com), a CSS framework that offers ready-to-use utility classes for styling and layout. You may customize your layout with CSS syntax, but it is not a requirement.

---

## Visualization Components (100 pts)

The template (Fig. 1) includes:
- A dropdown menu (stock selector)
- Three visualization panels

### Where to Add your Components

For each visualization view, create a separate component file inside: `src/component/`

Example:
```
src/
└── component/
    ├── LineChart.tsx   (or .jsx)
    ├── TSNEScatter.tsx (or .jsx)
    └── NewsList.tsx    (or .jsx)
```

### 1. Dropdown Menu (5 pts)

Replace the existing list in the drop-down menu with the 20 different stocks you queried in Homework 1.

- File to modify: `src/component/option`

### 2. Top left (View 1): Stock Overview Line Chart (35 pts)

I have placed an example demo bar chart view here, but it is not based on any of the data you will use for your submission!

Create a line chart that updates based on the selected stock from the drop-down menu, using the corresponding CSV file.

For example, if you select NVDA from the list, the chart should display the Open, High, Low, and Close values as four separate lines.

**Requirements:**
- A legend identifying each line.
- Properly labeled axes.
- Horizontal zooming.
- Horizontal scrolling when the time series is too long to fit in the visible area.

### 3. Bottom left (View 2): T-SNE Scatter Plot (35 pts)

Use the t-SNE coordinates generated from Homework 2 and visualize them in D3. Each point represents one stock. The `tsne.csv` file should come from your Homework 2 t-SNE result. It should contain one row per stock and include the stock ticker, two t-SNE coordinates, and the sector/category label.

**Requirements:**
- Color points by sector.
- Highlight selected stock:
  - Larger size
  - Show stock name
- A legend identifying each sector/color.
- Properly labeled axes.
- Zooming.

### 4. Right (View 3): List of News (25 pts)

Display a list of news for the selected stock.

**Requirements:**
- Show title and date.
- On click, it should expand to show full content.

---

## Bonus (Optional: +5 pts)

- Linking interactions between views:
  - Selecting a stock in the drop-down updates the Scatter plot in View 1, updates the Line Chart in View 2, and expands the corresponding news in View 3.
