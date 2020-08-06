---
title: 建立和對應伺服器環境 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isenvprop.variables.f1
- sql12.ssis.ssms.iscreateenv.f1
- sql12.ssis.ssms.isenvprop.permissions.f1
- sql12.ssis.ssms.isenvprop.general.f1
ms.assetid: b1cbb697-713f-48e4-b234-b23724d87451
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9331b5078effb562931f45c48bd8ff975c1d1998
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594613"
---
# <a name="create-and-map-a-server-environment"></a><span data-ttu-id="5eaae-102">建立和對應伺服器環境</span><span class="sxs-lookup"><span data-stu-id="5eaae-102">Create and Map a Server Environment</span></span>
  <span data-ttu-id="5eaae-103">您可以建立伺服器環境，針對已部署至 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器之專案中所包含的封裝，指定執行值。</span><span class="sxs-lookup"><span data-stu-id="5eaae-103">You create a server environment to specify runtime values for packages contained in a project you've deployed to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="5eaae-104">接著您可以針對特定封裝、進入點封裝，或給定專案中的所有封裝，將環境變數對應至參數。</span><span class="sxs-lookup"><span data-stu-id="5eaae-104">You can then map the environment variables to parameters, for a specific package, for entry-point packages, or for all the packages in a given project.</span></span> <span data-ttu-id="5eaae-105">進入點封裝通常是執行子封裝的父封裝。</span><span class="sxs-lookup"><span data-stu-id="5eaae-105">An entry-point package is typically a parent package that executes a child package.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5eaae-106">對於某個特定執行，封裝只能藉由單一伺服器環境中包含的值執行。</span><span class="sxs-lookup"><span data-stu-id="5eaae-106">For a given execution, a package can execute only with the values contained in a single server environment.</span></span>  
  
 <span data-ttu-id="5eaae-107">您可以透過查詢檢視表，取得伺服器環境、環境參考和環境變數的清單。</span><span class="sxs-lookup"><span data-stu-id="5eaae-107">You can query views for a list of server environments, environment references, and environment variables.</span></span> <span data-ttu-id="5eaae-108">您也可以呼叫預存程序來加入、刪除及修改環境、環境參考和環境變數。</span><span class="sxs-lookup"><span data-stu-id="5eaae-108">You can also call stored to add, delete, and modify environments, environment references, and environment variables.</span></span> <span data-ttu-id="5eaae-109">如需詳細資訊，請參閱 [SSIS 目錄](catalog/ssis-catalog.md)中的＜伺服器環境、伺服器變數和伺服器環境參考＞\*\*\*\* 一節。</span><span class="sxs-lookup"><span data-stu-id="5eaae-109">For more information, see the **Server Environments, Server Variables and Server Environment References** section in [SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
### <a name="to-create-and-use-a-server-environment"></a><span data-ttu-id="5eaae-110">若要建立和使用伺服器環境</span><span class="sxs-lookup"><span data-stu-id="5eaae-110">To create and use a server environment</span></span>  
  
1.  <span data-ttu-id="5eaae-111">在中 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] ，展開 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 物件總管中的 [目錄> **SSISDB** ] 節點，然後找出您想要為其建立環境之專案的 [**環境**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5eaae-111">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], expand the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Catalogs> **SSISDB** node in Object Explorer, and locate the **Environments** folder of the project for which you want to create an environment.</span></span>  
  
2.  <span data-ttu-id="5eaae-112">在以滑鼠右鍵按一下 [環境]\*\*\*\* 資料夾，然後按一下 [建立環境]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5eaae-112">Right-click the **Environments** folder, and then click **Create Environment**.</span></span>  
  
3.  <span data-ttu-id="5eaae-113">輸入環境的名稱，並選擇性地輸入描述，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5eaae-113">Type a name for the environment and optionally a description, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="5eaae-114">以滑鼠右鍵按一下新環境，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5eaae-114">Right-click the new environment and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="5eaae-115">在 [變數]\*\*\*\* 頁面上執行下列動作，以加入變數。</span><span class="sxs-lookup"><span data-stu-id="5eaae-115">On the **Variables** page, do the following to add a variable.</span></span>  
  
    1.  <span data-ttu-id="5eaae-116">選取變數的 [類型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5eaae-116">Select the **Type** for the variable.</span></span> <span data-ttu-id="5eaae-117">變數的名稱 **無須** 與對應至該變數之專案參數的名稱相符。</span><span class="sxs-lookup"><span data-stu-id="5eaae-117">The name of the variable **does not** need to match the name of the project parameter that you map to the variable.</span></span>  
  
    2.  <span data-ttu-id="5eaae-118">選擇性地輸入變數的 [描述]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5eaae-118">Enter an optional **Description** for the variable.</span></span>  
  
    3.  <span data-ttu-id="5eaae-119">輸入環境變數的 [值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5eaae-119">Enter the **Value** for the environment variable.</span></span>  
  
         <span data-ttu-id="5eaae-120">如需環境變數名稱規則的資訊，請參閱 [SSIS 目錄](catalog/ssis-catalog.md)中的＜環境變數＞\*\*\*\* 一節。</span><span class="sxs-lookup"><span data-stu-id="5eaae-120">For information about the rules for environment variable names, see the **Environment Variable** section in [SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
    4.  <span data-ttu-id="5eaae-121">選取或清除 [區分]\*\*\*\* 核取方塊，以指出此變數是否包含機密值。</span><span class="sxs-lookup"><span data-stu-id="5eaae-121">Indicate whether the variable contains sensitive value, by selecting or clearing the **Sensitive** checkbox.</span></span>  
  
         <span data-ttu-id="5eaae-122">如果您選取 [區分]\*\*\*\*，變數值就不會顯示在 [值]\*\*\*\* 欄位內。</span><span class="sxs-lookup"><span data-stu-id="5eaae-122">If you select **Sensitive**, the variable value does not display in the **Value** field.</span></span>  
  
         <span data-ttu-id="5eaae-123">機密值將在 SSISDB 目錄中進行加密。</span><span class="sxs-lookup"><span data-stu-id="5eaae-123">Sensitive values are encrypted in the SSISDB catalog.</span></span> <span data-ttu-id="5eaae-124">如需加密的詳細資訊，請參閱 [SSIS 目錄](catalog/ssis-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="5eaae-124">For more information about the encryption, see [SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
6.  <span data-ttu-id="5eaae-125">在 [權限]\*\*\*\* 頁面上執行下列動作，對選取的使用者和角色授與或拒絕任何權限。</span><span class="sxs-lookup"><span data-stu-id="5eaae-125">On the **Permissions** page, grant or deny permissions for selected users and roles by doing the following.</span></span>  
  
    1.  <span data-ttu-id="5eaae-126">按一下 [瀏覽]\*\*\*\*，然後從 [瀏覽所有主體]\*\*\*\* 對話方塊中選取一個或多個使用者和角色。</span><span class="sxs-lookup"><span data-stu-id="5eaae-126">Click **Browse**, and then select one or more users and roles in the **Browse All Principals** dialog box.</span></span>  
  
    2.  <span data-ttu-id="5eaae-127">在 [登入或角色]\*\*\*\* 區域內，選取您想要授與或拒絕其權限的使用者或角色。</span><span class="sxs-lookup"><span data-stu-id="5eaae-127">In the **Logins or roles** area, select the user or role that you want to grant or deny permissions for.</span></span>  
  
    3.  <span data-ttu-id="5eaae-128">在 [明確]\*\*\*\* 區域內，按一下每項權限旁的 [授與]\*\*\*\* 或 [拒絕]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5eaae-128">In the **Explicit** area, click **Grant** or **Deny** next to each permission.</span></span>  
  
7.  <span data-ttu-id="5eaae-129">若要編寫環境的指令碼，請按一下 [指令碼]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5eaae-129">To script the environment, click **Script**.</span></span> <span data-ttu-id="5eaae-130">預設情況下，指令碼會顯示在新的 [查詢編輯器] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="5eaae-130">By default, the script displays in a new Query Editor window.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="5eaae-131">只要環境屬性有所增減或變更 (例如加入變數)，您就必須按一下 [指令碼]\*\*\*\*，然後才按一下 [環境屬性]\*\*\*\* 對話方塊中的 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5eaae-131">You need to click **Script** after you've made one or changes to the environment properties, such as adding a variable, and before you click **OK** in the **Environment Properties** dialog box.</span></span> <span data-ttu-id="5eaae-132">否則將不會產生指令碼。</span><span class="sxs-lookup"><span data-stu-id="5eaae-132">Otherwise, a script is not generated.</span></span>  
  
8.  <span data-ttu-id="5eaae-133">按一下 [確定]\*\*\*\*，將變更儲存至環境屬性。</span><span class="sxs-lookup"><span data-stu-id="5eaae-133">Click **OK** to save your changes to the environment properties.</span></span>  
  
9. <span data-ttu-id="5eaae-134">在物件總管中的 [SSISDB]\*\*\*\* 節點下，展開 [專案]\*\*\*\* 資料夾，以滑鼠右鍵按一下專案，然後按一下 [設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5eaae-134">Under the **SSISDB** node in Object Explorer, expand the **Projects** folder, right-click the project, and then click **Configure**.</span></span>  
  
10. <span data-ttu-id="5eaae-135">在 [參考]\*\*\*\* 頁面上，按一下 [加入]\*\*\*\* 加入環境，然後按一下 [確定]\*\*\*\* 將參考儲存至環境。</span><span class="sxs-lookup"><span data-stu-id="5eaae-135">On the **References** page, click **Add** to add an environment, and then click **OK** to save the reference to the environment.</span></span>  
  
11. <span data-ttu-id="5eaae-136">再次以滑鼠右鍵按一下專案，然後按一下 [設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5eaae-136">Right-click the project again, and then click **Configure**.</span></span>  
  
12. <span data-ttu-id="5eaae-137">若要將環境變數對應至您在設計階段加入封裝中的參數，或對應至您將 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案轉換為專案部署模型時所產生的參數，請執行下列操作。</span><span class="sxs-lookup"><span data-stu-id="5eaae-137">To map the environment variable to a parameter that you added to the package at design-time or to a parameter that was generated when you converted the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to the project deployment model, do the following.,</span></span>  
  
    1.  <span data-ttu-id="5eaae-138">在 [參數]\*\*\*\* 頁面的 [參數]\*\*\*\* 索引標籤中，按一下 [值]\*\*\*\* 欄位旁的瀏覽按鈕。</span><span class="sxs-lookup"><span data-stu-id="5eaae-138">In the **Parameters** tab on the **Parameters** page, click the browse button next to the **Value** field.</span></span>  
  
    2.  <span data-ttu-id="5eaae-139">按一下 [使用環境變數]\*\*\*\*，然後選取您建立的環境變數。</span><span class="sxs-lookup"><span data-stu-id="5eaae-139">Click **Use environment variable**, and then select the environment variable you created.</span></span>  
  
13. <span data-ttu-id="5eaae-140">若要將環境變數對應至連線管理員屬性，請執行下列操作。</span><span class="sxs-lookup"><span data-stu-id="5eaae-140">To map the environment variable to a connection manager property, do the following.</span></span> <span data-ttu-id="5eaae-141">SSIS 伺服器上會自動產生連接管理員屬性的參數。</span><span class="sxs-lookup"><span data-stu-id="5eaae-141">Parameters are automatically generated on the SSIS server for the connection manager properties.</span></span>  
  
    1.  <span data-ttu-id="5eaae-142">在 [參數]\*\*\*\* 頁面的 [連線管理員]\*\*\*\* 索引標籤中，按一下 [值]\*\*\*\* 欄位旁的瀏覽按鈕。</span><span class="sxs-lookup"><span data-stu-id="5eaae-142">In the **Connection Managers** tab on the **Parameters** page, click the browse button next to the **Value** field.</span></span>  
  
    2.  <span data-ttu-id="5eaae-143">按一下 [使用環境變數]\*\*\*\*，然後選取您建立的環境變數。</span><span class="sxs-lookup"><span data-stu-id="5eaae-143">Click **Use environment variable**, and then select the environment variable you created.</span></span>  
  
14. <span data-ttu-id="5eaae-144">按 [確定]\*\*\*\* 兩次以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="5eaae-144">Click **OK** twice to save your changes.</span></span>  
  
  
