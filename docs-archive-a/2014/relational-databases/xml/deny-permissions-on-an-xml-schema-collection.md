---
title: 拒絕 XML 結構描述集合的權限 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- denying permissions [SQL Server], XML server collections
ms.assetid: e2b300b0-e734-4c43-a4da-c78e6e5d4fba
author: rothja
ms.author: jroth
ms.openlocfilehash: 0791a9bd9c7f6b323886a38bed27bea84940770d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585177"
---
# <a name="deny-permissions-on-an-xml-schema-collection"></a><span data-ttu-id="419ee-102">拒絕 XML 結構描述集合的權限</span><span class="sxs-lookup"><span data-stu-id="419ee-102">Deny Permissions on an XML Schema Collection</span></span>
  <span data-ttu-id="419ee-103">可以拒絕建立新 XML 結構描述集合或使用現有結構描述集合的權限。</span><span class="sxs-lookup"><span data-stu-id="419ee-103">Permission can be denied to either create a new XML schema collection or use an existing one.</span></span>  
  
## <a name="denying-permission-to-create-an-xml-schema-collection"></a><span data-ttu-id="419ee-104">對於建立 XML 結構描述集合的拒絕權限</span><span class="sxs-lookup"><span data-stu-id="419ee-104">Denying Permission to Create an XML Schema Collection</span></span>  
 <span data-ttu-id="419ee-105">您可以用下列方式來拒絕建立 XML 結構描述集合的權限：</span><span class="sxs-lookup"><span data-stu-id="419ee-105">You can deny permission to create an XML schema collection in the following ways:</span></span>  
  
-   <span data-ttu-id="419ee-106">拒絕對關聯式結構描述的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="419ee-106">Deny ALTER permission on the relational schema.</span></span>  
  
-   <span data-ttu-id="419ee-107">拒絕對關聯式結構描述的 CONTROL，以拒絕對於關聯式結構描述以及所有包含物件的所有權限。</span><span class="sxs-lookup"><span data-stu-id="419ee-107">Deny CONTROL on the relational schema to deny all permissions on the relational schema and on all the contained objects.</span></span>  
  
-   <span data-ttu-id="419ee-108">拒絕對資料庫的 ALTER ANY SCHEMA。</span><span class="sxs-lookup"><span data-stu-id="419ee-108">Deny ALTER ANY SCHEMA on the database.</span></span> <span data-ttu-id="419ee-109">在此情況下，主體將無法在資料庫中的任何位置建立 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="419ee-109">In this case, the principal cannot create an XML schema collection anywhere in the database.</span></span> <span data-ttu-id="419ee-110">請注意拒絕資料庫的 ALTER 或 CONTROL 權限，將會拒絕資料庫中所有物件的所有權限。</span><span class="sxs-lookup"><span data-stu-id="419ee-110">Note also that denying ALTER or CONTROL permission on the database denies all permissions on all objects in the database.</span></span>  
  
## <a name="denying-permissions-on-an-xml-schema-collection-object"></a><span data-ttu-id="419ee-111">XML 結構描述集合物件的拒絕權限</span><span class="sxs-lookup"><span data-stu-id="419ee-111">Denying Permissions on an XML Schema Collection Object</span></span>  
 <span data-ttu-id="419ee-112">以下是可拒絕現有 XML 結構描述集合與結果的權限：</span><span class="sxs-lookup"><span data-stu-id="419ee-112">Following are the permission that can be denied on an existing XML schema collection and the results:</span></span>  
  
-   <span data-ttu-id="419ee-113">拒絕 ALTER 權限可拒絕主體修改 XML 結構描述集合的內容。</span><span class="sxs-lookup"><span data-stu-id="419ee-113">Denying the ALTER permission denies the principal the ability to modify the contents of the XML schema collection.</span></span>  
  
