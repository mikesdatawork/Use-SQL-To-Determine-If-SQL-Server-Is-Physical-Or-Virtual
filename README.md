![MIKES DATA WORK GIT REPO](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_01.png "Mikes Data Work")        

# Use SQL To Determine If SQL Server Is Physical Or Virtual
**Post Date: March 6, 2015**        



## Contents    
- [About Process](##About-Process)  
- [SQL Logic](#SQL-Logic)  
- [Build Info](#Build-Info)  
- [Author](#Author)  
- [License](#License)       

## About-Process

<p>Here's a quick way to determine if the server is a physical machine, or virtual machine.
This query will also return the Server Name, Machine Type, Edition, Build Number, Version Number, and Number of CPU's on the server. Keep in mind if the server is Virtual then the type of CPU's will always be logical, and not physical.
Additionally I've included the xp_cmdshell 'systeminfo' to return the full set of OS information so you can double check the query, and if necessary get the 'type' of CPU in the machine.</p>      


## SQL-Logic
```SQL
use master;
set nocount on
 
select
'Server Name' = serverproperty('computernamephysicalnetbios')
,   'Machine Type' = case sdosi.virtual_machine_type when '1' then 'Virtual Machine' when '0' then 'Physical Machine' end , 'Edition' = serverproperty('edition')
,   'Build' = serverproperty('productlevel')
,   'Version Number'    = serverproperty('productversion')
,   'CPU Count' = sdosi.cpu_count
from
sys.dm_os_sys_info sdosi;
 
exec xp_cmdshell 'systeminfo';
```
Hope this is useful. 


[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

[![Gist](https://img.shields.io/badge/Gist-MikesDataWork-<COLOR>.svg)](https://gist.github.com/mikesdatawork)
[![Twitter](https://img.shields.io/badge/Twitter-MikesDataWork-<COLOR>.svg)](https://twitter.com/mikesdatawork)
[![Wordpress](https://img.shields.io/badge/Wordpress-MikesDataWork-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

     
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Mikes Data Work](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_02.png "Mikes Data Work")

