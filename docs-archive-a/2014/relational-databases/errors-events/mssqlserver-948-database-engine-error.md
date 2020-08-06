---
title: MSSQLSERVER_948 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "948"
helpviewer_keywords:
- 948 (Database Engine error)
ms.assetid: 95c4ad45-a518-4165-a5c4-6e6b932b0570
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e8461069a3fceb7bdca318b82a522f7f51af83d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595038"
---
# <a name="mssqlserver_948"></a><span data-ttu-id="c4654-102">MSSQLSERVER_948</span><span class="sxs-lookup"><span data-stu-id="c4654-102">MSSQLSERVER_948</span></span>
    
## <a name="details"></a><span data-ttu-id="c4654-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c4654-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c4654-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c4654-104">Product Name</span></span>|<span data-ttu-id="c4654-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c4654-105">SQL Server</span></span>|  
|<span data-ttu-id="c4654-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c4654-106">Event ID</span></span>|<span data-ttu-id="c4654-107">948</span><span class="sxs-lookup"><span data-stu-id="c4654-107">948</span></span>|  
|<span data-ttu-id="c4654-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c4654-108">Event Source</span></span>|<span data-ttu-id="c4654-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c4654-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c4654-110">元件</span><span class="sxs-lookup"><span data-stu-id="c4654-110">Component</span></span>|<span data-ttu-id="c4654-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c4654-111">SQLEngine</span></span>|  
|<span data-ttu-id="c4654-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c4654-112">Symbolic Name</span></span>|<span data-ttu-id="c4654-113">NA</span><span class="sxs-lookup"><span data-stu-id="c4654-113">NA</span></span>|  
|<span data-ttu-id="c4654-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c4654-114">Message Text</span></span>|<span data-ttu-id="c4654-115">無法開啟資料庫 '%.\*ls'，因為版本為 %d。</span><span class="sxs-lookup"><span data-stu-id="c4654-115">The database '%.\*ls' cannot be opened because it is version %d.</span></span> <span data-ttu-id="c4654-116">這個伺服器支援 %d 及更早的版本。</span><span class="sxs-lookup"><span data-stu-id="c4654-116">This server supports version %d and earlier.</span></span> <span data-ttu-id="c4654-117">不支援降級路徑。</span><span class="sxs-lookup"><span data-stu-id="c4654-117">A downgrade path is not supported.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c4654-118">說明</span><span class="sxs-lookup"><span data-stu-id="c4654-118">Explanation</span></span>  
 <span data-ttu-id="c4654-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的某些功能會影響資料庫檔案的結構。</span><span class="sxs-lookup"><span data-stu-id="c4654-119">Certain features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affect the structure of the database files.</span></span> <span data-ttu-id="c4654-120">當您將資料庫附加到另一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體時，檔案格式可能與不同的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 版本不相容。</span><span class="sxs-lookup"><span data-stu-id="c4654-120">When you attach a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the file format might not be compatible with a different version of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="c4654-121">例如，造成這項錯誤的原因可能是在較新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本中使用 Vardecimal 儲存格式，然後嘗試在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 之前的版本中附加資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="c4654-121">For example, this error can be caused by using the vardecimal storage format in a later version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and then trying to attach the database files in a version earlier than [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c4654-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c4654-122">User Action</span></span>  
 <span data-ttu-id="c4654-123">判斷原始伺服器上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="c4654-123">Determine the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on the originating server.</span></span> <span data-ttu-id="c4654-124">在中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，以滑鼠右鍵按一下伺服器，然後按一下 [**屬性**] 或 [ `SELECT @@VERSION` 在查詢視窗中輸入]。</span><span class="sxs-lookup"><span data-stu-id="c4654-124">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], either right-click the server and then click **Properties** or type `SELECT @@VERSION` in a query window.</span></span> <span data-ttu-id="c4654-125">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的原始版本開啟資料庫。</span><span class="sxs-lookup"><span data-stu-id="c4654-125">Open the database by using the original version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c4654-126">檢查 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中原始資料庫上啟用的功能。</span><span class="sxs-lookup"><span data-stu-id="c4654-126">Investigate the features that are enabled on the original database in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c4654-127">修改這些設定，以搭配用來附加資料庫的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="c4654-127">Modify these settings to work with the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in which the database will be attached.</span></span>  
  
  
