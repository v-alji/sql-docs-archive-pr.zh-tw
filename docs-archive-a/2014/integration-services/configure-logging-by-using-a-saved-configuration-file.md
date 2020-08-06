---
title: 使用儲存的設定檔來設定記錄 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], logs
- logs [Integration Services], containers
ms.assetid: e5fdbbcb-94ca-4912-aa7c-0d89cebbd308
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8eb517462d9e932906f739678fbd46c1004fb84d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597275"
---
# <a name="configure-logging-by-using-a-saved-configuration-file"></a><span data-ttu-id="21756-102">使用已儲存的組態檔來設定記錄</span><span class="sxs-lookup"><span data-stu-id="21756-102">Configure Logging by Using a Saved Configuration File</span></span>
  <span data-ttu-id="21756-103">此程序描述如何透過載入先前儲存的記錄組態檔，為封裝中的新容器設定記錄。</span><span class="sxs-lookup"><span data-stu-id="21756-103">This procedure describes how to configure logging for new containers in a package by loading a previously saved logging configuration file.</span></span>  
  
 <span data-ttu-id="21756-104">依預設，封裝中的所有容器都使用與其父容器相同的記錄組態。</span><span class="sxs-lookup"><span data-stu-id="21756-104">By default, all containers in a package use the same logging configuration as their parent container.</span></span> <span data-ttu-id="21756-105">例如，「Foreach 迴圈」中的工作會使用與「Foreach 迴圈」相同的記錄組態。</span><span class="sxs-lookup"><span data-stu-id="21756-105">For example, the tasks in a Foreach Loop use the same logging configuration as the Foreach Loop.</span></span>  
  
### <a name="to-configure-logging-for-a-container"></a><span data-ttu-id="21756-106">若要設定容器的記錄</span><span class="sxs-lookup"><span data-stu-id="21756-106">To configure logging for a container</span></span>  
  
1.  <span data-ttu-id="21756-107">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="21756-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="21756-108">在 **[SSIS]** 功能表上，按一下 **[記錄]** 。</span><span class="sxs-lookup"><span data-stu-id="21756-108">On the **SSIS** menu, click **Logging**.</span></span>  
  
3.  <span data-ttu-id="21756-109">展開封裝樹狀檢視，並選取要設定的容器。</span><span class="sxs-lookup"><span data-stu-id="21756-109">Expand the package tree view and select the container to configure.</span></span>  
  
4.  <span data-ttu-id="21756-110">在 [提供者與記錄]  索引標籤上，選取要用於容器的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="21756-110">On the **Providers and Logs** tab, select the logs to use for the container.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="21756-111">您只可在封裝層級建立記錄檔。</span><span class="sxs-lookup"><span data-stu-id="21756-111">You can create logs only at the package level.</span></span> <span data-ttu-id="21756-112">如需詳細資訊，請參閱 [在 SQL Server Data Tools 中啟用封裝記錄功能](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="21756-112">For more information, see [Enable Package Logging in SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md).</span></span>  
  
5.  <span data-ttu-id="21756-113">按一下 [詳細資料]  索引標籤，然後按一下 [載入]  。</span><span class="sxs-lookup"><span data-stu-id="21756-113">Click the **Details** tab and click **Load**.</span></span>  
  
6.  <span data-ttu-id="21756-114">尋找要使用的記錄組態檔，然後按一下 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="21756-114">Locate the logging configuration file you want to use and click **Open**.</span></span>  
  
7.  <span data-ttu-id="21756-115">(選擇性) 在 [事件]  資料行中選取核取方塊，以選取要記錄的另一個記錄項目。</span><span class="sxs-lookup"><span data-stu-id="21756-115">Optionally, select a different log entry to log by selecting its check box in the **Events** column.</span></span> <span data-ttu-id="21756-116">按一下 [進階]  ，選取此項目所要記錄的資訊類型。</span><span class="sxs-lookup"><span data-stu-id="21756-116">Click **Advanced** to select the type of information to log for this entry.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="21756-117">新容器可能會包含原來用於建立記錄組態之容器無法使用的其他記錄項目。</span><span class="sxs-lookup"><span data-stu-id="21756-117">The new container may include additional log entries that are not available for the container originally used to create the logging configuration.</span></span> <span data-ttu-id="21756-118">如果您要記錄這些其他記錄項目，則必須手動選取之。</span><span class="sxs-lookup"><span data-stu-id="21756-118">These additional log entries must be selected manually if you want them to be logged.</span></span>  
  
8.  <span data-ttu-id="21756-119">若要儲存記錄組態的更新版本，請按一下 [儲存]  。</span><span class="sxs-lookup"><span data-stu-id="21756-119">To save the updated version of the logging configuration, click **Save**.</span></span>  
  
9. <span data-ttu-id="21756-120">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="21756-120">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21756-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21756-121">See Also</span></span>  
 [<span data-ttu-id="21756-122">Integration Services &#40;SSIS&#41; 記錄</span><span class="sxs-lookup"><span data-stu-id="21756-122">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
