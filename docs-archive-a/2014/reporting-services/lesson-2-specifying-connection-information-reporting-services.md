---
title: 第 2 課：指定連線資訊 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c187f0abdc4b277a5f1428407b5c42ca4fd6fee6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699328"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a><span data-ttu-id="0a033-102">第 2 課：指定連接資訊 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="0a033-102">Lesson 2: Specifying Connection Information (Reporting Services)</span></span>
  <span data-ttu-id="0a033-103">將報表加入教學課程專案之後，您需要定義「資料來源」\*\*，這是讓報表從關聯式資料庫、多維度資料庫或其他資源存取資料所用的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="0a033-103">After you add a report to the Tutorial project, you need to define a *data source*, which is connection information the report uses to access data from either a relational database, multidimensional database, or other resource.</span></span>  
  
 <span data-ttu-id="0a033-104">在這一課，您將使用 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 範例資料庫做為您的資料來源。</span><span class="sxs-lookup"><span data-stu-id="0a033-104">In this lesson, you will use the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sample database as your data source.</span></span> <span data-ttu-id="0a033-105">本教學課程假設這個資料庫位於 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] 安裝在本機電腦上的預設實例中。</span><span class="sxs-lookup"><span data-stu-id="0a033-105">This tutorial assumes that this database is located in a default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] that is installed on your local computer.</span></span>  
  
### <a name="to-set-up-a-connection"></a><span data-ttu-id="0a033-106">設定連接</span><span class="sxs-lookup"><span data-stu-id="0a033-106">To set up a connection</span></span>  
  
1.  <span data-ttu-id="0a033-107">在 [**報表資料**] 窗格中，按一下 [**新增**]，然後按一下 [**資料來源**]。</span><span class="sxs-lookup"><span data-stu-id="0a033-107">In the **Report Data** pane, click **New** and then click **Data Source...**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0a033-108">如果看不到 [報表資料]\*\*\*\* 窗格，請按一下 [檢視]\*\*\*\* 功能表上的 [報表資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0a033-108">If the **Report Data** pane is not visible, from the **View** menu, click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="0a033-109">在 **[名稱]** 中，輸入 [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0a033-109">In **Name**, type [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)].</span></span>  
  
3.  <span data-ttu-id="0a033-110">確認 [內嵌連接]\*\*\*\* 已選取。</span><span class="sxs-lookup"><span data-stu-id="0a033-110">Make sure **Embedded connection** is selected.</span></span>  
  
4.  <span data-ttu-id="0a033-111">在 [類型]\*\*\*\* 中，選取 [Microsoft SQL Server]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0a033-111">In **Type**, select **Microsoft SQL Server**.</span></span>  
  
5.  <span data-ttu-id="0a033-112">在 [連接字串]\*\*\*\* 中，鍵入下列字串：</span><span class="sxs-lookup"><span data-stu-id="0a033-112">In **Connection string**, type the following:</span></span>  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2012  
    ```  
  
     <span data-ttu-id="0a033-113">這個連接字串假設 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、報表伺服器和 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫都安裝在本機電腦上，且您有登入 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫的權限。</span><span class="sxs-lookup"><span data-stu-id="0a033-113">This connection string assumes that [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the report server, and the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database are all installed on the local computer and that you have permission to log on to the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0a033-114">如果您使用 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services 或具名執行個體，則連接字串必須包括執行個體資訊：</span><span class="sxs-lookup"><span data-stu-id="0a033-114">If you are using [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services or a named instance, the connection string must include instance information:</span></span>  
    >   
    >  `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2012`  
    >   
    >  <span data-ttu-id="0a033-115">如需連接字串的詳細資訊，請參閱 Reporting Services 和[資料來源屬性對話方塊](data-source-properties-dialog-box-general.md)[中的資料連線、資料來源和連接字串](data-connections-data-sources-and-connection-strings-in-reporting-services.md)（一般）。</span><span class="sxs-lookup"><span data-stu-id="0a033-115">For more information about connection strings, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](data-connections-data-sources-and-connection-strings-in-reporting-services.md) and [Data Source Properties Dialog Box, General](data-source-properties-dialog-box-general.md).</span></span>  
  
6.  <span data-ttu-id="0a033-116">按一下左窗格中的 [認證]\*\*\*\*，然後按一下 [使用 Windows 驗證 (整合式安全性)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0a033-116">Click **Credentials** in the left pane and click **Use Windows Authentication (integrated security)**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]<span data-ttu-id="0a033-117">資料來源 [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] 會加入至 [**報表資料**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="0a033-117">data source [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] is added to the **Report Data** pane.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="0a033-118">下一項工作</span><span class="sxs-lookup"><span data-stu-id="0a033-118">Next Task</span></span>  
 <span data-ttu-id="0a033-119">您已順利定義 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 範例資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="0a033-119">You have successfully defined a connection to the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="0a033-120">下一步，您將建立報表。</span><span class="sxs-lookup"><span data-stu-id="0a033-120">Next, you will create the report.</span></span> <span data-ttu-id="0a033-121">請參閱[第 3 課：定義資料表報表的資料集 &#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0a033-121">See [Lesson 3: Defining a Dataset for the Table Report &#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a033-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a033-122">See Also</span></span>  
 [<span data-ttu-id="0a033-123">Data Connections, Data Sources, and Connection Strings in Reporting Services</span><span class="sxs-lookup"><span data-stu-id="0a033-123">Data Connections, Data Sources, and Connection Strings in Reporting Services</span></span>](data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
