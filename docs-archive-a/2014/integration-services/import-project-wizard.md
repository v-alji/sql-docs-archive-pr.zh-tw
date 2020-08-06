---
title: 匯入專案 Wizard |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.importprojectwizard.f1
ms.assetid: 9247ad6c-4bd1-43ab-b347-583181cb9917
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 81a990995d7e98c21b61f484372d31c9a1773102
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596195"
---
# <a name="import-project-wizard"></a><span data-ttu-id="899be-102">匯入專案精靈</span><span class="sxs-lookup"><span data-stu-id="899be-102">Import Project Wizard</span></span>
  <span data-ttu-id="899be-103">使用 [ [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 匯入專案精靈] 即可根據現有的 Integration Services 專案建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="899be-103">Use the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Import Project Wizard create a new Integration Services project based on an existing one.</span></span> <span data-ttu-id="899be-104">您可以匯入已部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 目錄的專案，或從專案部署檔案 (副檔名為 .ispac) 匯入專案。</span><span class="sxs-lookup"><span data-stu-id="899be-104">Import projects that have already been deployed to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog or import projects from a project deployment file (.ispac extension).</span></span>  
  
### <a name="to-create-a-project-based-on-a-project-in-ispac-file-or-in-catalog"></a><span data-ttu-id="899be-105">若要根據 .ispac 檔案或目錄中的專案建立專案</span><span class="sxs-lookup"><span data-stu-id="899be-105">To create a project based on a project in .ispac file or in catalog</span></span>  
  
1.  <span data-ttu-id="899be-106">按一下 [檔案]，指向 [**新增** **]，然後**按一下 [專案]。</span><span class="sxs-lookup"><span data-stu-id="899be-106">Click **File**, point to **New**, and click Project.</span></span>  
  
2.  <span data-ttu-id="899be-107">展開 **[商業智慧]**，然後按一下 **[Integration Services]**。</span><span class="sxs-lookup"><span data-stu-id="899be-107">Expand **Business Intelligence**, and click **Integration Services**.</span></span>  
  
3.  <span data-ttu-id="899be-108">選取中間窗格的 **[Integration Services 匯入精靈]** 、輸入方案和專案的 **[名稱]** 、指定專案的 **[資料夾]** ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="899be-108">Select **Integration Services Import Wizard** in the middle pane, type a **name** for the solution, project, and specify the **folder** for the project, and then click **OK**.</span></span>  
  
     <span data-ttu-id="899be-109">此時，您應該會看見 **[Integration Services 匯入專案精靈]**。</span><span class="sxs-lookup"><span data-stu-id="899be-109">You should see the **Integration Services Import Project Wizard**.</span></span> <span data-ttu-id="899be-110">這個精靈會根據現有的 Integration Services 專案建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="899be-110">This wizard creates a new Integration Services project based on an existing one</span></span>  
  
4.  <span data-ttu-id="899be-111">在 **[簡介]** 頁面上，按 **[下一步]** 即可看見 **[選取來源]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="899be-111">Click **Next** on the **Introduction** page to see the **Select Source** page.</span></span>  
  
5.  <span data-ttu-id="899be-112">指定您想要從 .ispac 檔案或目錄匯入專案。</span><span class="sxs-lookup"><span data-stu-id="899be-112">Specify whether you want to import project from an .ispac file or from a catalog.</span></span>  
  
    -   <span data-ttu-id="899be-113">如果您選取 **[專案部署檔案]** 選項，請指定 .ispac 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="899be-113">If you select **Project deployment file** option, specify the path to the .ispac file.</span></span>  
  
    -   <span data-ttu-id="899be-114">如果您選取 **[Integration Services 目錄]** 選項，請指定目錄所在之資料庫伺服器執行個體的名稱，以及目錄中專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="899be-114">If you select **Integration Services Catalog** option, specify the name of database server instance on which the catalog exists, and the path to the project in the catalog.</span></span>  
  
6.  <span data-ttu-id="899be-115">在 **[選取來源]** 頁面上，按 **[下一步]** 即可看見 **[檢閱]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="899be-115">Click **Next** on the **Select Source** page to see the **Review** page.</span></span> <span data-ttu-id="899be-116">在此頁面上檢閱精靈即將執行之匯入作業的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="899be-116">Review the information displayed on the page about the import operation the wizard is going to perform.</span></span>  
  
7.  <span data-ttu-id="899be-117">按一下 **[匯入]** ，根據您所選取的 Integration Services 專案建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="899be-117">Click **Import** to create a new Integration Services project based on the one you selected.</span></span>  
  
8.  <span data-ttu-id="899be-118">**[結果]** 頁面應該會顯示精靈已執行之匯入作業的結果。</span><span class="sxs-lookup"><span data-stu-id="899be-118">The **Results** page should display the results from import operation the wizard performed.</span></span> <span data-ttu-id="899be-119">按一下 **[儲存報表]** ，將報表儲存至 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="899be-119">Click **Save Report** to save the report to an XML file.</span></span>  
  
9. <span data-ttu-id="899be-120">按一下 [關閉]\*\*\*\* 以關閉精靈。</span><span class="sxs-lookup"><span data-stu-id="899be-120">Click **Close** to close the wizard.</span></span>  
  
  
