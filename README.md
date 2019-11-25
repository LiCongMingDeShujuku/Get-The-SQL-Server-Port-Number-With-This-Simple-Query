![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 使用此简单查询获取SQL Server端口号
#### Get The SQL Server Port Number With This Simple Query
**发布-日期: 2015年09月16日 (评论)**

![#](images/##############?raw=true "#")

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
使用此简单查询获取SQL Server端口号

## English
Get the SQL Server Port Number with this Simple Query

---
## Logic
```SQL
use master;
set nocount on
 
declare @key    varchar(255)
declare @port   varchar(50)
 
-- get the port number using the serverproperty function and xp_regread
-- 使用serverproperty函数和xp_regread获取端口号
if charindex('\',convert(char(255), serverproperty('servername')),0) <>0
    begin
        set @key = 'software\microsoft\microsoft sql server\' + @@servicename + '\mssqlserver\supersocketnetlib\tcp'
    end
else
    begin
        set @key = 'software\microsoft\mssqlserver\mssqlserver\supersocketnetlib\tcp'
    end
exec master..xp_regread
    @rootkey    = 'hkey_local_machine'
,   @key        = @key
,   @value_name = 'tcpport'
,   @value      = @port output
 
select
    'ServerName'    = @@servername
,   'Port'      = convert(varchar(10), @port)


```



[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

