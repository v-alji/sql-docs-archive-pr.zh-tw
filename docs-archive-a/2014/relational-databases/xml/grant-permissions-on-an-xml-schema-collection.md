---
title: 授與 XML 結構描述集合的權限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- granting permissions [SQL Server], XML schema collections
- ALTER permission
ms.assetid: ffbb829c-3b8f-4e5d-97d9-ab4059aab0db
author: rothja
ms.author: jroth
ms.openlocfilehash: 2dc6384acb2f079245c80923e683ebe2c03d2562
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687565"
---
# <a name="grant-permissions-on-an-xml-schema-collection"></a><span data-ttu-id="91293-102">授與 XML 結構描述集合的權限</span><span class="sxs-lookup"><span data-stu-id="91293-102">Grant Permissions on an XML Schema Collection</span></span>
  <span data-ttu-id="91293-103">您可以授與建立 XML 結構描述集合的權限，也可以授與 XML 結構描述集合物件的權限。</span><span class="sxs-lookup"><span data-stu-id="91293-103">You can grant permissions to create an XML schema collection and also grant permissions on an XML schema collection object.</span></span>  
  
## <a name="granting-permission-to-create-an-xml-schema-collection"></a><span data-ttu-id="91293-104">授與建立 XML 結構描述集合的權限</span><span class="sxs-lookup"><span data-stu-id="91293-104">Granting Permission to Create an XML Schema Collection</span></span>  
 <span data-ttu-id="91293-105">若要建立 XML 結構描述集合，將需要下列權限：</span><span class="sxs-lookup"><span data-stu-id="91293-105">To create an XML schema collection, the following permissions are required:</span></span>  
  
-   <span data-ttu-id="91293-106">主體需要在資料庫層級的 CREATE XML SCHEMA COLLECTION 權限。</span><span class="sxs-lookup"><span data-stu-id="91293-106">The principal requires CREATE XML SCHEMA COLLECTION permission at the database-level.</span></span>  
  
-   <span data-ttu-id="91293-107">因為 XML 結構描述集合是以關聯式結構描述限定範圍，主體也必須擁有關聯式結構描述的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="91293-107">Because the XML schema collections are relational schema-scoped, the principal must also have ALTER permission on the relational schema.</span></span>  
  
 <span data-ttu-id="91293-108">下列權限可讓主體在伺服器的資料庫中於關聯式結構描述內建立 XML 結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="91293-108">The following permissions let a principal create an XML schema collection in a relational schema in a database on a server:</span></span>  
  
-   <span data-ttu-id="91293-109">伺服器的 CONTROL 權限</span><span class="sxs-lookup"><span data-stu-id="91293-109">CONTROL permission on the server</span></span>  
  
-   <span data-ttu-id="91293-110">伺服器的 ALTER ANY DATABASE 權限</span><span class="sxs-lookup"><span data-stu-id="91293-110">ALTER ANY DATABASE permission on the server</span></span>  
  
-   <span data-ttu-id="91293-111">資料庫的 ALTER 權限</span><span class="sxs-lookup"><span data-stu-id="91293-111">ALTER permission on the database</span></span>  
  
-   <span data-ttu-id="91293-112">資料庫的 CONTROL 權限</span><span class="sxs-lookup"><span data-stu-id="91293-112">CONTROL permission in the database</span></span>  
  
-   <span data-ttu-id="91293-113">資料庫的 ALTER ANY SCHEMA 權限和 CREATE XML SCHEMA COLLECTION 權限</span><span class="sxs-lookup"><span data-stu-id="91293-113">ALTER ANY SCHEMA permission and CREATE XML SCHEMA COLLECTION permission in the database</span></span>  
  
