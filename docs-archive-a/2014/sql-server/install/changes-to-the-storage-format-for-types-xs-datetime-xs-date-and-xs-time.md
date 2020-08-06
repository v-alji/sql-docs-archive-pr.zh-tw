---
title: Xs： dateTime、xs： date 和 xs： time 類型之儲存格式的變更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- xs:date
- xs:time
- storage format
- DateTime
ms.assetid: b9f758df-030c-4aec-8ade-1bf904aa2c61
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e1ad0b80ee6963dde4b906a38c72e5c0fd8bab72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595515"
---
# <a name="changes-to-the-storage-format-for-types-xsdatetime-xsdate-and-xstime"></a><span data-ttu-id="69b12-102">針對 xs:dateTime、xs:date 和 xs:time 類型之儲存格式所做的變更</span><span class="sxs-lookup"><span data-stu-id="69b12-102">Changes to the storage format for types xs:dateTime, xs:date, and xs:time</span></span>
  <span data-ttu-id="69b12-103">XMLDATETIME 規則會識別您的資料庫是否包含升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 之後將成為無效的具類型 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="69b12-103">The XMLDATETIME rule identifies whether or not your databases contain typed XML data that will become invalid after upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="69b12-104">元件</span><span class="sxs-lookup"><span data-stu-id="69b12-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="69b12-105">描述</span><span class="sxs-lookup"><span data-stu-id="69b12-105">Description</span></span>  
 <span data-ttu-id="69b12-106">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]類型 xs： dateTime、xs： date 和 xs： time 的中的儲存格式已變更為支援具有或不含時區資訊的值，並允許保留時區。</span><span class="sxs-lookup"><span data-stu-id="69b12-106">The storage format in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] for types xs:dateTime, xs:date, and xs:time has been changed to support values with or without time zone information and to allow for preservation of the time zone.</span></span>  
  
 <span data-ttu-id="69b12-107">如果 XML 結構描述集合參考其中一種類型，在升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 之後，與此集合相關聯之所有資料行的 XML 索引都將停用。</span><span class="sxs-lookup"><span data-stu-id="69b12-107">If an XML Schema Collection references one of those types, XML indexes on all columns that are associated with the collection will be disabled after upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="69b12-108">您將能夠使用 SELECT 及/或 XQUERIES 來查詢它們，但是無法使用 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="69b12-108">You will be able to query them by using SELECT and/or XQUERIES, but the XML index will not be used.</span></span> <span data-ttu-id="69b12-109">如果遇到負的年份值，將產生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="69b12-109">If a negative year value is encountered, a runtime error will result.</span></span>  
  
 <span data-ttu-id="69b12-110">此外，[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 不支援含有負年份的值。</span><span class="sxs-lookup"><span data-stu-id="69b12-110">Additionally, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] does not support values with negative years.</span></span>  
  
 <span data-ttu-id="69b12-111">XMLDATETIME 規則會檢查是否有任何 XML 結構描述集合參考其中一個受影響的類型，以及是否有任何 XML 資料行具有這類集合的類型。</span><span class="sxs-lookup"><span data-stu-id="69b12-111">The XMLDATETIME rule checks if any of your XML Schema Collections reference one of the affected types and if there are any XML columns typed by such collections.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="69b12-112">更正動作</span><span class="sxs-lookup"><span data-stu-id="69b12-112">Corrective Action</span></span>  
 <span data-ttu-id="69b12-113">如果 XMLDATETIME 規則確認您擁有根據參考 xs:date、xs:time 或 xs:dateTime 的結構描述集合設定類型的 XML 資料行，您必須先找出資料中是否有含有負年份的值。</span><span class="sxs-lookup"><span data-stu-id="69b12-113">If the XMLDATETIME rule confirms that you have XML columns typed according to a schema collection that references xs:date, xs:time or xs:dateTime, you must first find out whether or not there are any values with negative years in your data.</span></span> <span data-ttu-id="69b12-114">如果存在這類值，就會讓您無法在升級之後重建 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="69b12-114">The presence of such values would prevent you from rebuilding your XML indexes after upgrading.</span></span>  
  
 <span data-ttu-id="69b12-115">下列查詢將會搜尋參考受影響類型的 XML 結構描述集合以及每個具類型的 XML 資料行。</span><span class="sxs-lookup"><span data-stu-id="69b12-115">The following query will search for XML schema collections that reference the affected types and for each typed XML column.</span></span> <span data-ttu-id="69b12-116">這會告訴您含有負年份值的執行個體是否存在。</span><span class="sxs-lookup"><span data-stu-id="69b12-116">This will tell you whether or not there are instances with negative year values.</span></span>  
  
