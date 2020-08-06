---
title: MSSQLSERVER_945 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 51284cdcf48f1bf713a853f9c87457cb5291cc4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595040"
---
# <a name="mssqlserver_945"></a><span data-ttu-id="0e442-102">MSSQLSERVER_945</span><span class="sxs-lookup"><span data-stu-id="0e442-102">MSSQLSERVER_945</span></span>
    
## <a name="details"></a><span data-ttu-id="0e442-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0e442-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0e442-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0e442-104">Product Name</span></span>|<span data-ttu-id="0e442-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0e442-105">SQL Server</span></span>|  
|<span data-ttu-id="0e442-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0e442-106">Event ID</span></span>|<span data-ttu-id="0e442-107">945</span><span class="sxs-lookup"><span data-stu-id="0e442-107">945</span></span>|  
|<span data-ttu-id="0e442-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="0e442-108">Event Source</span></span>|<span data-ttu-id="0e442-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0e442-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0e442-110">元件</span><span class="sxs-lookup"><span data-stu-id="0e442-110">Component</span></span>|<span data-ttu-id="0e442-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0e442-111">SQLEngine</span></span>|  
|<span data-ttu-id="0e442-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0e442-112">Symbolic Name</span></span>|<span data-ttu-id="0e442-113">DB_IS_SHUTDOWN</span><span class="sxs-lookup"><span data-stu-id="0e442-113">DB_IS_SHUTDOWN</span></span>|  
|<span data-ttu-id="0e442-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0e442-114">Message Text</span></span>|<span data-ttu-id="0e442-115">檔案無法存取、記憶體或磁碟空間不足，因此無法開啟資料庫 '%.\*ls'。</span><span class="sxs-lookup"><span data-stu-id="0e442-115">Database '%.\*ls' cannot be opened due to inaccessible files or insufficient memory or disk space.</span></span>  <span data-ttu-id="0e442-116">詳細資訊請參閱 SQL Server 錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0e442-116">See the SQL Server error log for details.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0e442-117">說明</span><span class="sxs-lookup"><span data-stu-id="0e442-117">Explanation</span></span>  
 <span data-ttu-id="0e442-118">資料庫無法存取，因為遺失檔案或其他資源。</span><span class="sxs-lookup"><span data-stu-id="0e442-118">The database could not be accessed because files or other resources are missing.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0e442-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0e442-119">User Action</span></span>  
 <span data-ttu-id="0e442-120">檢查錯誤記錄檔，以取得有關記憶體、磁碟空間或權限失敗的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0e442-120">Check the error log for additional information about memory, disk space, or permission failure.</span></span> <span data-ttu-id="0e442-121">確認受影響資料庫的 .mdf 和 .ndf 檔案位置，並確認 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 所使用的帳戶有權限可以存取這些檔案。</span><span class="sxs-lookup"><span data-stu-id="0e442-121">Confirm the location of the .mdf and .ndf files for the affected database and confirm that the account used by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] has permission to access those files.</span></span> <span data-ttu-id="0e442-122">更正問題之後，使用 ALTER DATABASE 將資料庫設定為 ONLINE，以重新啟動資料庫。</span><span class="sxs-lookup"><span data-stu-id="0e442-122">After correcting the problem, restart the database by using ALTER DATABASE to set it ONLINE.</span></span>  
  
  
