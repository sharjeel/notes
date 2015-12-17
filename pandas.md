Pandas (Python)
===

## Basic rows access

Trim rows by index range:

`result.head()`

`result.tail()`

`result[10:20]`

Change index column with a new data result:

`result2 = result.set_index('employee_id')`

Change index column in-place:

`result.set_index('employee_id', inplace=True)`

Revert back index to row numbers:

`result.reset_index(inplace=True)`

Access a row by id by special ix field:

`result.ix[31337]`

Access a particular field of a row id:

`result.ix[31337].last_name`

Access multiple rows by id:

`result.ix[[786, 31337, 3007]]`

### Joins

Inner join (uses intersection of keys):

`pandas.merge(employees, department, on='department_id')`

Left outer join (uses keys only from left):

`pandas.merge(employees, department, on='department_id', how='left')`

Left outer join (uses keys only from right):

`pandas.merge(employees, department, on='department_id', how='right')`

Fill outer join:

`pandas.merge(employees, department, on='department_id', how='outer')`

Combining or union:

`pandas.concat([result1, result2])`

Concatenate horozontally:

`pandas.concat([result1, result2], axis=1)`

Group by

```
grouped_data = result.groupby('department_id')
grouped_data.count() # Count the non-null values for every field in each group
grouped_data.size() # Total number of records in each group 
```

Sum, average and median:

```
grouped_data.sum()
grouped_data.mean()
grouped_data.median()
```

Operations within a group, e.g. distinct count and sorting:

`grouped_data.title.nunique().order(ascending=False)[5:]`

### Transformation operations

Applying a transformation on each row of a column

```
result['increased_salary'] = result['salary'].apply(lambda salary: salary + salary * 0.10)
result['increased_salary'] = result.apply(
  lambda row: row['salary'] + row['salary'] *  row['performance_evaluation'],
  axis=1)
```

### Data selection and filtering

SQL equivalent of WHERE field equals: 

`employee[employee.department_id == 3]`

And'ing and Or'ing

```
employee[(employee.department_id == 2) | (employee.salary > 10000)]
employee[(employee.department_id == 3) & (employee.salary < 50000)]
```

String search

`employee[(employee['bio'].contains("Java")]`

Regex also works

`employee[(employee['bio'].contains("Python|Ruby")]`

Convert column data into list

`list(employee['salary'])`

Iterate over rows:

```
for i, r in df.iterrows():
  print "Record number: " + i
  print "Employee Name: %s" % r.name
  print "Department: %s" % r.department
```
  
Print without index:

`print df.to_string(index=False)
