---
title: 設定檢查點以重新開機失敗的封裝 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- checkpoints [Integration Services]
- restarting packages
- starting packages
ms.assetid: 9afffa5a-d803-4653-8afc-386453fc163f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a85354377453e0b24692ab8c2b567cc8998b6b05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705350"
---
# <a name="configure-checkpoints-for-restarting-a-failed-package"></a><span data-ttu-id="cfb56-102">設定檢查點以重新啟動失敗的封裝</span><span class="sxs-lookup"><span data-stu-id="cfb56-102">Configure Checkpoints for Restarting a Failed Package</span></span>
  <span data-ttu-id="cfb56-103">您可以藉由設定套用到檢查點的屬性，來設定 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝，使之從失敗點重新啟動，而不必重新執行整個封裝。</span><span class="sxs-lookup"><span data-stu-id="cfb56-103">You configure [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages to restart from a point of failure, instead of rerunning the entire package, by setting the properties that apply to checkpoints.</span></span>  
  
### <a name="to-configure-a-package-to-restart"></a><span data-ttu-id="cfb56-104">設定封裝以重新啟動</span><span class="sxs-lookup"><span data-stu-id="cfb56-104">To configure a package to restart</span></span>  
  
1.  <span data-ttu-id="cfb56-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含要設定之封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="cfb56-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to configure.</span></span>  
  
2.  <span data-ttu-id="cfb56-106">在 **方案總管**中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="cfb56-106">In **Solution Explorer**, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="cfb56-107">按一下 **[控制流程]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cfb56-107">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="cfb56-108">以滑鼠右鍵按一下控制流程設計介面背景的任何位置，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="cfb56-108">Right-click anywhere in the background of the control flow design surface, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="cfb56-109">將 SaveCheckpoints 屬性設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="cfb56-109">Set the SaveCheckpoints property to `True`.</span></span>  
  
6.  <span data-ttu-id="cfb56-110">在 CheckpointFileName 屬性中輸入檢查點檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="cfb56-110">Type the name of the checkpoint file in the CheckpointFileName property.</span></span>  
  
7.  <span data-ttu-id="cfb56-111">將 CheckpointUsage 屬性設定為下列兩個值的其中一個：</span><span class="sxs-lookup"><span data-stu-id="cfb56-111">Set the CheckpointUsage property to one of two values:</span></span>  
  
    -   <span data-ttu-id="cfb56-112">選取 `Always`，將永遠從檢查點重新啟動封裝。</span><span class="sxs-lookup"><span data-stu-id="cfb56-112">Select `Always` to always restart the package from the checkpoint.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="cfb56-113">如果檢查點檔案不可用，則會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="cfb56-113">An error occurs if the checkpoint file is not available.</span></span>  
  
    -   <span data-ttu-id="cfb56-114">選取 `IfExists`，只有當檢查點檔案可用時才會重新啟動封裝。</span><span class="sxs-lookup"><span data-stu-id="cfb56-114">Select `IfExists` to restart the package only if the checkpoint file is available.</span></span>  
  
8.  <span data-ttu-id="cfb56-115">設定封裝可重新啟動的工作和容器。</span><span class="sxs-lookup"><span data-stu-id="cfb56-115">Configure the tasks and containers from which the package can restart.</span></span>  
  
    -   <span data-ttu-id="cfb56-116">以滑鼠右鍵按一下工作或容器，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="cfb56-116">Right-click a task or container and click **Properties**.</span></span>  
  
    -   <span data-ttu-id="cfb56-117">`True`針對每個選取的工作和容器，將 FailPackageOnFailure 屬性設定為。</span><span class="sxs-lookup"><span data-stu-id="cfb56-117">Set the FailPackageOnFailure property to `True` for each selected task and container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfb56-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfb56-118">See Also</span></span>  
 [<span data-ttu-id="cfb56-119">使用檢查點來重新啟動封裝</span><span class="sxs-lookup"><span data-stu-id="cfb56-119">Restart Packages by Using Checkpoints</span></span>](packages/restart-packages-by-using-checkpoints.md)  
  
  
