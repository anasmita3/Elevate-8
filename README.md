# Elevate-8
<br>
✅ Summary of the Interactive Sales Dashboard Code (ipywidgets + Plotly)

This code creates a fully interactive sales performance dashboard inside a Jupyter notebook or Google Colab, using:

    📊 Plotly for interactive charts

    🎛️ ipywidgets for dropdown filters

    🧮 Pandas for data manipulation

🧩 Components and Logic
1. Library Installation

!pip -q install pandas plotly ipywidgets --upgrade

Installs the required libraries: pandas, plotly, and ipywidgets.
2. File Upload

from google.colab import files
uploaded = files.upload()

Prompts the user to upload a CSV file (like sales_data_sample.csv), typically used in Google Colab.
3. Data Preprocessing

df["ORDERDATE"] = pd.to_datetime(df["ORDERDATE"])
df["Month"] = df["ORDERDATE"].dt.to_period("M").astype(str)
df.rename(columns={...}, inplace=True)

    Converts order dates to datetime format

    Extracts the month as a separate column

    Renames key columns to: Product, Region, and Revenue

4. Interactive Filters

widgets.SelectMultiple(...)

Creates three dropdown widgets for filtering:

    Product

    Region (country)

    Month

User selections dynamically control the data shown in the dashboard.
5. Output Area

out = widgets.Output()

Defines a blank output container where KPI metrics and charts will be displayed.
6. Update Function

def update_dashboard(*_):
    ...

Triggered when any filter is changed. It:

    Filters the DataFrame based on selected values

    Computes:

        💰 Total Revenue

        📦 Total Orders

        💵 Average Order Value

    Displays 3 charts using Plotly:

        Revenue by Product (Bar chart)

        Revenue by Region (Bar chart)

        Monthly Revenue Trend (Line chart)

7. Event Binding

w.observe(update_dashboard, names="value")

Links all dropdown filters to the update_dashboard() function, so the dashboard updates automatically.
8. Initial Render

update_dashboard()

Draws the dashboard once initially (with default filter selections).
