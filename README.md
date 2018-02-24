

```python
import pandas as pd
import numpy as np
```


```python
# Create a reference to the CSV and import it into a Pandas DataFrame
schools_csv = "raw_data/schools_complete.csv"
students_csv = "raw_data/students_complete.csv"
```


```python
schools_df = pd.read_csv(schools_csv)
students_df = pd.read_csv(students_csv)
```


```python
schools_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
  </tbody>
</table>
</div>




```python
students_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
#calculate  total budget
Total_Schools = schools_df["name"].count()
print(schools_total)
#calculate total students
Total_Students = students_df["name"].count()
print (students_total)
#calculate total budget
Total_Budget=schools_df["budget"].sum()
print (total_budget)
#average math score
Average_Math_Score=round(students_df["math_score"].mean(),2)
print (Average_Math_Score)
#average reading score
Average_Reading_Score=round(students_df["reading_score"].mean(),2)
print (Average_Reading_Score)
```

    15
    39170
    24649428
    78.99
    81.88
    


```python
#len(students_df[(["math_score"]>70)
math_pass=len(students_df[(students_df['math_score']>70)])
print(math_pass)
Passing_Math = round(math_pass/students_total*100, 2)
print(Passing_Math)

reading_pass=len(students_df[(students_df['reading_score']>70)])
print(reading_pass)
Passing_Reading = round(reading_pass/students_total*100, 2)
print(Passing_Reading)

Overall_Passing_Rate = (Passing_Math+Passing_Reading)/2
print(Overall_Passing_Rate) 
```

    28356
    72.39
    32500
    82.97
    77.68
    


```python
District_Summary=[Total_Schools, Total_Students, Total_Budget, Average_Math_Score, Average_Reading_Score, Passing_Math, Passing_Reading, 
                  Overall_Passing_Rate]
row_names=["Total Schools","Total Students","Total Budget", "Average Math Score", "Average Reading Score","% Passing Math","% Passing Reading",
           "Overall Passing Rate"]
district_summary_df=pd.DataFrame(District_Summary, row_names, columns=['District_Summary'])
district_summary_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>District_Summary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Total Schools</th>
      <td>15.00</td>
    </tr>
    <tr>
      <th>Total Students</th>
      <td>39170.00</td>
    </tr>
    <tr>
      <th>Total Budget</th>
      <td>24649428.00</td>
    </tr>
    <tr>
      <th>Average Math Score</th>
      <td>78.99</td>
    </tr>
    <tr>
      <th>Average Reading Score</th>
      <td>81.88</td>
    </tr>
    <tr>
      <th>% Passing Math</th>
      <td>72.39</td>
    </tr>
    <tr>
      <th>% Passing Reading</th>
      <td>82.97</td>
    </tr>
    <tr>
      <th>Overall Passing Rate</th>
      <td>77.68</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Create a new columns math_pass and reading_pass where the value is yes if score is greater than 70 and no if not
students_df["math_pass"] = np.where(students_df["math_score"]>=70, 'yes', 'no')
students_df["reading_pass"] = np.where(students_df["reading_score"]>=70, 'yes', 'no')
students_df.head()

```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
      <th>math_pass</th>
      <th>reading_pass</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
      <td>yes</td>
      <td>no</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
      <td>no</td>
      <td>yes</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
      <td>no</td>
      <td>yes</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
      <td>no</td>
      <td>no</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
      <td>yes</td>
      <td>yes</td>
    </tr>
  </tbody>
</table>
</div>




```python
#per student budget
schools_df["per student budget"]=schools_df["budget"]/schools_df["size"]

# calculate mean reading and math scores
grouped_students_avg_df = students_df.groupby(['school']).mean()
school_summary=schools_df.join(grouped_students_avg_df['reading_score'], on='name')
school_summary=school_summary.join(grouped_students_avg_df['math_score'], on='name')
school_summary.rename(columns={'reading_score':'Avg Reading Score'}, inplace=True)
school_summary.rename(columns={'math_score':'Avg Math Score'}, inplace=True)

# calculate total students per school
grouped_students_count_df = students_df.groupby(['school']).size()
school_summary = school_summary.join(grouped_students_count_df.to_frame(), on='name')
school_summary.rename(columns={0:'Total Students'}, inplace=True)

# calculate percent passing math per school
passed_math_df = students_df[students_df['math_pass'] == "yes"]
grouped_math_pass_df = passed_math_df.groupby(['school']).size()/ students_df.groupby(['school']).size()
school_summary = school_summary.join(grouped_math_pass_df.to_frame(), on='name')
school_summary.rename(columns={0:'Math Pass %'}, inplace=True)

