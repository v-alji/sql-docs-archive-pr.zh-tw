---
title: 將指令碼儲存為專案或解決方案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 72dfd37f-dbe7-4d1d-bda6-7eb54c7922d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9fade3900c8859f211bb0c66820dc97792262481
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702229"
---
# <a name="save-scripts-as-projects-or-solutions"></a><span data-ttu-id="24774-102">將指令碼儲存成專案或方案</span><span class="sxs-lookup"><span data-stu-id="24774-102">Save Scripts as Projects or Solutions</span></span>
  <span data-ttu-id="24774-103">熟悉 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 的開發人員會欣然接受 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的 [方案總管]。</span><span class="sxs-lookup"><span data-stu-id="24774-103">Developers familiar with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio will welcome Solution Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="24774-104">支援您商務的指令碼可以分組成不同的指令碼專案，而且這些指令碼專案可以當作一個方案來一起管理。</span><span class="sxs-lookup"><span data-stu-id="24774-104">The scripts that support your business can be grouped into script projects, and the script projects can be managed together as a solution.</span></span> <span data-ttu-id="24774-105">當您將指令碼放在指令碼專案和方案中時，您可以將它們當作一個群組來一起開啟，也可以將它們一起儲存在 Visual SourceSafe 之類的原始檔控制產品中。</span><span class="sxs-lookup"><span data-stu-id="24774-105">When scripts are placed in script projects and solutions they can be opened together as a group, or saved together to a source control product such as Visual SourceSafe.</span></span> <span data-ttu-id="24774-106">指令碼專案包括適當執行指令碼所需要的連接資訊，且可以包括支援文字檔之類的非指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="24774-106">Script projects include the connection information for the scripts to execute properly, and can include non-script files such as a supporting text file.</span></span>  
  
 <span data-ttu-id="24774-107">下列練習將建立一份簡短的指令碼來查詢放在指令碼專案和方案中的 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="24774-107">The following practice creates a short script that queries the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, placed in a script project and solution.</span></span>  
  
## <a name="using-script-projects-and-solutions"></a><span data-ttu-id="24774-108">使用指令碼專案和方案</span><span class="sxs-lookup"><span data-stu-id="24774-108">Using Script Projects and Solutions</span></span>  
  
#### <a name="to-create-a-script-project-and-solution"></a><span data-ttu-id="24774-109">若要建立指令碼專案和方案</span><span class="sxs-lookup"><span data-stu-id="24774-109">To create a script project and solution</span></span>  
  
