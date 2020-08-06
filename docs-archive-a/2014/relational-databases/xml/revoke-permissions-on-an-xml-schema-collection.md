---
title: 撤銷 XML 結構描述集合上的權限 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- revoking permissions [SQL Server]
ms.assetid: 4e542b70-2d56-4a65-8a39-96a1ed477ca6
author: rothja
ms.author: jroth
ms.openlocfilehash: 3ab37c915f14207376e0c4a9582611bf8e65e0d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688630"
---
# <a name="revoke-permissions-on-an-xml-schema-collection"></a><span data-ttu-id="4f2fa-102">撤銷 XML 結構描述集合上的權限</span><span class="sxs-lookup"><span data-stu-id="4f2fa-102">Revoke Permissions on an XML Schema Collection</span></span>
  <span data-ttu-id="4f2fa-103">建立 XML 結構描述集合的權限可以使用下列其中一種方式來撤銷：</span><span class="sxs-lookup"><span data-stu-id="4f2fa-103">The permission to create an XML schema collection can be revoked by using one of the following:</span></span>  
  
-   <span data-ttu-id="4f2fa-104">撤銷關聯式結構描述的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-104">Revoke the ALTER permission for the relational schema.</span></span> <span data-ttu-id="4f2fa-105">然後，主體便無法在關聯式結構描述中建立 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-105">Then, the principal cannot create an XML schema collection in the relational schema.</span></span> <span data-ttu-id="4f2fa-106">但是，主體仍然可以在同一資料庫的其他關聯式結構描述中建立 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-106">However, the principal can still do so in other relational schemas in the same database.</span></span>  
  
-   <span data-ttu-id="4f2fa-107">撤銷資料庫上主體的 ALTER ANY SCHEMA 權限。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-107">Revoke the ALTER ANY SCHEMA permission on the database for the principal.</span></span> <span data-ttu-id="4f2fa-108">然後，主體便無法在資料庫中的任何位置建立 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-108">Then, the principal cannot create an XML schema collection anywhere in the database.</span></span>  
  
-   <span data-ttu-id="4f2fa-109">撤銷資料庫上主體的 CREATE XML SCHEMA COLLECTION 或 ALTER XML SCHEMA COLLECTION 權限。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-109">Revoke the CREATE XML SCHEMA COLLECTION or ALTER XML SCHEMA COLLECTION permission on the database for the principal.</span></span> <span data-ttu-id="4f2fa-110">這樣可以防止主體於資料庫中匯入 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-110">This prevents the principal from importing an XML schema collection within the database.</span></span> <span data-ttu-id="4f2fa-111">撤銷資料庫上的 ALTER 或 CONTROL 權限也有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-111">Revoking the ALTER or CONTROL permission on the database has the same effect.</span></span>  
  
## <a name="revoking-permissions-on-an-existing-xml-schema-collection-object"></a><span data-ttu-id="4f2fa-112">撤銷現有 XML 結構描述集合物件上的權限</span><span class="sxs-lookup"><span data-stu-id="4f2fa-112">Revoking Permissions on an Existing XML Schema Collection Object</span></span>  
 <span data-ttu-id="4f2fa-113">下列為可以在 XML 結構描述集合上撤銷的權限，以及其結果：</span><span class="sxs-lookup"><span data-stu-id="4f2fa-113">Following are the permissions that can be revoked on an XML schema collection and the results:</span></span>  
  
-   <span data-ttu-id="4f2fa-114">撤銷 ALTER 權限會讓主體無法修改 XML 結構描述集合的內容。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-114">Revoking the ALTER permission revokes a principal's ability to modify the content of the XML schema collection.</span></span>  
  
-   <span data-ttu-id="4f2fa-115">撤銷 TAKE OWNERSHIP 權限會讓主體無法轉移 XML 結構描述集合的擁有權。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-115">Revoking the TAKE OWNERSHIP permission revokes a principal's ability to transfer ownership of the XML schema collection.</span></span>  
  
-   <span data-ttu-id="4f2fa-116">撤銷 REFERENCES 權限會讓主體無法使用 XML 結構描述集合設定 xml 類型的資料行和參數類型，或約束 xml 類型的資料行和參數 (資料行限於資料表和檢視)。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-116">Revoking the REFERENCES permission revokes a principal's ability to use the XML schema collection for typing or constraining xml type columns, in tables and views, and parameters.</span></span> <span data-ttu-id="4f2fa-117">這樣也會撤銷從其他 XML 結構描述集合參考此結構描述集合的權限。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-117">It also revokes the permission to refer to this schema collection from other XML schema collections.</span></span>  
  
-   <span data-ttu-id="4f2fa-118">撤銷 VIEW DEFINITION 權限會讓主體無法檢視 XML 結構描述集合的內容。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-118">Revoking the VIEW DEFINITION permission revokes a principal's ability to view the contents of an XML schema collection.</span></span>  
  
