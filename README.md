# EXPERIMENT 4: Data Wrangling and Data Visualization

**Submitted by:** Mariedel O. Domingo  
---

## I. Intended Learning Outcomes

#### The intended learning outcome is to recognize and apply Python codes and functions for data cleaning, wrangling, and visualization effectively.

---

## II. Instructions

### ECE BOARD EXAM PROBLEM

> [!IMPORTANT]
> Download the ECE Board Exam 2 dataset
> * The following .xlsx file can be downloaded [here](https://ust.instructure.com/courses/52283/files/5682138?module_item_id=1204061)
  >###
>    NOTE: 
  >   Ensure that the following file is saved in the same directory as your Jupyter notebook so that the notebook can locate it.

---

### NUMBER 1

#### $\color{Apricot}{Create\ the\ following\ data\ frames\ based\ on\ the\ format\ provided:\ :}$ 

| Name          | Gender        |     Track      |     Math      |
| ------------- |:-------------:| :-------------:|:-------------:|
| S4            |     Male      | Instrumentation|        65     |
| S11           |     Female    |  Communication |        48     |
| S22           |     Female    | Communication  |        64     |

#### a. Filename: _Instru = [“Name”, “GEAS”, “Electronics >70”]_ ; where track is constant as Instrumentation and hometown Luzon

#### b. Filename: _Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]_ ; where hometown is constant as Mindanao and gender Female


### NUMBER 2

#### $\color{Apricot}{Create\ a\ visualization\ that\ shows\ how\ the\ different\ features\ contributes\ to\ average\ grade.\ Does\ chosen\ track\ in\ college,\ gender,\ or}$  
#### $\color{Apricot}{hometown\ contributes\ to\ a\ higher\ average\ score.}$ 

---

## III. Solutions

### ECE BOARD EXAM PROBLEM

### NUMBER 1
* Using this **_import convention_** enables access to the Pandas library, which will be used throughout the entire program.
```python
import pandas as pd
```

* Once the Pandas library is accessed,  **_save the .xlsx file_** in the same directory as your Jupyter notebook to ensure it can be found by the notebook.
```python
board = pd.read_excel("board2.xlsx")
board
```
* By using the **_pd.read_excel() function_**, the file will be accessed, and its dataset will be stored in the variable board.
  
#### OUTPUT:

<img width="614" height="628" alt="image" src="https://github.com/user-attachments/assets/c23210d4-295c-405f-bc83-1c6ce3705731" />

---

**a.** To be able to filter the dataset and display particular rows and columns, utilize the **_board.loc function_**.
```python
Instru = board.loc[(board['Hometown'] == 'Luzon') & (board['Track'] == 'Instrumentation') & (board['Electronics'] > 70), ['Name','GEAS','Electronics']]
Instru
```

* The **_board.loc function_**  serves as a search engine, showing only the specific rows and columns you require.

#### OUTPUT:

<img width="221" height="122" alt="image" src="https://github.com/user-attachments/assets/5836bfe1-07e3-4e79-b645-58651569bd6d" />

---

#### Before moving on to the next section, it's necessary to calculate the average for each track, as the next step requires displaying a column with the average for each track.
```python
board['Average'] = round(board[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1),2)
```

* **_board['Average'] function_** will calculate the average of each column specified and will be stored in variable Average

**b.** Proceeding, employ **_board.loc function_** to filter the dataset and display particular rows and columns.
```python
Mindy = board.loc[(board['Hometown'] == 'Mindanao') & (board['Gender'] == 'Female') & (board['Average'] >= 55), ['Name','Track','Electronics', 'Average']]
Mindy
```

* Similar to the previous code, by using the **_board.loc function_** will serve as your search tool, showing only the rows and columns you specify.
  
#### OUTPUT:
<img width="339" height="193" alt="image" src="https://github.com/user-attachments/assets/4d12dbb3-fb33-4af6-8fe1-e5fd8ae0a251" />

---

### NUMBER 2:

* Using this **_import convention_** allows access to the pyplot library, which will be utilized throughout the entire program.
```python
import matplotlib.pyplot as plt
```

* To graph the values, the size of the graph must be specified.
```python
plt.figure(figsize=(10,4))
```

* By using  **_plt.figure_** , this function sets the size of the graph.

* 
Next, after setting the graph size, the **_plt.bar() function_** will be utilized
```python
plt.bar(board['Track'],board['Average'])
```
* This function specifies the type of graph to be used and sets the values for the x-axis and y-axis.
  
* Wherein:
 ```python
plt.bar(board['x-axis'],board['y-axis'])
```
 
#### OUTPUT:
<img width="824" height="364" alt="image" src="https://github.com/user-attachments/assets/05e2c119-3b5d-4999-87c6-cade40803e5f" />


#### $\color{Apricot}{The\ bar\ graph\ indicates\ that\ Microelectronics\ has\ the\ highest\ average\ grade,\ whereas\ Instrumentation\ has\ the\ lowest. :}$ 


---

* Next, the comparison will focus on identifying which gender has the highest and lowest average grade, by using the same **_plt.bar() function_**
```python
plt.bar(board['Gender'],board['Average'])
```

#### OUTPUT:
<img width="839" height="345" alt="image" src="https://github.com/user-attachments/assets/db789716-8f79-4bce-83a8-d7fc664b925a" />


#### $\color{Apricot}{The\ bar\ graph\ below\ shows\ that\ females\ have\ the\ highest\ average\ grade,\ while\ males\ have\ the\ lowest. :}$ 


* Finally, the comparison will be made to determine which hometown has the highest and lowest average grade, utilizing the sam **_plt.bar() function_**
```python
plt.bar(board['Hometown'],board['Average'])
```

#### OUTPUT:
<img width="847" height="357" alt="image" src="https://github.com/user-attachments/assets/84ac8a29-d1fb-4d08-baf2-dd4c29533d5c" />

#### $\color{Apricot}{The\ bar\ graph\ below\ demonstrates\ that\ Luzon\ has\ the\ highest\ average\ grade,\ whereas\ the\ Mindanao\ region\ has\ the\ lowest. :}$ 

---