```sql
CREATE PROCEDURE DateTimeInvestigation(@withdata bit)  
-- @withdata = 0: only get the affected meta data information  
-- @withdata = 1: get the affected meta data and instance information  
AS  
BEGIN  
-- First get XML containing all schema collections containing affected element and attributes  
-- components (model groups?)   
-- and columns that are affected by the schema collections.   
CREATE table #_dt_collector(x xml);   
;with dttypes as  
  (SELECT * FROM sys.xml_schema_components   
   where base_xml_component_id IN   
      (SELECT xml_component_id   
       FROM sys.xml_schema_types   
       where (name='dateTime' or name='date') and kind='P'  
      )   
   union all  
   SELECT * FROM sys.xml_schema_components  
   where xml_component_id IN   
      (SELECT xml_component_id   
       FROM sys.xml_schema_types   
       where (name='dateTime' or name='date') and kind='P'  
       or kind='N' or kind='Z')   
   ),   
dtplaced as  
  (SELECT scp.*   
   FROM sys.xml_schema_component_placements scp   
   JOIN dttypes on scp.placed_xml_component_id=dttypes.xml_component_id  
  )   
insert into #_dt_collector SELECT x FROM (SELECT  
  xsc.xml_collection_id as "@collid"  
, s.name as "@schema"  
, xscol.name as "@name"  
, count(xsc.xml_component_id) as "@affected_elems_and_attrs"  
, (SELECT S.Name as "@schema", T.Name as "@table"  
        , C.Name as "@column"   
   FROM sys.columns C   
   JOIN sys.tables T ON C.object_id = T.object_id  
   JOIN sys.schemas S ON S.schema_id = T.schema_id  
   WHERE C.xml_collection_id = xsc.xml_collection_id  
   FOR XML PATH('Columns'), TYPE  
  )   
FROM sys.xml_schema_components xsc  
JOIN dtplaced on xsc.xml_component_id=dtplaced.xml_component_id  
JOIN sys.xml_schema_collections xscol on xsc.xml_collection_id =xscol.xml_collection_id  
JOIN sys.schemas s on xscol.schema_id=s.schema_id  
group by xsc.xml_collection_id, s.name, xscol.name  
FOR XML PATH('XML_Schema_Collections'), TYPE) as T(x);   
if (@withdata = 0)    
  BEGIN  
  SELECT x as "*" FROM #_dt_collector for xml path(''), root('data');   
  drop table #_dt_collector;   
  return;   
  END;   
-- Declare cursor to find all columns bound to the schema collections  
DECLARE C CURSOR FOR  
SELECT S.Name, T.Name, C.Name   
FROM sys.columns C   
JOIN sys.tables T ON C.object_id = T.object_id  
JOIN sys.schemas S ON S.schema_id = T.schema_id  
WHERE C.xml_collection_id  
IN (SELECT distinct xsc.xml_collection_id  
    FROM sys.xml_schema_components xsc  
    JOIN (SELECT scp.*   
          FROM sys.xml_schema_component_placements scp   
          JOIN (SELECT * FROM sys.xml_schema_components   
                where base_xml_component_id    
                in (SELECT xml_component_id   
                    FROM sys.xml_schema_types   
                    where (name='dateTime' or name='date') and kind='P'  
                   )   
                union all  
                SELECT * FROM sys.xml_schema_components  
                where xml_component_id   
                in (SELECT xml_component_id   
                    FROM sys.xml_schema_types   
                    where (name='dateTime' or name='date') and kind='P'  
                    or kind='N' or kind='Z')   
               ) dttypes on scp.placed_xml_component_id=dttypes.xml_component_id  
          ) dtplaced on xsc.xml_component_id=dtplaced.xml_component_id);   
DECLARE @SchemaName nvarchar(max);   
DECLARE @TableName nvarchar(max);   
DECLARE @ColumnName nvarchar(max);   
DECLARE @strSQL nvarchar(MAX);   
OPEN C;   
FETCH NEXT FROM C INTO @SchemaName, @TableName, @ColumnName;   
WHILE (@@FETCH_STATUS = 0)   
BEGIN  
      SET @strSQL = 'INSERT INTO #_dt_collector SELECT x FROM ( ';   
      SET @strSQL = @strSQL +    
                    'SELECT ''' + @SchemaName + '.' + @TableName + '.' + @ColumnName   
                  + ''' as "@Column", ';   
      SET @strSQL = @strSQL +    
      'sum(' + @ColumnName + '.value(''count(//*[. instance of element(*,xs:dateTime?)])'', ''bigint'')) as "@dT_elements"  
     , sum(' + @ColumnName + '.value(''count(//*[. instance of element(*,xs:dateTime?)][substring(string(.),1,1) ="-"])'', ''bigint'')) as "@neg_dT_elements"  
     , sum(' + @ColumnName + '.value(''count(//*[. instance of element(*,xs:date?)])'', ''bigint'')) as "@date_elements"  
     , sum(' + @ColumnName + '.value(''count(//*[. instance of element(*,xs:date?)][substring(string(.),1,1) ="-"])'', ''bigint'')) as "@neg_date_elements"   
     , sum(' + @ColumnName + '.value(''count(for $d in //@*, $v in data($d)  
                      where $v instance of xs:dateTime?   
                      return 1)'', ''bigint'')) as "@dT_attributes"   
     , sum(' + @ColumnName + '.value(''count(for $d in //@*, $v in data($d)   
                      where $v instance of xs:dateTime?   
                      and substring(string($v),1,1)= "-"  
                      return 1)'', ''bigint'')) as "@neg_dt_attributes"  
     , sum(' + @ColumnName + '.value(''count(for $d in //@*, $v in data($d)   
                      where $v instance of xs:date?   
                      return 1)'', ''bigint'')) as "@date_attributes"   
     , sum('+ @ColumnName + '.value(''count(for $d in //@*, $v in data($d)   
                      where $v instance of xs:date?   
                      and substring(string($v),1,1)= "-"  
                      return 1)'', ''bigint'')) as "@neg_date_attributes"'  
      + ' FROM ' + @SchemaName + '.' + @TableName  
      + ' FOR XML PATH(''data''), type) T(x)';   
      --SELECT @strSQL;   
      EXEC sp_executesql @strSQL;   
      FETCH NEXT FROM C INTO @SchemaName, @TableName, @ColumnName;   
END;   
CLOSE C;   
DEALLOCATE C;   
SELECT x as "*" FROM #_dt_collector for xml path(''), root('data');   
drop table #_dt_collector;   
END;   
go  
-- Get the dependent columns per affected XML Schema Collection and the  
-- number of affected values  
EXECUTE DateTimeInvestigation 1;   
```  
  
 <span data-ttu-id="69b12-117">如果找到負的年份值，您便擁有多種解決方案：</span><span class="sxs-lookup"><span data-stu-id="69b12-117">If negative year values are found, you have multiple solutions:</span></span>  
  
