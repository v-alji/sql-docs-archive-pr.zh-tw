---
title: 移動啟用 FILESTREAM 功能的資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], moving a FILESTREAM-enabled database
ms.assetid: dd4d270d-9283-431a-aa6b-e571fced1893
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 79740ee86a89566113650865e3fd6ec54c7cb918
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686991"
---
# <a name="move-a-filestream-enabled-database"></a><span data-ttu-id="be028-102">移動啟用 FILESTREAM 功能的資料庫</span><span class="sxs-lookup"><span data-stu-id="be028-102">Move a FILESTREAM-Enabled Database</span></span>
  <span data-ttu-id="be028-103">本主題將示範如何移動已啟用 FILESTREAM 功能的資料庫。</span><span class="sxs-lookup"><span data-stu-id="be028-103">This topic shows how to move a FILESTREAM-enabled database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be028-104">這個主題的範例，需要使用在 [建立啟用 FILESTREAM 的資料庫](create-a-filestream-enabled-database.md)中建立的 Archive 資料庫。</span><span class="sxs-lookup"><span data-stu-id="be028-104">The examples in this topic require the Archive database that is created in [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md).</span></span>  
  
### <a name="to-move-a-filestream-enabled-database"></a><span data-ttu-id="be028-105">移動已啟用 FILESTREAM 功能的資料庫</span><span class="sxs-lookup"><span data-stu-id="be028-105">To move a FILESTREAM-enabled database</span></span>  
  
1.  <span data-ttu-id="be028-106">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，按一下 [新增查詢] 開啟 [查詢編輯器]。</span><span class="sxs-lookup"><span data-stu-id="be028-106">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click **New Query** to open the Query Editor.</span></span>  
  
2.  <span data-ttu-id="be028-107">將下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼複製到 [查詢編輯器]，然後按一下 [執行]。</span><span class="sxs-lookup"><span data-stu-id="be028-107">Copy the following [!INCLUDE[tsql](../../includes/tsql-md.md)] script into the Query Editor, and then click **Execute**.</span></span> <span data-ttu-id="be028-108">此指令碼會顯示 FILESTREAM 資料庫使用之實體資料庫檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="be028-108">This script displays the location of the physical database files that the FILESTREAM database uses.</span></span>  
  
    ```sql  
    USE Archive  
    GO  
    SELECT type_desc, name, physical_name from sys.database_files  
    ```  
  
3.  <span data-ttu-id="be028-109">將下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼複製到 [查詢編輯器]，然後按一下 [執行]。</span><span class="sxs-lookup"><span data-stu-id="be028-109">Copy the following [!INCLUDE[tsql](../../includes/tsql-md.md)] script into the Query Editor, and then click **Execute**.</span></span> <span data-ttu-id="be028-110">此程式碼會讓 `Archive` 資料庫離線。</span><span class="sxs-lookup"><span data-stu-id="be028-110">This code takes the `Archive` database offline.</span></span>  
  
    ```sql  
    USE master  
    EXEC sp_detach_db Archive  
    GO  
    ```  
  
4.  <span data-ttu-id="be028-111">建立 `C:\moved_location`資料夾，然後將步驟 2 所列的檔案和資料夾移到這個資料夾中。</span><span class="sxs-lookup"><span data-stu-id="be028-111">Create the folder `C:\moved_location`, and then move the files and folders that are listed in step 2 into it.</span></span>  
  
5.  <span data-ttu-id="be028-112">將下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼複製到 [查詢編輯器]，然後按一下 [執行]。</span><span class="sxs-lookup"><span data-stu-id="be028-112">Copy the following [!INCLUDE[tsql](../../includes/tsql-md.md)] script into the Query Editor, and then click **Execute**.</span></span> <span data-ttu-id="be028-113">此指令碼會將 `Archive` 資料庫設定為線上。</span><span class="sxs-lookup"><span data-stu-id="be028-113">This script sets the `Archive` database online.</span></span>  
  
    ```sql  
    CREATE DATABASE Archive ON  
    PRIMARY ( NAME = Arch1,  
        FILENAME = 'c:\moved_location\archdat1.mdf'),  
    FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
        FILENAME = 'c:\moved_location\filestream1')  
    LOG ON  ( NAME = Archlog1,  
        FILENAME = 'c:\moved_location\archlog1.ldf')  
    FOR ATTACH  
    GO  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="be028-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be028-114">See Also</span></span>  
 [<span data-ttu-id="be028-115">sp_detach_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="be028-115">sp_detach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
  
