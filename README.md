# Marketing Attribution Model Using Markov Chains

## Overview

This repository contains a Python implementation of a marketing attribution model based on Markov chains. The model provides a more comprehensive approach to marketing attribution by analyzing the entire customer journey instead of simply attributing conversions to the first or last touchpoint.

Unlike traditional attribution models used by platforms such as Google Analytics 4 or Google Ads, which often provide conflicting attribution data, this model offers valuable insights into how different marketing channels interact within your marketing mix.

## Key Features

1. **Complete Customer Journey Analysis**: Evaluates all interactions that lead to conversion, not just isolated touchpoints.

2. **Combined Attribution Approach**: Integrates three models:
   - Removal effect (what happens if a channel is removed)
   - First-touch attribution
   - A "balanced" method that combines both approaches in a 60/40 proportion (60% removal effect, 40% first-touch)
   
   This balanced approach is designed to give more weight to entry channels, which are traditionally undervalued in GA4.

3. **Convergence Testing**: Tests different numbers of iterations to determine when results stabilize, ensuring an optimal balance between accuracy and computation time.

4. **Clear Visualization**: Includes Sankey diagrams to intuitively show how users flow between different channels before converting.

## Requirements

- Python 3.x
- pandas
- numpy
- matplotlib
- plotly
- Google Colab (recommended for easy execution)

## Input Data Format

To use this model with your own data, you'll need a CSV file with the following columns:
- **path**: The sequence of channels in the customer journey, separated by a delimiter (default is ' > ')
- **conversions**: The number of conversions for each path

Example:
```
path,conversions
Organic > Direct > Email,120
Direct > Social > Email,85
Paid Search > Email,105
```

## How to Use

1. **Setup in Google Colab**:
   - Open the notebook in Google Colab
   - Upload your CSV file or use the provided sample data
   - Run the cells in order

2. **Configure Parameters**:
   - Set the number of iterations to test (default: [100000, 150000, 175000, 200000, 225000])
   - Choose the attribution method (default: 'balanced')
   - Set the minimum attribution threshold (default: 0.001)

3. **Analyze Results**:
   - Review the generated Sankey diagram showing channel flow
   - Examine comparison charts for execution time, conversion probability, and attribution stability
   - Check the attribution tables for each number of iterations

4. **Download Results**:
   - Use the provided functions to download results to your computer
   - Results include HTML visualizations, PNG charts, and CSV data files

## Implementation Details

The model works through several key steps:

1. **Data Loading and Processing**: Loads the journey data and creates a transition matrix
2. **Simulation**: Uses Monte Carlo simulation to estimate conversion probabilities
3. **Attribution Calculation**: Computes attribution values using different methods
4. **Sensitivity Analysis**: Tests different iteration counts to ensure stability
5. **Visualization**: Generates Sankey chart and diagrams to show sensibility

## Performance Notes

The model has been tested with up to 16 different channels, taking approximately 45 minutes to run the complete analysis. With fewer channels, fewer iterations may be sufficient.

It's recommended to start with lower iteration sequences and gradually increase them to find the optimal convergence point for your specific data.

## Files in this Repository

- `markov_attribution.ipynb`: The main Google Colab notebook with the implementation
- `markov-chains-marketing-attribution-model.ipynb`: complete model to use in Jupyter.
- `sample_data.csv`: Sample data file for testing the model

## Limitations

While this model provides valuable insights, it's not a complete replacement for Media Mix Models (MMM), especially for cross-platform attribution. It works with the path data already collected by tools like GA4, but offers a more nuanced understanding of channel interactions and contributions.

## Output files

The model generates several outputs:

1. **Sankey Diagram**: Shows how users flow between channels
2. **Comparison Charts**: 
   - Execution time vs. iterations
   - Conversion probability vs. iterations
   - Number of channels with non-zero attribution vs. iterations
   - Percentage difference between consecutive iteration counts
3. **Attribution Tables**: Shows the participation of the different channels in the conversion, the removal effect and first touch attribution.

## Contact

mnavas@myriamnavas.com

---

*This model was developed to provide a more comprehensive approach to marketing attribution, use it wisely and at your own discretion.*
