---
title: 如何：偵錯自訂組件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services], debugging
- debugging custom assemblies [Reporting Services]
- troubleshooting [Reporting Services], custom assemblies
ms.assetid: 3a3215b3-548c-4474-81ba-3a98dd3912bf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1b5f9f5a4595d59cce98da4f753422cd07529926
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702497"
---
# <a name="how-to-debug-custom-assemblies"></a><span data-ttu-id="d3fe2-102">如何：針對自訂組件進行偵錯</span><span class="sxs-lookup"><span data-stu-id="d3fe2-102">How to: Debug Custom Assemblies</span></span>
  <span data-ttu-id="d3fe2-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 提供數個偵錯工具，可協助您分析自訂群組解碼，並找出其中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] provides several debugging tools that can help you analyze your custom assembly code and locate errors in it.</span></span> <span data-ttu-id="d3fe2-104">要使用的最佳工具將視您嘗試完成的項目而定。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-104">The best tool to use will depend on what you are trying to accomplish.</span></span> <span data-ttu-id="d3fe2-105">此範例會使用 [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-105">This example uses [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)].</span></span>  
  
 <span data-ttu-id="d3fe2-106">設計、開發和測試 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 自訂組件的建議方法，是建立包含測試報表與自訂組件的方案。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-106">The recommended way to design, develop, and test custom assemblies for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is to create a solution that contains both your test reports and your custom assembly.</span></span>  
  
### <a name="to-debug-assemblies-using-a-single-instance-of-visual-studio"></a><span data-ttu-id="d3fe2-107">若要使用 Visual Studio 的單一執行個體偵錯組件</span><span class="sxs-lookup"><span data-stu-id="d3fe2-107">To debug assemblies using a single instance of Visual Studio</span></span>  
  
1.  <span data-ttu-id="d3fe2-108">使用 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 建立新報表專案。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-108">Create a new report project using [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span>  
  
     <span data-ttu-id="d3fe2-109">在建立報表專案時，[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 也會建立一個包含該專案的方案。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-109">At the time you create a report project, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] also creates a solution to contain it.</span></span>  
  
2.  <span data-ttu-id="d3fe2-110">將新的類別庫專案加入現有的方案中。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-110">Add a new Class Library project to the existing solution.</span></span> <span data-ttu-id="d3fe2-111">請確定將報表專案設定為啟動專案。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-111">Make sure that the report project is set as the startup project.</span></span> <span data-ttu-id="d3fe2-112">如需有關如何完成這項動作的詳細資訊，請參閱您的 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 文件集。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-112">For more information about how to accomplish this, see your [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documentation.</span></span>  
  
3.  <span data-ttu-id="d3fe2-113">在 [方案總管] 中，選取方案。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-113">In Solution Explorer, select the solution.</span></span>  
  
4.  <span data-ttu-id="d3fe2-114">在 [檢視]\*\*\*\* 功能表上按一下 [屬性頁]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-114">On the **View** menu, click **Property Pages**.</span></span>  
  
     <span data-ttu-id="d3fe2-115">[方案屬性頁]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-115">The **Solution Property Pages** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="d3fe2-116">在左窗格中，若有需要，請展開 [通用屬性]\*\*\*\*，然後按一下 [專案相依性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-116">In the left pane, expand **Common Properties** if necessary, and click **Project Dependencies**.</span></span> <span data-ttu-id="d3fe2-117">從 [專案]\*\*\*\* 下拉式清單中，選取報表專案。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-117">Select the report project from the **Project** drop-down list.</span></span> <span data-ttu-id="d3fe2-118">在 [相依於]\*\*\*\* 清單中選取組件專案。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-118">Select your assembly project in the **Depends On** list.</span></span>  
  
6.  <span data-ttu-id="d3fe2-119">按一下 [確定]\*\*\*\* 儲存變更，然後關閉 [屬性頁]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-119">Click **OK** to save the changes, and close the **Property Pages** dialog.</span></span>  
  
7.  <span data-ttu-id="d3fe2-120">在 [方案總管] 中，選取自訂組件專案。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-120">In Solution Explorer, select your custom assembly project.</span></span>  
  
8.  <span data-ttu-id="d3fe2-121">在 [檢視]\*\*\*\* 功能表上按一下 [屬性頁]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-121">On the **View** menu, click **Property Pages**.</span></span>  
  
     <span data-ttu-id="d3fe2-122">[專案屬性頁]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-122">The **Project Property Pages** dialog box opens.</span></span>  
  
9. <span data-ttu-id="d3fe2-123">按一下 [建立]\*\*\*\* 索引標籤 (如果您在 C# 專案中) 或 [編譯]\*\*\*\* 索引標籤 (如果您在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 專案中)。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-123">Click the **Build** tab if you're in a C# project or the **Compile** tab if you're in a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] project.</span></span>  
  
10. <span data-ttu-id="d3fe2-124">在 [**組建** / **編譯**] 頁面上，輸入報表設計師資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-124">On the **Build**/**Compile** page, enter the path to the Report Designer folder.</span></span> <span data-ttu-id="d3fe2-125">根據預設，這是 [輸出路徑]\*\*\*\* 文字方塊中的 C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE)。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-125">By default, this is C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE) in the **Output Path** text box.</span></span> <span data-ttu-id="d3fe2-126">這將會在執行報表之前，建立自訂組件的更新版本並將它直接部署到報表設計師。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-126">This builds and deploys an updated version of your custom assembly directly to Report Designer before your report is executed.</span></span>  
  
11. <span data-ttu-id="d3fe2-127">一旦您已設計報表並開發自訂組件，請在自訂組件程式碼中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-127">Once you have designed your report and developed your custom assembly, set breakpoints in your custom assembly code.</span></span>  
  
12. <span data-ttu-id="d3fe2-128">請按 F5 鍵在 **DebugLocal** 模式之下執行報表。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-128">Run the report under **DebugLocal** mode by pressing the F5 key.</span></span> <span data-ttu-id="d3fe2-129">當報表在快顯預覽視窗中執行時，偵錯程式會叫用任何對應至組件中可執行的程式碼之中斷點。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-129">When the report executes in the pop-up preview window, the debugger hits any breakpoints that correspond to executable code in your assembly.</span></span> <span data-ttu-id="d3fe2-130">使用 F11 逐步完成自訂組件程式碼。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-130">Use F11 to step through your custom assembly code.</span></span>  
  
### <a name="to-debug-assemblies-using-two-instances-of-visual-studio"></a><span data-ttu-id="d3fe2-131">若要使用 Visual Studio 的兩個執行個體偵錯組件</span><span class="sxs-lookup"><span data-stu-id="d3fe2-131">To debug assemblies using two instances of Visual Studio</span></span>  
  
1.  <span data-ttu-id="d3fe2-132">啟動 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，然後開啟自訂組件專案。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-132">Start [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] and open your custom assembly project.</span></span>  
  
2.  <span data-ttu-id="d3fe2-133">建立專案，然後將自訂組件與隨附的 .pdb 檔案部署到報表設計師。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-133">Build the project, and deploy your custom assembly and the accompanying .pdb file to the Report Designer.</span></span> <span data-ttu-id="d3fe2-134">如需部署的詳細資訊，請參閱[部署自訂組件](deploying-a-custom-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-134">For more information about deployment, see [Deploying a Custom Assembly](deploying-a-custom-assembly.md).</span></span>  
  
3.  <span data-ttu-id="d3fe2-135">開啟使用自訂組件的報表專案，同時在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 的個別執行個體中，將自訂組件程式碼保持在開啟的狀態。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-135">Open up a report project that uses your custom assembly while leaving your custom assembly code open in a separate instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span>  
  
4.  <span data-ttu-id="d3fe2-136">導覽到包含自訂組件專案的 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 執行個體，並在程式碼中設定某些中斷點。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-136">Navigate to the instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] that contains your custom assembly project and set some break points in your code.</span></span>  
  
5.  <span data-ttu-id="d3fe2-137">當自訂組件專案仍為使用中視窗時，按一下 [偵錯]\*\*\*\* 功能表上的 [附加至處理序]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-137">With the custom assembly project still the active window, click **Attach to Process** on the **Debug** menu.</span></span>  
  
     <span data-ttu-id="d3fe2-138">[附加至處理序]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-138">The **Attach to Process** dialog opens.</span></span>  
  
6.  <span data-ttu-id="d3fe2-139">從處理序清單中，選取對應至報表專案的 devenv.exe 處理序，然後按一下 [附加]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-139">From the list of processes, select the devenv.exe process that corresponds to your Report Project and click **Attach**.</span></span>  
  
7.  <span data-ttu-id="d3fe2-140">定義在報表中將從自訂組件使用的運算式，並設計報表。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-140">Define the expressions that you will use in your report from your custom assembly and design your report.</span></span>  
  
8.  <span data-ttu-id="d3fe2-141">當您完成設計報表時，請按一下 [預覽]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-141">When you are finished designing your report, click the **Preview** tab.</span></span>  
  
     <span data-ttu-id="d3fe2-142">報表會執行，而且自訂組件程式碼應該在預先定義的中斷點中斷。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-142">The report executes, and the custom assembly code should break at your predefined break points.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d3fe2-143">使用 [預覽]\*\*\*\* 索引標籤並不會強制組件的程式碼權限。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-143">Using the **Preview** tab does not enforce code permissions for the assembly.</span></span> <span data-ttu-id="d3fe2-144">如需包括任何程式碼存取安全性錯誤的完整測試，請在 **DebugLocal** 組態設定之下啟動報表專案。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-144">For a complete test, which includes any code access security errors, start the report project under the **DebugLocal** configuration setting.</span></span>  
  
9. <span data-ttu-id="d3fe2-145">使用 F11 鍵逐步執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-145">Step through your code using the F11 key.</span></span> <span data-ttu-id="d3fe2-146">如需有關使用 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 來偵錯的詳細資訊，請參閱 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 文件集。</span><span class="sxs-lookup"><span data-stu-id="d3fe2-146">For more information about debugging using [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], see the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3fe2-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3fe2-147">See Also</span></span>  
 [<span data-ttu-id="d3fe2-148">將自訂組件與報表搭配使用</span><span class="sxs-lookup"><span data-stu-id="d3fe2-148">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