-   <span data-ttu-id="91293-114">關聯式結構描述的 ALTER 或 CONTROL 權限和資料庫的 CREATE XML SCHEMA COLLECTION 權限</span><span class="sxs-lookup"><span data-stu-id="91293-114">ALTER or CONTROL permission on the relational schema and CREATE XML SCHEMA COLLECTION permission in the database</span></span>  
  
 <span data-ttu-id="91293-115">這個最後一個權限的方法用於下列範例中。</span><span class="sxs-lookup"><span data-stu-id="91293-115">This last method of permissions is used in the following example.</span></span>  
  
 <span data-ttu-id="91293-116">關聯式結構描述的擁有者變成在該結構描述中建立的 XML 結構描述集合的擁有者。</span><span class="sxs-lookup"><span data-stu-id="91293-116">The owner of the relational schema becomes the owner of the XML schema collection created in that schema.</span></span> <span data-ttu-id="91293-117">此擁有者對於 XML 結構描述集合擁有完整的控制權。</span><span class="sxs-lookup"><span data-stu-id="91293-117">This owner then has full control over the XML schema collection.</span></span> <span data-ttu-id="91293-118">因此，此擁有者可修改 XML 結構描述集合、設定 xml 資料行的類型或是卸除 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="91293-118">Therefore, this owner can modify the XML schema collection, type an xml column, or drop the XML schema collection.</span></span>  
  
## <a name="granting-permissions-on-an-xml-schema-collection-object"></a><span data-ttu-id="91293-119">授與 XML 結構描述集合物件的權限</span><span class="sxs-lookup"><span data-stu-id="91293-119">Granting Permissions on an XML Schema Collection Object</span></span>  
 <span data-ttu-id="91293-120">下列權限可用於 XML 結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="91293-120">The following permissions are allowed on the XML schema collection:</span></span>  
  
-   <span data-ttu-id="91293-121">當使用 ALTER XML SCHEMA COLLECTION 陳述式修改現有 XML 結構描述集合的內容時，就需要 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="91293-121">The ALTER permission is required when modifying contents of an existing XML schema collection by using the ALTER XML SCHEMA COLLECTION statement.</span></span>  
  
-   <span data-ttu-id="91293-122">CONTROL 權限可讓使用者針對 XML 結構描述集合執行任何作業。</span><span class="sxs-lookup"><span data-stu-id="91293-122">The CONTROL permission lets a user perform any operation on the XML schema collection.</span></span>  
  
-   <span data-ttu-id="91293-123">TAKE OWNERSHIP 權限需要從某個主體傳送 XML 結構描述集合的擁有權至另一個主體。</span><span class="sxs-lookup"><span data-stu-id="91293-123">The TAKE OWNERSHIP permission is required to transfer ownership of the XML schema collection from one principal to another.</span></span>  
  
-   <span data-ttu-id="91293-124">REFERENCES 權限可授權主體使用 XML 結構描述集合，以便約束資料表、檢視表和參數中的 `xml` 類型資料行並設定其類型。</span><span class="sxs-lookup"><span data-stu-id="91293-124">The REFERENCES permission authorizes the principal to use the XML schema collection to type or constrain `xml` type columns, in tables and views and parameters.</span></span> <span data-ttu-id="91293-125">當 XML 結構描述集合參考另一個權限時，也需要 REFERENCES 權限。</span><span class="sxs-lookup"><span data-stu-id="91293-125">The REFERENCES permission is also required when one XML schema collection refers to another.</span></span>  
  
-   <span data-ttu-id="91293-126">假設此主體擁有集合上的任一個 ALTER、REFERENCES 或 CONTROL 權限，VIEW DEFINITION 權限就可透過 XML_SCHEMA_NAMESPACE 或透過目錄檢視，讓主體查詢 XML 結構描述集合的內容。</span><span class="sxs-lookup"><span data-stu-id="91293-126">The VIEW DEFINITION permission allows the principal to query the contents of an XML schema collection either through XML_SCHEMA_NAMESPACE or through the catalog views, provided this principal also has one of the ALTER, REFERENCES, or CONTROL permissions on the collection.</span></span>  
  