# calculate percent passing reading per school
passed_read_df = students_df[students_df['reading_pass'] == "yes"]
grouped_read_pass_df = passed_read_df.groupby(['school']).size()/ students_df.groupby(['school']).size()
school_summary = school_summary.join(grouped_read_pass_df.to_frame(), on='name')
school_summary.rename(columns={0:'Read Pass %'}, inplace=True)

# calculate average percent passing per school
average_passing_rate_df = (grouped_read_pass_df + grouped_math_pass_df) / 2
school_summary = school_summary.join(average_passing_rate_df.to_frame(), on='name')
school_summary.rename(columns={0:'Average Pass %'}, inplace=True)
school_summary
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>per student budget</th>
      <th>Avg Reading Score</th>
      <th>Avg Math Score</th>
      <th>Total Students</th>
      <th>Math Pass %</th>
      <th>Read Pass %</th>
      <th>Average Pass %</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>81.182722</td>
      <td>76.629414</td>
      <td>2917</td>
      <td>0.656839</td>
      <td>0.813164</td>
      <td>0.735002</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
      <td>81.158020</td>
      <td>76.711767</td>
      <td>2949</td>
      <td>0.659885</td>
      <td>0.807392</td>
      <td>0.733639</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
      <td>600.0</td>
      <td>83.725724</td>
      <td>83.359455</td>
      <td>1761</td>
      <td>0.938671</td>
      <td>0.958546</td>
      <td>0.948609</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
      <td>652.0</td>
      <td>80.934412</td>
      <td>77.289752</td>
      <td>4635</td>
      <td>0.667530</td>
      <td>0.808630</td>
      <td>0.738080</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
      <td>83.816757</td>
      <td>83.351499</td>
      <td>1468</td>
      <td>0.933924</td>
      <td>0.971390</td>
      <td>0.952657</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
      <td>83.989488</td>
      <td>83.274201</td>
      <td>2283</td>
      <td>0.938677</td>
      <td>0.965396</td>
      <td>0.952037</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
      <td>83.975780</td>
      <td>83.061895</td>
      <td>1858</td>
      <td>0.941335</td>
      <td>0.970398</td>
      <td>0.955867</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Bailey High School</td>
      <td>District</td>
      <td>4976</td>
      <td>3124928</td>
      <td>628.0</td>
      <td>81.033963</td>
      <td>77.048432</td>
      <td>4976</td>
      <td>0.666801</td>
      <td>0.819333</td>
      <td>0.743067</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Holden High School</td>
      <td>Charter</td>
      <td>427</td>
      <td>248087</td>
      <td>581.0</td>
      <td>83.814988</td>
      <td>83.803279</td>
      <td>427</td>
      <td>0.925059</td>
      <td>0.962529</td>
      <td>0.943794</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
      <td>84.044699</td>
      <td>83.839917</td>
      <td>962</td>
      <td>0.945946</td>
      <td>0.959459</td>
      <td>0.952703</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>Wright High School</td>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400</td>
      <td>583.0</td>
      <td>83.955000</td>
      <td>83.682222</td>
      <td>1800</td>
      <td>0.933333</td>
      <td>0.966111</td>
      <td>0.949722</td>
    </tr>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
      <td>80.744686</td>
      <td>76.842711</td>
      <td>3999</td>
      <td>0.663666</td>
      <td>0.802201</td>
      <td>0.732933</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
      <td>80.966394</td>
      <td>77.072464</td>
      <td>4761</td>
      <td>0.660576</td>
      <td>0.812224</td>
      <td>0.736400</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
      <td>644.0</td>
      <td>80.746258</td>
      <td>77.102592</td>
      <td>2739</td>
      <td>0.683096</td>
      <td>0.792990</td>
      <td>0.738043</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>638.0</td>
      <td>83.848930</td>
      <td>83.418349</td>
      <td>1635</td>
      <td>0.932722</td>
      <td>0.973089</td>
      <td>0.952905</td>
    </tr>
  </tbody>
</table>
</div>




