# PowerShell Version
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

Some references:
https://regex101.com/
https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/

# Python Version

WIP . I'll probably have to translate this into **Python**
This is still in Development:
``` Java
import re

#To Mask Domain
#regex = r"((?<=^.)[^@]*|(?<=@.).*(?=\.[^.]+$))"

regex = r"((?<=.).(?=[^@]\*?@))"

email_Address = (
    "john.doe@gmail.com\n"
	"foo@gmail.com\n"
	"foo-and.more!here@gmail.com\n"
	"franko@gmail.com\n"
	"fay@gmail.com"
    )

subst = "***"

# You can manually specify the number of replacements by changing the 4th argument
result = re.sub(regex, subst, email_Address , 0, re.MULTILINE)

if result:
    print (result)

# Note: for Python 2.7 compatibility, use ur"" to prefix the regex and u"" to prefix the test string and substitution.
```
