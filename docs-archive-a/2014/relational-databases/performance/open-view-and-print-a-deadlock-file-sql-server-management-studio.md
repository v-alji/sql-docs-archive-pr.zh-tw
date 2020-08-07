---
title: 開啟、檢視及列印死結檔案 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], printing files
- deadlocks [SQL Server], opening files
- opening deadlock files
- printing deadlock files
ms.assetid: 5061b13f-2cb7-457a-b8d0-fbd437b510ab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 08bacd7a99e45e10163216c69057b167088441ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597786"
---
# <a name="open-view-and-print-a-deadlock-file-sql-server-management-studio"></a><span data-ttu-id="d8a1f-102">開啟、檢視及列印死結檔案 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="d8a1f-102">Open, View, and Print a Deadlock File (SQL Server Management Studio)</span></span>
  <span data-ttu-id="d8a1f-103">當 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 產生死結時，您可以擷取死結資訊並將資訊儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="d8a1f-103">When [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] generates a deadlock, you can capture and save the deadlock information to a file.</span></span> <span data-ttu-id="d8a1f-104">在儲存死結檔案之後，您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中開啟檔案，再檢視或列印它。</span><span class="sxs-lookup"><span data-stu-id="d8a1f-104">After you have saved the deadlock file, you can open it in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to view or print.</span></span>  
  
### <a name="to-open-and-view-a-deadlock-file"></a><span data-ttu-id="d8a1f-105">若要開啟和檢視死結檔案</span><span class="sxs-lookup"><span data-stu-id="d8a1f-105">To open and view a deadlock file</span></span>  
  
1.  <span data-ttu-id="d8a1f-106">**在的 [檔案**] 功能表上 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，指向 [**開啟**]， **File**然後按一下 [檔案]。</span><span class="sxs-lookup"><span data-stu-id="d8a1f-106">On the **File** menu in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="d8a1f-107">在 [開啟檔案] 對話方塊中，從 [檔案類型] 方塊中選取 .xdl 檔案類型。</span><span class="sxs-lookup"><span data-stu-id="d8a1f-107">In the **Open File** dialog box, select the .xdl file type in the **Files of type** box.</span></span> <span data-ttu-id="d8a1f-108">您現在會有一份只有死結檔案的篩選清單。</span><span class="sxs-lookup"><span data-stu-id="d8a1f-108">You will now have a filtered list of only deadlock files.</span></span>  
  
### <a name="to-print-a-deadlock-file"></a><span data-ttu-id="d8a1f-109">若要列印死結檔案</span><span class="sxs-lookup"><span data-stu-id="d8a1f-109">To print a deadlock file</span></span>  
  
1.  <span data-ttu-id="d8a1f-110">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的 [檔案]\*\*\*\* 功能表上，指向 [開啟]\*\*\*\* 並按一下 [檔案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d8a1f-110">On the **File** menu in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], point to **Open,** and then click **File**.</span></span>  
  
2.  <span data-ttu-id="d8a1f-111">在 [開啟檔案] 對話方塊中，從 [檔案類型] 方塊中選取 .xdl 檔案類型。</span><span class="sxs-lookup"><span data-stu-id="d8a1f-111">In the **Open File** dialog box, select the .xdl file type in the **Files of type** box.</span></span> <span data-ttu-id="d8a1f-112">您現在會有一份只有死結檔案的篩選清單。</span><span class="sxs-lookup"><span data-stu-id="d8a1f-112">You will now have a filtered list of only deadlock files.</span></span>  
  
3.  <span data-ttu-id="d8a1f-113">選取您要列印的死結檔案，並按一下 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d8a1f-113">Select the deadlock file you want to print, and click **Open**.</span></span>  
  
4.  <span data-ttu-id="d8a1f-114">在 [檔案]\*\*\*\* 功能表上，按一下 [列印]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d8a1f-114">On the **File** menu, click **Print.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8a1f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8a1f-115">See Also</span></span>  
 [<span data-ttu-id="d8a1f-116">儲存死結圖形 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="d8a1f-116">Save Deadlock Graphs &#40;SQL Server Profiler&#41;</span></span>](save-deadlock-graphs-sql-server-profiler.md)  
  
  
