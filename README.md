# python-tricks

Honestly not that amazing, I just wanted to keep a notebook of Python tricks

## Check if data is numeric

If you just use `isnumeric()` it doesn't work if you run it on an `int` since `int` does not have `isnumeric()`. You will get the error message "'int' object has no attribute 'isnumeric'"!

So, as per https://stackoverflow.com/a/73725567:

```python
str(n).isnumeric()
```

## Assessment Marking

Override marks from one CSV file based on another "overrides" CSV file:

```python
def apply_override(this_team, this_mrkc, this_mark, df_working_sheet):
    df_working_sheet.loc[df_working_sheet["team_name_full"] == this_team, this_mrkc] = int(this_mark)


df_working_sheet = pd.read_csv("./datasets/dataset_01_consolidated_tutor_supplied.csv")
df_mark_overrides = pd.read_csv("./datasets/dataset_03_mark_overrides.csv")

df_mark_overrides.apply(lambda row: apply_override(
    row["team_name_full"],
    row["marking_criteron"],
    row["mark"],
    df_working_sheet
), axis=1)

```
