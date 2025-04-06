# Markov Attribution Model
A robust Python implementation for marketing attribution analysis using Markov chains. This tool helps marketers understand the contribution of each channel in their customer journey by analyzing conversion paths and applying Markov-based attribution modeling.

**Overview**  
This repository contains a comprehensive solution for multi-channel attribution modeling, allowing marketers and analysts to:

* Understand the real impact of each marketing channel on conversions.  
* Visualize user journeys across different touchpoints.  
* Apply different attribution methodologies.  
* Compare results across various simulation parameters.  

# Features

**Core Functionality**

* Path Analysis: Process conversion paths from CSV data with customizable path separators.  
* Markov Chain Modeling: Build transition matrices representing user journey patterns.  
* Monte Carlo Simulation: Run configurable numbers of simulations to ensure statistical reliability.

**Multiple Attribution Methods:**

* Removal Effect: Measures the impact of removing a channel from the conversion path
* First-Touch: Weights attribution toward the channel that initiates customer journeys
* Balanced Method: Applies a weighted combination of attribution methods (default: 60% removal effect, 40% first-touch)

**Visualization & Analysis**

* Sankey Diagrams: Interactive flow visualizations showing user movements between channels.  
* Comparative Analysis: Automatically test multiple simulation iterations to find optimal settings.  
* Consistency Validation: Measure attribution stability across different numbers of simulations.  
* Performance Metrics: Track execution time and conversion probability at different simulation counts.  

**Output & Reporting**

* HTML Visualizations: Interactive Sankey diagrams for sharing with stakeholders.  
* CSV Exports: Detailed attribution data for further analysis.  
* Comparison Tables: See how attribution values change with different simulation parameters.  
* Summary Graphics: Visual representation of key metrics and findings.  


**Output Files**
The script generates several output files:

* output/sankey_markov.html: Interactive visualization of channel flows.  
* comparacion_iteraciones.png: Charts comparing metrics across different iteration counts.  
* comparacion_atribucion.csv: Table showing attribution values for top channels.  
* atribucion_completa_X_iter.csv: Complete attribution results for each iteration count.  

**How It Works**

Data Loading: Conversion paths are loaded from the CSV file.  
Transition Matrix Creation: A Markov chain transition matrix is built from the paths.  
Baseline Simulation: Monte Carlo simulations establish the baseline conversion probability.  
Channel Impact Analysis: For each channel, we measure conversion impact by:
* Removal effect: Removing the channel and measuring conversion drop.  
* First-touch impact: Measuring the channel's frequency as an entry point.  

Attribution Calculation: Values are normalized and combined according to the chosen method
Convergence Analysis: Multiple iteration counts are tested to ensure stable results
Output Generation: Results are saved as visualizations and data files

**Convergence Process**
A key aspect of this implementation is its rigorous approach to ensuring convergence and stability of the attribution results.  

The tool:
1. Executes Multiple Simulations: Runs the model with progressively increasing numbers of iterations (e.g., 100,000, 150,000, 175,000, 200,000, 225,000)
2. Measures Stability: Calculates the percentage difference in attribution values between consecutive iteration counts
3. Visualizes Convergence: Generates charts showing how key metrics change as iterations increase:
   * Attribution stability for top channels.  
   * Execution time scaling.  
   * Conversion probability convergence.  
   * Number of channels with non-zero attribution.  

**Provides Recommendations: **
Automatically analyzes differences between iteration counts and suggests the optimal number of iterations based on a balance between accuracy and computational efficiency

This convergence-focused methodology ensures that the attribution values are statistically reliable and not artifacts of insufficient sampling.  
The visualization tools allow analysts to clearly see at what point increasing iterations yields diminishing returns in terms of improved accuracy.

