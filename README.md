# python-tricks

Honestly not that amazing, I just wanted to keep a notebook of Python tricks

## Assessment Marking

Override marks from one CSV file based on an overrides CSV file:

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