1.  <span data-ttu-id="24774-110">開啟 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]，再利用 [物件總管] 來連接伺服器。</span><span class="sxs-lookup"><span data-stu-id="24774-110">Open [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and connect to a server with Object Explorer.</span></span>  
  
2.  <span data-ttu-id="24774-111">在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。</span><span class="sxs-lookup"><span data-stu-id="24774-111">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="24774-112">此時會開啟 [新增專案]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="24774-112">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="24774-113">在 [名稱]\*\*\*\* 文字方塊中，輸入 **StatusCheck**，並在 [範本]\*\*\*\* 中按一下 [SQL Server 指令碼]\*\*\*\*，然後按一下 [確定]\*\*\*\* 來開啟新的方案和指令碼專案。</span><span class="sxs-lookup"><span data-stu-id="24774-113">In the **Name** text box, type **StatusCheck**, click **SQL Server Scripts** in **Templates**, and then click **OK** to open a new solution and script project.</span></span>  
  
4.  <span data-ttu-id="24774-114">在方案總管中，以滑鼠右鍵按一下 [連接]\*\*\*\*，然後按一下 [新增連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="24774-114">In Solution Explorer, right-click **Connections**, and then click **New Connection**.</span></span> <span data-ttu-id="24774-115">[連接到伺服器] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="24774-115">The **Connect to Server** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="24774-116">在 [伺服器名稱]\*\*\*\* 清單方塊中，輸入您伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="24774-116">In the **Server name** list box, type the name of your server.</span></span>  
  
6.  <span data-ttu-id="24774-117">按一下 [選項]\*\*\*\*，然後按一下 [連接屬性]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="24774-117">Click **Options**, and then click the **Connection Properties** tab.</span></span>  
  
7.  <span data-ttu-id="24774-118">在 [連接到資料庫]\*\*\*\* 方塊中，瀏覽伺服器，並選取 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫，然後按一下 [連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="24774-118">In the **Connect to database** box, browse the server, select the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, and then click **Connect**.</span></span> <span data-ttu-id="24774-119">此時會將包括資料庫的連接資訊加入專案中。</span><span class="sxs-lookup"><span data-stu-id="24774-119">The connection information including the database is added to the project.</span></span>  
  
8.  <span data-ttu-id="24774-120">如果 [屬性] 視窗沒有出現，請在 [方案總管] 中按一下新的連接，再按 F4 鍵。</span><span class="sxs-lookup"><span data-stu-id="24774-120">If the Properties window is not displayed, click the new connection in Solution Explorer, and then press F4.</span></span> <span data-ttu-id="24774-121">此時會出現連接的屬性，且會顯示連接的相關資訊，其中包括 [初始資料庫]\*\*\*\* 是 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="24774-121">The properties for the connection appear, and show information about the connection including the **Initial Database** as [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
9. <span data-ttu-id="24774-122">在方案總管中，以滑鼠右鍵按一下連接，然後按一下 [新增查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="24774-122">In Solution Explorer, right-click the connection, and then click **New Query**.</span></span> <span data-ttu-id="24774-123">此時會建立一個稱為 **SQLQuery1.sql** 的新查詢，這個查詢會連接到伺服器上的 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫，並新增至您的指令碼專案中。</span><span class="sxs-lookup"><span data-stu-id="24774-123">A new query called **SQLQuery1.sql** is created, connected to the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database on your server, and added to your script project.</span></span>  
  
10. <span data-ttu-id="24774-124">在 [查詢編輯器] 中，輸入下列查詢來判斷多少工作訂單的到期日在工作訂單開始日期之前。</span><span class="sxs-lookup"><span data-stu-id="24774-124">In Query Editor, type the following query to determine how many work orders have due dates, before the work order starting dates.</span></span> <span data-ttu-id="24774-125">(您可以從 [教學課程] 視窗中複製和貼上程式碼)。</span><span class="sxs-lookup"><span data-stu-id="24774-125">(You can copy and paste the code from the Tutorial window.)</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT COUNT(WorkOrderID)  
    FROM Production.WorkOrder  
    WHERE DueDate < StartDate;  
  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="24774-126">如果您需要更多空間來輸入您的查詢，請按 SHIFT+ALT+ENTER 鍵，切換成全螢幕模式。</span><span class="sxs-lookup"><span data-stu-id="24774-126">If you need more room to type your query, press SHIFT+ALT+ENTER, to switch to full-screen mode.</span></span>  
  
11. <span data-ttu-id="24774-127">在方案總管中，以滑鼠右鍵按一下 [SQLQuery1]\*\*\*\*，然後按一下 [重新命名]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="24774-127">In Solution Explorer, right-click **SQLQuery1**, and then click **Rename**.</span></span> <span data-ttu-id="24774-128">輸入**Check sql-dmo**作為查詢的新名稱，然後按 enter。</span><span class="sxs-lookup"><span data-stu-id="24774-128">Type **Check Workorders.sql** as the new name for the query and press ENTER.</span></span>  
  
12. <span data-ttu-id="24774-129">若要儲存您的方案和指令碼專案，請在 [檔案]\*\*\*\* 功能表上，按一下 [全部儲存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="24774-129">To save your solution and script project, on the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="24774-130">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="24774-130">Next Task in Lesson</span></span>  
 [<span data-ttu-id="24774-131">摘要：方案及指令碼專案</span><span class="sxs-lookup"><span data-stu-id="24774-131">Summary: Solutions and Script Projects</span></span>](lesson-3-4-summary-solutions-and-script-projects.md)  
  
  