-   <span data-ttu-id="69b12-118">刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="69b12-118">Delete the rows.</span></span>  
  
-   <span data-ttu-id="69b12-119">更新這些值。</span><span class="sxs-lookup"><span data-stu-id="69b12-119">Update those values.</span></span>  
  
-   <span data-ttu-id="69b12-120">清除整個 XML 資料行。</span><span class="sxs-lookup"><span data-stu-id="69b12-120">Clear the entire XML column.</span></span>  
  
-   <span data-ttu-id="69b12-121">以不使用 xs:date 或 xs:dateTime (例如，使用 xs:string) 的結構描述集合，重新設定 XML 資料行的類型。</span><span class="sxs-lookup"><span data-stu-id="69b12-121">Retype the XML column with a schema collection that doesn't use xs:date or xs:dateTime (use xs:string for example)</span></span>  
  
 <span data-ttu-id="69b12-122">在您已解決負年份的問題之後，就可以升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="69b12-122">After you have reconciled negative year issues, you can upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="69b12-123">若要在升級之後於 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中使用 XML 索引，您必須針對使用 xs:date、xs:time 或 xs:dateTime 的資料行重建 XML 索引或重新設定 XML 資料行的類型。</span><span class="sxs-lookup"><span data-stu-id="69b12-123">To use XML indexes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] after the upgrade, you must rebuild XML indexes or retype XML columns for all columns that use xs:date, xs:time or xs:dateTime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b12-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69b12-124">See Also</span></span>  
 [<span data-ttu-id="69b12-125">資料庫引擎升級問題</span><span class="sxs-lookup"><span data-stu-id="69b12-125">Database Engine Upgrade Issues</span></span>](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
  
