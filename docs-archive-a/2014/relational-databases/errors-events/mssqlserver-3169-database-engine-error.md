---
title: MSSQLSERVER_3169 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "3169"
helpviewer_keywords:
- 3169 (Database Engine error)
ms.assetid: 7d4dbed6-bb94-4908-bc03-2040a9cf63bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8b13d9c1c17eddb34648bc4a536e2fccf371b99a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596024"
---
# <a name="mssqlserver_3169"></a><span data-ttu-id="bfc2c-102">MSSQLSERVER_3169</span><span class="sxs-lookup"><span data-stu-id="bfc2c-102">MSSQLSERVER_3169</span></span>
    
## <a name="details"></a><span data-ttu-id="bfc2c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bfc2c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bfc2c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bfc2c-104">Product Name</span></span>|<span data-ttu-id="bfc2c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="bfc2c-105">SQL Server</span></span>|  
|<span data-ttu-id="bfc2c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bfc2c-106">Event ID</span></span>|<span data-ttu-id="bfc2c-107">3169</span><span class="sxs-lookup"><span data-stu-id="bfc2c-107">3169</span></span>|  
|<span data-ttu-id="bfc2c-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="bfc2c-108">Event Source</span></span>|<span data-ttu-id="bfc2c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="bfc2c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="bfc2c-110">元件</span><span class="sxs-lookup"><span data-stu-id="bfc2c-110">Component</span></span>|<span data-ttu-id="bfc2c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="bfc2c-111">SQLEngine</span></span>|  
|<span data-ttu-id="bfc2c-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bfc2c-112">Symbolic Name</span></span>|<span data-ttu-id="bfc2c-113">NA</span><span class="sxs-lookup"><span data-stu-id="bfc2c-113">NA</span></span>|  
|<span data-ttu-id="bfc2c-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bfc2c-114">Message Text</span></span>|<span data-ttu-id="bfc2c-115">資料庫是在執行 %ls 版的伺服器上備份。</span><span class="sxs-lookup"><span data-stu-id="bfc2c-115">The database was backed up on a server running version %ls.</span></span> <span data-ttu-id="bfc2c-116">該版本和此伺服器不相容，此伺服器目前執行 %ls 版。</span><span class="sxs-lookup"><span data-stu-id="bfc2c-116">That version is incompatible with this server, which is running version %ls.</span></span> <span data-ttu-id="bfc2c-117">請將資料庫還原到支援此備份的伺服器，或使用與此伺服器相容的備份。</span><span class="sxs-lookup"><span data-stu-id="bfc2c-117">Either restore the database on a server that supports the backup, or use a backup that is compatible with this server.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bfc2c-118">說明</span><span class="sxs-lookup"><span data-stu-id="bfc2c-118">Explanation</span></span>  
 <span data-ttu-id="bfc2c-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的某些功能會影響資料庫檔案的結構。</span><span class="sxs-lookup"><span data-stu-id="bfc2c-119">Certain features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affect the structure of the database files.</span></span> <span data-ttu-id="bfc2c-120">當您將資料庫還原到另一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時，檔案格式可能與不同的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 版本不相容。</span><span class="sxs-lookup"><span data-stu-id="bfc2c-120">When you restore a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the file format might not be compatible with a different version of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="bfc2c-121">例如，造成這項錯誤的原因可能是在較新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本中使用 Vardecimal 儲存格式，然後嘗試在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 之前的版本中還原資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="bfc2c-121">For example, this error can be caused by using the vardecimalstorage format in a later version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and then trying to restore the database files in a version earlier than [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bfc2c-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bfc2c-122">User Action</span></span>  
 <span data-ttu-id="bfc2c-123">判斷原始伺服器上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="bfc2c-123">Determine the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on the originating server.</span></span> <span data-ttu-id="bfc2c-124">在中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，以滑鼠右鍵按一下伺服器，然後按一下 [**屬性**] 或 [ `SELECT @@VERSION` 在查詢視窗中輸入]。</span><span class="sxs-lookup"><span data-stu-id="bfc2c-124">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], either right-click the server and then click **Properties** or type `SELECT @@VERSION` in a query window.</span></span> <span data-ttu-id="bfc2c-125">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的原始版本開啟資料庫。</span><span class="sxs-lookup"><span data-stu-id="bfc2c-125">Open the database by using the original version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bfc2c-126">檢查 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中原始資料庫上啟用的功能。</span><span class="sxs-lookup"><span data-stu-id="bfc2c-126">Investigate the features that are enabled on the original database in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bfc2c-127">修改這些設定，以搭配用來還原資料庫的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="bfc2c-127">Modify these settings to work with the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in which the database will be restored.</span></span>  
  
  