-   <span data-ttu-id="419ee-114">拒絕 CONTROL 權限可拒絕主體執行 XML 結構描述集合的任何作業。</span><span class="sxs-lookup"><span data-stu-id="419ee-114">Denying the CONTROL permission denies the principal the ability to perform any operation on the XML schema collection.</span></span>  
  
-   <span data-ttu-id="419ee-115">拒絕 REFERENCES 權限可拒絕主體使用結構描述集合，來約束 xml 類型資料行與參數或設定其類型。</span><span class="sxs-lookup"><span data-stu-id="419ee-115">Denying the REFERENCES permission denies the principal the ability to type or constrain xml type columns and parameters using the XML schema collection.</span></span> <span data-ttu-id="419ee-116">它也會拒絕主體從其他 XML 結構描述集合參考此 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="419ee-116">It also denies the principal the ability to refer to this XML schema collection from other XML schema collections.</span></span>  
  
-   <span data-ttu-id="419ee-117">拒絕 VIEW DEFINITION 權限可拒絕主體檢視 XML 結構描述集合的內容。</span><span class="sxs-lookup"><span data-stu-id="419ee-117">Denying the VIEW DEFINITION permission denies the principal the ability to view the contents of an XML schema collection.</span></span>  
  
-   <span data-ttu-id="419ee-118">拒絕 EXECUTE 權限可拒絕主體在 XML 結構描述集合所約束或設定其類型的資料行、變數及參數中插入或更新值。</span><span class="sxs-lookup"><span data-stu-id="419ee-118">Denying the EXECUTE permission denies the principal the ability to insert or update the values in columns, variables, and parameters that are typed or constrained by the XML schema collection.</span></span> <span data-ttu-id="419ee-119">它也會拒絕主體在相同的 xml 類型資料行與變數中查詢值。</span><span class="sxs-lookup"><span data-stu-id="419ee-119">It also denies the principal the ability to query the values in those same xml type columns and variables.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="419ee-120">範例</span><span class="sxs-lookup"><span data-stu-id="419ee-120">Examples</span></span>  
 <span data-ttu-id="419ee-121">下列範例中的狀況顯示 XML 結構描述權限的運作方式。</span><span class="sxs-lookup"><span data-stu-id="419ee-121">The scenarios in the following examples show how XML schema permissions work.</span></span> <span data-ttu-id="419ee-122">每個範例都會建立所需的測試資料庫、關聯式結構描述和登入。</span><span class="sxs-lookup"><span data-stu-id="419ee-122">Each example creates the necessary test database, relational schemas, and logins.</span></span> <span data-ttu-id="419ee-123">將會授與這些登入必要的 XML 結構描述集合權限。</span><span class="sxs-lookup"><span data-stu-id="419ee-123">These logins are granted the necessary XML schema collection permissions.</span></span> <span data-ttu-id="419ee-124">每個範例都會在結束時執行必要的清除。</span><span class="sxs-lookup"><span data-stu-id="419ee-124">Each example does the necessary cleanup at the end.</span></span>  
  
