# Data Analytics (CS301) Lab 5 Assignment

## On Vaccines

**Assigned** : Monday 20 March 2023

**Due** : Monday 27 March 2023

![logo](graphics/byYear.png)

Figure 1: A grouping the counts of infections by year. The code for this plot is provided in this lab.

## Objectives

To enhance the understanding of the exploratory data analysis while practicing skills of data trans- formation. To investigate the issues of ethics, privilege and inequality surrounding vaccine refusal.

## Reading Assignment

Please read Chapters 3 and 5 in the course book, corresponding to Chapters 5 and 7 in the website (online) version of the book. You may be required to look up the syntax of coding to prepare types of plots as you go through this lab.

## Exploratory Data Analysis On Vaccines

Vaccines have helped save millions of lives. In the 19th century, before herd immunization was achieved through vaccination programs, deaths from infectious diseases, like smallpox and polio, were common. However, today, despite all the scientific evidence for their importance, vaccination programs have become somewhat controversial.

The controversy started with a paper published in 1988 and lead by Andrew Wakefield claiming there was a link between the administration of the measles, mumps and rubella (MMR) vaccine, and the appearance of autism and bowel disease. Despite much science contradicting this finding, sensationalistic media reporting and fear mongering from conspiracy theorists, led parts of the public to believe that vaccines were harmful. Some parents stopped vaccinating their children as a result of wide-felt fear. However, the Center for Disease Control (CDC) estimated that vaccinations prevented more than 21 million hospitalizations and 732,000 deaths among children born in the last 20 years. For more information on this, please see _Benefits from Immunization during the Vaccines for Children Program Era United States_, 1994-2013, [MMWR](https://www.cdc.gov/mmwr/preview/mmwrhtml/mm6316a4.htm).
Effective communication of data is a strong antidote to misinformation and fear mongering. In this lab you are going to prepare a report to have ready in case you need to help a family member, friend or acquaintance that is not aware of the positive impact vaccines have had for public health.
The data used for these plots were collected, organized and distributed by the [Tycho Project](www.tycho.pitt.edu). To find more about this dataset, load the its library, view the data and read the code book using the below commands.

``` r
install.packages("dslabs")
library(dslabs)
?us_contagious_diseases
View(us_contagious_diseases)
```

 group who's weekly reported counts data for seven diseases from 1928 to 2011, from all fifty states. We include the yearly totals in the dslabs package:

---

## Part 1. Steps to Follow

1. Begin with the above code block to install the libraries.
    + a. Describe this dataset; What types of data does it contain?
    + b. Name two types of questions can you expect to answer using this dataset?
2. Create a dataset called dat by assigning it to the `us_contagious_diseases` dataset. You should now see this variable, `dat`, pop-up in your Global Environment section of RStudio.
3. Create another dataset from dat called `dat_measles_rate` which is created using the the following criteria.
    + a. This new dataset contains rows concerning only Measles data. Hint: use `filter()` on the dataset, `dat`.
    + b. Add a new column to this dataset called `rate` using the `mutate()` function. To create your `rate` variable, you are invited to use the below equation which combines several other variables together, however you may decide to create your own `rate` variable. If you think of a new rate to try in your analysis, please feel free to try it and be sure to discuss it in your lab deliverable.

        + $rate = \frac{C*52}{Wr} / \frac{P}{100000}$, for 

        + $Wr = weeks\_reporting$

        + $C = count$

        + $P = population$
      
    + c. What kind of data is contained in the created rate column?
    + d. In terms of its informational content, how could this column be useful in an analysis?

4. Because they became states recently, remove the two states (_Alaska_ and _Hawaii_) from your dataset. For this, create a variable for a new dataset called, `dat_measles_rate_lessTwoStates` from the `dat_measles_rate` dataset. The new dataset will not have rows pertaining to the two states. For this step, use the `filter()` function to remove _Alaska_ and _Hawaii_.

5. Preparing and studying results from plots.
  + a. Prepare a plot of the dat `measles_rate_lessTwoStates` dataset that relates the data of 48 states by editing the below code. Set your _x_ and _y_ variables to `year` and `rate`, respectively. Be sure to add a relevant title to the code where appropriate. A hint for the syntax of your code is provided below.

``` r
ggplot(data = dat_measles_rate_lessTwoStates,
  mapping = aes(
    x = ADD_VARIABLE_HERE, 
    y = ADD_VARIABLE_HERE, color = year)) +
    geom_point() +
    geom_vline(xintercept = 1963, color = "red") +
    labs(y = "ADD A TITLE")
```

  + b. Describe this plot; What information does it contain? Is there any evidence of a pattern that you see? Explain.
  + c. What is significant about the red vertical line? (You may have to go online to search for this answer.)

6. Create a new dataset from dat measles rate lessTwoStates, called dat caliFocus in which California is the __only__ state present in the data.

7. More on plots
  + a. Prepare a plot of this dataset where _x_ is the `year` and _y_ is the `rate`. Hint, modify the given plotting code from above to make a plot for `dat_caliFocus`.  
  + b. In clear and meaningful language, interrupt your results from the plot.
  + c. Compare this plot to the one that you made earlier. Could California be used to represent the rest of the country in terms of general and similar patterns? Why or why not? What are these patterns?
  + d. Describe what both of these plots are showing. Why is the analysis that you have just completed so revolutionary in medical science?

---

## Part 2. Writing About Ethics

Please write your reflections in markdown. Please save your work in the file, `writing/discussion.md`.

* In the `reading/` directory of your project repository, there is any article to read; _Journal Retracts 1998 Paper Linking Autism to Vaccines_, By Gardiner Harris. Please read the article and address the reflection questions in your `writing/reflection.md` work file.

# Important Details

All of your R code should be executable without errors. All writing to address questions is to be added to the `writing/reflection.md` document.
Note: Please remember to include your name on everything you submit for the class.

---

### Required Deliverables

* A complete and executable source code in File, `src/code.r`. Your instructor should be able to run the file without additional editing.

* Complete the `reflections.md` text file with your responses to the questions from the Parts described above.

### Checks for GatorGrader

For immediate feedback on submissions, we will be using Gator Grade to inform the of missing components in the submission. As you submit, you will notice that there is a thick red X that will change to a green check mark when all components have been included in the submission. You are encouraged to click on the red X to find a listing of the components to address.

## Project Assessment

The grade that a student receives on this assignment will have the following components.

- **GitHub Actions CI Build Status [up to 15%]:**: For the lab01 repository associated with this assignment students will receive a checkmark grade if their last before-the-deadline build passes. This is only checking some baseline writing and commit requirements as well as correct running of the program. An additional reduction will given if the commit log shows a cluster of commits at the end clearly used just to pass this requirement. An addition reduction will also be given if there is no commit during lab work times. All other requirements are evaluated manually.

- **Mastery of Technical Writing [up to 85%]:**: Students will also receive a checkmark grade when the responses to the writing questions presented in the `reflection.md` reveal a proficiency of both writing skills and technical knowledge. To receive a checkmark grade, the submitted writing should have correct spelling, grammar, and punctuation in addition to following the rules of Markdown and providing conceptually and technically accurate answers.

## GatorGrade

You can check the baseline writing and commit requirements for this lab assignment by running department's assignment checking `gatorgrade` tool. To use `gatorgrade`, you first need to make sure you have Python3 installed (type `python --version` to check). If you do not have Python installed, please see:

- [Setting Up Python on Windows](https://realpython.com/lessons/python-windows-setup/)
- [Python 3 Installation and Setup Guide](https://realpython.com/installing-python/)
- [How to Install Python 3 and Set Up a Local Programming Environment on Windows 10](https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-local-programming-environment-on-windows-10)

Then, if you have not done so already, you need to install `gatorgrade`:

- First, [install `pipx`](https://pypa.github.io/pipx/installation/)
- Then, install `gatorgrade` with `pipx install gatorgrade`

Finally, you can run `gatorgrade`:

`gatorgrade --config config/gatorgrade.yml`

## Submitting Your Work

Use GitHub to submit your work. The commands are the following.

```
git add -A
git commit -m "add meaningful commit message"
git push
```

## Seeking Assistance

* Extra resources for using markdown include;
  + [Markdown Tidbits](https://www.youtube.com/watch?v=cdJEUAy5IyA)
  + [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
* Do not forget to use the above git commands to push your work to the cloud for the instructor to grade your assignment. You can go to your GitHub repository using your browser to verify that your files have been submitted. Please see the TL’s or the instructor if you have any questions about assignment submission.

Students who have questions about this project outside of the lab time are invited to ask them in the course's Discord channel or during instructor's or TL's office hours.
