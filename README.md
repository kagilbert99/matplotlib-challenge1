# matplotlib-challenge1

# Dependencies and Setup
import matplotlib.pyplot as plt
import pandas as pd
import scipy.stats as st

# Study data files
mouse_metadata_path = "data/Mouse_metadata.csv"
study_results_path = "data/Study_results.csv"

# Read the mouse data and the study results
mouse_metadata = pd.read_csv(mouse_metadata_path)
study_results = pd.read_csv(study_results_path)

# Combine the data into a single DataFrame
inner_merge = pd.merge(mouse_metadata, study_results, on=["Mouse ID"])

# Display the data table for preview
inner_merge.head()
# Checking the number of mice.
df = inner_merge
pd.value_counts(df['Mouse ID'])
# Our data should be uniquely identified by Mouse ID and Timepoint
# Get the duplicate mice by ID number that shows up for Mouse ID and Timepoint. 
duplicate = inner_merge[inner_merge.duplicated('Mouse ID')]
print(duplicate)
duplicate.info()
