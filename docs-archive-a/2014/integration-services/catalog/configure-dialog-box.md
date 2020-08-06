---
title: 設定對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.SSIS.SSMS.ISPROJECTPROP.PARAMETERS.F1
- SQL12.SSIS.SSMS.ISPROJECTPROP.REFERENCES.F1
- sql12.dts.designer.configure.f1
ms.assetid: 10183c8d-b1be-420f-972a-96ea97d4f4d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 857baf3421f2744144e10b0df0b770538f533192
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597291"
---
# <a name="configure-dialog-box"></a><span data-ttu-id="8066a-102">設定對話方塊</span><span class="sxs-lookup"><span data-stu-id="8066a-102">Configure Dialog Box</span></span>
  <span data-ttu-id="8066a-103">使用 **[設定]** 對話方塊來針對封裝和專案設定參數、連接管理員及環境的參考。</span><span class="sxs-lookup"><span data-stu-id="8066a-103">Use the **Configure** dialog box to configure parameters, connection managers, and references to environments, for packages and projects.</span></span>  
  
 <span data-ttu-id="8066a-104">**您想要做什麼事？**</span><span class="sxs-lookup"><span data-stu-id="8066a-104">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="8066a-105">開啟設定對話方塊</span><span class="sxs-lookup"><span data-stu-id="8066a-105">Open the Configure Dialog Box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="8066a-106">在參數頁面上設定選項</span><span class="sxs-lookup"><span data-stu-id="8066a-106">Set the options on the Parameters page</span></span>](#parameter)  
  
-   [<span data-ttu-id="8066a-107">在參考頁面上設定選項</span><span class="sxs-lookup"><span data-stu-id="8066a-107">Set the options on the References page</span></span>](#references)  
  
##  <a name="open-the-configure-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="8066a-108">開啟設定對話方塊</span><span class="sxs-lookup"><span data-stu-id="8066a-108">Open the Configure Dialog Box</span></span>  
  
1.  <span data-ttu-id="8066a-109">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="8066a-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="8066a-110">您正在連線到裝載 SSISDB 資料庫的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8066a-110">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="8066a-111">在 [物件總管] 中，展開樹狀目錄以顯示 **[Integration Services 目錄]** 節點。</span><span class="sxs-lookup"><span data-stu-id="8066a-111">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="8066a-112">展開 **[SSISDB]** 節點。</span><span class="sxs-lookup"><span data-stu-id="8066a-112">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="8066a-113">展開包含您要設定之封裝或專案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="8066a-113">Expand the folder that contains the package or project that you want to configure.</span></span>  
  
5.  <span data-ttu-id="8066a-114">以滑鼠右鍵按一下封裝或專案，然後按一下 [設定]  。</span><span class="sxs-lookup"><span data-stu-id="8066a-114">Right-click the package or project, and then click **Configure**.</span></span>  
  
##  <a name="set-the-options-on-the-parameters-page"></a><a name="parameter"></a> <span data-ttu-id="8066a-115">在參數頁面上設定選項</span><span class="sxs-lookup"><span data-stu-id="8066a-115">Set the options on the Parameters page</span></span>  
 <span data-ttu-id="8066a-116">使用 **[參數]** 頁面檢視參數名稱和值，並修改這些值。</span><span class="sxs-lookup"><span data-stu-id="8066a-116">Use the **Parameters** page to view parameter names and values, and to modify the values.</span></span>  
  
 <span data-ttu-id="8066a-117">選取 [參數]  和 [連線管理員]  索引標籤的 [範圍]  下拉式清單中所顯示之參數的範圍。</span><span class="sxs-lookup"><span data-stu-id="8066a-117">Select the scope of the parameters displayed in the **Parameters** and **Connection Managers** tabs, in the **Scope** drop-down list.</span></span>  
  
 <span data-ttu-id="8066a-118">以下是 **[參數]** 索引標籤中的選項清單。</span><span class="sxs-lookup"><span data-stu-id="8066a-118">The following is a list of the options in the **Parameters** tab.</span></span>  
  
 <span data-ttu-id="8066a-119">**容器**</span><span class="sxs-lookup"><span data-stu-id="8066a-119">**Container**</span></span>  
 <span data-ttu-id="8066a-120">列出包含參數的物件。</span><span class="sxs-lookup"><span data-stu-id="8066a-120">Lists the object that contains the parameter.</span></span>  
  
 <span data-ttu-id="8066a-121">**名稱**</span><span class="sxs-lookup"><span data-stu-id="8066a-121">**Name**</span></span>  
 <span data-ttu-id="8066a-122">列出參數名稱。</span><span class="sxs-lookup"><span data-stu-id="8066a-122">Lists the parameter name.</span></span>  
  
 <span data-ttu-id="8066a-123">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="8066a-123">**Value**</span></span>  
 <span data-ttu-id="8066a-124">列出參數值。</span><span class="sxs-lookup"><span data-stu-id="8066a-124">Lists the parameter value.</span></span> <span data-ttu-id="8066a-125">按一下省略符號按鈕，在 **[設定參數值]** 對話方塊中變更此值。</span><span class="sxs-lookup"><span data-stu-id="8066a-125">Click the ellipsis button to change the value in the **Set Parameter Value** dialog box.</span></span>  
  
 <span data-ttu-id="8066a-126">以下是 **[連接管理員]** 索引標籤中的選項清單。使用此索引標籤可變更連接管理員屬性的值。</span><span class="sxs-lookup"><span data-stu-id="8066a-126">The following is a list of the options in the **Connection Managers** tab. You use this tab to change values for connection manager properties.</span></span> <span data-ttu-id="8066a-127">SSIS 伺服器上會自動產生屬性的參數。</span><span class="sxs-lookup"><span data-stu-id="8066a-127">Parameters are automatically generated on the SSIS server for the properties.</span></span>  
  
 <span data-ttu-id="8066a-128">**容器**</span><span class="sxs-lookup"><span data-stu-id="8066a-128">**Container**</span></span>  
 <span data-ttu-id="8066a-129">列出包含連接管理員的物件。</span><span class="sxs-lookup"><span data-stu-id="8066a-129">Lists the object that contains the connection manager.</span></span>  
  
 <span data-ttu-id="8066a-130">**名稱**</span><span class="sxs-lookup"><span data-stu-id="8066a-130">**Name**</span></span>  
 <span data-ttu-id="8066a-131">列出連接管理員名稱。</span><span class="sxs-lookup"><span data-stu-id="8066a-131">Lists the connection manager name.</span></span>  
  
 <span data-ttu-id="8066a-132">**屬性名稱**</span><span class="sxs-lookup"><span data-stu-id="8066a-132">**Property name**</span></span>  
 <span data-ttu-id="8066a-133">列出連接管理員屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="8066a-133">Lists the name of the connection manager property.</span></span>  
  
 <span data-ttu-id="8066a-134">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="8066a-134">**Value**</span></span>  
 <span data-ttu-id="8066a-135">列出指派給連接管理員屬性的值。</span><span class="sxs-lookup"><span data-stu-id="8066a-135">Lists the value assigned to the connection manager property.</span></span> <span data-ttu-id="8066a-136">按一下省略符號按鈕，在 **[設定參數值]** 對話方塊中變更此值。</span><span class="sxs-lookup"><span data-stu-id="8066a-136">Click the ellipsis button to change the value in the **Set Parameter Value** dialog box.</span></span> <span data-ttu-id="8066a-137">您可以輸入常值、對應包含您要使用之值的環境變數，或使用封裝中的預設值。</span><span class="sxs-lookup"><span data-stu-id="8066a-137">You can enter a literal value, map an environment variable that contains the value you want to use, or use the default value from the package.</span></span>  
  
##  <a name="set-the-options-on-the-references-page"></a><a name="references"></a> <span data-ttu-id="8066a-138">在參考頁面上設定選項</span><span class="sxs-lookup"><span data-stu-id="8066a-138">Set the options on the References page</span></span>  
 <span data-ttu-id="8066a-139">使用 **[參考]** 頁面加入及移除環境的參考，並存取環境屬性。</span><span class="sxs-lookup"><span data-stu-id="8066a-139">Use the **References** page to add and remove references to environments, and to access environment properties.</span></span>  
  
 <span data-ttu-id="8066a-140">環境會針對已部署至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器之專案中所包含的套件，指定執行值。</span><span class="sxs-lookup"><span data-stu-id="8066a-140">An environment specifies runtime values for packages contained in the projects you've deployed to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
 <span data-ttu-id="8066a-141">**環境**</span><span class="sxs-lookup"><span data-stu-id="8066a-141">**Environment**</span></span>  
 <span data-ttu-id="8066a-142">列出環境。</span><span class="sxs-lookup"><span data-stu-id="8066a-142">Lists the environment.</span></span>  
  
 <span data-ttu-id="8066a-143">**環境資料夾**</span><span class="sxs-lookup"><span data-stu-id="8066a-143">**Environment Folder**</span></span>  
 <span data-ttu-id="8066a-144">列出包含環境的資料夾。</span><span class="sxs-lookup"><span data-stu-id="8066a-144">Lists the folder that contains the environment.</span></span>  
  
 <span data-ttu-id="8066a-145">**開啟**</span><span class="sxs-lookup"><span data-stu-id="8066a-145">**Open**</span></span>  
 <span data-ttu-id="8066a-146">按一下以開啟 [環境屬性]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8066a-146">Click to open the **Environment Properties** dialog box.</span></span>  
  
 <span data-ttu-id="8066a-147">**加入**</span><span class="sxs-lookup"><span data-stu-id="8066a-147">**Add**</span></span>  
 <span data-ttu-id="8066a-148">按一下以加入環境的參考。</span><span class="sxs-lookup"><span data-stu-id="8066a-148">Click to add a reference to an environment.</span></span> <span data-ttu-id="8066a-149">在 **[瀏覽環境]** 對話方塊中，按一下環境，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="8066a-149">In the **Browse Environments** dialog box click an environment and then click **OK**.</span></span>  
  
 <span data-ttu-id="8066a-150">您可以選取 **[SSISDB]** 節點底下的任何專案資料夾中所包含的環境。</span><span class="sxs-lookup"><span data-stu-id="8066a-150">You can select an environment contained in any project folder under the **SSISDB** node.</span></span>  
  
 <span data-ttu-id="8066a-151">**移除**</span><span class="sxs-lookup"><span data-stu-id="8066a-151">**Remove**</span></span>  
 <span data-ttu-id="8066a-152">按一下 [參考]  區域中所列的環境，然後按一下 [移除]  。</span><span class="sxs-lookup"><span data-stu-id="8066a-152">Click an environment listed in the **References** area, and then click **Remove**.</span></span>  
  
  
