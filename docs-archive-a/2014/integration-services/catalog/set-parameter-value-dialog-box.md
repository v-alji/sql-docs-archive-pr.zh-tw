---
title: 設定參數值對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ce9c2201-4e9a-4495-948f-b68deeaa7955
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 637267603c66921a566ca0d2a3f49f6142cfd203
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705354"
---
# <a name="set-parameter-value-dialog-box"></a><span data-ttu-id="14379-102">設定參數值對話方塊</span><span class="sxs-lookup"><span data-stu-id="14379-102">Set Parameter Value Dialog Box</span></span>
  <span data-ttu-id="14379-103">使用 **[設定參數值]** 對話方塊來針對專案和封裝設定參數與連接管理員屬性的值。</span><span class="sxs-lookup"><span data-stu-id="14379-103">Use the **Set Parameter Value** dialog box to set values for parameters and connection manager properties, for projects and packages.</span></span>  
  
 <span data-ttu-id="14379-104">**您想要做什麼事？**</span><span class="sxs-lookup"><span data-stu-id="14379-104">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="14379-105">開啟設定參數值對話方塊</span><span class="sxs-lookup"><span data-stu-id="14379-105">Open the Set Parameter Value dialog box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="14379-106">設定選項</span><span class="sxs-lookup"><span data-stu-id="14379-106">Configure the options</span></span>](#option)  
  
##  <a name="open-the-set-parameter-value-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="14379-107">開啟設定參數值對話方塊</span><span class="sxs-lookup"><span data-stu-id="14379-107">Open the Set Parameter Value dialog box</span></span>  
  
1.  <span data-ttu-id="14379-108">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="14379-108">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="14379-109">您正在連線到裝載 SSISDB 資料庫的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="14379-109">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="14379-110">在 [物件總管] 中，展開樹狀目錄以顯示 **[Integration Services 目錄]** 節點。</span><span class="sxs-lookup"><span data-stu-id="14379-110">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="14379-111">展開 **[SSISDB]** 節點。</span><span class="sxs-lookup"><span data-stu-id="14379-111">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="14379-112">以滑鼠右鍵按一下封裝或專案，再按一下 [設定]  ，然後按一下 [參數]  索引標籤或 [連線管理員]  索引標籤中的省略符號按鈕。</span><span class="sxs-lookup"><span data-stu-id="14379-112">Right-click a package or project, click **Configure**, and then click the ellipsis button in the **Parameters** tab or in the **Connection Managers** tab.</span></span>  
  
##  <a name="configure-the-options"></a><a name="option"></a> <span data-ttu-id="14379-113">設定選項</span><span class="sxs-lookup"><span data-stu-id="14379-113">Configure the options</span></span>  
 <span data-ttu-id="14379-114">**參數**</span><span class="sxs-lookup"><span data-stu-id="14379-114">**Parameter**</span></span>  
 <span data-ttu-id="14379-115">列出參數名稱。</span><span class="sxs-lookup"><span data-stu-id="14379-115">Lists the parameter name.</span></span>  
  
 <span data-ttu-id="14379-116">**型別**</span><span class="sxs-lookup"><span data-stu-id="14379-116">**Type**</span></span>  
 <span data-ttu-id="14379-117">列出參數值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="14379-117">Lists the data type of the parameter value.</span></span>  
  
 <span data-ttu-id="14379-118">**說明**</span><span class="sxs-lookup"><span data-stu-id="14379-118">**Description**</span></span>  
 <span data-ttu-id="14379-119">顯示參數的選擇性描述。</span><span class="sxs-lookup"><span data-stu-id="14379-119">Shows an optional description for the parameter.</span></span>  
  
 <span data-ttu-id="14379-120">**編輯值**</span><span class="sxs-lookup"><span data-stu-id="14379-120">**Edit value**</span></span>  
 <span data-ttu-id="14379-121">選取此選項來編輯參數值。</span><span class="sxs-lookup"><span data-stu-id="14379-121">Select this option to edit the parameter value.</span></span>  
  
 <span data-ttu-id="14379-122">**使用封裝中的預設值**</span><span class="sxs-lookup"><span data-stu-id="14379-122">**Use default value from package**</span></span>  
 <span data-ttu-id="14379-123">選取此選項可使用儲存在封裝中的預設參數值。</span><span class="sxs-lookup"><span data-stu-id="14379-123">Select this option to use the default parameter value stored in the package.</span></span>  
  
 <span data-ttu-id="14379-124">**使用環境變數**</span><span class="sxs-lookup"><span data-stu-id="14379-124">**Use environment variable**</span></span>  
 <span data-ttu-id="14379-125">選取此選項可使用儲存在環境中的變數值，該值是由專案或封裝所參考。</span><span class="sxs-lookup"><span data-stu-id="14379-125">Select this option to use a variable value stored in the environment, which is referenced by the project or package.</span></span> <span data-ttu-id="14379-126">若要將環境參考加入至專案或封裝中，請使用 **[設定]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="14379-126">To add an environment reference to a project or package, use the **Configure** dialog box.</span></span> <span data-ttu-id="14379-127">如需相關資訊，請參閱 [Configure Dialog Box](configure-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="14379-127">For more information, see [Configure Dialog Box](configure-dialog-box.md).</span></span>  
  
  
