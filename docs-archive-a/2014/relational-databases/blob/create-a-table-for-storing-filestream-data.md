---
title: 建立儲存 FILESTREAM 資料的資料表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], table storage
ms.assetid: 029c3059-5c83-43e2-a859-9027031b7de1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 484d7b58ce949df79dc7e17ee4dc7307b70c0154
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699781"
---
# <a name="create-a-table-for-storing-filestream-data"></a><span data-ttu-id="de2fa-102">建立儲存 FILESTREAM 資料的資料表</span><span class="sxs-lookup"><span data-stu-id="de2fa-102">Create a Table for Storing FILESTREAM Data</span></span>
  <span data-ttu-id="de2fa-103">此主題說明如何建立儲存 FILESTREAM 資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="de2fa-103">This topic shows how to create a table for storing FILESTREAM data.</span></span>  
  
 <span data-ttu-id="de2fa-104">當檔案庫中已有 FILESTREAM 檔案群組時，您就可以建立或修改資料表，以便儲存 FILESTREAM 檔案。</span><span class="sxs-lookup"><span data-stu-id="de2fa-104">When the database has a FILESTREAM filegroup, you can create or modify tables to store FILESTREAM data.</span></span> <span data-ttu-id="de2fa-105">若要指定包含 FILESTREAM 資料的資料行，您可以建立 `varbinary(max)` 資料行，並加入 FILESTREAM 屬性。</span><span class="sxs-lookup"><span data-stu-id="de2fa-105">To specify that a column contains FILESTREAM data, you create a `varbinary(max)` column and add the FILESTREAM attribute.</span></span>  
  
### <a name="to-create-a-table-to-store-filestream-data"></a><span data-ttu-id="de2fa-106">建立可儲存 FILESTREAM 資料的資料表</span><span class="sxs-lookup"><span data-stu-id="de2fa-106">To create a table to store FILESTREAM data</span></span>  
  
1.  <span data-ttu-id="de2fa-107">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，按一下 **[新增查詢]** 顯示 [查詢編輯器]。</span><span class="sxs-lookup"><span data-stu-id="de2fa-107">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click **New Query** to display the Query Editor.</span></span>  
  
2.  <span data-ttu-id="de2fa-108">將下列範例的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼複製到 [查詢編輯器] 中。</span><span class="sxs-lookup"><span data-stu-id="de2fa-108">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] code from the following example into the Query Editor.</span></span> <span data-ttu-id="de2fa-109">這個 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼會建立稱為 Records 的啟用 FILESTREAM 資料表。</span><span class="sxs-lookup"><span data-stu-id="de2fa-109">This [!INCLUDE[tsql](../../includes/tsql-md.md)] code creates a FILESTREAM-enabled table called Records.</span></span>  
  
3.  <span data-ttu-id="de2fa-110">若要建立此資料表，請按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="de2fa-110">To create the table, click **Execute**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de2fa-111">範例</span><span class="sxs-lookup"><span data-stu-id="de2fa-111">Example</span></span>  
 <span data-ttu-id="de2fa-112">下列程式碼範例示範如何建立名為 `Records`的資料表。</span><span class="sxs-lookup"><span data-stu-id="de2fa-112">The following code example shows how to create a table that is named `Records`.</span></span> <span data-ttu-id="de2fa-113">`Id` 資料行是 `ROWGUIDCOL` 資料行，而且必須搭配 Win32 API 使用 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="de2fa-113">The `Id` column is a `ROWGUIDCOL` column and is required to use FILESTREAM data with Win32 APIs.</span></span> <span data-ttu-id="de2fa-114">`SerialNumber` 資料行屬於 `UNIQUE INTEGER`。</span><span class="sxs-lookup"><span data-stu-id="de2fa-114">The `SerialNumber` column is a `UNIQUE INTEGER`.</span></span> <span data-ttu-id="de2fa-115">`Chart` 資料行是 `FILESTREAM` 資料行，而且可用來將 `Chart` 儲存在檔案系統中。</span><span class="sxs-lookup"><span data-stu-id="de2fa-115">The `Chart` column is a `FILESTREAM` column and is used to store the `Chart` in the file system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="de2fa-116">這個範例參考在 [建立啟用 FILESTREAM 的資料庫](create-a-filestream-enabled-database.md)中建立的 Archive 資料庫。</span><span class="sxs-lookup"><span data-stu-id="de2fa-116">This example refers to the Archive database that is created in [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md).</span></span>  
  
 [!code-sql[FILESTREAM#FS_CreateTable](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_createtable)]  
  
## <a name="see-also"></a><span data-ttu-id="de2fa-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de2fa-117">See Also</span></span>  
 <span data-ttu-id="de2fa-118">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="de2fa-118">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 [<span data-ttu-id="de2fa-119">ALTER TABLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="de2fa-119">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
  