-   <span data-ttu-id="91293-127">針對約束 `xml` 類型資料行、變數和參數並設定其類型的 XML 結構描述集合來驗證主體所插入或更新的值時，將需要 EXECUTE 權限。</span><span class="sxs-lookup"><span data-stu-id="91293-127">The EXECUTE permission is required to validate values inserted or updated by the principal against the XML schema collection that is typing or constraining the `xml` type columns, variables, and parameters.</span></span> <span data-ttu-id="91293-128">當您查詢儲存在這些資料行和變數的 XML 時，您也需要此權限。</span><span class="sxs-lookup"><span data-stu-id="91293-128">You also need this permission when you are querying the XML stored in these columns and variables.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="91293-129">範例</span><span class="sxs-lookup"><span data-stu-id="91293-129">Examples</span></span>  
 <span data-ttu-id="91293-130">下列範例中的狀況說明 XML 結構描述權限如何運作。</span><span class="sxs-lookup"><span data-stu-id="91293-130">The scenarios in the following examples illustrate how XML schema permissions work.</span></span> <span data-ttu-id="91293-131">每個範例都會建立所需的測試資料庫、關聯式結構描述和登入。</span><span class="sxs-lookup"><span data-stu-id="91293-131">Each example creates the necessary test database, relational schemas, and logins.</span></span> <span data-ttu-id="91293-132">將會授與這些登入必要的 XML 結構描述集合權限。</span><span class="sxs-lookup"><span data-stu-id="91293-132">These logins are granted the necessary XML schema collection permissions.</span></span> <span data-ttu-id="91293-133">每個範例都會在結束時執行必要的清除。</span><span class="sxs-lookup"><span data-stu-id="91293-133">Each example does the necessary clean up at the end.</span></span>  
  
### <a name="a-granting-permissions-to-create-an-xml-schema-collection"></a><span data-ttu-id="91293-134">A.</span><span class="sxs-lookup"><span data-stu-id="91293-134">A.</span></span> <span data-ttu-id="91293-135">授與建立 XML 結構描述集合的權限</span><span class="sxs-lookup"><span data-stu-id="91293-135">Granting permissions to create an XML schema collection</span></span>  
 <span data-ttu-id="91293-136">下列範例將示範如何授與權限，以便讓主體可建立 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="91293-136">The following example shows how to grant permissions so that a principal can create an XML schema collection.</span></span> <span data-ttu-id="91293-137">此範例將建立範例資料庫和測試使用者 `TestLogin1`。</span><span class="sxs-lookup"><span data-stu-id="91293-137">The example creates a sample database and a test user, `TestLogin1`.</span></span> <span data-ttu-id="91293-138">`TestLogin1` 接著會被授與關聯式結構描述的 `ALTER` 權限，而且被授與資料庫的 `CREATE XML SCHEMA COLLECTION` 權限。</span><span class="sxs-lookup"><span data-stu-id="91293-138">`TestLogin1` is then given `ALTER` permission on the relational schema and given `CREATE XML SCHEMA COLLECTION` permission on the database.</span></span> <span data-ttu-id="91293-139">透過這些權限， `TestLogin1` 可成功地建立範例 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="91293-139">With these permissions, `TestLogin1` succeeds in creating a sample XML schema collection.</span></span>  
  
```  
SETUSER  
GO  
USE master  
GO  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
CREATE USER TestLogin1  
GO  
-- User must have ALTER permission on the relational schema in the database.  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
GO  
-- User also must have permission to create XML schema collections in the database.  
GRANT CREATE XML SCHEMA COLLECTION   
TO TestLogin1  
GO  
-- Execute CREATE XML SCHEMA COLLECTION.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="AdditionalContactInfo" >  
  <xsd:complexType mixed="true" >  
    <xsd:sequence>  
      <xsd:any processContents="strict"    
               namespace="http://schemas.adventure-works.com/Contact/Record   
                          http://schemas.adventure-works.com/AdditionalContactTypes"  
               minOccurs="0" maxOccurs="unbounded" />  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
<xsd:element name="root" type="xsd:byte"/>  
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
  
### <a name="b-granting-permission-to-use-an-existing-xml-schema-collection"></a><span data-ttu-id="91293-140">B.</span><span class="sxs-lookup"><span data-stu-id="91293-140">B.</span></span> <span data-ttu-id="91293-141">授與使用現有 XML 結構描述集合的權限</span><span class="sxs-lookup"><span data-stu-id="91293-141">Granting permission to use an existing XML schema collection</span></span>  
 <span data-ttu-id="91293-142">下列範例進一步說明 XML 結構描述集合的權限模式。</span><span class="sxs-lookup"><span data-stu-id="91293-142">The following example further shows the permission model for the XML schema collection.</span></span> <span data-ttu-id="91293-143">此範例將說明建立和使用 XML 結構描述集合所需的不同權限。</span><span class="sxs-lookup"><span data-stu-id="91293-143">The example shows how different permissions are required to create and use the XML schema collection.</span></span>  
  
 <span data-ttu-id="91293-144">此範例將建立測試資料庫與登入 `TestLogin1`。</span><span class="sxs-lookup"><span data-stu-id="91293-144">The example creates a test database and a login, `TestLogin1`.</span></span> <span data-ttu-id="91293-145">`TestLogin1` 可在資料庫中建立 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="91293-145">`TestLogin1` creates an XML schema collection in the database.</span></span> <span data-ttu-id="91293-146">該登入接著會建立資料表，並使用 XML 結構描述集合來建立具類型的 xml 資料行。</span><span class="sxs-lookup"><span data-stu-id="91293-146">The login then creates a table and uses the XML schema collection to create a typed xml column.</span></span> <span data-ttu-id="91293-147">然後使用者會插入資料並查詢它。</span><span class="sxs-lookup"><span data-stu-id="91293-147">The user then inserts data and queries it.</span></span> <span data-ttu-id="91293-148">所有的這些步驟需要必要的結構描述權限，如程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="91293-148">All these steps require the necessary schema permissions, as shown in the code.</span></span>  
  
```  
SETUSER  
GO  
USE master  
GO  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
CREATE USER TestLogin1  
GO  
-- Grant permission to the user.  
SETUSER  
GO  
-- User must have ALTER permission on the relational schema in the database.  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
GO  
-- User also must have permission to create XML schema collections in the database.  
GRANT CREATE XML SCHEMA COLLECTION   
TO TestLogin1  
GO  
-- Now user can execute the previous CREATE XML SCHEMA COLLECTION statement.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
  