### <a name="a-preventing-a-user-from-creating-an-xml-schema-collection"></a><span data-ttu-id="419ee-125">A.</span><span class="sxs-lookup"><span data-stu-id="419ee-125">A.</span></span> <span data-ttu-id="419ee-126">防止使用者建立 XML 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="419ee-126">Preventing a user from creating an XML schema collection</span></span>  
 <span data-ttu-id="419ee-127">有一個方法可防止使用者建立 XML 結構描述集合，就是拒絕對關聯式結構描述的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="419ee-127">One of the ways to prevent a user from creating an XML schema collection is by denying the ALTER permission on a relational schema.</span></span> <span data-ttu-id="419ee-128">下列範例會顯示這一點。</span><span class="sxs-lookup"><span data-stu-id="419ee-128">This is shown in the following example.</span></span>  
  
 <span data-ttu-id="419ee-129">本範例會建立使用者 `TestLogin1`和資料庫。</span><span class="sxs-lookup"><span data-stu-id="419ee-129">The example creates a user, `TestLogin1`, and a database.</span></span> <span data-ttu-id="419ee-130">除了 `dbo` 結構描述之外，它也在資料庫中建立關聯式結構描述。</span><span class="sxs-lookup"><span data-stu-id="419ee-130">It also creates a relational schema, in addition to the `dbo` schema, in the database.</span></span> <span data-ttu-id="419ee-131">一開始， `CREATE XML SCHEMA` 權限允許使用者在資料庫中的任何位置建立結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="419ee-131">Initially, the `CREATE XML SCHEMA` permission allows the user to create a schema collection anywhere in the database.</span></span> <span data-ttu-id="419ee-132">此範例接著會在其中一個關聯式結構描述上，拒絕使用者的 `ALTER` 權限。</span><span class="sxs-lookup"><span data-stu-id="419ee-132">The example then denies `ALTER` permission to the user on one of the relational schemas.</span></span> <span data-ttu-id="419ee-133">這將可防止使用者在該關聯式結構描述中建立 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="419ee-133">This prevents the user from creating an XML schema collection in that relational schema.</span></span>  
  
```  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
-- Create another relational schema in the database.  
CREATE SCHEMA myOtherDBSchema  
GO  
CREATE USER TestLogin1  
GO  
-- For TestLogin1 to create/import XML schema collection, following  
-- permission needed.  
-- Database-level permissions  
GRANT CREATE XML SCHEMA COLLECTION TO TestLogin1  
GO  
GRANT ALTER ANY SCHEMA TO TestLogin1  
GO  
-- Now TestLogin1 can import an XML schema collection.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
DROP XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection  
GO  
-- Now deny permission from TestLogin1 to alter myOtherDBSchema.  
setuser  
GO  
DENY ALTER ON SCHEMA::myOtherDBSchema TO TestLogin1  
GO  
-- Now TestLogin1 cannot create xml schema collection.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
-- Final cleanup  
SETUSER  
GO  
USE master  
GO  
DROP DATABASE SampleDBForSchemaPermissions  
GO  
DROP LOGIN TestLogin1  
GO  
```  
  
### <a name="b-denying-permissions-on-an-xml-schema-collection"></a><span data-ttu-id="419ee-134">B.</span><span class="sxs-lookup"><span data-stu-id="419ee-134">B.</span></span> <span data-ttu-id="419ee-135">XML 結構描述集合的拒絕權限</span><span class="sxs-lookup"><span data-stu-id="419ee-135">Denying permissions on an XML schema collection</span></span>  
 <span data-ttu-id="419ee-136">下列範例顯示如何針對某個登入來拒絕現有 XML 結構描述集合上的特定權限。</span><span class="sxs-lookup"><span data-stu-id="419ee-136">The following example shows how a specific permission on an existing XML schema collection can be denied to a login.</span></span> <span data-ttu-id="419ee-137">在此範例中，對某個測試登入拒絕現有 XML 結構描述集合的 REFERENCES 權限。</span><span class="sxs-lookup"><span data-stu-id="419ee-137">In this example, a test login is denied REFERENCES permission on an existing XML schema collection.</span></span>  
  
 <span data-ttu-id="419ee-138">本範例會建立使用者 `TestLogin1`和資料庫。</span><span class="sxs-lookup"><span data-stu-id="419ee-138">The example creates a user, `TestLogin1`, and a database.</span></span> <span data-ttu-id="419ee-139">除了 `dbo` 結構描述之外，它也在資料庫中建立關聯式結構描述。</span><span class="sxs-lookup"><span data-stu-id="419ee-139">It also creates a relational schema, in addition to the `dbo` schema, in the database.</span></span> <span data-ttu-id="419ee-140">一開始， `CREATE XML SCHEMA` 權限允許使用者在資料庫中的任何位置建立結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="419ee-140">Initially, the `CREATE XML SCHEMA` permission allows the user to create a schema collection anywhere in the database.</span></span>  
  
 <span data-ttu-id="419ee-141">XML 結構描述集合上的 `REFERENCES` 權限能讓 `TestLogin1` 在資料表中建立具類型的 `xml` 資料行時使用結構描述。</span><span class="sxs-lookup"><span data-stu-id="419ee-141">The `REFERENCES` permission on the XML schema collection lets `TestLogin1` use the schema in creating a typed `xml` column in a table.</span></span> <span data-ttu-id="419ee-142">如果拒絕 XML 結構描述集合上的 `REFERENCES` 權限，會使得 `TestLogin1` 無法使用 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="419ee-142">If the `REFERENCES` permission on the XML schema collection is denied, it prevents the `TestLogin1` from using the XML schema collection.</span></span>  
  
