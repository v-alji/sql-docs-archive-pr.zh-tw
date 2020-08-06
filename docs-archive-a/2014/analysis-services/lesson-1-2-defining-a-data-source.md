---
title: 定義資料來源 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5a3e83c9-8788-431e-85b0-a68c79377ff3
author: minewiskan
ms.author: owend
ms.openlocfilehash: fdf00b47360341e2b9a99654482d65be83b86503
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584802"
---
# <a name="defining-a-data-source"></a><span data-ttu-id="23175-102">定義資料來源</span><span class="sxs-lookup"><span data-stu-id="23175-102">Defining a Data Source</span></span>
  <span data-ttu-id="23175-103">建立 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案之後，您通常會定義專案要使用的一或多個資料來源來開始使用專案。</span><span class="sxs-lookup"><span data-stu-id="23175-103">After you create an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, you generally start working with the project by defining one or more data sources that the project will use.</span></span> <span data-ttu-id="23175-104">當您定義資料來源時，要定義用來連接到資料來源的連接字串資訊。</span><span class="sxs-lookup"><span data-stu-id="23175-104">When you define a data source, you are defining the connection string information that will be used to connect to the data source.</span></span> <span data-ttu-id="23175-105">如需詳細資訊，請參閱 [建立資料來源 &#40;SSAS 多維度&#41;](multidimensional-models/create-a-data-source-ssas-multidimensional.md)。</span><span class="sxs-lookup"><span data-stu-id="23175-105">For more information, see [Create a Data Source &#40;SSAS Multidimensional&#41;](multidimensional-models/create-a-data-source-ssas-multidimensional.md).</span></span>  
  
 <span data-ttu-id="23175-106">在下列工作中，您會將 AdventureWorksDWSQLServer2012 範例資料庫定義為 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程專案的資料來源。</span><span class="sxs-lookup"><span data-stu-id="23175-106">In the following task, you define the AdventureWorksDWSQLServer2012 sample database as the data source for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project.</span></span> <span data-ttu-id="23175-107">基於這個教學課程的目的，這個資料庫是位於本機電腦上，而來源資料庫常常受主控於一部或多部遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="23175-107">While this database is located on your local computer for the purposes of this tutorial, source databases are frequently hosted on one or more remote computers.</span></span>  
  
### <a name="to-define-a-new-data-source"></a><span data-ttu-id="23175-108">若要定義新的資料來源</span><span class="sxs-lookup"><span data-stu-id="23175-108">To define a new data source</span></span>  
  
1.  <span data-ttu-id="23175-109">在方案總管中 (於 [Microsoft Visual Studio] 視窗右側)，以滑鼠右鍵按一下 [資料來源]\*\*\*\*，然後按一下 [新增資料來源]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23175-109">In Solution Explorer (on the right of the Microsoft Visual Studio window), right-click **Data Sources**, and then click **New Data Source**.</span></span>  
  
2.  <span data-ttu-id="23175-110">在 [**資料來源 wizard**] 的 [**歡迎使用資料來源嚮導]** 頁面上，按 **[下一步]** 開啟 [**選取如何定義連接**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="23175-110">On the **Welcome to the Data Source Wizard** page of the **Data Source Wizard**, click **Next** to open the **Select how to define the connection** page.</span></span>  
  
3.  <span data-ttu-id="23175-111">在 [選取如何定義連接]\*\*\*\* 頁面上，您可以根據新連接、現有的連接或先前定義的資料來源物件定義資料來源。</span><span class="sxs-lookup"><span data-stu-id="23175-111">On the **Select how to define the connection** page, you can define a data source based on a new connection, based on an existing connection, or based on a previously defined data source object.</span></span> <span data-ttu-id="23175-112">在此教學課程中，您將根據據新連接定義資料來源。</span><span class="sxs-lookup"><span data-stu-id="23175-112">In this tutorial, you define a data source based on a new connection.</span></span> <span data-ttu-id="23175-113">確認已選取 [依據現有的或新的連接建立資料來源]\*\*\*\*，然後按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23175-113">Verify that **Create a data source based on an existing or new connection** is selected, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="23175-114">在 [連線管理員]\*\*\*\* 對話方塊中，您可以定義資料來源的連線屬性。</span><span class="sxs-lookup"><span data-stu-id="23175-114">In the **Connection Manager** dialog box, you define connection properties for the data source.</span></span> <span data-ttu-id="23175-115">在 [提供者]\*\*\*\* 清單方塊中，確認已選取 [Native OLE DB\SQL Server Native Client 11.0]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23175-115">In the **Provider** list box, verify that **Native OLE DB\SQL Server Native Client 11.0** is selected.</span></span>  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]<span data-ttu-id="23175-116">也支援**提供者**清單中顯示的其他提供者。</span><span class="sxs-lookup"><span data-stu-id="23175-116">also supports other providers, which are displayed in the **Provider** list.</span></span>  
  
5.  <span data-ttu-id="23175-117">在 [**伺服器名稱**] 文字方塊中，輸入 `localhost` 。</span><span class="sxs-lookup"><span data-stu-id="23175-117">In the **Server name** text box, type `localhost`.</span></span>  
  
     <span data-ttu-id="23175-118">若要連接到本機電腦上的已命名實例，請輸入**localhost \\<\> 實例名稱**。</span><span class="sxs-lookup"><span data-stu-id="23175-118">To connect to a named instance on your local computer, type **localhost\\<instance name\>**.</span></span> <span data-ttu-id="23175-119">若要連接至特定電腦而非本機電腦，請輸入電腦名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="23175-119">To connect to the specific computer instead of the local computer, type the computer name or IP address.</span></span>  
  
6.  <span data-ttu-id="23175-120">確認已選取 [使用 Windows 驗證]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23175-120">Verify that **Use Windows Authentication** is selected.</span></span> <span data-ttu-id="23175-121">在 [選取或輸入資料庫名稱]\*\*\*\* 清單中，選取 [AdventureWorksDW2012]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23175-121">In the **Select or enter a database name** list, select **AdventureWorksDW2012**.</span></span>  
  
7.  <span data-ttu-id="23175-122">按一下 [測試連接]\*\*\*\* 測試與伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="23175-122">Click **Test Connection** to test the connection to the database.</span></span>  
  
8.  <span data-ttu-id="23175-123">按一下 [確定]\*\*\*\*，然後按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23175-123">Click **OK**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="23175-124">在精靈的 [模擬資訊]\*\*\*\* 頁面上，您可以定義 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 用來連接到資料來源的安全性認證。</span><span class="sxs-lookup"><span data-stu-id="23175-124">On the **Impersonation Information** page of the wizard, you define the security credentials for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to use to connect to the data source.</span></span> <span data-ttu-id="23175-125">模擬會影響在選取 Windows 驗證時，用於連接至資料來源的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="23175-125">Impersonation affects the Windows account used to connect to the data source when Windows Authentication is selected.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="23175-126">不支援模擬處理 OLAP 物件。</span><span class="sxs-lookup"><span data-stu-id="23175-126">does not support impersonation for processing OLAP objects.</span></span> <span data-ttu-id="23175-127">選取 [使用服務帳戶]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23175-127">Select **Use the service account**, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="23175-128">在 [正在完成精靈]\*\*\*\* 頁面上，接受預設名稱 **Adventure Works DW 2012**，然後按一下 [完成]\*\*\*\* 來建立新的資料來源。</span><span class="sxs-lookup"><span data-stu-id="23175-128">On the **Completing the Wizard** page, accept the default name, **Adventure Works DW 2012**, and then click **Finish** to create the new data source.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="23175-129">若要在建立資料來源之後修改其屬性，請按兩下 [資料來源]\*\*\*\* 資料夾中的資料來源，以便在 [資料來源設計師]\*\*\*\* 中顯示資料來源屬性。</span><span class="sxs-lookup"><span data-stu-id="23175-129">To modify the properties of the data source after it has been created, double-click the data source in the **Data Sources** folder to display the data source properties in **Data Source Designer**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="23175-130">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="23175-130">Next Task in Lesson</span></span>  
 [<span data-ttu-id="23175-131">定義資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="23175-131">Defining a Data Source View</span></span>](lesson-1-3-defining-a-data-source-view.md)  
  
## <a name="see-also"></a><span data-ttu-id="23175-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23175-132">See Also</span></span>  
 [<span data-ttu-id="23175-133">建立資料來源 &#40;SSAS 多維度&#41;</span><span class="sxs-lookup"><span data-stu-id="23175-133">Create a Data Source &#40;SSAS Multidimensional&#41;</span></span>](multidimensional-models/create-a-data-source-ssas-multidimensional.md)  
  
  
