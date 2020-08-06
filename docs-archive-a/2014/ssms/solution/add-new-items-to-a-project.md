---
title: 將新項目加入專案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 76af8692-324f-4f5e-b1a0-d72ca8a107e3
author: stevestein
ms.author: sstein
ms.openlocfilehash: c73c58952c7801b3a0e2c86652feb461292cf37c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606531"
---
# <a name="add-new-items-to-a-project"></a><span data-ttu-id="fed40-102">將新項目加入專案</span><span class="sxs-lookup"><span data-stu-id="fed40-102">Add New Items to a Project</span></span>
  <span data-ttu-id="fed40-103">請將新的項目加入專案中，來延伸應用程式功能。</span><span class="sxs-lookup"><span data-stu-id="fed40-103">Add new items to a project to extend application functionality.</span></span> <span data-ttu-id="fed40-104">新項目可以是查詢或連接。</span><span class="sxs-lookup"><span data-stu-id="fed40-104">A new item can be a query or a connection.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="fed40-105">有兩種專案類型： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指令碼專案和 Analysis Services 指令碼專案。</span><span class="sxs-lookup"><span data-stu-id="fed40-105">has two project types: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Script Project, and Analysis Services Script Project.</span></span> <span data-ttu-id="fed40-106">專案類型決定了可以加入專案中的項目。</span><span class="sxs-lookup"><span data-stu-id="fed40-106">The project type determines the items that you can add to the project.</span></span> <span data-ttu-id="fed40-107">例如，您可以將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢 (副檔名是 .sql 的檔案) 加入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指令碼專案中，但您不能將它加入 Analysis Services 指令碼專案中。</span><span class="sxs-lookup"><span data-stu-id="fed40-107">For example, you can add a [!INCLUDE[tsql](../../includes/tsql-md.md)] query (a file with a .sql extension) to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Script project, but you cannot add it to an Analysis Services Script Project.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="fed40-108">不允許您在專案內建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="fed40-108">does not allow you to create folders within projects.</span></span> <span data-ttu-id="fed40-109">若要組織您的工作，請在方案內建立多個專案。</span><span class="sxs-lookup"><span data-stu-id="fed40-109">To organize your work, create multiple projects within the solution.</span></span>  
  
### <a name="to-add-a-new-query-to-an-existing-project"></a><span data-ttu-id="fed40-110">將新查詢加入現有的專案中</span><span class="sxs-lookup"><span data-stu-id="fed40-110">To add a new query to an existing project</span></span>  
  
1.  <span data-ttu-id="fed40-111">在 [方案總管] 中，選取一個目標專案。</span><span class="sxs-lookup"><span data-stu-id="fed40-111">In Solution Explorer, select a target project.</span></span>  
  
2.  <span data-ttu-id="fed40-112">在 [專案]  功能表上，按一下 [加入新項目]  。</span><span class="sxs-lookup"><span data-stu-id="fed40-112">On the **Project** menu, click **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="fed40-113">在 [新增項目]  對話方塊的左窗格中，選取一個類別目錄。</span><span class="sxs-lookup"><span data-stu-id="fed40-113">In the **Add New Item** dialog box, select a category in the left pane.</span></span>  
  
4.  <span data-ttu-id="fed40-114">在右窗格中，選取一個查詢範本，再按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="fed40-114">Select a query template in the right pane, and then click **Add**.</span></span> <span data-ttu-id="fed40-115">此時會在專案的 [查詢]  資料夾中，加入新的查詢。</span><span class="sxs-lookup"><span data-stu-id="fed40-115">The new query is added in the **Queries** folder of the project.</span></span>  
  
5.  <span data-ttu-id="fed40-116">在 [連接到 Database Engine]  對話方塊中，指定新查詢的連接，再按一下 [連接]  。</span><span class="sxs-lookup"><span data-stu-id="fed40-116">In the **Connect to Database Engine** dialog box, specify a connection for the new query, and then click **Connect**.</span></span> <span data-ttu-id="fed40-117">如果您不要將連接關聯於這項新查詢，您可以在連接對話中，按一下 [取消]  。</span><span class="sxs-lookup"><span data-stu-id="fed40-117">You can click **Cancel** on the connection dialog if you do not want to associate a connection to the new query.</span></span>  
  
6.  <span data-ttu-id="fed40-118">如果想要的話，請在 [方案總管] 中重新命名查詢。</span><span class="sxs-lookup"><span data-stu-id="fed40-118">Rename the query in Solution Explorer if you wish.</span></span>  
  
### <a name="to-add-a-new-connection-to-an-existing-project"></a><span data-ttu-id="fed40-119">將新連接加入現有的專案中</span><span class="sxs-lookup"><span data-stu-id="fed40-119">To add a new connection to an existing project</span></span>  
  
1.  <span data-ttu-id="fed40-120">在 [方案總管] 中，選取一個目標專案。</span><span class="sxs-lookup"><span data-stu-id="fed40-120">In Solution Explorer, select a target project.</span></span>  
  
2.  <span data-ttu-id="fed40-121">在 [專案]  功能表上，按一下 [加入新項目]  。</span><span class="sxs-lookup"><span data-stu-id="fed40-121">On the **Project** menu, click **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="fed40-122">在左窗格中，選取 [連接]  。</span><span class="sxs-lookup"><span data-stu-id="fed40-122">Select **Connection** in the left pane.</span></span>  
  
4.  <span data-ttu-id="fed40-123">在右窗格中，選取 [新增連接]  ，再按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="fed40-123">Select **New Connection** in the right pane, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="fed40-124">在 [連接到 Database Engine]  對話方塊中，指定新查詢的連接，再按一下 [連接]  。</span><span class="sxs-lookup"><span data-stu-id="fed40-124">In the **Connect to Database Engine** dialog box, specify a connection for the new query, and then click **Connect**.</span></span> <span data-ttu-id="fed40-125">此時會在專案的 [連接]  資料夾中，新增連接。</span><span class="sxs-lookup"><span data-stu-id="fed40-125">The new connection gets added in the **Connections** folder of the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fed40-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fed40-126">See Also</span></span>  
 <span data-ttu-id="fed40-127">[方案總管](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="fed40-127">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="fed40-128">[使副檔名與程式碼編輯器產生關聯](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md) </span><span class="sxs-lookup"><span data-stu-id="fed40-128">[Associate File Extensions to a Code Editor](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md) </span></span>  
 <span data-ttu-id="fed40-129">[將現有專案加入至專案](add-existing-items-to-a-project.md) </span><span class="sxs-lookup"><span data-stu-id="fed40-129">[Add Existing Items to a Project](add-existing-items-to-a-project.md) </span></span>  
 [<span data-ttu-id="fed40-130">移除或刪除項目或專案</span><span class="sxs-lookup"><span data-stu-id="fed40-130">Remove or Delete an Item or Project</span></span>](remove-or-delete-an-item-or-project.md)  
  
  
