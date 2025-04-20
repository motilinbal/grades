# Interactive Grade Distribution Analyzer & Simulator

## What is this?

Welcome! This tool helps you visualize and experiment with lists of grades (like from a class). You can paste your raw grades (including values below 0 or above 100), see how they are distributed, compare initial vs. current statistics, set a passing grade, and simulate what might happen if the average grade or the spread of grades were different using a linear transformation.

As you make changes to the target mean or standard deviation, the list of grades will update right in the text box, so you can easily copy the new list if you need it!

## Features

* **Paste Your Grades:** Copy a list of grades (one per line, numeric values) and paste them in. The tool accepts and analyzes grades exactly as entered.
* **See the Distribution:** Get a smooth graph showing how the currently displayed grades are spread out. The graph axis adjusts automatically to fit the grade range.
* **Compare Statistics:** View the statistics (Count, Mean, Standard Deviation, Min, Max) of your *initial raw input* grades side-by-side with the statistics of the *currently displayed* grades after transformations.
* **Set a Passing Grade:** Use a slider or type in the grade required to pass to visualize the impact on the current distribution.
* **Visualize Passing/Failing:**
    * See exactly how many students are below the passing grade in the current distribution.
    * The graph clearly highlights the area representing failing grades.
    * A line on the graph shows the exact passing cutoff.
* **Track Key Metrics:** Instantly see counts based on the *currently displayed* grades:
    * Number of grades currently **above 100**.
    * Number of students **failing** (below the threshold).
    * Number of grades **reduced** compared to their original input value, along with the **average decrease** for those grades.
* **Experiment with Average & Spread:**
    * The tool calculates the average (mean) and spread (standard deviation) of your initial *raw* grades.
    * Use sliders or type in new *target* values for the mean and standard deviation.
    * See how the grade distribution graph changes based on a **linear transformation** (detailed below). This transformation can result in grades outside the 0-100 range.
* **Instant Updates:**
    * The graph, current statistics, and counts change instantly when you adjust the target mean, standard deviation, or passing threshold.
    * The grades listed in the text box update immediately based on the target mean/SD adjustments.

## A Little Bit About the Math (How Transformations Work)

Wondering how the tool adjusts grades when you change the target mean or standard deviation? It uses a standard statistical method involving **normalization** (calculating Z-scores from your raw input) and then applying a **linear transformation**.

1.  **Calculate Initial Stats:** First, it calculates the original average ($\mu_{orig}$) and original standard deviation ($\sigma_{orig}$) directly from the **raw grades** you pasted.
2.  **Normalization (Z-scores):** It then converts every single original grade ($g_{orig}$) into a "Z-score". This score tells us how many standard deviations away from the original raw average each grade was:
    $Z = \frac{g_{orig} - \mu_{orig}}{\sigma_{orig}}$
    (If $\sigma_{orig}$ is 0, all Z-scores are treated as 0). This normalized list, based on your raw input's relative positions, is stored internally as a reference.
3.  **Linear Transformation:** When you adjust the sliders to a *new target* mean ($\mu_{target}$) and *new target* spread ($\sigma_{target}$), the tool applies these directly to the stored Z-scores to calculate the grades displayed on screen ($g_{displayed}$):
    $g_{displayed} = (Z \times \sigma_{target}) + \mu_{target}$

This process transforms the grades according to your desired target average and spread, based on the original relative distribution. **Importantly, this linear transformation does not impose 0-100 bounds**, so the resulting `displayedGrades` can be less than 0 or greater than 100. This is reflected in the "Current Statistics" and the "Number Above 100" count.

## How to Use

1.  **Visit the Webpage:** Navigate to the application's URL [https://motilinbal.github.io/grades/](https://motilinbal.github.io/grades/).
2.  **Paste Grades:** Copy your list of numeric grades (remember, one grade on each line) and paste them into the text box.
3.  **Analyze:** Click the "Analyze Grades" button.
    * You'll see statistics calculated from your *raw input grades* in the "Initial Statistics" column. The "Current Statistics" column will initially mirror these stats.
    * The graph showing your initial grade distribution will appear.
    * You'll see the initial counts for failing students, grades above 100 (if any), and reduced grades (initially 0), based on your raw input.
    * The text box will show your input grades (formatted to one decimal place).
4.  **Adjust Passing Grade:** Use the "Failing Threshold" slider or type in a number to set the grade needed to pass. Watch the graph's highlighted area and the failing count change instantly based on the currently displayed grades.
5.  **Experiment!** Play with the "Target Mean" (average) and "Target Standard Deviation" (spread) sliders or boxes.
    * See how the graph shifts and reshapes based on the linear transformation.
    * Observe the "Current Statistics" column updating to reflect the transformed grades.
    * Notice how the counts for failing, above 100, and reduced grades change based on the transformed grades.
    * Check the text box – the grades listed there have changed based on your simulation! Feel free to copy them.