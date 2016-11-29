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
<p><b>Row Key = MigDetails</b> – Property and Value mapping to Web App
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

<p><b>Row Key = All Other</b> – Row Key Information
<br>datastdarm.vhds.APPL-20160630-154426
<br>datastdarm – Account Name
<br>vhds – Container Name
<br>APPL-20160630-154426 – VHD Name
<p>All Other – Property and Value mapping to Web App
<br>CloudService – Fig9
<br>VMName – Fig10
<br>DiskName – Fig11
<br>CopiedBytes – Not to be displayed
<br>CopiedKBytes – Not to be displayed
<br>CopiedMBytes – Not to be displayed
<br>CopiedGBytes – Fig12
<br>CopiedTBytes – Not to be displayed 
<br>CopiedPercent – Fig13
<br>CopyingStatus – Fig14
<br>TotalBytes – Not to be displayed
<br>TotalKBytes – Not to be displayed
<br>TotalMBytes – Not to be displayed
<br>TotalTGbytes – Fig15
<br>TotalTBytes – Not to be displayed
<h2>How to display the data</h2>
<br>Combine all DiskName with same VMName under VMName on Web App

<p>![alt tag](https://raw.githubusercontent.com/AKonCloud/MigStatus/master/app/MigStatus/MigStatusSec1.png)

<br>Combine all VMName with same CloudService on Web App

<p>![alt tag](https://raw.githubusercontent.com/AKonCloud/MigStatus/master/app/MigStatus/MigStatusSec1.png)

<h2>DiskName sorting</h2>
<br>Show DiskName where Row Key Container starts with OSS at the top
<br>Show DiskName where Row Key Container starts with any other other than OSS, after OSS
<br>Show DiskName where CopyingStatus is Complete first
<br>Show DiskName where CopyingStatus is Copying second
<br>Show DiskName where CopyingStatus is Waiting third
<br>If multiple DiskName in CopyingStatus, sort alphabetically
