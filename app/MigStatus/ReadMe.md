<h1>Azure Migration Dashboard</h1>
<h2>Application Requirements</h2>
Application to be run using Azure Web App with code stored and published from GitHub
Data will be store in Azure Table Storage
Azure Table Storage Read-Only Access
SAS Token
?sv=2015-04-05&ss=t&srt=c&sp=r&se=2017-01-31T17:14:33Z&st=2016-11-29T09:14:33Z&spr=https,http&sig=W7XcS7QVB5UbadfODu5YcAt8HhFPZsZPAD8b3pZgjjw%3D
SAS URL
https://migstatus.table.core.windows.net/?sv=2015-04-05&ss=t&srt=c&sp=r&se=2017-01-31T17:14:33Z&st=2016-11-29T09:14:33Z&spr=https,http&sig=W7XcS7QVB5UbadfODu5YcAt8HhFPZsZPAD8b3pZgjjw%3D
Data Guidelines
Partition Key
This groups and identifies each individual unique migration
Row Keys
MigDetails – Contains static details such as customer name, etc.
All other – Contains all progress information
MigDetails – Property and Value mapping to Web App
CustomerName – Fig1
CutOffDate – Fig2
CutOffTime – Fig3
EstimatedHours – Fig4
PartnerMPN – Not to be displayed
PartnerName – Not to be displayed
StartDate – Fig5
StartTime – Fig6
StatusAssessment – Fig7 (Orange if Current, Green if True, Grey if False)
StatusComplete – Fig7 (Orange if Current, Green if True, Grey if False)
StatusMigrate – Fig7 (Orange if Current, Green if True, Grey if False)
StatusSignOFf – Fig7 (Orange if Current, Green if True, Grey if False)
StatusSignOn – Fig7 (Orange if Current, Green if True, Grey if False)
TimeZone – Not to be displayed
TotalPercent – Fig8

All Other – Row Key Information
datastdarm.vhds.APPL-20160630-154426
datastdarm – Account Name
vhds – Container Name
APPL-20160630-154426 – VHD Name
All Other – Property and Value mapping to Web App
CloudService – Fig9
VMName – Fig10
DiskName – Fig11
CopiedBytes – Not to be displayed
CopiedKBytes – Not to be displayed
CopiedMBytes – Not to be displayed
CopiedGBytes – Fig12
CopiedTBytes – Not to be displayed 
CopiedPercent – Fig13
CopyingStatus – Fig14
TotalBytes – Not to be displayed
TotalKBytes – Not to be displayed
TotalMBytes – Not to be displayed
TotalTGbytes – Fig15
TotalTBytes – Not to be displayed
How to display the data
Combine all DiskName with same VMName under VMName on Web App

<<Sample>>

Combine all VMName with same CloudService on Web App

<<Sample>>

DiskName sorting
Show DiskName where Row Key Container starts with OSS at the top
Show DiskName where Row Key Container starts with any other other than OSS, after OSS
Show DiskName where CopyingStatus is Complete first
Show DiskName where CopyingStatus is Copying second
Show DiskName where CopyingStatus is Waiting third
If multiple DiskName in CopyingStatus, sort alphabetically

