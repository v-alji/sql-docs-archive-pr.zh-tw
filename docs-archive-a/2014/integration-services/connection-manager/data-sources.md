---
title: 資料來源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data sources [Integration Services], about data sources
ms.assetid: 7ac81612-9822-470f-8d0f-a1dc96142fe3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a52889627dbe61254ac1359ae97f25ee8521b6e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597270"
---
# <a name="data-sources"></a><span data-ttu-id="25b13-102">資料來源</span><span class="sxs-lookup"><span data-stu-id="25b13-102">Data Sources</span></span>
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="25b13-103">包含您可以在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件中使用的設計階段物件：資料來源。</span><span class="sxs-lookup"><span data-stu-id="25b13-103">includes a design-time object that you can use in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages: the data source.</span></span>  
  
 <span data-ttu-id="25b13-104">資料來源物件是連接的參考，且至少包含連接字串和資料來源識別碼。</span><span class="sxs-lookup"><span data-stu-id="25b13-104">A data source object is a reference to a connection, and at a minimum, it includes a connection string and a data source identifier.</span></span> <span data-ttu-id="25b13-105">它也可以包含描述、名稱、使用者名稱和密碼等其他中繼資料。</span><span class="sxs-lookup"><span data-stu-id="25b13-105">It can also include additional metadata such a description, a name, a user name, and a password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25b13-106">您只能將資料來源加入到設定為使用封裝部署模型的專案。</span><span class="sxs-lookup"><span data-stu-id="25b13-106">You can add data sources only to projects that are configured to use the package deployment model.</span></span> <span data-ttu-id="25b13-107">若專案設定為使用專案部署模型，您就可以使用在專案層級建立的連接管理員來共用連接，取代使用資料來源的方式。</span><span class="sxs-lookup"><span data-stu-id="25b13-107">If a project is configured to use the project deployment model, you use connection managers created at the project level to share connections, in place of using data sources.</span></span>  
>   
>  <span data-ttu-id="25b13-108">如需有關部署模型的詳細資訊，請參閱＜ [Deployment of Projects and Packages](../packages/deploy-integration-services-ssis-projects-and-packages.md)＞。</span><span class="sxs-lookup"><span data-stu-id="25b13-108">For more information about the deployment models, see [Deployment of Projects and Packages](../packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span> <span data-ttu-id="25b13-109">如需將專案轉換為專案部署模型的詳細資訊，請參閱 [將專案部署至 Integration Services 伺服器](../deploy-projects-to-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="25b13-109">For more information about converting a project to the project deployment model, see [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="25b13-110">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝中使用資料來源的好處包括：</span><span class="sxs-lookup"><span data-stu-id="25b13-110">The advantages of using data sources in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages include the following:</span></span>  
  
-   <span data-ttu-id="25b13-111">資料來源有專案範圍，這表示 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案中建立的資料來源可使用於專案中的所有封裝。</span><span class="sxs-lookup"><span data-stu-id="25b13-111">A data source has project scope, which means that a data source created in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project is available to all the packages in the project.</span></span> <span data-ttu-id="25b13-112">資料來源只要定義一次，即可由多個封裝中的連接管理員參考。</span><span class="sxs-lookup"><span data-stu-id="25b13-112">A data source can be defined one time and then referenced by connection managers in multiple packages.</span></span>  
  
-   <span data-ttu-id="25b13-113">資料來源提供資料來源物件與其封裝參考之間的同步處理。</span><span class="sxs-lookup"><span data-stu-id="25b13-113">A data source offers synchronization between the data source object and its package references.</span></span> <span data-ttu-id="25b13-114">如果資料來源與參考資料來源的封裝位於同一專案，則資料來源參考的連接字串屬性便會在資料來源變更時自動更新。</span><span class="sxs-lookup"><span data-stu-id="25b13-114">If the data source and the packages that reference it reside in the same project, the connection string property of the data source references is automatically updated when the data source changes.</span></span>  
  
## <a name="reference-data-sources"></a><span data-ttu-id="25b13-115">參考資料來源</span><span class="sxs-lookup"><span data-stu-id="25b13-115">Reference Data Sources</span></span>  
 <span data-ttu-id="25b13-116">如果要將資料來源物件加入 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案，請以滑鼠右鍵按一下**方案總管**中的 [資料來源] 資料夾，然後按一下 [新增資料來源]。</span><span class="sxs-lookup"><span data-stu-id="25b13-116">To add a data source object to an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project, right-click the **Data Sources** folder in **Solution Explorer** and then click **New Data Source**.</span></span> <span data-ttu-id="25b13-117">項目會隨即加入至 [資料來源]  資料夾。</span><span class="sxs-lookup"><span data-stu-id="25b13-117">The item is added to the **Data Sources** folder.</span></span> <span data-ttu-id="25b13-118">如果您要使用在其他專案中建立的資料來源物件，您必須先將物件加入專案。</span><span class="sxs-lookup"><span data-stu-id="25b13-118">If you want to use data source objects that were created in other projects, you must first add them to the project.</span></span>  
  
 <span data-ttu-id="25b13-119">如果您要在封裝中使用資料來源物件，可以將參考該資料來源物件的連接管理員新增至封裝中。</span><span class="sxs-lookup"><span data-stu-id="25b13-119">You use a data source object in a package by adding a connection manager that references the data source object to the package.</span></span> <span data-ttu-id="25b13-120">在建立封裝控制流程及資料流程之前，或作為建構控制流程或資料流程程序中的一個步驟，將它新增至封裝中。</span><span class="sxs-lookup"><span data-stu-id="25b13-120">You can add it to the package before you build the package control flow and data flows, or as a step in constructing the control flow or data flow.</span></span>  
  
 <span data-ttu-id="25b13-121">資料來源物件代表至資料來源的簡單連接，並提供其參考之資料存放區中物件的存取權。</span><span class="sxs-lookup"><span data-stu-id="25b13-121">A data source object represents a simple connection to a data source and provides access to the objects in the data store that it references.</span></span> <span data-ttu-id="25b13-122">例如，連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]AdventureWorks 範例資料庫的資料來源物件包含資料庫中的所有 60 個資料表。</span><span class="sxs-lookup"><span data-stu-id="25b13-122">For example, a data source object that connects to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]AdventureWorks Sample Database includes all 60 tables from the database.</span></span>  
  
 <span data-ttu-id="25b13-123">資料來源與參考資料來源的連接管理員之間沒有相依性。</span><span class="sxs-lookup"><span data-stu-id="25b13-123">There is no dependency between a data source and the connection managers that reference it.</span></span> <span data-ttu-id="25b13-124">如果資料來源不再是專案的一部分，封裝將繼續有效，因為有關資料來源的資訊 (例如其連接類型和連接字串) 都包含在封裝定義中。</span><span class="sxs-lookup"><span data-stu-id="25b13-124">If a data source is no longer part of the project, the packages continue to be valid, because information about the data source, such as its connection type and connection string, is included in the package definition.</span></span>  
  
  
