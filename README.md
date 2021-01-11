# pandas-data-transormations

## GROUPBY + apply different aggregations
```python
df_result.groupby(["SAP_code", "Concurrent_code", "Concurrent_nom"]).agg(
    most_common_price=('Prix_Num', lambda x: x.value_counts().index[0]),
    avg=('Prix_Num', 'mean'),
    std=('Prix_Num', 'std'),
)
```
