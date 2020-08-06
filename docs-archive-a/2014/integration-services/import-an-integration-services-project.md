---
title: 匯入 Integration Services 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3301c328-b0f5-4517-915c-93713413e453
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6a98219f3a04d11e086957d64a62e7c64cd51418
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592133"
---
# <a name="import-an-integration-services-project"></a><span data-ttu-id="37ce4-102">匯入 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="37ce4-102">Import an Integration Services Project</span></span>
  <span data-ttu-id="37ce4-103">使用 [[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 匯入專案精靈]\*\*\*\* 從現有的部署檔 (.ispac)，或從部署到 Integration Services 目錄的專案建立一個專案。</span><span class="sxs-lookup"><span data-stu-id="37ce4-103">Use the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]**Import Project Wizard** to create a project from an existing deployment file (.ispac) or from a project deployed to Integration services catalog.</span></span> <span data-ttu-id="37ce4-104">當您沒有專案的原始副本，但又想從 .ispac 檔或 SSISDB 目錄建立一個專案時，此功能特別有用。</span><span class="sxs-lookup"><span data-stu-id="37ce4-104">This feature is especially useful when you do not have the original copy of the project but you want to create one from an .ispac file or SSISDB catalog.</span></span>  
  
### <a name="to-import-a-project"></a><span data-ttu-id="37ce4-105">若要匯入專案</span><span class="sxs-lookup"><span data-stu-id="37ce4-105">To Import a Project</span></span>  
  
1.  <span data-ttu-id="37ce4-106">在中 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ， **New**按一下 [檔案]  >  功能表上的 [新增**專案**]。 **File**</span><span class="sxs-lookup"><span data-stu-id="37ce4-106">In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], click **New** > **Project** on the **File** menu.</span></span>  
  
2.  <span data-ttu-id="37ce4-107">在 **[新增專案]** 視窗的 **[已安裝的範本]** 區域中，展開 **[Business Intelligence]**，然後按一下 **[Integration Services]**。</span><span class="sxs-lookup"><span data-stu-id="37ce4-107">In the **Installed Templates** area of the **New Project** window, expand **Business Intelligence**, and click **Integration Services**.</span></span>  
  
3.  <span data-ttu-id="37ce4-108">從專案類型清單中選取 **[Integration Services 匯入專案精靈]** 。</span><span class="sxs-lookup"><span data-stu-id="37ce4-108">Select **Integration Services Import Project Wizard** from the project types list.</span></span>  
  
4.  <span data-ttu-id="37ce4-109">在 **[名稱]** 文字方塊中，為要建立的新專案輸入一個名稱。</span><span class="sxs-lookup"><span data-stu-id="37ce4-109">Type a name for the new project to be created in the **Name** text box.</span></span>  
  
5.  <span data-ttu-id="37ce4-110">在 **[位置]** 文字方塊中輸入專案的路徑或位置，或按一下 **[瀏覽]** 來選取一個路徑或位置。</span><span class="sxs-lookup"><span data-stu-id="37ce4-110">Type the path or location for the project in the **Location** text box, or click **Browse** to select one.</span></span>  
  
6.  <span data-ttu-id="37ce4-111">在 **[方案名稱]** 文字方塊中輸入方案的名稱。</span><span class="sxs-lookup"><span data-stu-id="37ce4-111">Type a name for the solution in the **Solution name** text box.</span></span>  
  
7.  <span data-ttu-id="37ce4-112">按一下 **[確定]** ，啟動 **[Integration Services 匯入專案精靈]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="37ce4-112">Click **OK** to launch the **Integration Services Import Project Wizard** dialog box.</span></span>  
  
8.  <span data-ttu-id="37ce4-113">按 **[下一步]** ，切換到 **[選取來源]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="37ce4-113">Click **Next** to switch to the **Select Source** page.</span></span>  
  
9. <span data-ttu-id="37ce4-114">如果您要從 **.ispac** 檔匯入，請在 **[路徑]** 文字方塊中輸入路徑，包括檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="37ce4-114">If you are importing from an **.ispac** file, type the path including file name in the **Path** text box.</span></span> <span data-ttu-id="37ce4-115">按一下 **[瀏覽]** 導覽到您希望儲存方案的資料夾，並在 **[檔案名稱]** 文字方塊中輸入檔案名稱，然後按一下 **[開啟]**。</span><span class="sxs-lookup"><span data-stu-id="37ce4-115">Click **Browse** to navigate to the folder where you want the solution to be stored and type file name in the **File name** text box, and click **Open**.</span></span>  
  
     <span data-ttu-id="37ce4-116">如果您要從 **[Integration Services 目錄]** 匯入，請在 **[伺服器名稱]** 文字方塊中輸入資料庫執行個體名稱，或按一下 **[瀏覽]** ，然後選取包含該目錄的資料庫執行個體。</span><span class="sxs-lookup"><span data-stu-id="37ce4-116">If you are importing from an **Integration Services Catalog**, type the database instance name in the **Server name** text box or click **Browse** and select the database instance that contains the catalog.</span></span>  
  
     <span data-ttu-id="37ce4-117">按一下 **[路徑]** 文字方塊旁的 **[瀏覽]** 、展開目錄中的資料夾、選取您要匯入的專案，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="37ce4-117">Click **Browse** next to **Path** text box, expand folder in the catalog, select the project you want to import, and click **OK**.</span></span>  
  
     <span data-ttu-id="37ce4-118">按 **[下一步]** ，切換到 **[檢閱]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="37ce4-118">Click **Next** to switch to the **Review** page.</span></span>  
  
10. <span data-ttu-id="37ce4-119">檢閱資訊，然後按一下 **[匯入]** ，即可根據您所選取的現有專案建立一個專案。</span><span class="sxs-lookup"><span data-stu-id="37ce4-119">Review the information and click **Import** to create a project based on the existing project you selected.</span></span>  
  
11. <span data-ttu-id="37ce4-120">選擇性：按一下 **[儲存報表]** ，將結果儲存到檔案中。</span><span class="sxs-lookup"><span data-stu-id="37ce4-120">Optional: click **Save Report** to save the results to a file</span></span>  
  
12. <span data-ttu-id="37ce4-121">按一下 **[關閉]** ，關閉 **[Integration Services 匯入專案精靈]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="37ce4-121">Click **Close** to close the **Integration Services Import Project Wizard** dialog box.</span></span>  
  
  
