---
title: FOR XML 安全性考慮 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- client-side XML formatting
- FOR XML clause, security
- server-side XML formatting
- AUTO mode
- security [SQLXML], FOR XML
ms.assetid: facba279-df93-475b-ad43-0043dc5bae03
author: rothja
ms.author: jroth
ms.openlocfilehash: 9a64fa61848e4b5435b2aa944c53953a8c083ab6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598780"
---
# <a name="for-xml-security-considerations-sqlxml-40"></a><span data-ttu-id="af51a-102">FOR XML 安全性考量 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="af51a-102">FOR XML Security Considerations (SQLXML 4.0)</span></span>
  <span data-ttu-id="af51a-103">FOR XML AUTO 模式會產生 XML 階層，在此階層中，元素名稱會對應到資料表名稱，而屬性名稱會對應到資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="af51a-103">The FOR XML AUTO mode generates an XML hierarchy in which element names map to table names and attribute names map to column names.</span></span> <span data-ttu-id="af51a-104">這樣會公開資料庫資料表和資料行資訊。</span><span class="sxs-lookup"><span data-stu-id="af51a-104">This exposes the database table and column information.</span></span> <span data-ttu-id="af51a-105">當您在查詢中指定資料表和資料行別名來使用 AUTO 模式 (伺服器端格式化) 時，可以隱藏資料庫資訊。</span><span class="sxs-lookup"><span data-stu-id="af51a-105">You can hide the database information when you use AUTO mode (server-side formatting) by specifying table and column aliases in the query.</span></span> <span data-ttu-id="af51a-106">這些別名會當做產生之 XML 文件中的元素和屬性名稱來傳回。</span><span class="sxs-lookup"><span data-stu-id="af51a-106">These aliases are returned in the resulting XML document as element and attribute names.</span></span>  
  
 <span data-ttu-id="af51a-107">例如，下列查詢會指定 AUTO 模式；因此，XML 格式化是在伺服器上完成：</span><span class="sxs-lookup"><span data-stu-id="af51a-107">For example, the following query specifies AUTO mode; therefore, the XML formatting is done on the server:</span></span>  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 <span data-ttu-id="af51a-108">在產生的 XML 文件中，這些別名是用於元素和屬性名稱：</span><span class="sxs-lookup"><span data-stu-id="af51a-108">In the resulting XML document, the aliases are used for element and attribute names:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <C F="Nancy" L="Fuller" />   
  <CE F="Andrew" L="Peacock" />   
  <C F="Janet" L="Leverling" />   
  ...  
</root>  
```  
  
 <span data-ttu-id="af51a-109">當您使用 NESTED 模式 (用戶端格式化) 時，只有產生之 XML 文件中的屬性才會傳回別名。</span><span class="sxs-lookup"><span data-stu-id="af51a-109">When you use NESTED mode (client-side formatting), aliases are returned only for attributes in the resulting XML document.</span></span> <span data-ttu-id="af51a-110">基底資料表的名稱一定會當做元素名稱傳回。</span><span class="sxs-lookup"><span data-stu-id="af51a-110">The names of the base tables are always returned as element names.</span></span> <span data-ttu-id="af51a-111">例如，下列查詢會指定 NESTED 模式。</span><span class="sxs-lookup"><span data-stu-id="af51a-111">For example, the following query specifies NESTED mode.</span></span>  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 <span data-ttu-id="af51a-112">在產生的 XML 文件中，基底資料表的名稱會當做元素名稱傳回，而且不會使用資料表別名：</span><span class="sxs-lookup"><span data-stu-id="af51a-112">In the resulting XML document, the names of the base tables are returned as element names and table aliases are not used:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Person.Contact F="Nancy" L="Fuller" />   
  <Person.Contact F="Andrew" L="Peacock" />   
  <Person.Contact F="Janet" L="Leverling" />   
       ...  
</root>  
```  
  
  
