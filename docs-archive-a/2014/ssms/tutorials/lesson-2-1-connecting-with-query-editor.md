---
title: 連接查詢編輯器 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 48725f54-a7b6-4b79-948e-965c1fe4eef1
author: stevestein
ms.author: sstein
ms.openlocfilehash: b50783450dfb9516c78a465806ee322d7a575377
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597509"
---
# <a name="connecting-with-query-editor"></a><span data-ttu-id="bd379-102">連接查詢編輯器</span><span class="sxs-lookup"><span data-stu-id="bd379-102">Connecting with Query Editor</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="bd379-103">允許您在未連接伺服器的情況下，撰寫或編輯程式碼。</span><span class="sxs-lookup"><span data-stu-id="bd379-103">permits you to write or edit code while disconnected from the server.</span></span> <span data-ttu-id="bd379-104">當伺服器無法使用，或您想節省寶貴的伺服器或網路資源時，這可能很有用。</span><span class="sxs-lookup"><span data-stu-id="bd379-104">This can be useful when the server is not available or when you want to conserve scarce server or network resources.</span></span> <span data-ttu-id="bd379-105">您也可以在不開啟新 [查詢編輯器] 視窗或重新輸入程式碼的情況下，將查詢編輯器改成連接到新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bd379-105">You can also change the connection of Query Editor to a new instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without opening a new Query Editor window or retyping your code.</span></span>  
  
## <a name="coding-offline"></a><span data-ttu-id="bd379-106">離線撰寫程式碼</span><span class="sxs-lookup"><span data-stu-id="bd379-106">Coding Offline</span></span>  
  
#### <a name="to-write-code-offline-and-then-connect-to-different-servers"></a><span data-ttu-id="bd379-107">若要離線撰寫程式碼，然後連接到不同的伺服器</span><span class="sxs-lookup"><span data-stu-id="bd379-107">To write code offline and then connect to different servers</span></span>  
  
1.  <span data-ttu-id="bd379-108">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 工具列上，按一下 [Database Engine 查詢]\*\*\*\* 來開啟 [查詢編輯器]。</span><span class="sxs-lookup"><span data-stu-id="bd379-108">On the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] toolbar, click **Database Engine Query** to open the Query Editor.</span></span>  
  
2.  <span data-ttu-id="bd379-109">在 [連接到 Database Engine]\*\*\*\* 對話方塊中，按一下 [取消]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd379-109">In the **Connect to Database Engine** dialog box, click **Cancel**.</span></span> <span data-ttu-id="bd379-110">此時會開啟查詢編輯器，查詢編輯器的標題列會指出您尚未連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bd379-110">The Query Editor opens, and the title bar for the Query Editor indicates that you are not connected to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="bd379-111">在 [程式碼] 窗格中，輸入下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="bd379-111">In the code pane, type the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    SELECT * FROM Production.Product;  
    GO  
    ```  
  
     <span data-ttu-id="bd379-112">此時您可以按一下 [連接]\*\*\*\*、[執行]\*\*\*\*、[剖析]\*\*\*\* 或 [顯示估計執行計畫]\*\*\*\* 來連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，您可以從 [查詢]\*\*\*\* 功能表或 [查詢編輯器] 工具列來找到它們，也可以用滑鼠右鍵按一下 [查詢編輯器] 視窗，在捷徑功能表中找到它們。</span><span class="sxs-lookup"><span data-stu-id="bd379-112">At this point you can connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by clicking **Connect**, **Execute**, **Parse**, or **Display Estimated Execution Plan**, all of which are available from either the **Query** menu, the Query Editor toolbar, or from the shortcut menu when you right-click in the Query Editor window.</span></span> <span data-ttu-id="bd379-113">在這個練習中，我們將使用工具列。</span><span class="sxs-lookup"><span data-stu-id="bd379-113">For this practice, we'll use the toolbar.</span></span>  
  
4.  <span data-ttu-id="bd379-114">在工具列上，按一下 [執行]\*\*\*\* 按鈕來開啟 [連接到 Database Engine]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="bd379-114">On the toolbar, click the **Execute** button to open the **Connect to Database Engine** dialog box.</span></span>  
  
5.  <span data-ttu-id="bd379-115">在 [伺服器名稱]\*\*\*\* 文字方塊中，輸入您的伺服器名稱，然後按一下 [選項]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd379-115">In the **Server name** text box, type your server name, and then click **Options**.</span></span>  
  
6.  <span data-ttu-id="bd379-116">在 [連接屬性]\*\*\*\* 索引標籤的 [連接到資料庫]\*\*\*\* 清單中，瀏覽伺服器來選取 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]，然後按一下 [連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd379-116">On the **Connection Properties** tab, in the **Connect to database** list, browse the server to select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] and then click **Connect**.</span></span>  
  
7.  <span data-ttu-id="bd379-117">若要利用相同連接來開啟另一個 [查詢編輯器] 視窗，請在工具列上，按一下 [新增查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd379-117">To open another Query Editor window with the same connection, on the toolbar click **New Query**.</span></span>  
  
8.  <span data-ttu-id="bd379-118">若要變更連接，請以滑鼠右鍵按一下 [查詢編輯器] 視窗，指向 [連接]\*\*\*\*，然後按一下 [變更連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd379-118">To change connections, right-click in the Query Editor window, point to **Connection**, and then click **Change Connection**.</span></span>  
  
9. <span data-ttu-id="bd379-119">在 [連接到 SQL Server]\*\*\*\* 對話方塊中，如果有另一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，請選取它，然後按一下 [連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bd379-119">In the **Connect to SQL Server** dialog box, select another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if available, and then click **Connect**.</span></span>  
  
 <span data-ttu-id="bd379-120">您可以利用查詢編輯器的這項新功能，輕易地在多部伺服器中執行相同的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bd379-120">This new feature of Query Editor enables you to easily run the same code on several servers.</span></span> <span data-ttu-id="bd379-121">如果維護動作涉及多部類似的伺服器，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="bd379-121">This may be useful for maintenance actions involving similar servers.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="bd379-122">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="bd379-122">Next Task in Lesson</span></span>  
 [<span data-ttu-id="bd379-123">加入縮排</span><span class="sxs-lookup"><span data-stu-id="bd379-123">Adding Indentation</span></span>](lesson-2-2-adding-indentation.md)  
  
  
