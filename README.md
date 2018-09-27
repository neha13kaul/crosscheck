# crosscheck
check one excel file data against another file
# Import pandas
import pandas as pd

# Assign spreadsheet filename to `file`
fileref = 'C://Users//npankow//Documents//REU impact data//myNSF_ER_Project Summary.xlsx'
file2 = 'C://Users//npankow//Documents//REU impact data//from MP//FY19REUSiteProps_NKP.xlsm'

# Load spreadsheet
xlref = pd.ExcelFile(fileref)
xl2 = pd.ExcelFile(file2)

# Print the sheet names
shnameref = xlref.sheet_names
print(shnameref)
shname2 = xl2.sheet_names
print(shname2)

# Load a sheet into a DataFrame by name: df1
dfref = xlref.parse(shnameref[0])
df2 = xl2.parse(shname2[2])
#df2 = pd.read_excel(xl2, shname2[2])

#create dataframe with only propID and Instt name
dfrefprop = dfref.iloc[:,8]
df2prop = df2.iloc[:,13]

#create dictionary from ref to check if all listed proposals are current