-   <span data-ttu-id="4f2fa-119">撤銷 EXECUTE 權限會讓主體無法插入或更新具類型或受 XML 集合所約束之資料行、變數和參數中的值。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-119">Revoking the EXECUTE permission revokes a principal's ability to insert or update values in columns, variables, and parameters that are typed or constrained by the XML collection.</span></span> <span data-ttu-id="4f2fa-120">這樣也撤銷了查詢這種 **xml** 類型之資料行、變數或參數的能力。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-120">It also revokes the ability to query such **xml** type columns, variables, or parameters.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4f2fa-121">範例</span><span class="sxs-lookup"><span data-stu-id="4f2fa-121">Examples</span></span>  
 <span data-ttu-id="4f2fa-122">下列範例中的狀況說明 XML 結構描述權限如何運作。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-122">The scenarios in the following examples illustrate how XML schema permissions work.</span></span> <span data-ttu-id="4f2fa-123">每個範例都會建立所需的測試資料庫、關聯式結構描述和登入。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-123">Each example creates the necessary test database, relational schemas, and logins.</span></span> <span data-ttu-id="4f2fa-124">將會授與這些登入必要的 XML 結構描述集合權限。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-124">These logins are granted the necessary XML schema collection permissions.</span></span> <span data-ttu-id="4f2fa-125">每個範例都會在結束時執行必要的清除。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-125">Each example does the necessary cleanup at the end.</span></span>  
  
### <a name="a-revoking-permissions-to-create-an-xml-schema-collection"></a><span data-ttu-id="4f2fa-126">A.</span><span class="sxs-lookup"><span data-stu-id="4f2fa-126">A.</span></span> <span data-ttu-id="4f2fa-127">撤銷可建立 XML 結構描述集合的權限</span><span class="sxs-lookup"><span data-stu-id="4f2fa-127">Revoking permissions to create an XML schema collection</span></span>  
 <span data-ttu-id="4f2fa-128">這個範例將建立登入和範例資料庫，</span><span class="sxs-lookup"><span data-stu-id="4f2fa-128">This example creates a login and a sample database.</span></span> <span data-ttu-id="4f2fa-129">並在資料庫中加入關聯式結構描述。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-129">It also adds a relational schema in the database.</span></span> <span data-ttu-id="4f2fa-130">首先，登入會被授與兩個關聯式結構描述上的 ALTER 權限，以及其他建立 XML 結構描述集合的必要權限。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-130">Initially, the login is granted ALTER permission on both relational schemas and other necessary permissions to create XML schema collections.</span></span> <span data-ttu-id="4f2fa-131">然後，此範例會撤銷資料庫中其中一個關聯式結構描述上的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-131">The example then revokes the ALTER permission on one of the relational schemas in the database.</span></span> <span data-ttu-id="4f2fa-132">這樣登入就無法建立 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="4f2fa-132">This prevents the login from creating an XML schema collection.</span></span>  
  
```  
setuser  
go  
create login TestLogin1 with password='SQLSvrPwd1'  
go  
create database SampleDBForSchemaPermissions  
go  
use SampleDBForSchemaPermissions  
go  
-- Create another relational schema in the db (in addition to dbo schema)  
CREATE SCHEMA myOtherDBSchema  
go  
CREATE USER TestLogin1  
go  
-- For TestLogin1 to create/import XML schema collection, following  
-- permission needed  
-- CREATE XML SCHEMA is a database level permission  
GRANT CREATE XML SCHEMA COLLECTION TO TestLogin1  
go  
GRANT ALTER ON SCHEMA::myOtherDBSchema TO TestLogin1  
go  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
go  
-- Now TestLogin1 can import an XML schema collection in both relational schemas.  
setuser 'TestLogin1'  
go  
CREATE XML SCHEMA COLLECTION dbo.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
go  
-- TestLogin1 can create XML schema collection in myOtherDBSchema relational schema  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
go  
-- Let us drop XML schema collections from both relational schemas  
DROP XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection  
go  
DROP XML SCHEMA COLLECTION dbo.myTestSchemaCollection  
go  
-- now REVOKE permission from TestLogin1 to alter myOtherDBSchema  
setuser  
go  
REVOKE ALTER ON SCHEMA::myOtherDBSchema FROM TestLogin1  
go  
-- now TestLogin1 cannot create xml schema collection in myOtherDBSchema  
setuser 'TestLogin1'  
go  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
go  
  
-- TestLogin1 can still create XML schema collections in dbo  
-- It cannot create XML schema collections anywhere in the database  
-- if we REVOKE CREATE XML SCHEMA COLLECTION permission  
SETUSER  
go  
REVOKE CREATE XML SCHEMA COLLECTION FROM TestLogin1  
go  
  
setuser 'TestLogin1'  
go  
-- the following now should fail  
CREATE XML SCHEMA COLLECTION dbo.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
go  
  
-- Final cleanup  
SETUSER  
go  
USE master  
go  
DROP DATABASE SampleDBForSchemaPermissions  
go  
DROP LOGIN TestLogin1  
Go  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f2fa-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f2fa-133">See Also</span></span>  
 <span data-ttu-id="4f2fa-134">[XML 資料 &#40;SQL Server&#41;](xml-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4f2fa-134">[XML Data &#40;SQL Server&#41;](xml-data-sql-server.md) </span></span>  
 <span data-ttu-id="4f2fa-135">[比較具類型的 XML 與不具類型的 XML](compare-typed-xml-to-untyped-xml.md) </span><span class="sxs-lookup"><span data-stu-id="4f2fa-135">[Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md) </span></span>  
 <span data-ttu-id="4f2fa-136">[XML 結構描述集合 &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4f2fa-136">[XML Schema Collections &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span></span>  
 [<span data-ttu-id="4f2fa-137">伺服器上 XML 結構描述集合的需求與限制</span><span class="sxs-lookup"><span data-stu-id="4f2fa-137">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