<xsd:element name="AdditionalContactInfo" >  
  <xsd:complexType mixed="true" >  
    <xsd:sequence>  
      <xsd:any processContents="strict"    
               namespace="http://schemas.adventure-works.com/Contact/Record   
                          http://schemas.adventure-works.com/AdditionalContactTypes"  
               minOccurs="0" maxOccurs="unbounded" />  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
  
-- Create a table by using the collection to type an XML column.   
--TestLogin1 must have permission to create a table.  
SETUSER  
GO  
GRANT CREATE TABLE TO TestLogin1  
GO  
-- The user also must have REFERENCES permission to use the XML schema collection  
-- to create a typed XML column (REFERENCES permission on schema   
-- collection is not needed).  
GRANT REFERENCES ON XML SCHEMA COLLECTION::myTestSchemaCollection   
TO TestLogin1  
GO  
-- Now user can create a table and use the XML schema collection to create   
-- a typed XML column.  
SETUSER 'TestLogin1'  
GO  
CREATE TABLE MyTestTable (xmlCol xml (dbo.myTestSchemaCollection))  
GO  
-- To insert data in the table, the user needs EXECUTE permission on the XML schema collection.  
-- GRANT EXECUTE permission to TestLogin2 on the xml schema collection.  
SETUSER  
GO  
GRANT EXECUTE ON XML SCHEMA COLLECTION::myTestSchemaCollection   
TO TestLogin1  
GO  
-- TestLogin1 does not own the dbo schema. This user must have INSERT permission.  
GRANT INSERT TO TestLogin1  
GO  
-- Now the user can insert data into the table.  
SETUSER 'TestLogin1'  
GO  
INSERT INTO MyTestTable VALUES('  
<telephone xmlns="http://schemas.adventure-works.com/Additional/ContactInfo">111-1111</telephone>  
')  
GO  
-- To query the table, TestLogin1 must have permissions: SELECT on the table and EXECUTE on the XML schema collection.  
SETUSER  
GO  
GRANT SELECT TO TestLogin1  
GO  
-- TestLogin1 already has EXECUTE permission on the schema (granted before inserting a record in the table).  
SELECT xmlCol.query('declare default element namespace "http://schemas.adventure-works.com/Additional/ContactInfo" /telephone[1]')  
FROM MyTestTable  
GO  
-- To show that the user must have EXECUTE permission to query, revoke the  
-- previously granted permission and return the query.  
SETUSER  
GO  
REVOKE EXECUTE ON XML SCHEMA COLLECTION::myTestSchemaCollection to TestLogin1  
Go  
-- Now TestLogin1 cannot execute the query.  
SETUSER 'TestLogin1'  
GO  
SELECT xmlCol.query('declare default element namespace "http://schemas.adventure-works.com/Additional/ContactInfo" /telephone[1]')  
FROM MyTestTable  
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
  
### <a name="c-granting-alter-permission-on-an-xml-schema-collection"></a><span data-ttu-id="91293-149">C.</span><span class="sxs-lookup"><span data-stu-id="91293-149">C.</span></span> <span data-ttu-id="91293-150">授與 XML 結構描述集合的 ALTER 權限</span><span class="sxs-lookup"><span data-stu-id="91293-150">Granting ALTER permission on an XML schema collection</span></span>  
 <span data-ttu-id="91293-151">使用者必須擁有 ALTER 權限，才能修改資料庫中的現有 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="91293-151">A user must have ALTER permission to modify an existing XML schema collection in the database.</span></span> <span data-ttu-id="91293-152">下列範例將示範如何授與 `ALTER` 權限。</span><span class="sxs-lookup"><span data-stu-id="91293-152">The following example shows how to grant `ALTER` permission.</span></span>  
  
```  
SETUSER  
GO  
USE master  
GO  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
CREATE USER TestLogin1  
GO  
-- Grant permission to the user.  
SETUSER  
GO  
-- User must have ALTER permission on the relational schema in the database.  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
GO  
-- User also must have permission to create XML schema collections in the database.  
GRANT CREATE XML SCHEMA COLLECTION   
TO TestLogin1  
GO  
-- Now user can execute the previous CREATE XML SCHEMA COLLECTION statement.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
  
<xsd:element name="AdditionalContactInfo" >  
  <xsd:complexType mixed="true" >  
    <xsd:sequence>  
      <xsd:any processContents="strict"    
               namespace="http://schemas.adventure-works.com/Contact/Record   
                          http://schemas.adventure-works.com/AdditionalContactTypes"  
               minOccurs="0" maxOccurs="unbounded" />  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
-- Grant ALTER permission to TestLogin1.  
setuser  
GO  
GRANT ALTER ON XML SCHEMA COLLECTION::myTestSchemaCollection TO TestLogin1  
GO  
-- TestLogin1 should be able to add components to the collection.  
SETUSER 'TestLogin1'  
GO  
ALTER XML SCHEMA COLLECTION myTestSchemaCollection ADD '  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns="http://schemas.adventure-works.com/Additional/ContactInfo"   
elementFormDefault="qualified">  
 <xsd:element name="pager" type="xsd:string"/>  
</xsd:schema>  
'  
Go  
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
  
### <a name="d-granting-take-ownership-permission-on-an-xml-schema-collection"></a><span data-ttu-id="91293-153">D.</span><span class="sxs-lookup"><span data-stu-id="91293-153">D.</span></span> <span data-ttu-id="91293-154">授予 XML 結構描述集合的 TAKE OWNERSHIP 權限</span><span class="sxs-lookup"><span data-stu-id="91293-154">Granting TAKE OWNERSHIP permission on an XML schema collection</span></span>  
 <span data-ttu-id="91293-155">下列範例將示範如何從某個使用者傳送 XML 結構描述的擁有權至另一個使用者。</span><span class="sxs-lookup"><span data-stu-id="91293-155">The following example shows how to transfer XML schema ownership from one user to another.</span></span> <span data-ttu-id="91293-156">為了使範例更加有趣，本範例中的使用者分別在不同的預設關聯式結構描述中運作。</span><span class="sxs-lookup"><span data-stu-id="91293-156">To make the example more interesting, the users in this example work in different default relational schemas.</span></span>  
  
 <span data-ttu-id="91293-157">此範例會執行下列各項：</span><span class="sxs-lookup"><span data-stu-id="91293-157">This example does the following:</span></span>  
  
-   <span data-ttu-id="91293-158">使用兩個關聯式結構描述 `dbo` 和 `myOtherDBSchema`建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="91293-158">Creates a database with two relational schemas, `dbo` and `myOtherDBSchema`).</span></span>  
  
-   <span data-ttu-id="91293-159">建立兩個使用者， `TestLogin1` 和 `TestLogin2`。</span><span class="sxs-lookup"><span data-stu-id="91293-159">Creates two users, `TestLogin1` and `TestLogin2`.</span></span> <span data-ttu-id="91293-160">`TestLogin2` 會成為 `myOtherDBSchema` 關聯式結構描述的擁有者。</span><span class="sxs-lookup"><span data-stu-id="91293-160">`TestLogin2` is made the owner of the `myOtherDBSchema` relational schema.</span></span>  
  
-   <span data-ttu-id="91293-161">`TestLogin1` 會在 `dbo` 關聯式結構描述中建立 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="91293-161">`TestLogin1` creates an XML schema collection in the `dbo` relational schema.</span></span>  
  
-   <span data-ttu-id="91293-162">`TestLogin1` 然後會提供 XML 結構描述集合的 `TAKE OWNERSHIP` 權限給 `TestLogin2`。</span><span class="sxs-lookup"><span data-stu-id="91293-162">`TestLogin1` then gives `TAKE OWNERSHIP` permission on the XML schema collection to `TestLogin2`.</span></span>  
  
-   <span data-ttu-id="91293-163">`TestLogin2` 將會變成 `myOtherDBSchema`中 XML 結構描述集合的擁有者，而不需變更 XML 結構描述集合的關聯式結構描述。</span><span class="sxs-lookup"><span data-stu-id="91293-163">`TestLogin2` becomes the owner of the XML schema collection in `myOtherDBSchema`, without changing the relational schema of the XML schema collection.</span></span>  
  
```  
CREATE LOGIN TestLogin1 with password='SQLSvrPwd1'  
GO  
CREATE LOGIN TestLogin2 with password='SQLSvrPwd2'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
-- Create another relational schema in the database.  
CREATE SCHEMA myOtherDBSchema  
GO  
-- Create users in the database. Note TestLogin2's default schema is  
-- myOtherDBSchema.  
CREATE USER TestLogin1  
GO  
CREATE USER TestLogin2 WITH DEFAULT_SCHEMA=myOtherDBSchema  
GO  
-- TestLogin2 will own myOtherDBSchema relational schema.  
ALTER AUTHORIZATION ON SCHEMA::myOtherDBSchema TO TestLogin2  
GO  
  
-- For TestLogin1 to create XML schema collection, the following  
-- permission is required.  
GRANT CREATE XML SCHEMA COLLECTION   
TO TestLogin1  
GO  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
GO  
-- Now TestLogin1 can create an XML schema collection.  
setuser 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
  
<xsd:element name="AdditionalContactInfo" >  
 <xsd:complexType mixed="true" >  
    <xsd:sequence>  
      <xsd:any processContents="strict"   
               namespace="http://schemas.adventure-works.com/Contact/Record   
                          http://schemas.adventure-works.com/AdditionalContactTypes"  
               minOccurs="0" maxOccurs="unbounded" />  
    </xsd:sequence>  
 </xsd:complexType>  
</xsd:element>  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
  
-- Grant TAKE OWNERSHIP to TestLogin2.  
SETUSER  
GO  
GRANT TAKE OWNERSHIP ON XML SCHEMA COLLECTION::dbo.myTestSchemaCollection   
TO TestLogin2  
GO  
-- Verify the owner. Note the UserName and Principal_id is null.   
SELECT user_name(sys.xml_schema_collections.principal_id) as UserName,   
       sys.schemas.name as RelSchemaName,*   
FROM   sys.xml_schema_collections   
      JOIN sys.schemas   
      ON sys.schemas.schema_id=sys.xml_schema_collections.schema_id  
GO  
-- TestLogin2 can take ownership now.  
setuser 'TestLogin2'  
GO  
ALTER AUTHORIZATION ON XML SCHEMA COLLECTION::dbo.myTestSchemaCollection   
TO TestLogin2  
GO  
-- Note that although TestLogin2 is the owner,the XML schema collection   
-- is still in dbo.  
SELECT user_name(sys.xml_schema_collections.principal_id) as UserName,   
      sys.schemas.name as RelSchemaName,*   
FROM sys.xml_schema_collections JOIN sys.schemas   
     ON sys.schemas.schema_id=sys.xml_schema_collections.schema_id  
GO  
  
-- TestLogin2 moves the collection from dbo to myOtherDBSchema relational schema.  
-- TestLogin2 already has all necessary permissions.  
-- 1) TestLogin2 owns the destination relational schema so he can alter it.  
-- 2) TestLogin2 owns the XML schema collection (therefore, has CONTROL permission).  
ALTER SCHEMA myOtherDBSchema  
TRANSFER XML SCHEMA COLLECTION::dbo.myTestSchemaCollection  
GO  
  
