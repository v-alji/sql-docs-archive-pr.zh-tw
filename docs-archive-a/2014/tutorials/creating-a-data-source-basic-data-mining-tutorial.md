---
title: 建立資料來源 (基本資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d7107c32-69ed-49a8-9b6e-32753eebf42c
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d8d5974c3685476f5d7a5751fb71bfa98384cf36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594290"
---
# <a name="creating-a-data-source-basic-data-mining-tutorial"></a><span data-ttu-id="7fe77-102">建立資料來源 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="7fe77-102">Creating a Data Source (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="7fe77-103">*資料來源*是在您的專案中儲存和管理的資料連線，並部署至您的 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="7fe77-103">A *data source* is a data connection that is saved and managed in your project and deployed to your [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="7fe77-104">資料來源包含來源資料所在的伺服器和資料庫名稱，以及任何其他必要的連接屬性。</span><span class="sxs-lookup"><span data-stu-id="7fe77-104">The data source contains the names of the server and database where your source data resides, in addition to any other required connection properties.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7fe77-105">資料庫的名稱為 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7fe77-105">The name of the database is [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].</span></span> <span data-ttu-id="7fe77-106">如果您尚未安裝此資料庫，請參閱[MICROSOFT SQL 範例資料庫](https://go.microsoft.com/fwlink/?LinkId=88417)頁面。</span><span class="sxs-lookup"><span data-stu-id="7fe77-106">If you have not already installed this database, see the [Microsoft SQL Sample Databases](https://go.microsoft.com/fwlink/?LinkId=88417) page.</span></span>  
  
### <a name="to-create-a-data-source"></a><span data-ttu-id="7fe77-107">建立資料來源</span><span class="sxs-lookup"><span data-stu-id="7fe77-107">To create a data source</span></span>  
  
1.  <span data-ttu-id="7fe77-108">在**方案總管**中，以滑鼠右鍵按一下 [**資料來源**] 資料夾，然後選取 [**新增資料來源**]。</span><span class="sxs-lookup"><span data-stu-id="7fe77-108">In **Solution Explorer**, right-click the **Data Sources** folder and select **New Data Source**.</span></span>  
  
2.  <span data-ttu-id="7fe77-109">在 [歡迎使用資料來源精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="7fe77-109">On the **Welcome to the Data Source Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="7fe77-110">在 [**選取如何定義連接**] 頁面上，按一下 [**新增**]，將連接加入 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="7fe77-110">On the **Select how to define the connection** page, click **New** to add a connection to the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
4.  <span data-ttu-id="7fe77-111">在 [**連線管理員**] 的 [**提供者**] 清單中，選取 [**原生 OLE DB\SQL Server native Client 11.0**]。</span><span class="sxs-lookup"><span data-stu-id="7fe77-111">In the **Provider** list in **Connection Manager**, select **Native OLE DB\SQL Server Native Client 11.0**.</span></span>  
  
5.  <span data-ttu-id="7fe77-112">在 [**伺服器名稱**] 方塊中，輸入或選取您已安裝的伺服器名稱 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7fe77-112">In the **Server name** box, type or select the name of the server on which you installed [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].</span></span>  
  
     <span data-ttu-id="7fe77-113">例如，如果資料庫裝載于本機伺服器上，請輸入**localhost** 。</span><span class="sxs-lookup"><span data-stu-id="7fe77-113">For example, type **localhost** if the database is hosted on the local server.</span></span>  
  
6.  <span data-ttu-id="7fe77-114">在 [**登入伺服器**] 群組中，選取 [**使用 Windows 驗證**]。</span><span class="sxs-lookup"><span data-stu-id="7fe77-114">In the **Log onto the server** group, select **Use Windows Authentication**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="7fe77-115">實作者應該盡可能使用 Windows 驗證，因為它所提供的驗證方法要比 SQL Server 驗證更安全。</span><span class="sxs-lookup"><span data-stu-id="7fe77-115">Whenever possible, implementers should use Windows Authentication, as it provides a more secure authentication method than SQL Server Authentication.</span></span> <span data-ttu-id="7fe77-116">但是，提供 SQL Server 驗證的目的是為了回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="7fe77-116">However, SQL Server Authentication is provided for backward compatibility.</span></span> <span data-ttu-id="7fe77-117">如需驗證方法的詳細資訊，請參閱[資料庫引擎設定-帳戶提供](../../2014/sql-server/install/database-engine-configuration-account-provisioning.md)。</span><span class="sxs-lookup"><span data-stu-id="7fe77-117">For more information about authentication methods, see [Database Engine Configuration - Account Provisioning](../../2014/sql-server/install/database-engine-configuration-account-provisioning.md).</span></span>  
  
7.  <span data-ttu-id="7fe77-118">在 [**選取或輸入資料庫名稱**] 清單中，選取 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] []，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="7fe77-118">In the **Select or enter a database name** list, select [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="7fe77-119">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="7fe77-119">Click **Next**.</span></span>  
  
9. <span data-ttu-id="7fe77-120">在 [模擬**資訊**] 頁面上，按一下 [**使用服務帳戶**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="7fe77-120">On the **Impersonation Information** page, click **Use the service account**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="7fe77-121">在 [**正在完成嚮導]** 頁面上，請注意，根據預設，資料來源的名稱為 [艾德作品] [DW 2012]。</span><span class="sxs-lookup"><span data-stu-id="7fe77-121">On the **Completing the Wizard** page, notice that, by default, the data source is named Adventure Works DW 2012.</span></span>  
  
10. <span data-ttu-id="7fe77-122">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="7fe77-122">Click **Finish**.</span></span>  
  
     <span data-ttu-id="7fe77-123">新的資料來源 [艾德公司 DW 2012] 會出現在方案總管的 [**資料來源**] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="7fe77-123">The new data source, Adventure Works DW 2012, appears in the **Data Sources** folder in Solution Explorer.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="7fe77-124">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="7fe77-124">Next Task in Lesson</span></span>  
 [<span data-ttu-id="7fe77-125">建立資料來源視圖 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="7fe77-125">Creating a Data Source View &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-view-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="7fe77-126">本課程的前一項工作</span><span class="sxs-lookup"><span data-stu-id="7fe77-126">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="7fe77-127">建立 Analysis Services 專案 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="7fe77-127">Creating an Analysis Services Project &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="7fe77-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fe77-128">See Also</span></span>  
 <span data-ttu-id="7fe77-129">[建立 &#40;SSAS 多維度&#41;的資料來源](https://docs.microsoft.com/analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional) </span><span class="sxs-lookup"><span data-stu-id="7fe77-129">[Create a Data Source &#40;SSAS Multidimensional&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional) </span></span>  
 <span data-ttu-id="7fe77-130">[定義資料來源](../analysis-services/lesson-1-2-defining-a-data-source.md) </span><span class="sxs-lookup"><span data-stu-id="7fe77-130">[Defining a Data Source](../analysis-services/lesson-1-2-defining-a-data-source.md) </span></span>  
 [<span data-ttu-id="7fe77-131">設定模擬選項 &#40;SSAS - 多維度&#41;</span><span class="sxs-lookup"><span data-stu-id="7fe77-131">Set Impersonation Options &#40;SSAS - Multidimensional&#41;</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/set-impersonation-options-ssas-multidimensional)  
  
  
