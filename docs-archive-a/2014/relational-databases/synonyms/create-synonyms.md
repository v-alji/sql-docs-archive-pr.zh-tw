---
title: 建立同義字 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- sql12.swb.synonym.general.f1
helpviewer_keywords:
- creating synonyms
- synonyms [SQL Server], creating
ms.assetid: fedfa7a5-d0b6-4e2b-90f4-a08122958e33
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3dc18c9d0d6048c4190ba56725dd332f2dfb629e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584348"
---
# <a name="create-synonyms"></a><span data-ttu-id="2ea4b-102">建立同義字</span><span class="sxs-lookup"><span data-stu-id="2ea4b-102">Create Synonyms</span></span>
  <span data-ttu-id="2ea4b-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立同義字。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-103">This topic describes how to create a synonym in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2ea4b-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="2ea4b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2ea4b-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="2ea4b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2ea4b-106">安全性</span><span class="sxs-lookup"><span data-stu-id="2ea4b-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2ea4b-107">**若要使用下列項目來建立同義字：**</span><span class="sxs-lookup"><span data-stu-id="2ea4b-107">**To create a synonym, using:**</span></span>  
  
     [<span data-ttu-id="2ea4b-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2ea4b-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2ea4b-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2ea4b-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2ea4b-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="2ea4b-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2ea4b-111">Security</span><span class="sxs-lookup"><span data-stu-id="2ea4b-111">Security</span></span>  
 <span data-ttu-id="2ea4b-112">若要以給定結構描述建立同義字，使用者必須擁有 CREATE SYNONYM 權限，並擁有該結構描述或 ALTER SCHEMA 權限。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-112">To create a synonym in a given schema, a user must have CREATE SYNONYM permission and either own the schema or have ALTER SCHEMA permission.</span></span> <span data-ttu-id="2ea4b-113">CREATE SYNONYM 權限是可授與的權限。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-113">The CREATE SYNONYM permission is a grantable permission.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2ea4b-114">權限</span><span class="sxs-lookup"><span data-stu-id="2ea4b-114">Permissions</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2ea4b-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2ea4b-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-synonym"></a><span data-ttu-id="2ea4b-116">若要建立同義字</span><span class="sxs-lookup"><span data-stu-id="2ea4b-116">To Create a Synonym</span></span>  
  
1.  <span data-ttu-id="2ea4b-117">在 **[物件總管]** 中，展開您要建立新檢視表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-117">In **Object Explorer**, expand the database where you want to create your new view.</span></span>  
  
2.  <span data-ttu-id="2ea4b-118">以滑鼠右鍵按一下 [同義字]  資料夾，然後按一下 [新增同義字]  。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-118">Right-click the **Synonyms** folder, then click **New Synonym...**.</span></span>  
  
3.  <span data-ttu-id="2ea4b-119">在 **[加入新的同義字]** 對話方塊中，輸入下列資訊。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-119">In the **Add Synonym** dialog box, enter the following information.</span></span>  
  
     <span data-ttu-id="2ea4b-120">**同義字名稱**</span><span class="sxs-lookup"><span data-stu-id="2ea4b-120">**Synonym name**</span></span>  
     <span data-ttu-id="2ea4b-121">輸入用於此物件的新名稱。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-121">Type the new name you will use for this object.</span></span>  
  
     <span data-ttu-id="2ea4b-122">**同義字結構描述**</span><span class="sxs-lookup"><span data-stu-id="2ea4b-122">**Synonym schema**</span></span>  
     <span data-ttu-id="2ea4b-123">輸入用於此物件之新名稱的結構描述。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-123">Type the schema of the new name you will use for this object.</span></span>  
  
     <span data-ttu-id="2ea4b-124">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="2ea4b-124">**Server name**</span></span>  
     <span data-ttu-id="2ea4b-125">輸入要連接的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-125">Type the server instance to connect to.</span></span>  
  
     <span data-ttu-id="2ea4b-126">**資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="2ea4b-126">**Database name**</span></span>  
     <span data-ttu-id="2ea4b-127">輸入或選取含有物件的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-127">Type or select the database containing the object.</span></span>  
  
     <span data-ttu-id="2ea4b-128">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="2ea4b-128">**Schema**</span></span>  
     <span data-ttu-id="2ea4b-129">輸入或選取擁有物件的結構描述。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-129">Type or select the schema that owns the object.</span></span>  
  
     <span data-ttu-id="2ea4b-130">**物件類型**</span><span class="sxs-lookup"><span data-stu-id="2ea4b-130">**Object type**</span></span>  
     <span data-ttu-id="2ea4b-131">選取物件的類型。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-131">Select the type of object.</span></span>  
  
     <span data-ttu-id="2ea4b-132">**物件名稱**</span><span class="sxs-lookup"><span data-stu-id="2ea4b-132">**Object name**</span></span>  
     <span data-ttu-id="2ea4b-133">輸入同義字所參考之物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-133">Type the name of the object to which the synonym refers.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2ea4b-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2ea4b-134">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-synonym"></a><span data-ttu-id="2ea4b-135">若要建立同義字</span><span class="sxs-lookup"><span data-stu-id="2ea4b-135">To Create a Synonym</span></span>  
  
1.  <span data-ttu-id="2ea4b-136">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2ea4b-137">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2ea4b-138">將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-138">Copy and paste the following examples into the query window and click **Execute**.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="2ea4b-139">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2ea4b-139">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="2ea4b-140">下列範例會針對 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫中的現有資料表建立同義字。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-140">The following example creates a synonym for an existing table in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="2ea4b-141">然後，此同義字將用於後續範例中。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-141">The synonym is then used in subsequent examples.</span></span>  
  
```  
USE tempdb;  
GO  
CREATE SYNONYM MyAddressType  
FOR AdventureWorks2012.Person.AddressType;  
GO  
```  
  
 <span data-ttu-id="2ea4b-142">下列範例將在 `MyAddressType` 同義字所參考的基底資料表中插入一列。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-142">The following example inserts a row into the base table that is referenced by the `MyAddressType` synonym.</span></span>  
  
```  
USE tempdb;  
GO  
INSERT INTO MyAddressType (Name)  
VALUES ('Test');  
GO  
```  
  
 <span data-ttu-id="2ea4b-143">下列範例示範如何在動態 SQL 中參考同義字。</span><span class="sxs-lookup"><span data-stu-id="2ea4b-143">The following example demonstrates how a synonym can be referenced in dynamic SQL.</span></span>  
  
```  
USE tempdb;  
GO  
EXECUTE ('SELECT Name FROM MyAddressType');  
GO  
```  
  
  