SELECT user_name(sys.xml_schema_collections.principal_id) as UserName,   
       sys.schemas.name as RelSchemaName,*   
FROM   sys.xml_schema_collections JOIN sys.schemas   
       ON sys.schemas.schema_id=sys.xml_schema_collections.schema_id  
GO  
-- Final cleanup   
SETUSER  
GO  
USE master  
GO  
DROP DATABASE SampleDBForSchemaPermissions  
GO  
DROP LOGIN TestLogin1  
DROP LOGIN TestLogin2  
go   
```  
  
### <a name="e-granting-view-definition-permission-on-an-xml-schema-collection"></a><span data-ttu-id="91293-164">E.</span><span class="sxs-lookup"><span data-stu-id="91293-164">E.</span></span> <span data-ttu-id="91293-165">授與 XML 結構描述集合的 VIEW DEFINITION 權限</span><span class="sxs-lookup"><span data-stu-id="91293-165">Granting VIEW DEFINITION permission on an XML schema collection</span></span>  
 <span data-ttu-id="91293-166">下列範例將示範如何授與 XML 結構描述集合的 VIEW DEFINITION 權限。</span><span class="sxs-lookup"><span data-stu-id="91293-166">The following example shows how to grant VIEW DEFINITION permissions for an XML schema collection.</span></span>  
  
```  
SETUSER  
GO  
USE master  
GO  
IF EXISTS( SELECT * FROM sysdatabases WHERE name='permissionsDB' )  
   DROP DATABASE permissionsDB  