```python
top_performing_schools = school_summary.sort_values('Average Pass %', ascending=False).head(5)
top_performing_schools
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>per student budget</th>
      <th>Avg Reading Score</th>
      <th>Avg Math Score</th>
      <th>Total Students</th>
      <th>Math Pass %</th>
      <th>Read Pass %</th>
      <th>Average Pass %</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
      <td>83.975780</td>
      <td>83.061895</td>
      <td>1858</td>
      <td>0.941335</td>
      <td>0.970398</td>
      <td>0.955867</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>638.0</td>
      <td>83.848930</td>
      <td>83.418349</td>
      <td>1635</td>
      <td>0.932722</td>
      <td>0.973089</td>
      <td>0.952905</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
      <td>84.044699</td>
      <td>83.839917</td>
      <td>962</td>
      <td>0.945946</td>
      <td>0.959459</td>
      <td>0.952703</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
      <td>83.816757</td>
      <td>83.351499</td>
      <td>1468</td>
      <td>0.933924</td>
      <td>0.971390</td>
      <td>0.952657</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
      <td>83.989488</td>
      <td>83.274201</td>
      <td>2283</td>
      <td>0.938677</td>
      <td>0.965396</td>
      <td>0.952037</td>
    </tr>
  </tbody>
</table>
</div>




```python
worst_performing_schools = school_summary.sort_values('Average Pass %', ascending=True).head(5)
worst_performing_schools
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>per student budget</th>
      <th>Avg Reading Score</th>
      <th>Avg Math Score</th>
      <th>Total Students</th>
      <th>Math Pass %</th>
      <th>Read Pass %</th>
      <th>Average Pass %</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
      <td>80.744686</td>
      <td>76.842711</td>
      <td>3999</td>
      <td>0.663666</td>
      <td>0.802201</td>
      <td>0.732933</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
      <td>81.158020</td>
      <td>76.711767</td>
      <td>2949</td>
      <td>0.659885</td>
      <td>0.807392</td>
      <td>0.733639</td>
    </tr>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>81.182722</td>
      <td>76.629414</td>
      <td>2917</td>
      <td>0.656839</td>
      <td>0.813164</td>
      <td>0.735002</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
      <td>80.966394</td>
      <td>77.072464</td>
      <td>4761</td>
      <td>0.660576</td>
      <td>0.812224</td>
      <td>0.736400</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
      <td>644.0</td>
      <td>80.746258</td>
      <td>77.102592</td>
      <td>2739</td>
      <td>0.683096</td>
      <td>0.792990</td>
      <td>0.738043</td>
    </tr>
  </tbody>
</table>
</div>




```python
grouped_by_grader = students_df.groupby(['school','grade']).mean()
math_scores_by_grade = grouped_by_grader['math_score'].to_frame()
math_scores_by_grade
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>math_score</th>
    </tr>
    <tr>
      <th>school</th>
      <th>grade</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="4" valign="top">Bailey High School</th>
      <th>10th</th>
      <td>76.996772</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>77.515588</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>76.492218</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>77.083676</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Cabrera High School</th>
      <th>10th</th>
      <td>83.154506</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>82.765560</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>83.277487</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.094697</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Figueroa High School</th>
      <th>10th</th>
      <td>76.539974</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>76.884344</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>77.151369</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>76.403037</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Ford High School</th>
      <th>10th</th>
      <td>77.672316</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>76.918058</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>76.179963</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>77.361345</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Griffin High School</th>
      <th>10th</th>
      <td>84.229064</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>83.842105</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>83.356164</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>82.044010</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Hernandez High School</th>
      <th>10th</th>
      <td>77.337408</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>77.136029</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>77.186567</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>77.438495</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Holden High School</th>
      <th>10th</th>
      <td>83.429825</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>85.000000</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>82.855422</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.787402</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Huang High School</th>
      <th>10th</th>
      <td>75.908735</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>76.446602</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>77.225641</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>77.027251</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Johnson High School</th>
      <th>10th</th>
      <td>76.691117</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>77.491653</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>76.863248</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>77.187857</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Pena High School</th>
      <th>10th</th>
      <td>83.372000</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>84.328125</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>84.121547</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.625455</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Rodriguez High School</th>
      <th>10th</th>
      <td>76.612500</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>76.395626</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>77.690748</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>76.859966</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Shelton High School</th>
      <th>10th</th>
      <td>82.917411</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>83.383495</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>83.778976</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.420755</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Thomas High School</th>
      <th>10th</th>
      <td>83.087886</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>83.498795</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>83.497041</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.590022</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Wilson High School</th>
      <th>10th</th>
      <td>83.724422</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>83.195326</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>83.035794</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.085578</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Wright High School</th>
      <th>10th</th>
      <td>84.010288</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>83.836782</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>83.644986</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.264706</td>
    </tr>
  </tbody>
</table>
</div>




```python
reading_scores_by_grade = grouped_by_grader['reading_score'].to_frame()
reading_scores_by_grade
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>reading_score</th>
    </tr>
    <tr>
      <th>school</th>
      <th>grade</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="4" valign="top">Bailey High School</th>
      <th>10th</th>
      <td>80.907183</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>80.945643</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>80.912451</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>81.303155</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Cabrera High School</th>
      <th>10th</th>
      <td>84.253219</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>83.788382</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>84.287958</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.676136</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Figueroa High School</th>
      <th>10th</th>
      <td>81.408912</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>80.640339</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>81.384863</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>81.198598</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Ford High School</th>
      <th>10th</th>
      <td>81.262712</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>80.403642</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>80.662338</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>80.632653</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Griffin High School</th>
      <th>10th</th>
      <td>83.706897</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>84.288089</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>84.013699</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.369193</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Hernandez High School</th>
      <th>10th</th>
      <td>80.660147</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>81.396140</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>80.857143</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>80.866860</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Holden High School</th>
      <th>10th</th>
      <td>83.324561</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>83.815534</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>84.698795</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.677165</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Huang High School</th>
      <th>10th</th>
      <td>81.512386</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>81.417476</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>80.305983</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>81.290284</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Johnson High School</th>
      <th>10th</th>
      <td>80.773431</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>80.616027</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>81.227564</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>81.260714</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Pena High School</th>
      <th>10th</th>
      <td>83.612000</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>84.335938</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>84.591160</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.807273</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Rodriguez High School</th>
      <th>10th</th>
      <td>80.629808</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>80.864811</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>80.376426</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>80.993127</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Shelton High School</th>
      <th>10th</th>
      <td>83.441964</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>84.373786</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>82.781671</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>84.122642</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Thomas High School</th>
      <th>10th</th>
      <td>84.254157</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>83.585542</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>83.831361</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.728850</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Wilson High School</th>
      <th>10th</th>
      <td>84.021452</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>83.764608</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>84.317673</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.939778</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Wright High School</th>
      <th>10th</th>
      <td>83.812757</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>84.156322</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>84.073171</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.833333</td>
    </tr>
  </tbody>
