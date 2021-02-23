# pandas-data-transormations

#### GROUPBY + apply different aggregations
```python
df_result.groupby(["SAP_code", "Concurrent_code", "Concurrent_nom"]).agg(
    most_common_price=('Prix_Num', lambda x: x.value_counts().index[0]),
    avg=('Prix_Num', 'mean'),
    std=('Prix_Num', 'std'),
)
df_grouped= df_grouped.reset_index()
```

#### Preserve shape after groupby
```python
df['avg_price'] = df.groupby(['col1', 'col2', 'col3', 'col4'])['price'].transform('mean')
```

#### Apply multiple condition over different columns
```python
def func(row):
    if row['row1'] > 0 and row['row2'] > 0 and \
        row['row3'] > 0 and row['row4'] == 20:
        
        if row['row1'] < 50 or row['row2'] > 200:
            return 'case 1'
        else:
            return 'case 2'
    else:
        return 'case 3'
df['new_col'] = df.apply(func, axis=1)
```
#### Pivot
