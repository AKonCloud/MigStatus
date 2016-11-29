<h1>Azure Migration Dashboard</h1>
<h2>Application Requirements</h2>
Application to be run using Azure Web App with code stored and published from GitHub
<br>Data will be store in Azure Table Storage
<h2>Azure Table Storage Read-Only Access</h2>
<b>SAS Token</b>
<br>?sv=2015-04-05&ss=t&srt=c&sp=r&se=2017-01-31T17:14:33Z&st=2016-11-29T09:14:33Z&spr=https,http&sig=W7XcS7QVB5UbadfODu5YcAt8HhFPZsZPAD8b3pZgjjw%3D
<p><b>SAS URL</b>
<br>https://migstatus.table.core.windows.net/?sv=2015-04-05&ss=t&srt=c&sp=r&se=2017-01-31T17:14:33Z&st=2016-11-29T09:14:33Z&spr=https,http&sig=W7XcS7QVB5UbadfODu5YcAt8HhFPZsZPAD8b3pZgjjw%3D
<h2>Data Guidelines</h2>
<b>Partition Key</b>
<br>This groups and identifies each individual unique migration
<p><b>Row Keys</b>
<br>MigDetails – Contains static details such as customer name, etc.
<br>All other – Contains all progress information
<p>MigDetails – Property and Value mapping to Web App
<br>CustomerName – Fig1
<br>CutOffDate – Fig2
<br>CutOffTime – Fig3
<br>EstimatedHours – Fig4
<br>PartnerMPN – Not to be displayed
<br>PartnerName – Not to be displayed
<br>StartDate – Fig5
<br>StartTime – Fig6
<br>StatusAssessment – Fig7 (Orange if Current, Green if True, Grey if False)
<br>StatusComplete – Fig7 (Orange if Current, Green if True, Grey if False)
<br>StatusMigrate – Fig7 (Orange if Current, Green if True, Grey if False)
<br>StatusSignOFf – Fig7 (Orange if Current, Green if True, Grey if False)
<br>StatusSignOn – Fig7 (Orange if Current, Green if True, Grey if False)
<br>TimeZone – Not to be displayed
<br>TotalPercent – Fig8

<p><b>All Other</b> – Row Key Information
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
<h2>How to display the data</h2>
Combine all DiskName with same VMName under VMName on Web App

![alt tag](https://raw.githubusercontent.com/AKonCloud/MigStatus/master/app/MigStatus/MigStatusSec1.png)

Combine all VMName with same CloudService on Web App

![alt tag](https://raw.githubusercontent.com/AKonCloud/MigStatus/master/app/MigStatus/MigStatusSec2.png)

DiskName sorting
Show DiskName where Row Key Container starts with OSS at the top
Show DiskName where Row Key Container starts with any other other than OSS, after OSS
Show DiskName where CopyingStatus is Complete first
Show DiskName where CopyingStatus is Copying second
Show DiskName where CopyingStatus is Waiting third
If multiple DiskName in CopyingStatus, sort alphabetically