</table>
</div>




```python
school_summary
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>per student budget</th>
      <th>Avg Reading Score</th>
      <th>Avg Math Score</th>
      <th>Total Students</th>
      <th>Math Pass %</th>
      <th>Read Pass %</th>
      <th>Average Pass %</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>81.182722</td>
      <td>76.629414</td>
      <td>2917</td>
      <td>0.656839</td>
      <td>0.813164</td>
      <td>0.735002</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
      <td>81.158020</td>
      <td>76.711767</td>
      <td>2949</td>
      <td>0.659885</td>
      <td>0.807392</td>
      <td>0.733639</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
      <td>600.0</td>
      <td>83.725724</td>
      <td>83.359455</td>
      <td>1761</td>
      <td>0.938671</td>
      <td>0.958546</td>
      <td>0.948609</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
      <td>652.0</td>
      <td>80.934412</td>
      <td>77.289752</td>
      <td>4635</td>
      <td>0.667530</td>
      <td>0.808630</td>
      <td>0.738080</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
      <td>83.816757</td>
      <td>83.351499</td>
      <td>1468</td>
      <td>0.933924</td>
      <td>0.971390</td>
      <td>0.952657</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
      <td>83.989488</td>
      <td>83.274201</td>
      <td>2283</td>
      <td>0.938677</td>
      <td>0.965396</td>
      <td>0.952037</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
      <td>83.975780</td>
      <td>83.061895</td>
      <td>1858</td>
      <td>0.941335</td>
      <td>0.970398</td>
      <td>0.955867</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Bailey High School</td>
      <td>District</td>
      <td>4976</td>
      <td>3124928</td>
      <td>628.0</td>
      <td>81.033963</td>
      <td>77.048432</td>
      <td>4976</td>
      <td>0.666801</td>
      <td>0.819333</td>
      <td>0.743067</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Holden High School</td>
      <td>Charter</td>
      <td>427</td>
      <td>248087</td>
      <td>581.0</td>
      <td>83.814988</td>
      <td>83.803279</td>
      <td>427</td>
      <td>0.925059</td>
      <td>0.962529</td>
      <td>0.943794</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
      <td>84.044699</td>
      <td>83.839917</td>
      <td>962</td>
      <td>0.945946</td>
      <td>0.959459</td>
      <td>0.952703</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>Wright High School</td>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400</td>
      <td>583.0</td>
      <td>83.955000</td>
      <td>83.682222</td>
      <td>1800</td>
      <td>0.933333</td>
      <td>0.966111</td>
      <td>0.949722</td>
    </tr>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
      <td>80.744686</td>
      <td>76.842711</td>
      <td>3999</td>
      <td>0.663666</td>
      <td>0.802201</td>
      <td>0.732933</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
      <td>80.966394</td>
      <td>77.072464</td>
      <td>4761</td>
      <td>0.660576</td>
      <td>0.812224</td>
      <td>0.736400</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
      <td>644.0</td>
      <td>80.746258</td>
      <td>77.102592</td>
      <td>2739</td>
      <td>0.683096</td>
      <td>0.792990</td>
      <td>0.738043</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>638.0</td>
      <td>83.848930</td>
      <td>83.418349</td>
      <td>1635</td>
      <td>0.932722</td>
      <td>0.973089</td>
      <td>0.952905</td>
    </tr>
  </tbody>
</table>
</div>




```python
bins = [500,550,600,650,700]
# Create labels for these bins
group_labels = ["500 to 550","550 to 600","600 to 650", "650 to 700"]
                # Slice the data and place it into bins
