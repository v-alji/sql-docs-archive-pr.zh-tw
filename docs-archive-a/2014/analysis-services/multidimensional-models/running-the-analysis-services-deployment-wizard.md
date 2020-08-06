---
title: 執行 Analysis Services 部署嚮導 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard, running
ms.assetid: 3a38d489-4625-4878-bd18-c6f903be33df
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6207e3e7981f52ca158f50515166d237e0524ea7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710905"
---
# <a name="running-the-analysis-services-deployment-wizard"></a><span data-ttu-id="d7226-102">執行 Analysis Services 部署精靈</span><span class="sxs-lookup"><span data-stu-id="d7226-102">Running the Analysis Services Deployment Wizard</span></span>
  <span data-ttu-id="d7226-103">當您使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署嚮導來部署專案時 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，您可以透過下列方式執行嚮導：</span><span class="sxs-lookup"><span data-stu-id="d7226-103">When you use the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard to deploy a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, you can run the wizard in the following ways:</span></span>  
  
-   <span data-ttu-id="d7226-104">**互動式** ：以互動方式執行時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈會產生以輸入檔為基礎的 XML 部署指令碼，而由使用者輸入以互動方式加以修改。</span><span class="sxs-lookup"><span data-stu-id="d7226-104">**Interactively** When run interactively, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard generates an XML deployment script based on the input files, as modified interactively by user input.</span></span> <span data-ttu-id="d7226-105">精靈只會將使用者修改套用至部署指令碼。</span><span class="sxs-lookup"><span data-stu-id="d7226-105">The wizard applies any user modifications only to the deployment script.</span></span> <span data-ttu-id="d7226-106">精靈不會修改輸入檔。</span><span class="sxs-lookup"><span data-stu-id="d7226-106">The wizard does not modify the input files.</span></span> <span data-ttu-id="d7226-107">如需關於輸入檔的詳細資訊，請參閱 [了解用來建立部署指令碼的輸入檔](deployment-script-files-input-used-to-create-deployment-script.md)。</span><span class="sxs-lookup"><span data-stu-id="d7226-107">For more information about the input files, see [Understanding the Input Files Used to Create the Deployment Script](deployment-script-files-input-used-to-create-deployment-script.md).</span></span>  
  
-   <span data-ttu-id="d7226-108">**從命令提示**字元當在命令提示字元下執行時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署嚮導會根據您用來執行嚮導的參數，產生 XML for Analysis (XMLA) 部署腳本。</span><span class="sxs-lookup"><span data-stu-id="d7226-108">**From the command prompt** When run at the command prompt, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard generates an XML for Analysis (XMLA) deployment script based upon the switches that you use to run the wizard.</span></span> <span data-ttu-id="d7226-109">此精靈可以是下列其中之一：提示使用者輸入並依據該輸入來修改輸入檔；依現狀使用輸入檔來執行無訊息自動部署；或建立可稍後使用的部署指令碼。</span><span class="sxs-lookup"><span data-stu-id="d7226-109">The wizard may any one of the following: prompt you for user input and modify input files based on that input; run a silent, unattended deployment using the input files as is; or create a deployment script that you can use later.</span></span>  
  
