---
title: 連接到伺服器 (其他連接參數頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttoserver.options.registeredservers.f1
ms.assetid: ba34b01a-6289-4eb8-8341-fa3d9ec87b3f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5c6a23df6a6b9ea324d54fd270f5aa2269471ed8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607075"
---
# <a name="connect-to-server-additional-connection-parameters-page"></a><span data-ttu-id="8c77d-102">連接到伺服器 (其他連接參數頁面)</span><span class="sxs-lookup"><span data-stu-id="8c77d-102">Connect to Server (Additional Connection Parameters Page)</span></span>
  <span data-ttu-id="8c77d-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 的 [連接到]\*\*\*\* 對話方塊會將最常用的連接字串值呈現為選項。</span><span class="sxs-lookup"><span data-stu-id="8c77d-103">The **Connect to** dialog box of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] presents the most common connection string values as options.</span></span> <span data-ttu-id="8c77d-104">使用 [其他連接參數]\*\*\*\* 頁面可將更多連接參數新增到連接字串。</span><span class="sxs-lookup"><span data-stu-id="8c77d-104">Use the **Additional Connection Parameters** page to add more connection parameters to the connection string.</span></span>  
  
-   <span data-ttu-id="8c77d-105">其他連接參數可以是任何 ODBC 連接參數。</span><span class="sxs-lookup"><span data-stu-id="8c77d-105">Additional connection parameters can be any ODBC connection parameter.</span></span>  
  
-   <span data-ttu-id="8c77d-106">其他連接參數應該使用以下格式來新增： **;parameter1=value1;parameter2=value2**。</span><span class="sxs-lookup"><span data-stu-id="8c77d-106">Additional connection parameters should be added in the format **;parameter1=value1;parameter2=value2**.</span></span>  
  
-   <span data-ttu-id="8c77d-107">使用 [其他連接參數]\*\*\*\* 頁面新增的參數會新增到使用 [連接到]\*\*\*\* 對話方塊選項所選取的參數中。</span><span class="sxs-lookup"><span data-stu-id="8c77d-107">Parameters added using the **Additional Connection Parameters** page are added to the parameters selected using the **Connect to** dialog box options.</span></span>  
  
-   <span data-ttu-id="8c77d-108">提供之每一個參數的最後一個執行個體都會覆寫該參數之前的任何執行個體。</span><span class="sxs-lookup"><span data-stu-id="8c77d-108">The last instance of each parameter provided overrides any previous instances of the parameter.</span></span> <span data-ttu-id="8c77d-109">使用 [其他連接參數]\*\*\*\* 頁面新增的參數會遵循及取代 [登入]\*\*\*\* 或 [連接屬性]\*\*\*\* 索引標籤內提供的參數。</span><span class="sxs-lookup"><span data-stu-id="8c77d-109">Parameters added using the **Additional Connection Parameters** page follow and replace the parameters provided in the **Login** or **Connection Properties** tabs.</span></span> <span data-ttu-id="8c77d-110">例如，如果 [登入]\*\*\*\* 索引標籤提供 **SERVER1** 當作 [伺服器名稱]\*\*\*\*，而且 [其他連接參數]\*\*\*\* 頁面包含 **;SERVER=SERVER2**，將會對 **SERVER2** 進行連接。</span><span class="sxs-lookup"><span data-stu-id="8c77d-110">For example, if the **Login** tab provides **SERVER1** as the **Server name**, and the **Additional Connection Parameters** page contains **;SERVER=SERVER2**, the connection will be made to **SERVER2**.</span></span>  
  
-   <span data-ttu-id="8c77d-111">使用 [其他連接參數]\*\*\*\* 頁面新增的參數一定會以純文字格式傳遞。</span><span class="sxs-lookup"><span data-stu-id="8c77d-111">Parameters added using the **Additional Connection Parameters** page are always passed as plain text.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="8c77d-112">請勿在 [其他連接參數]\*\*\*\* 頁面上包含登入認證和密碼。</span><span class="sxs-lookup"><span data-stu-id="8c77d-112">Do not include login credentials and passwords in the **Additional Connection Parameters** page.</span></span> <span data-ttu-id="8c77d-113">當透過網路傳遞認證和密碼時，將不會加密。</span><span class="sxs-lookup"><span data-stu-id="8c77d-113">They will not be encrypted when they are passed across the network.</span></span> <span data-ttu-id="8c77d-114">請改用 [登入]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8c77d-114">Use the **Login** tab instead.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="8c77d-115">工作清單</span><span class="sxs-lookup"><span data-stu-id="8c77d-115">Task List</span></span>  
  
### <a name="to-show-the-additional-connection-parameters-page"></a><span data-ttu-id="8c77d-116">顯示其他連接參數頁面</span><span class="sxs-lookup"><span data-stu-id="8c77d-116">To show the Additional Connection Parameters page</span></span>  
  
1.  <span data-ttu-id="8c77d-117">在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 的 [查詢]\*\*\*\* 功能表上，指向 [連接]\*\*\*\*，然後按一下 [連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8c77d-117">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], on the **Query** menu, point to **Connection**, and then click **Connect**.</span></span>  
  
2.  <span data-ttu-id="8c77d-118">在 [連接到]\*\*\*\* 對話方塊中，按一下 [選項]\*\*\*\*，然後按一下 [其他連接參數]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8c77d-118">In the **Connect to** dialog box, click **Options**, and then click the **Additional Connection Parameters** tab.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8c77d-119">範例</span><span class="sxs-lookup"><span data-stu-id="8c77d-119">Examples</span></span>  
  
### <a name="example-a-connecting-to-the-database-engine"></a><span data-ttu-id="8c77d-120">範例 A：連接到 Database Engine</span><span class="sxs-lookup"><span data-stu-id="8c77d-120">Example A: Connecting to the Database Engine</span></span>  
 <span data-ttu-id="8c77d-121">若要連接到 ACCOUNTING 伺服器上的 [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] 資料庫，請在 [其他連接參數]\*\*\*\* 頁面內輸入以下程式碼：</span><span class="sxs-lookup"><span data-stu-id="8c77d-121">To connect to the [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] database on a server named ACCOUNTING, enter the following in the **Additional connection parameters** page:</span></span>  
  
```  
;SERVER=ACCOUNTING;DATABASE=AdventureWorks2012  
```  
  
### <a name="example-b-connecting-to-analysis-services"></a><span data-ttu-id="8c77d-122">範例 B：連接到 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="8c77d-122">Example B: Connecting to Analysis Services</span></span>  
 <span data-ttu-id="8c77d-123">若要連接到 Analysis Servers 並使得接聽通知的所有資料分割都得以即時查詢 (略過快取)，同時將回寫逾時值設定為 5，請在 [其他連接參數]\*\*\*\* 頁面內輸入以下程式碼：</span><span class="sxs-lookup"><span data-stu-id="8c77d-123">To connect to the Analysis Servers and cause all the partitions listening for notifications to be queried as real time (bypassing caching), and to set the writeback time out value to 5, enter the following in the **Additional connection parameters** page:</span></span>  
  
```  
;Real Time Olap=TRUE;Writeback Timeout=5  
```  
  
  