```  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
-- Create another relational schema in the database.  
CREATE SCHEMA myOtherDBSchema  
GO  
CREATE USER TestLogin1  
GO  
-- For TestLogin1 to create/import XML schema collection, the following  
-- permission is required.  
-- Database-level permissions  
GRANT CREATE XML SCHEMA COLLECTION TO TestLogin1  
GO  
GRANT ALTER ANY SCHEMA TO TestLogin1  
GO  
-- Now TestLogin1 can import an XML schema collection.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
-- Grant permission to TestLogin1 to create a table and reference the XML schema collection.  
SETUSER  
GO  
GRANT CREATE TABLE TO TestLogin1  
GO  
-- The user also needs REFERENCES permission to use the XML schema collection  
-- to create a typed XML column (REFERENCES permission on the schema   
-- collection is not needed).  
GRANT REFERENCES ON XML SCHEMA COLLECTION::myOtherDBSchema.myTestSchemaCollection   
TO TestLogin1  
GO  
  
--TestLogin1 can use the schema.  
CREATE TABLE T(i int, x xml (myOtherDBSchema.myTestSchemaCollection))  
GO  
-- Drop the table.  
DROP TABLE T  
GO  
-- Now deny REFERENCES permission to TestLogin1 on the schema created previously.  
SETUSER  
GO  
DENY REFERENCES ON XML SCHEMA COLLECTION::myOtherDBSchema.myTestSchemaCollection TO TestLogin1  
  
GO  
-- Now TestLogin1 cannot create xml schema collection  
SETUSER 'TestLogin1'  
GO  
-- Following statement fails. TestLogin1 does not have REFERENCES   
-- permission on the XML schema collection.  
CREATE TABLE T(i int, x xml (myOtherDBSchema.myTestSchemaCollection))  
GO  
  
-- Final cleanup  
SETUSER  
GO  
USE master  
GO  
DROP DATABASE SampleDBForSchemaPermissions  
GO  
DROP LOGIN TestLogin1  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="419ee-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="419ee-143">See Also</span></span>  
 <span data-ttu-id="419ee-144">[比較具類型的 XML 與不具類型的 XML](compare-typed-xml-to-untyped-xml.md) </span><span class="sxs-lookup"><span data-stu-id="419ee-144">[Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md) </span></span>  
 <span data-ttu-id="419ee-145">[XML 結構描述集合 &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="419ee-145">[XML Schema Collections &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span></span>  
 <span data-ttu-id="419ee-146">[伺服器上 XML 結構描述集合的需求與限制](requirements-and-limitations-for-xml-schema-collections-on-the-server.md) </span><span class="sxs-lookup"><span data-stu-id="419ee-146">[Requirements and Limitations for XML Schema Collections on the Server](requirements-and-limitations-for-xml-schema-collections-on-the-server.md) </span></span>  
 <span data-ttu-id="419ee-147">[DENY 物件權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-object-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="419ee-147">[DENY Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-object-permissions-transact-sql) </span></span>  
 <span data-ttu-id="419ee-148">[GRANT 物件權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="419ee-148">[GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql) </span></span>  
 [<span data-ttu-id="419ee-149">XML 資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="419ee-149">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
