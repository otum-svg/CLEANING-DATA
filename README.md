# CLEANING-DATA
import pandas as p
# Load dataset
f = p.read_csv(r"C:\Users\ORG\Desktop\marketing_campaign.csv")
print("Missing values\n", f.isnull().sum())
f.fillna('Unknown', inplace=True)
# Remove duplicate rows
f.drop_duplicates(inplace=True)
# text values
f['Gender'] = f['Gender'].str.lower()
f['Country'] = f['Country'].str.title()
# Date format
f['Date'] = p.to_datetime(f['Date'], format='%d-%m-%Y', errors='coerce')
# rename columns
f.columns = [col.lower().replace(' ', '_') for col in f.columns]
# data type
f['Age'] = f['Age'].astype(int)
# print info message
print("Data info after processing:\n")
print(f.info())
# Save cleaned dataset
f.to_csv(r"C:\Users\ORG\Desktop\marketing_campaign.csv", index=False)
print("Cleaned dataset saved successfully!")