## <a name="running-the-analysis-services-deployment-wizard-interactively"></a><span data-ttu-id="d7226-110">以互動方式執行 Analysis Services 部署精靈</span><span class="sxs-lookup"><span data-stu-id="d7226-110">Running the Analysis Services Deployment Wizard Interactively</span></span>  
 <span data-ttu-id="d7226-111">當您以互動方式執行時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈會從輸入檔讀取值，並呈現此資訊。</span><span class="sxs-lookup"><span data-stu-id="d7226-111">When you run interactively, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard reads the values from the input files and presents this information to you.</span></span> <span data-ttu-id="d7226-112">您可以修改這些輸入值，例如部署目的地、設定、部署選項和連接字串密碼，或保持原狀。</span><span class="sxs-lookup"><span data-stu-id="d7226-112">You can modify these input values-such as deployment destination, configuration settings, deployment options, and connection string passwords-or leave them as is.</span></span> <span data-ttu-id="d7226-113">如果您變更輸入值，在產生 XMLA 部署指令碼時，精靈會使用這些變更。</span><span class="sxs-lookup"><span data-stu-id="d7226-113">If you change any input values, the wizard uses these changes when generating the XMLA deployment script.</span></span> <span data-ttu-id="d7226-114">不過，精靈不會對輸入檔中的值做任何變更。</span><span class="sxs-lookup"><span data-stu-id="d7226-114">However, the wizard does not make any changes to the values in the input file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7226-115">如果您想要讓 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈修改輸入值，請在命令提示字元下執行精靈，並設定精靈在回應檔案模式中執行。</span><span class="sxs-lookup"><span data-stu-id="d7226-115">If you want to have the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard modify the input values, run the wizard at the command prompt and set the wizard to run in answer file mode.</span></span>  
  
 <span data-ttu-id="d7226-116">在檢閱輸入值和進行任何變更之前，精靈會產生 XMLA 部署指令碼。</span><span class="sxs-lookup"><span data-stu-id="d7226-116">After you review the input values and make any wanted changes, the wizard generates the XMLA deployment script.</span></span> <span data-ttu-id="d7226-117">您可以在目的地伺服器上立即執行此部署指令碼，或儲存指令碼供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="d7226-117">You can run this deployment script immediately on the destination server or save the script for later use.</span></span>  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-interactively"></a><span data-ttu-id="d7226-118">以互動方式執行 Analysis Services 部署精靈</span><span class="sxs-lookup"><span data-stu-id="d7226-118">To run the Analysis Services Deployment Wizard interactively</span></span>  
  
-   <span data-ttu-id="d7226-119">按一下 **[開始]** 功能表，依序指向 **[所有程式]**、 **[Microsoft SQL Server]** 和 **[Analysis Services]**，然後按一下 **[部署精靈]**。</span><span class="sxs-lookup"><span data-stu-id="d7226-119">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Analysis Services**, and then click **Deployment Wizard**.</span></span>  
  
     <span data-ttu-id="d7226-120">-或-</span><span class="sxs-lookup"><span data-stu-id="d7226-120">-or-</span></span>  
  
-   <span data-ttu-id="d7226-121">在專案的 [**專案**] 資料夾中 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，按兩下 .asdatabase 檔案 *\<project name>* 。</span><span class="sxs-lookup"><span data-stu-id="d7226-121">In the **Projects** folder of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, double-click the *\<project name>*.asdatabase file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d7226-122">如果您找不到 *\<project name>* .asdatabase 檔案，請嘗試使用 [搜尋] 並指定 \*. .asdatabase。</span><span class="sxs-lookup"><span data-stu-id="d7226-122">If you cannot find the *\<project name>*.asdatabase file, try using Search and specify \*.asdatabase.</span></span>  
  
