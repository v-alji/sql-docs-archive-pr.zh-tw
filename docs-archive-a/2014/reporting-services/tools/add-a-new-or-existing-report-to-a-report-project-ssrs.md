---
title: 將新的或現有的報表新增至報表專案 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], creating
ms.assetid: 8bc0bb53-ad8a-464d-bb6a-7fea5fa62c5c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b66bf8ef0181b549900d984d20b1279f9b5005c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706189"
---
# <a name="add-a-new-or-existing-report-to-a-report-project-ssrs"></a><span data-ttu-id="29621-102">將新的或現有的報表加入報表專案 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="29621-102">Add a New or Existing Report to a Report Project (SSRS)</span></span>
  <span data-ttu-id="29621-103">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，您可以使用 [報表精靈] 或將新的空白報表加入至專案，藉以加入新的報表。</span><span class="sxs-lookup"><span data-stu-id="29621-103">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can add a new report by using the Report Wizard or by adding a new blank report to your project.</span></span> <span data-ttu-id="29621-104">您也可以加入現有的報表。</span><span class="sxs-lookup"><span data-stu-id="29621-104">You can also add an existing report.</span></span> <span data-ttu-id="29621-105">新增報表之後，您就可以看到報表名稱列在專案的 [報表]  資料夾下。</span><span class="sxs-lookup"><span data-stu-id="29621-105">After you add a report, you can see the report name listed under the **Reports** folder in your project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="29621-106">若要預覽具有現有資料來源的報表，您必須擁有報表撰寫用戶端之資料來源的權限。</span><span class="sxs-lookup"><span data-stu-id="29621-106">To preview a report with existing data sources, you must have permissions to the data source from your report authoring client.</span></span> <span data-ttu-id="29621-107">如需詳細資訊，請參閱[建立內嵌或共用資料來源 &#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="29621-107">For more information, see [Create an Embedded or Shared Data Source &#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md).</span></span>  
  
 <span data-ttu-id="29621-108">在您加入報表之後，就可以定義資料來源和資料集，以及設計報表配置。</span><span class="sxs-lookup"><span data-stu-id="29621-108">After you add a report, you can define data sources, datasets, and design a report layout.</span></span> <span data-ttu-id="29621-109">若要開始使用，請參閱[建立基本資料表報表 &#40;SSRS 教學課程&#41;](../create-a-basic-table-report-ssrs-tutorial.md) 或[資料表 &#40;報表產生器及 SSRS&#41;](../report-design/tables-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="29621-109">To get started, see [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../create-a-basic-table-report-ssrs-tutorial.md) or [Tables &#40;Report Builder  and SSRS&#41;](../report-design/tables-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-add-a-new-report-using-the-report-wizard"></a><span data-ttu-id="29621-110">使用報表精靈來加入新的報表</span><span class="sxs-lookup"><span data-stu-id="29621-110">To add a new report using the Report Wizard</span></span>  
  
1.  <span data-ttu-id="29621-111">在方案總管中，以滑鼠右鍵按一下 [報表] 資料夾，然後按一下 [新增新的報表]  。</span><span class="sxs-lookup"><span data-stu-id="29621-111">In Solution Explorer, right-click the Reports folder, and then click **Add New Report**.</span></span> <span data-ttu-id="29621-112">[報表精靈]  對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="29621-112">The **Report Wizard** dialog box opens.</span></span>  
  
     <span data-ttu-id="29621-113">這個精靈會逐步引導您建立資料來源、建立含有查詢的資料集、定義群組、指定配置、選擇含有色彩和字型的樣式，以及建立報表。</span><span class="sxs-lookup"><span data-stu-id="29621-113">The wizard steps you through creating a data source, creating a dataset with a query, defining groups, specifying a layout, choosing a style that includes color and font, and creating the report.</span></span> <span data-ttu-id="29621-114">步驟包括：</span><span class="sxs-lookup"><span data-stu-id="29621-114">The steps include:</span></span>  
  
    -   <span data-ttu-id="29621-115">**選取資料來源。**</span><span class="sxs-lookup"><span data-stu-id="29621-115">**Select a Data Source.**</span></span> <span data-ttu-id="29621-116">建立報表的第一個步驟是定義資料來源。</span><span class="sxs-lookup"><span data-stu-id="29621-116">The first step in creating a report is to define a data source.</span></span> <span data-ttu-id="29621-117">[報表精靈] 提供報表專案中所有共用資料來源的清單，也提供建立新資料來源的選項。</span><span class="sxs-lookup"><span data-stu-id="29621-117">Report Wizard provides a list of all shared data sources in the report project, in addition to an option to create a new data source.</span></span>  
  
    -   <span data-ttu-id="29621-118">**設計查詢。**</span><span class="sxs-lookup"><span data-stu-id="29621-118">**Design a Query.**</span></span> <span data-ttu-id="29621-119">下一個步驟是設計查詢。</span><span class="sxs-lookup"><span data-stu-id="29621-119">The next step is to design a query.</span></span> <span data-ttu-id="29621-120">您可以輸入查詢字串、使用查詢設計工具來建立它，或從其他報表匯入查詢。</span><span class="sxs-lookup"><span data-stu-id="29621-120">You can type the query string, build it using Query Designer, or import a query from another report.</span></span> <span data-ttu-id="29621-121">如需查詢設計工具的相關資訊，請參閱 [Reporting Services 查詢設計工具](../reporting-services-query-designers.md)。</span><span class="sxs-lookup"><span data-stu-id="29621-121">For information about Query Designers, see [Reporting Services Query Designers](../reporting-services-query-designers.md).</span></span>  
  
    -   <span data-ttu-id="29621-122">**選擇報表類型。**</span><span class="sxs-lookup"><span data-stu-id="29621-122">**Choose a Report Type.**</span></span> <span data-ttu-id="29621-123">下一個步驟是選取您要的報表類型。</span><span class="sxs-lookup"><span data-stu-id="29621-123">The next step is to select the type of report you want.</span></span> <span data-ttu-id="29621-124">您可以選擇表格式或矩陣報表。</span><span class="sxs-lookup"><span data-stu-id="29621-124">You can choose a tabular or matrix report.</span></span> <span data-ttu-id="29621-125">表格式報表有固定的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="29621-125">A tabular report has a fixed number of columns.</span></span> <span data-ttu-id="29621-126">矩陣 (或稱為交叉資料表) 報表會根據查詢的結果，而有不同的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="29621-126">A matrix, or crosstab, report has a variable number of columns based on the results of the query.</span></span> <span data-ttu-id="29621-127">對應報表會針對地理背景顯示分析。</span><span class="sxs-lookup"><span data-stu-id="29621-127">A map report displays analytical against a geographic background.</span></span>  
  
    -   <span data-ttu-id="29621-128">**選擇樣式。**</span><span class="sxs-lookup"><span data-stu-id="29621-128">**Choose a Style.**</span></span> <span data-ttu-id="29621-129">下一個步驟是使用樣式範本，將樣式套用至報表。</span><span class="sxs-lookup"><span data-stu-id="29621-129">The next step is to apply a style to the report using a style template.</span></span> <span data-ttu-id="29621-130">請選取範本，以便將字型、色彩和框線等樣式套用至報表。</span><span class="sxs-lookup"><span data-stu-id="29621-130">Select a template to apply styles such as font, color, and border style to the report.</span></span> <span data-ttu-id="29621-131">報表設計師提供六種樣式範本：Slate、Forest、Corporate、Bold、Ocean 和 Generic。</span><span class="sxs-lookup"><span data-stu-id="29621-131">Report Designer provides six style templates: Slate, Forest, Corporate, Bold, Ocean, and Generic.</span></span> <span data-ttu-id="29621-132">您也可以加入其他樣式範本。</span><span class="sxs-lookup"><span data-stu-id="29621-132">You can also add additional style templates.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="29621-133">您可以藉由編輯 \Program Files\Microsoft Visual Studio 10.0 \ Common7\IDE\PrivateAssemblies\Business 情報 Wizards\Reports\Styles<lang 資料夾中的 StyleTemplates.xml 檔案來改變現有的範本或加入新範本 \\ \> ，其中 \<lang> 是您使用的語言 (例如，如果您使用的是英文版 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ，則資料夾名稱會是 "EN" ) 。</span><span class="sxs-lookup"><span data-stu-id="29621-133">You can alter existing templates or add new ones by editing the StyleTemplates.xml file in the \Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\Business Intelligence Wizards\Reports\Styles\\<lang\> folder, where \<lang> is the language you are using (for example, if you are using the English language version of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], the folder name is "EN").</span></span> <span data-ttu-id="29621-134">此資料夾位於安裝報表設計師的電腦上。</span><span class="sxs-lookup"><span data-stu-id="29621-134">This folder is located on the computer on which Report Designer is installed.</span></span> <span data-ttu-id="29621-135">StyleTemplates.xml 檔案有兩個副本。</span><span class="sxs-lookup"><span data-stu-id="29621-135">There are two copies of the StyleTemplates.xml file.</span></span> <span data-ttu-id="29621-136">若要修改透過 [報表精靈] 套用的樣式，請編輯針對您使用的語言所建立之資料夾內的檔案。</span><span class="sxs-lookup"><span data-stu-id="29621-136">To modify the styles that are applied through the Report Wizard, edit the file that is in the folder created for the language you are using.</span></span>  
  
    -   <span data-ttu-id="29621-137">**為報表命名。**</span><span class="sxs-lookup"><span data-stu-id="29621-137">**Name the Report.**</span></span>  <span data-ttu-id="29621-138">：最後一個步驟是為報表命名，並確認報表中將要包含的欄位。</span><span class="sxs-lookup"><span data-stu-id="29621-138">The final step is to name the report and verify the fields that will be included in the report.</span></span> <span data-ttu-id="29621-139">所有步驟都完成之後，報表設計師會建立報表，並將其加入報表伺服器專案。</span><span class="sxs-lookup"><span data-stu-id="29621-139">When all steps are completed, Report Designer creates the report and adds it to the report server project.</span></span>  
  
### <a name="to-add-a-new-blank-report"></a><span data-ttu-id="29621-140">加入新的空白報表</span><span class="sxs-lookup"><span data-stu-id="29621-140">To add a new blank report</span></span>  
  
1.  <span data-ttu-id="29621-141">在 [專案]\*\*\*\* 功能表中，按一下 [新增項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="29621-141">From the **Project** menu, click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="29621-142">在 [範本]\*\*\*\* 中，按一下 [報表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="29621-142">In **Templates**, click **Report**.</span></span>  
  
3.  <span data-ttu-id="29621-143">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="29621-143">Click **Add**.</span></span>  
  
     <span data-ttu-id="29621-144">新的空白報表就會加入至專案並且顯示在設計介面上。</span><span class="sxs-lookup"><span data-stu-id="29621-144">A new blank report is added to the project and displayed on the design surface.</span></span>  
  
### <a name="to-add-an-existing-report"></a><span data-ttu-id="29621-145">加入現有的報表</span><span class="sxs-lookup"><span data-stu-id="29621-145">To add an existing report</span></span>  
  
1.  <span data-ttu-id="29621-146">從 [**專案**] 功能表中，依序按一下 [**加入**] 和 [**現有專案**]。</span><span class="sxs-lookup"><span data-stu-id="29621-146">From the **Project** menu, click **Add**, and then **Existing Item**.</span></span>  
  
2.  <span data-ttu-id="29621-147">巡覽至 .rdl 檔的位置、選取該檔案，然後按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="29621-147">Navigate to the location of the .rdl file, select it, and then click **Add**.</span></span>  
  
     <span data-ttu-id="29621-148">報表就會新增至 [報表]\*\*\*\* 資料夾底下的專案。</span><span class="sxs-lookup"><span data-stu-id="29621-148">The report is added to the project under the **Reports** folder.</span></span> <span data-ttu-id="29621-149">當您關閉並重新開啟專案時，這些報表就會按照字母順序排序。</span><span class="sxs-lookup"><span data-stu-id="29621-149">When you close and re-open the project, reports are sorted alphabetically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29621-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29621-150">See Also</span></span>  
 [<span data-ttu-id="29621-151">Reporting Services 教學課程 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="29621-151">Reporting Services Tutorials &#40;SSRS&#41;</span></span>](../reporting-services-tutorials-ssrs.md)  
  
  
