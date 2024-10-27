
# Financial Data Analysis and Forecasting for MIGA

## Dataset Description
This dataset, `miga_summary_income_statement_26-10-2024.csv`, contains MIGA's financial income statement from 2012 to recent years. It includes data on various income and expense categories in millions of USD.

- **Organization**: The organization name which is MIGA in all 
- **Category**: Income or Expenses of MIGA
- **Line Item**: Specific description of the financial item
- **Fiscal Year**: The fiscal year of the record
- **Amount (US$, Millions)**: The amount in USD millions

## Summary of Findings
The dataset shows the incomes and expenses of MIGA through the years. Income sources, particularly "Investment Income" and "Net Premium Income," is consistent which implies that the revenue is stable. While the expense categories like "Administrative Expenses" and "Translation Loss" varies depending on the year which implies shifts in operational costs or currency impacts. Comparing both the income and expense shows that the organization is showing strong financial performance alongside periods with tighter margins, pointing to opportunities for strategic financial planning to optimize future outcomes. Finally, time-series forecasting suggests potential future trends, enabling MIGA to enhance budgetary decisions and resource allocation.

## Data Preprocessing
- Converted "Amount (US$, Millions)" to numeric data.
- Created a pivot table with fiscal years as rows and financial line items as columns for trend analysis.
- Checked for and addressed missing values.

## Exploratory Data Analysis
### Visualization
![alt](https://github.com/UnlimitedAvailableUsername/Revenue-or-Expense-Forecasting/blob/main/images/1.png)
1. **Income Trends** - The `plot_income_trends` function generates a line plot that visualizes income trends over time. It first selects columns related to income in `pivot_df`, then plots them with markers for each fiscal year to highlight trends. The function adds a title, axis labels, and positions the legend outside the plot for clarity.
![alt](https://github.com/UnlimitedAvailableUsername/Revenue-or-Expense-Forecasting/blob/main/images/2.png)
2. **Expense Trends** - The `plot_expense_trends` function creates a line plot to show trends in expenses over time. It first identifies income columns in `pivot_df` to separate out the expense columns, then plots only the expense data with markers to represent each fiscal year. The plot is labeled with a title, axis labels, and a legend positioned outside the plot area for clarity.
![alt](https://github.com/UnlimitedAvailableUsername/Revenue-or-Expense-Forecasting/blob/main/images/3.png)
3. **Net Premium Income Distribution** - The `plot_premium_distribution` function creates a box plot to visualize the distribution of "Net Premium Income" amounts. It filters the data in the dataset to select only rows where the "Line Item" is "Net Premium Income" and plots this using `sns.boxplot`. The plot is titled "Net Premium Income Distribution," and `tight_layout()` is used to ensure it fits well within the figure. This provides a concise summary of the range, median, and potential outliers in the "Net Premium Income" data.
![alt](https://github.com/UnlimitedAvailableUsername/Revenue-or-Expense-Forecasting/blob/main/images/4.png)
4. **Correlation Heatmap** - The `plot_correlation_heatmap` function takes a the daatset (`pivot_df`) as input and creates a heatmap to visualize the correlation matrix of its numerical columns. It uses `Matplotlib` to set the figure size and Seaborn to generate the heatmap, with annotations for correlation coefficients and a color palette ranging from cool to warm shades. The `center=0` argument centers the color map at zero, and `plt.tight_layout()` ensures that the layout is adjusted to prevent overlapping elements.
![alt](https://github.com/UnlimitedAvailableUsername/Revenue-or-Expense-Forecasting/blob/main/images/5.png)   
5. **Year over Year Growth in Total Financial activity** - The `plot_yearly_growth` function visualizes the year-over-year growth in total financial activity from the dataset. It first groups the data by 'Fiscal Year' and calculates the total amount for each year. Then, it computes the percentage change in total amounts from year to year using the `pct_change(`) method, multiplying by 100 to convert it into a percentage. The resulting growth rates are plotted as a bar chart, with appropriate titles and axis labels. The `plt.tight_layout()` adjusts the layout for better presentation.

## Model Development
1. **Prophet Model**:Used for time-series forecasting, this model is particularly effective in handling seasonal patterns and holidays based on historical income statement data.
2. **Linear Regression**: Developed as a baseline regression model, it assesses linear relationships between variables to predict outcomes.
3. **Random Forest Regressor**: This model captures potential non-linear relationships within the data, providing a more robust predictive performance compared to simpler models.
4. **Gradient Boosting**: This model technique builds strong predictive models by combining the predictions of multiple weak learners (decision trees), capturing complex patterns in the data.
   
## Model Evaluation
Each model's performance was evaluated using RMSE (Root Mean Squared Error) and R² (R-squared) to compare prediction accuracy.

1. **Prophet Model**: Generated future trend forecasts, with evaluation metrics focused on forecast accuracy.
2. **Linear Regression**: RMSE and R² scores evaluated against the test set.
3. **Random Forest**: Evaluated for better accuracy in non-linear trends.
4. **Gradient Boosting**: Capture complex relationships and compared against the performance of other models.

## Conclusion
These models shows the feasibility of using historical financial data to predict future financial performance. The insights from this analysis provide a valuable foundation for strategic financial decision-making. By accurately forecasting revenue trends and understanding key expense drivers, stakeholders are better equipped to anticipate future financial outcomes, allocate resources more effectively, and identify opportunities for growth or cost optimization. With the insights gained, the models can serve as a decision support tool, guiding organizations toward more informed and proactive financial strategies. Future improvements could include incorporating additional data sources and exploring alternative model architectures for enhanced accuracy.
