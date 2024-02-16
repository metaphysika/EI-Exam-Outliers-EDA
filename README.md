# EI-Exam-Outliers-EDA

Exploratory Data Analysis with high dose outlier radiological exams data

[Link](https://pixelhero.com/exposure-index-outliers/) to blog post about case.

NOTE: I am not uploading the actual data or jupyter notebook for protected patient data concerns.

# Problem

In radiology, patient safety is paramount. One challenge we've faced is the presence of outlier high Exposure Index (EI) exams, often indicative of improper techniques or technological errors, leading to unnecessarily high radiation doses for patients. A prominent issue was the detection and rectification of these outliers, which are not only a safety concern but also a quality control metric in our imaging processes.

# Action

To tackle this, I delved into the data using Jupyter Notebook, armed with Python and its powerful libraries for data manipulation and visualization. My EDA process involved:

- Importing and cleaning the data from radiological exams.

- Using statistical methods to identify outliers in EI values.

- Conducting a thorough investigation into extreme outliers.

The data set I worked with was challenging as it was scraped from emails sent out from our dose database alert system.

The data had a lot of extra "\n\n" characters in multiple columns and at the beginning, middle, and end of items in each cell.

![1](https://github.com/metaphysika/EI-Exam-Outliers-EDA/blob/main/images/1.png)

I could see there was a potential problem with display name, accession numbers, and OpenREM Link because they had some null values. I found it was due to some columns where the scraping didn't always work properly, and it joined the data from the adjacent column. 

![2](https://github.com/metaphysika/EI-Exam-Outliers-EDA/blob/main/images/2.png)

In this screenshot, you can see that the Display\nname is concatenated with the institution name and the actual display name column has a NaN value.

![3](https://github.com/metaphysika/EI-Exam-Outliers-EDA/blob/main/images/3.png)

To fix this, I copied the institution name to the display name column wherever there was NaN values in the display name column.

![4](https://github.com/metaphysika/EI-Exam-Outliers-EDA/blob/main/images/4.png)

I then split the strings in each column, keeping the section I needed for each and cleaned out the \n values.

![5](https://github.com/metaphysika/EI-Exam-Outliers-EDA/blob/main/images/5.png)

I had some similar cleaning to do with the accession and OpenREM Link columns, and then finally removing all the extra \n values from all columns. I was then left with a clean set of data that was ready for analysis.

![6](https://github.com/metaphysika/EI-Exam-Outliers-EDA/blob/main/images/6.png)

The analysis was comprehensive, with meticulous attention to detail in cleaning the data, calculating z-scores, and visualizing the data to pinpoint the anomalies.

I first looked at the top 10 outliers. I saw there were a few very high EI/z-score values that didn't seem realistic. I looked up the exam in PACS to find out they were service images from testing equipment. I dropped those values and continued with the analysis.

I then looked at how many items fell outside a z-score of 3. I found 26 that did so and wrote these out to an excel sheet to follow up with individually. 

![7](https://github.com/metaphysika/EI-Exam-Outliers-EDA/blob/main/images/7.png)

Lastly, I created some charts of the exams that had a z-score of range 1-2 and 2-3. These are also high exams that I wanted to identify any larger patterns for to see if there was room for improvement at specific imaging sites.

![8](https://github.com/metaphysika/EI-Exam-Outliers-EDA/blob/main/images/8.png)

# Results

The results were telling. At one particular site, I discovered that incorrect techniques set for pelvis exams were causing high EI values. With this insight, we adjusted the techniques, and subsequent analyses showed a significant drop in EI values, bringing them back into a normal range.

I also could see from this data that intuitions from outside my organization that send studies to us for reading were contributing to the highest group of outlier EI exams. This provided us with data to approach these groups and ask them to review their practices.

Other internal outlier EI exam trends identified particular sites and staff members that needed some extra coaching to help establish better practices.

This case study underscores my adeptness at EDA, showcasing my capability to not only identify critical issues but also to pave the way for tangible improvements in medical imaging practices.
