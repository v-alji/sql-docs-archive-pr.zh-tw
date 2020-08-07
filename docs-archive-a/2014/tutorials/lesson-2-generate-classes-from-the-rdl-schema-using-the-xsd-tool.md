---
title: 第2課：使用 xsd 工具，從 RDL 架構產生類別 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a81c87f1-7977-4b30-b6ac-b38b3e2b6398
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 2c5db118ad8f94afc72cea44b9a2489f2b4fd7f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703534"
---
# <a name="lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool"></a><span data-ttu-id="4d2b6-102">第 2 課：使用 xsd 工具，從 RDL 結構描述產生類別</span><span class="sxs-lookup"><span data-stu-id="4d2b6-102">Lesson 2: Generate Classes from the RDL Schema using the xsd Tool</span></span>
  <span data-ttu-id="4d2b6-103">建立 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案之後，下一個步驟就是擷取報表定義結構描述的本機副本，並執行 XML 結構描述定義工具 (Xsd.exe)。</span><span class="sxs-lookup"><span data-stu-id="4d2b6-103">After you have created your [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] project, the next step is to retrieve a local copy of the report definition schema and run the XML Schema Definition Tool (Xsd.exe).</span></span>  
  
### <a name="to-generate-the-rdl-classes"></a><span data-ttu-id="4d2b6-104">產生 RDL 類別</span><span class="sxs-lookup"><span data-stu-id="4d2b6-104">To generate the RDL classes</span></span>  
  
1.  <span data-ttu-id="4d2b6-105">開啟 [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 的實例 (或對等的 Web 瀏覽器) 並流覽至下列 URL：</span><span class="sxs-lookup"><span data-stu-id="4d2b6-105">Open an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer (or equivalent Web browser) and navigate to the following URL:</span></span>  
  
    ```  
    https://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition/ReportDefinition.xsd  
    ```  
  
2.  <span data-ttu-id="4d2b6-106">在瀏覽器中開啟 RDL 架構之後，流覽至 [檔案]**功能表，** 然後選取 [**另存**新檔]。</span><span class="sxs-lookup"><span data-stu-id="4d2b6-106">Once the RDL schema has been opened in the browser, browse to the **File** menu, and select **Save As**.</span></span>  
  
3.  <span data-ttu-id="4d2b6-107">瀏覽至建立 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案的位置，然後以 ReportDefinition.xsd 檔案名稱儲存結構描述。</span><span class="sxs-lookup"><span data-stu-id="4d2b6-107">Browse to the location where you created your [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] project and save the schema with the file name ReportDefinition.xsd.</span></span>  
  
4.  <span data-ttu-id="4d2b6-108">儲存檔案之後，開啟命令提示字元的實例 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4d2b6-108">After the file has been saved, open an instance of the [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] command prompt.</span></span> <span data-ttu-id="4d2b6-109">若要開啟命令提示字元的實例，請按一下 [開始] 功能表，指向 [**所有程式**]，指向 [ **Microsoft Visual Studio 2010**]，指向 [ **Visual Studio Tools**然後按一下 [ \*\*Visual Studio 命令提示字元 (2010) \*\*]。</span><span class="sxs-lookup"><span data-stu-id="4d2b6-109">To open an instance of the command prompt, click the Start menu, point to **All Programs**, point to **Microsoft Visual Studio 2010**, point to **Visual Studio Tools** and click **Visual Studio Command Prompt (2010)**.</span></span>  
  
5.  <span data-ttu-id="4d2b6-110">變更目前路徑至儲存 ReportDefinition.xsd 檔案的位置：</span><span class="sxs-lookup"><span data-stu-id="4d2b6-110">Change the current path to the location where you saved the ReportDefinition.xsd file:</span></span>  
  
     `CD\<ReportDefinition.xsd Path>`  
  
6.  <span data-ttu-id="4d2b6-111">以下列命令產生其中包含 RDL 結構描述類別的 ReportDefinition.cs 檔案：</span><span class="sxs-lookup"><span data-stu-id="4d2b6-111">Generate the ReportDefinition.cs file that contains the classes for the RDL schema with the following command:</span></span>  
  
     `xsd /c /n:SampleRDLSchema ReportDefinition.xsd`  
  
     <span data-ttu-id="4d2b6-112">若要使用此命令產生 ReportDefinition.vb 檔：</span><span class="sxs-lookup"><span data-stu-id="4d2b6-112">To generate a ReportDefinition.vb file use this command:</span></span>  
  
     `xsd /c /l:VB /n:SampleRDLSchema ReportDefinition.xsd`  
  
7.  <span data-ttu-id="4d2b6-113">將 ReportDefinition.xsd 加入至您的專案。</span><span class="sxs-lookup"><span data-stu-id="4d2b6-113">Add ReportDefinition.xsd your project.</span></span> <span data-ttu-id="4d2b6-114">從 [**專案**] 功能表中，按一下 [**加入現有專案**]。</span><span class="sxs-lookup"><span data-stu-id="4d2b6-114">From the **Project** menu, click **Add Existing Item**.</span></span> <span data-ttu-id="4d2b6-115">流覽至 Reportdefinition.xsd 的位置，選取 [Reportdefinition.xsd]，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="4d2b6-115">Browse to the location of the ReportDefinition.xsd file, select ReportDefinition.xsd, and click **Add**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4d2b6-116">將 Reportdefinition.xsd 新增至專案之後，您會注意到**方案總管**ReportDefinition.cs ( .vb) 檔案不存在。</span><span class="sxs-lookup"><span data-stu-id="4d2b6-116">After you have added the ReportDefinition.xsd file to the project you will notice in **Solution Explorer** that the ReportDefinition.cs (.vb) file is not there.</span></span> <span data-ttu-id="4d2b6-117">若要顯示檔案，請按一下 ReportDefinition.xsd 檔案旁邊的展開/摺疊按鈕。</span><span class="sxs-lookup"><span data-stu-id="4d2b6-117">To display the file, click the expand/collapse button next to the ReportDefinition.xsd file.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="4d2b6-118">下一課</span><span class="sxs-lookup"><span data-stu-id="4d2b6-118">Next Lesson</span></span>  
 <span data-ttu-id="4d2b6-119">在下一課，您將撰寫程式碼，使用您從 RDL 結構描述產生的類別，從報表伺服器載入報表定義。</span><span class="sxs-lookup"><span data-stu-id="4d2b6-119">In the next lesson, you will write code to load a report definition from a report server using the classes you generated from the RDL schema.</span></span> <span data-ttu-id="4d2b6-120">請參閱[第3課：從報表伺服器載入報表定義](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4d2b6-120">See [Lesson 3: Load a Report Definition from the Report Server](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d2b6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d2b6-121">See Also</span></span>  
 <span data-ttu-id="4d2b6-122">[使用從 RDL 架構產生的類別更新報表 &#40;SSRS 教學課程&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="4d2b6-122">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="4d2b6-123">報表定義語言 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4d2b6-123">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