## <a name="running-the-analysis-services-deployment-wizard-at-the-command-prompt"></a><span data-ttu-id="d7226-123">在命令提示字元下執行 Analysis Services 部署精靈</span><span class="sxs-lookup"><span data-stu-id="d7226-123">Running the Analysis Services Deployment Wizard at the Command Prompt</span></span>  
 <span data-ttu-id="d7226-124">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈也可以在命令提示字元下執行。</span><span class="sxs-lookup"><span data-stu-id="d7226-124">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard can also be run at the command prompt.</span></span> <span data-ttu-id="d7226-125">當您在命令提示字元中執行精靈時，請提供 .asdatabase 檔案的完整路徑，並在下列其中一個模式下執行精靈：</span><span class="sxs-lookup"><span data-stu-id="d7226-125">When you run the wizard at the command prompt, you provide the full path to the .asdatabase file and  run the wizard in one of the following modes:</span></span>  
  
 <span data-ttu-id="d7226-126">**回應檔案模式**</span><span class="sxs-lookup"><span data-stu-id="d7226-126">**Answer file mode**</span></span>  
 <span data-ttu-id="d7226-127">在回應檔案模式中，精靈可讓您以互動方式修改 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中建立時原先產生的輸入檔。</span><span class="sxs-lookup"><span data-stu-id="d7226-127">In answer file mode, the wizard lets you interactively modify the input files that were originally generated when the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project was built in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="d7226-128">在產生 XMLA 部署指令碼之前，精靈會儲存這些修改的輸入檔。</span><span class="sxs-lookup"><span data-stu-id="d7226-128">The wizard saves these modified input files before generating the XMLA deployment script.</span></span> <span data-ttu-id="d7226-129">下次執行精靈時，已修改的輸入檔會變成新的起點。</span><span class="sxs-lookup"><span data-stu-id="d7226-129">The modified input files become the new starting point the next time that the wizard is run.</span></span>  
  
 <span data-ttu-id="d7226-130">若要在回應檔案模式中執行嚮導，請使用 **/a**參數。</span><span class="sxs-lookup"><span data-stu-id="d7226-130">To run the wizard in answer file mode, use the **/a** switch.</span></span>  
  
 <span data-ttu-id="d7226-131">**無訊息模式**</span><span class="sxs-lookup"><span data-stu-id="d7226-131">**Silent mode**</span></span>  
 <span data-ttu-id="d7226-132">在無訊息模式中，精靈會依據輸入檔的資訊來執行無訊息自動部署。</span><span class="sxs-lookup"><span data-stu-id="d7226-132">In silent mode, the wizard runs a silent, unattended deployment based on the information resident in the input files.</span></span>  
  
 <span data-ttu-id="d7226-133">若要在無訊息模式中執行嚮導，請使用 **/s**參數。</span><span class="sxs-lookup"><span data-stu-id="d7226-133">To run the wizard in silent mode, use the **/s** switch.</span></span> <span data-ttu-id="d7226-134">當您在無訊息模式中執行精靈時，訊息會輸出到主控台，或是所提供的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="d7226-134">When you run the wizard in silent mode, messages are output to the console or to a log file if one is provided.</span></span>  
  
 <span data-ttu-id="d7226-135">**輸出模式**</span><span class="sxs-lookup"><span data-stu-id="d7226-135">**Output mode**</span></span>  
 <span data-ttu-id="d7226-136">在輸出模式中，精靈會依據輸入檔產生 XMLA 部署指令碼供稍後執行。</span><span class="sxs-lookup"><span data-stu-id="d7226-136">In output mode, the wizard generates an XMLA deployment script for later execution based on the input files.</span></span>  
  
 <span data-ttu-id="d7226-137">若要在輸出模式中執行嚮導，請使用 **/o**參數並提供輸出檔名稱。</span><span class="sxs-lookup"><span data-stu-id="d7226-137">To run the wizard in output mode, use the **/o** switch and provide an output file name.</span></span>  
  
 <span data-ttu-id="d7226-138">如需關於這些命令列參數的詳細資訊，請參閱 [使用部署公用程式的部署模型方案](deploy-model-solutions-with-the-deployment-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="d7226-138">For more information about these command line switches, see [Deploy Model Solutions with the Deployment Utility](deploy-model-solutions-with-the-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="d7226-139">下列程序描述如何在命令提示字元下執行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈。</span><span class="sxs-lookup"><span data-stu-id="d7226-139">The following procedure describes how to run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard at the command prompt.</span></span>  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-at-the-command-prompt"></a><span data-ttu-id="d7226-140">在命令提示字元下執行 Analysis Services 部署精靈</span><span class="sxs-lookup"><span data-stu-id="d7226-140">To run the Analysis Services Deployment Wizard at the command prompt</span></span>  
  
1.  <span data-ttu-id="d7226-141">開啟命令提示字元，並導覽到 C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d7226-141">Open a command prompt and navigate to the C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE folder.</span></span>  
  
2.  <span data-ttu-id="d7226-142">輸入 **Microsoft.AnalysisServices.Deployment.exe** ，後面接著您要用於執行精靈之模式的對應參數。</span><span class="sxs-lookup"><span data-stu-id="d7226-142">Type **Microsoft.AnalysisServices.Deployment.exe** followed by the switches that correspond to the mode in which you want to run the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7226-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7226-143">See Also</span></span>  
 <span data-ttu-id="d7226-144">[瞭解 Analysis Services 部署腳本](understanding-the-analysis-services-deployment-script.md) </span><span class="sxs-lookup"><span data-stu-id="d7226-144">[Understanding the Analysis Services Deployment Script](understanding-the-analysis-services-deployment-script.md) </span></span>  
 [<span data-ttu-id="d7226-145">使用部署精靈部署模型解決方案</span><span class="sxs-lookup"><span data-stu-id="d7226-145">Deploy Model Solutions Using the Deployment Wizard</span></span>](deploy-model-solutions-using-the-deployment-wizard.md)  
  
  
