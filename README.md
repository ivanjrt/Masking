# Masking
Helpful Tools to Mask Confidential information
string -replace  = comes from **Regex** found .NET
string.replace   =  This is more powershellish

Here are some examples of Masking
``` Javascript
$Email2Mask = "john.doe@gmail.com"
$Email2Mask -replace '(?<=...).(?=.*@)', '*'
```

``` Javascript
$SSN = "My SSN is 123-45-6789"
$SSN -replace '\d\d\d-\d\d-\d\d\d\d', '###-##-####'
```

``` Javascript
$phoneN = "123-456-7890"
$phoneN -replace '\d\d\d-\d\d\d-\d\d\d\d', 'xxx-xxx-xxxx'
```

Real Actual Example:
``` Javascript
  $VariableObject | Select FullName, @{N="CensuredEmail";E={($_.UserEmail) -replace '(?<=...).(?=.*@)', '*'}}, Date
```

