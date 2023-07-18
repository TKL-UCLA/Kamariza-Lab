# Kamariza-Lab
# TKL-UCLA-Scripts-Plate-Reader #

for thorough walkthrough watch this youtube video
- https://youtu.be/Aevvbb6DXcQ
- https://youtu.be/7CVXwPNjW7U
      
### **Introduction** ###

Automated graphing file (jupyter notebook) to streamline graphing plate reader data (OD and fluorescence)

## **Materials**

- Software
    - Software to run jupyter notebook file
    - Examples include (but not exclusive to):
    - Visual Studio (https://code.visualstudio.com/) -- My favorite
    - Anaconda (https://www.anaconda.com/download)
    - Jupyter Notebook (https://jupyter.org/)
- Files
    - Plate Reader Layout (file path)
    - Plate Reader Data (OD or Fluorescence) (file path)
    - Jupyter Notebook File

## **Procedure**

- Download and Set-up Jupyter Notebook

1. Download any software to run Jupyter Notebook files

- For Help Watch These Videos
- (these videos are for installing anaconda and running jupyter notebook)
- https://www.youtube.com/watch?v=XCvgyvBFjyM
- https://www.youtube.com/watch?v=6kXLUvsnhuI
- https://www.youtube.com/watch?v=sv0ca-6liM8
- https://www.youtube.com/watch?v=Fw6VYgsbJ4o

2. Set up and enter the virtual environment

- For Help Watch This Video
- (video uses anaconda)
- https://www.youtube.com/watch?v=mIB7IZFCE_k

3. Download Jupyter Notebook File

- Access this file from google shared drive
- Shared Drive -> Researchers -> Zachary Caterer-> (file_name).ipynb

4. Download this file to desktop and move this file into a folder that has the data which you will be analyzing

- Opening and Running Jupyter Notebook File

5. Open Jupyter Notebook (ensure you are in a virtual environment)

6. Open Jupyter Notebook File

- File -> Open -> Find the folder where you saved the .ipynb file and data files. Click the .ipynb file to open it

7. Once File is Open, Click on the cell containing "## Imports ##" and click and hold "Shift" then click "Enter" or "Return"

- This will run the cell, and bring you to the next cell

8. Click on "##Read Data##" cell.

- The User must change the file_path_layout and file_path_data
- Please input the file path to each of these files, make sure you include the extension (.csv, .png, .pdf, .txt)
- If the files are in the same folder as the jupyter notebook, all you have to do is include the file name with the extension
- Ensure that the names of layout file are the same

9. Click and Hold "Shift" and Click "Enter" or "Return" to run the cell

10. Next run all the function cells, do this by repeating click and hold "shift" and click "enter" or "return" until all the functions have been ran

11. Once all the functions have been called, please run the cell containing "developing_new_df_from_input_data"

- this uses all of the functions we ran, taking the input data and creating a new data-frame containing all of the datapoints from the groupings

12. Run the Next cell to see the dataframe that was created

- Dilutions

13. If you made and dilutions follow steps 14-18, if you did not make any dilutions please skip to step 19

14. Please change the name of the groups that contained the dilutions

- this might consist of "Control" or "Time-Trial-1"
- make sure these names of the groups are in "" Quotiation Marks ""
- seperate each group by a comma

15. In the same order as the groups are listed in step 14, please enter the dilution that you made

- this might consist of "1:10" or "1:5"
- please make sure that these dilutions are in ""Quotation marks ""
- please make sure the dilutions are in the format of (1:number)
- please make sure they are seperated by a colon

16. Please change the final_volums_in_ml to the final volume you used to dilute your solution to

- Make sure this value is in (mL)

17. The run the cell that you made all of the changes in

- this cell contains:
- columns_need_to_be_adjusted
- diluted_from_original_density
- final_volume_in_ml

18. Run the cell containing "calculate_the_original_density"

- Graphing Data

19. Please change the style that you prefer for the graphs,

- I prefer the style "whitegrid"
- to find more styles
- https://seaborn.pydata.org/tutorial/aesthetics.html
- make sure this is in "" quotation marks ""

20. choose how many graphs you want in the figure

- for one graph please enter (1,1)
- for making a figure contining subplots use (rows, columns)
- so if you want 6 subplots examples might consist of (3,2) or (2,3) or (1,6)
- play around until you find what you like and want
- also change the figure size to what you want
- can also change the dpi to whatever you want, reccomended 600 for high quality figures

21. depending on how many graphs you have will determining how many lists you have. Include the same amount of lists per graphs

- choose which groups you want to compare per graph, change the names in the quotation marks to represent the names of the groups, seperate all of the groups by a comma
- example includes
- graph1 = ['Blank', '1-1', '2-1', '3-1', '3-3', '2-2']
- to include more, copy and paste the example above and change accordingly

22. Move onto the ##plotting the data## section

- please choose the style of graph you wish to plot
- https://seaborn.pydata.org/tutorial/function_overview.html
- common examples include
- sns.barplot(data=df[graph1], ax=axes[0])
- sns.boxplot(data=df[graph3], ax=axes[2])
- please ensure that you change the section of df['graph#'] to which list you included in step 21
- If you have more than 1 row, change the axes[#] to axes[#,#] the numbers listed are [row, columns]

23. Change and choose the labels and titles for the graphs, can also set the y limits if you desire

- axes[0].set_ylim(0,10)
- choose and change the limits, copy and paste this into the document

24. Change the supertitle, this will be the big title on the figure, there can be subplot titles

25. Run the cell and observe the graphs shown right below the cell, continue to change information in this cell until you are happy with the results

- repeat steps 19-25 until happy with figures

26. Once you are happy with the results, remove the '##' infront of the "plt.savefig()" then change the file name that will be the file produced containing the figure

- choose the extension you want
- examples include: .png, .pdf
- make sure the entire file name is contained in "" quotation marks ""

27. Run this cell again, this will save the figure to the file where you are running the jupyter notebook.

- find the file in your computer and move it to its final destination

Checking and Plotting Graphs with Statistical Significance

28. Please choose which groups you want to check for stastical significance. Please define the maximum p value that you want to graph, and choose the dataframe that you are using

- finding_statistically_significant_groups(##groups in a list##, ##p-value##, ##dataframe##)
- this will plot a graph where any p value less than or equal to the defined p value is shown on the graph
- if you have p values that overlap or want to change the text of the p-value
    * please enter the function (def finding_statistically_significant_groups(list_of_columns, p_value, dataframe_df):
    * plt.text((x1 + x2) * 0.5, y+h, f"p={p_value_test:.4f}", ha='center', va='bottom', color=col, rotation=45)
    * modify the line above to get the correct values
    * Also, depending on the scaling factor of the graph, you will want to change the step size between p value lines



