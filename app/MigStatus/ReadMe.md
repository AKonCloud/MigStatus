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
<table>
  <tr>
    <th>Property</th>
    <th>Value</th> 
  </tr>
  <tr>
    <td>CustomerName</td>
    <td>Fig1</td> 
  </tr>
  <tr>
    <td>CutOffDate</td>
    <td>Fig2</td> 
  </tr>
    <tr>
    <td>CutOffTime</td>
    <td>Fig3</td> 
  </tr>
      <tr>
    <td>EstimatedHours</td>
    <td>Fig4</td> 
  </tr>
      <tr>
    <td>PartnerMPN</td>
    <td>Not to be displayed</td> 
  </tr>
      <tr>
    <td>PartnerName</td>
    <td>Not to be displayed</td> 
  </tr>
      <tr>
    <td>StartDate</td>
    <td>Fig5</td> 
  </tr>
      <tr>
    <td>StartTime</td>
    <td>Fig6</td> 
  </tr>
      <tr>
    <td>StatusAssessmen</td>
    <td>Fig7 (Orange if Current, Green if True, Grey if False)</td> 
  </tr>
      <tr>
    <td>StatusComplete</td>
    <td>Fig7 (Orange if Current, Green if True, Grey if False)</td> 
  </tr>
      <tr>
    <td>StatusMigrate</td>
    <td>Fig7 (Orange if Current, Green if True, Grey if False)</td> 
  </tr>
      <tr>
    <td>StatusSignOFf</td>
    <td>Fig7 (Orange if Current, Green if True, Grey if False)</td> 
  </tr>
      <tr>
    <td>StatusSignOn</td>
    <td>Fig7 (Orange if Current, Green if True, Grey if False)</td> 
  </tr>
      <tr>
    <td>TimeZone</td>
    <td>Not to be displayed</td> 
  </tr>
      <tr>
    <td>TotalPercent</td>
    <td>Fig8</td> 
  </tr>
        <tr>
    <td>TotalCloudServices</td>
    <td>Fig9</td> 
  </tr>
        <tr>
    <td>TotalVMs</td>
    <td>Fig10</td> 
  </tr>
        <tr>
    <td>TotalTBs</td>
    <td>Fig11</td> 
  </tr>
          <tr>
    <td>SupportNumber</td>
    <td>Fig12</td> 
  </tr>
</table>

<p><p>![alt tag](https://raw.githubusercontent.com/AKonCloud/MigStatus/master/app/MigStatus/MigStatusSec1.png)
<p><b>Row Key = All Other</b> – Row Key Information
<br>datastdarm.vhds.APPL-20160630-154426.vhd
<br>datastdarm – Storage Account Name
<br>vhds – Container Name
<br>APPL-20160630-154426.vhd – VHD Name
<p>All Other – Property and Value mapping to Web App
<table>
  <tr>
    <th>Property</th>
    <th>Value</th> 
  </tr>
      <tr>
    <td>CloudService</td>
    <td>Fig20</td> 
  </tr>
        <tr>
    <td>VMName</td>
    <td>Fig21</td> 
  </tr>
        <tr>
    <td>DiskName</td>
    <td>Fig22</td> 
  </tr>
        <tr>
    <td>CopiedBytes</td>
    <td>Not to be displayed</td> 
  </tr>
        <tr>
    <td>CopiedKBytes</td>
    <td>Not to be displayed</td> 
  </tr>
        <tr>
    <td>CopiedMBytes</td>
    <td>Not to be displayed</td> 
  </tr>
        <tr>
    <td>CopiedGBytes</td>
    <td>Fig23</td> 
  </tr>
        <tr>
    <td>CopiedTBytes</td>
    <td>Not to be displayed</td> 
  </tr>
        <tr>
    <td>CopiedPercent</td>
    <td>Fig24</td> 
  </tr>
        <tr>
    <td>CopyingStatus</td>
    <td>Fig25</td> 
  </tr>
        <tr>
    <td>TotalBytes</td>
    <td>Not to be displayed</td> 
  </tr>
        <tr>
    <td>TotalKBytes</td>
    <td>Not to be displayed</td> 
  </tr>
        <tr>
    <td>TotalMBytes</td>
    <td>Not to be displayed</td> 
  </tr>
        <tr>
    <td>TotalGBytes</td>
    <td>Fig26</td> 
  </tr>
        <tr>
    <td>TotalTBytes</td>
    <td>Not to be displayed</td> 
  </tr>
  </table>
<p>![alt tag](https://raw.githubusercontent.com/AKonCloud/MigStatus/master/app/MigStatus/MigStatusSec1.png)
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