GO  
IF EXISTS( SELECT * FROM sys.sql_logins WHERE name='schemaUser' )  
   DROP LOGIN schemaUser  
GO  
CREATE DATABASE permissionsDB  
GO  
CREATE LOGIN schemaUser WITH PASSWORD='Pass#123',DEFAULT_DATABASE=permissionsDB  
GO  
GRANT CONNECT SQL TO schemaUser  
GO  
USE permissionsDB  
GO  
CREATE USER schemaUser WITH DEFAULT_SCHEMA=dbo  
GO  
CREATE XML SCHEMA COLLECTION MySC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns"  
xmlns:ns="http://ns">  
  
   <simpleType name="ListOfIntegers">  
      <list itemType="integer"/>  
   </simpleType>  
  
   <element name="root" type="ns:ListOfIntegers"/>  
  
   <element name="gRoot" type="gMonth"/>  
  
</schema>  
'  
GO  
-- schemaUser cannot see the contents of the collection.  
SETUSER 'schemaUser'  
GO  
SELECT XML_SCHEMA_NAMESPACE(N'dbo',N'MySC')  
GO  
  
-- Grant schemaUser VIEW DEFINITION and REFERENCES permissions  
-- on the XML schema collection.  
SETUSER  
GO  
GRANT VIEW DEFINITION ON XML SCHEMA COLLECTION::dbo.MySC TO schemaUser  
GO  
GRANT REFERENCES ON XML SCHEMA COLLECTION::dbo.MySC TO schemaUser  
GO  
-- Now schemaUser can see the content of the collection.  
SETUSER 'schemaUser'  
GO  
SELECT XML_SCHEMA_NAMESPACE(N'dbo',N'MySC')  
GO  
-- Revoke schemaUser VIEW DEFINITION permissions  
-- on the XML schema collection.  
SETUSER  
GO  
REVOKE VIEW DEFINITION ON XML SCHEMA COLLECTION::dbo.MySC FROM schemaUser  
GO  
-- Now schemaUser cannot see the contents of   
-- the collection.  
setuser 'schemaUser'  
GO  
SELECT XML_SCHEMA_NAMESPACE(N'dbo',N'MySC')  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="91293-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91293-167">See Also</span></span>  
 <span data-ttu-id="91293-168">[XML 資料 &#40;SQL Server&#41;](xml-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="91293-168">[XML Data &#40;SQL Server&#41;](xml-data-sql-server.md) </span></span>  
 <span data-ttu-id="91293-169">[比較具類型的 XML 與不具類型的 XML](compare-typed-xml-to-untyped-xml.md) </span><span class="sxs-lookup"><span data-stu-id="91293-169">[Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md) </span></span>  
 <span data-ttu-id="91293-170">[XML 結構描述集合 &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="91293-170">[XML Schema Collections &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span></span>  
 [<span data-ttu-id="91293-171">伺服器上 XML 結構描述集合的需求與限制</span><span class="sxs-lookup"><span data-stu-id="91293-171">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
