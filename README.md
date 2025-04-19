# Interactive Grade Distribution Analyzer & Simulator

## What is this?

Welcome! This tool helps you visualize and play around with lists of grades (like from a class). You can paste your grades (from 0 to 100), see how they are distributed, set a passing grade, and even see what might happen if the average grade or the spread of grades were different.

As you make changes, the list of grades will update right in the text box, so you can easily copy the new list if you need it!

## Features

* **Paste Your Grades:** Just copy a list of grades (one per line) and paste them in.
* **See the Distribution:** Get a smooth graph showing how the grades are spread out.
* **Set a Passing Grade:** Use a slider or type in the grade required to pass (0-100).
* **Visualize Passing/Failing:**
    * See exactly how many students are below the passing grade.
    * The graph clearly highlights the area representing failing grades.
    * A line on the graph shows the exact passing cutoff.
* **Experiment with Average & Spread:**
    * The tool calculates the average (mean) and spread (standard deviation) of your grades.
    * Use sliders or type in new values to see how the grade distribution graph changes.
* **Instant Updates:**
    * The graph changes instantly when you adjust the passing grade, average, or spread.
    * The number of failing students updates right away.
    * **The grades in the text box update automatically** to show the results of your adjustments. You can copy this new list!

## A Little Bit About the Math (How Transformations Work)

Ever wonder how the tool adjusts the grades when you change the mean (average) or standard deviation (spread) sliders? It uses a standard method called **normalization** (specifically, calculating Z-scores) behind the scenes.

1.  **Centering:** First, it calculates the original average ($\mu$) of the grades you pasted. It then subtracts this average from every single grade ($g_{original} - \mu$). This step shifts all grades so the new average is zero.
2.  **Scaling:** Next, it calculates the original spread ($\sigma$, standard deviation) of your grades. It divides the shifted grades from step 1 by this spread ($\frac{g_{original} - \mu}{\sigma}$). This rescales the grades, telling us how many 'standard spread units' each grade was away from the original average. The result is a "normalized" grade list with an average of 0 and a spread of 1.

**Why do this?** This normalized list acts like a blueprint of your original grades' relative positions. When you adjust the sliders to a *new* mean ($\mu_{new}$) and *new* spread ($\sigma_{new}$), the tool applies these to the blueprint:

$g_{displayed} = (\text{normalized grade} \times \sigma_{new}) + \mu_{new}$

This process accurately transforms the grades according to your desired new average and spread, updating the graph and the grade list you see in the text box.

## How to Use

1.  **Visit the Webpage:** Navigate to the application's URL (https://motilinbal.github.io/grades/).
2.  **Paste Grades:** Copy your list of grades (remember, one grade on each line) and paste them into the text box.
3.  **Analyze:** Click the "Analyze Grades" button.
    * You'll see the calculated average and spread appear on the sliders.
    * The graph showing your grade distribution will pop up.
    * You'll see the count of failing students based on the initial passing grade (usually 60).
4.  **Adjust Passing Grade:** Use the "Failing Threshold" slider or type in a number to set the grade needed to pass. Watch the graph and the failing count change.
5.  **Experiment!** Play with the "Mean" (average) and "Standard Deviation" (spread) sliders or boxes.
    * See how the graph shifts and reshapes.
    * Notice how the failing count changes based on your adjustments.
    * Check the text box – the grades listed there have changed based on your simulation! Feel free to copy them.

