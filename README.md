# test
#first github repository

#Creating New Ad Users from an HR Excel file.
#Convert .xls file to a .csv file and store on the c:\ drive of the lab client computer

$import_users = import-csv -path c:\newusers.csv

$import_users | foreach-object {new-aduser `
-name $($_.firstname + " " + $_.lastname) `
-givenname $_.firstname `
-surname $_.lastname `
-department $_.department `
-state $_.state `
-employeeid $_.employeeid `
-displayname $($_.firstname + " " + $_.lastname) `
-office $_.office `
-userprincipalname $_.userprincipalname `
-samaccountname $_.samaccountname `
-accountpassword $(convertto-securestring $_.password -asplaintext -force) `
-enabled $true `
}
