# PowerBI_Practical_Exam_Weldesenbet_Aregay


### Model View: Star Schema
<img width="1000" height="500" alt="image" src="https://github.com/user-attachments/assets/67a6a29c-4bd1-4d7e-b4db-341ba77e9d69" />


### Row-Level Security implementation
<img width="1000" height="400" alt="image" src="https://github.com/user-attachments/assets/b1b6d1fd-44fc-482a-aeee-85d3aa889d37" />

## Top 5 Sales DAX Measure 

This DAX measure returns the total sales amount for only the **top 5 products** based on sales.

### DAX Code
```DAX
Top 5 Sales = 
IF (
    RANKX (
        ALL ( Products[ProductName] ),
        [Total Sales]
    ) <= 5,
    [Total Sales]
)

```
### Here is the visual of the above DAX
<img width="1000" height="300" alt="image" src="https://github.com/user-attachments/assets/d1e69084-bd0b-4885-8662-980e5d436cda" />