school_summary['school_spending'] = pd.cut(school_summary["per student budget"],bins,labels=group_labels)
scores_by_school_spending = school_summary.groupby('school_spending').mean()[['Avg Math Score', 
                                                                              'Avg Reading Score',
                                                                              'Math Pass %',
                                                                              'Read Pass %',
                                                                              'Average Pass %']]
scores_by_school_spending
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Avg Math Score</th>
      <th>Avg Reading Score</th>
      <th>Math Pass %</th>
      <th>Read Pass %</th>
      <th>Average Pass %</th>
    </tr>
    <tr>
      <th>school_spending</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>500 to 550</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>550 to 600</th>
      <td>83.436210</td>
      <td>83.892196</td>
      <td>0.935415</td>
      <td>0.964596</td>
      <td>0.950006</td>
    </tr>
    <tr>
      <th>600 to 650</th>
      <td>79.423466</td>
      <td>82.044963</td>
      <td>0.768327</td>
      <td>0.867260</td>
      <td>0.817793</td>
    </tr>
    <tr>
      <th>650 to 700</th>
      <td>76.959583</td>
      <td>81.058567</td>
      <td>0.662184</td>
      <td>0.810897</td>
      <td>0.736541</td>
    </tr>
  </tbody>
</table>
</div>




```python
bins = [0,2000,4000,6000]
# Create labels for these bins
group_labels = ["Small","Medium","Large"]
                # Slice the data and place it into bins
school_summary['scores_by_size'] = pd.cut(school_summary["size"],bins,labels=group_labels)
scores_by_school_size = school_summary.groupby('scores_by_size').mean()[['Avg Math Score', 
                                                                              'Avg Reading Score',
                                                                              'Math Pass %',
                                                                              'Read Pass %',
                                                                              'Average Pass %']]
scores_by_school_size
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Avg Math Score</th>
      <th>Avg Reading Score</th>
      <th>Math Pass %</th>
      <th>Read Pass %</th>
      <th>Average Pass %</th>
    </tr>
    <tr>
      <th>scores_by_size</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Small</th>
      <td>83.502373</td>
      <td>83.883125</td>
      <td>0.935856</td>
      <td>0.965932</td>
      <td>0.950894</td>
    </tr>
    <tr>
      <th>Medium</th>
      <td>78.112137</td>
      <td>81.564235</td>
      <td>0.720433</td>
      <td>0.836229</td>
      <td>0.778331</td>
    </tr>
    <tr>
      <th>Large</th>
      <td>77.136883</td>
      <td>80.978256</td>
      <td>0.664969</td>
      <td>0.813396</td>
      <td>0.739182</td>
    </tr>
  </tbody>
</table>
</div>




```python
school_summary.groupby('type').mean()[['Avg Math Score', 
                                       'Avg Reading Score',
                                       'Math Pass %',
                                       'Read Pass %',
                                       'Average Pass %']]
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Avg Math Score</th>
      <th>Avg Reading Score</th>
      <th>Math Pass %</th>
      <th>Read Pass %</th>
      <th>Average Pass %</th>
    </tr>
    <tr>
      <th>type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Charter</th>
      <td>83.473852</td>
      <td>83.896421</td>
      <td>0.936208</td>
      <td>0.965865</td>
      <td>0.951037</td>
    </tr>
    <tr>
      <th>District</th>
      <td>76.956733</td>
      <td>80.966636</td>
      <td>0.665485</td>
      <td>0.807991</td>
      <td>0.736738</td>
    </tr>
  </tbody>
</table>
</div>



## Three observable data trends 

### 1. Charter schools tend to have higher average performance
### 2. Smaller schools have significantly higher average performance 
### 3. Increased spending per student does not necessarily increase average performance. 
