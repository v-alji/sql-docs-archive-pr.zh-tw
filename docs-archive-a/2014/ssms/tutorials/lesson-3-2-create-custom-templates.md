---
title: 建立自訂範本 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- tql
- templates [Transact-SQL], creating
- templates [Transact-SQL]
ms.assetid: 41098e78-b482-410e-bfe8-2ac10769ac4a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 771547b9c47672d2c075b5e7215d78744fe5f18e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702234"
---
# <a name="create-custom-templates"></a><span data-ttu-id="1adbf-102">建立自訂範本</span><span class="sxs-lookup"><span data-stu-id="1adbf-102">Create Custom Templates</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="1adbf-103">提供了許多一般工作的範本，但範本真正的威力，在於能夠建立您經常需要建立之複雜指令碼的自訂範本。</span><span class="sxs-lookup"><span data-stu-id="1adbf-103">comes with templates for many common tasks, but the real power of templates lies in the ability to create a custom template for a complex script that you must create frequently.</span></span> <span data-ttu-id="1adbf-104">在這個練習中，您將利用幾個參數來建立簡單的指令碼，但冗長而重複的指令碼也適合使用範本。</span><span class="sxs-lookup"><span data-stu-id="1adbf-104">In this practice you will create a simple script with few parameters, but templates are useful for long, repetitive scripts, too.</span></span>  
  
## <a name="using-custom-templates"></a><span data-ttu-id="1adbf-105">使用自訂範本</span><span class="sxs-lookup"><span data-stu-id="1adbf-105">Using Custom Templates</span></span>  
  
#### <a name="to-create-a-custom-template"></a><span data-ttu-id="1adbf-106">若要建立自訂範本</span><span class="sxs-lookup"><span data-stu-id="1adbf-106">To create a custom template</span></span>  
  
1.  <span data-ttu-id="1adbf-107">在範本總管中，展開 [SQL Server 範本]\*\*\*\*，以滑鼠右鍵按一下 [預存程序]\*\*\*\*，指向 [新增]\*\*\*\*，然後按一下 [資料夾]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1adbf-107">In Template Explorer, expand **SQL Server Templates**, right-click **Stored Procedure**, point to **New**, and then click **Folder**.</span></span>  
  
2.  <span data-ttu-id="1adbf-108">輸入 **Custom** 作為新範本資料夾的名稱，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="1adbf-108">Type **Custom** as the name of your new template folder, and then press ENTER.</span></span>  
  
3.  <span data-ttu-id="1adbf-109">以滑鼠右鍵按一下 [Custom]\*\*\*\*，指向 [新增]\*\*\*\*，然後按一下 [範本]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1adbf-109">Right-click **Custom**, point to **New**, and then click **Template**.</span></span>  
  
4.  <span data-ttu-id="1adbf-110">輸入 **WorkOrdersProc** 作為新範本的名稱，然後按 **Enter** 鍵。</span><span class="sxs-lookup"><span data-stu-id="1adbf-110">Type **WorkOrdersProc** as the name of your new template, and then press **Enter**.</span></span>  
  
5.  <span data-ttu-id="1adbf-111">以滑鼠右鍵按一下 [WorkOrdersProc]\*\*\*\*，然後按一下 [編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1adbf-111">Right-click **WorkOrdersProc**, and then click **Edit**.</span></span>  
  
6.  <span data-ttu-id="1adbf-112">在 [連接到 Database Engine]\*\*\*\* 對話方塊中，驗證連接資訊，然後按一下 [連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1adbf-112">In the **Connect to Database Engine** dialog box, verify the connection information and then click **Connect**.</span></span>  
  
7.  <span data-ttu-id="1adbf-113">在 [查詢編輯器] 中，輸入下列指令碼來建立查閱特定零件的訂單之預存程序，這裡的零件是刀片 (Blade)。</span><span class="sxs-lookup"><span data-stu-id="1adbf-113">In Query Editor, type the following script to create a stored procedure that looks up orders for a particular part, in this case the Blade.</span></span> <span data-ttu-id="1adbf-114">(您可以從 [教學課程] 視窗中複製和貼上程式碼)。</span><span class="sxs-lookup"><span data-stu-id="1adbf-114">(You can copy and paste the code from the Tutorial window.)</span></span>  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersForBlade')  
       DROP PROCEDURE dbo.WorkOrdersForBlade;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersForBlade  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = 'Blade';  
    GO  
    ```  
  
8.  <span data-ttu-id="1adbf-115">按 F5 鍵來執行此指令碼，並建立 **WorkOrdersForBlade** 程序。</span><span class="sxs-lookup"><span data-stu-id="1adbf-115">Press F5 to execute this script, creating the **WorkOrdersForBlade** procedure.</span></span>  
  
9. <span data-ttu-id="1adbf-116">在物件總管中，以滑鼠右鍵按一下您的伺服器，然後按一下 [新增查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1adbf-116">In Object Explorer, right-click your server, and then click **New Query**.</span></span> <span data-ttu-id="1adbf-117">此時會開啟一個新的 [查詢編輯器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="1adbf-117">A new Query Editor window opens.</span></span>  
  
10. <span data-ttu-id="1adbf-118">在 [查詢編輯器] 中，輸入 **EXECUTE dbo.WorkOrdersForBlade**，然後按 F5 鍵來執行查詢。</span><span class="sxs-lookup"><span data-stu-id="1adbf-118">In Query Editor, type **EXECUTE dbo.WorkOrdersForBlade**, and then press F5 to execute the query.</span></span> <span data-ttu-id="1adbf-119">確認 [結果]\*\*\*\* 窗格會傳回刀鋒視窗的工單清單。</span><span class="sxs-lookup"><span data-stu-id="1adbf-119">Confirm that the **Results** pane returns a list of work orders for blades.</span></span>  
  
11. <span data-ttu-id="1adbf-120"> (步驟 7) 中的腳本編輯範本腳本，並在四個位置以參數<strong> *<* product_name</strong>、 `nvarchar(50)` 、 <strong> *>* 名稱</strong>取代 [產品名稱] 分葉。</span><span class="sxs-lookup"><span data-stu-id="1adbf-120">Edit the template script (the script in step 7), replacing the product name Blade with the parameter <strong>*<* product_name</strong>, `nvarchar(50)`, <strong>name*>*</strong>, in four places.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1adbf-121">參數具備三個元素：想要取代的參數名稱、參數的資料類型和參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="1adbf-121">Parameters require three elements: the name of the parameter that you want to replace, the data type of the parameter, and a default value for the parameter.</span></span>  
  
12. <span data-ttu-id="1adbf-122">現在，指令碼看起來應該如下：</span><span class="sxs-lookup"><span data-stu-id="1adbf-122">Now the script should look like:</span></span>  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersFor<product_name, nvarchar(50), name>')  
       DROP PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = '<product_name, nvarchar(50), name>';  
    GO  
    ```  
  
13. <span data-ttu-id="1adbf-123">在 [檔案]\*\*\*\* 功能表上，按一下 [儲存 WorkOrdersProc.sql]\*\*\*\* 來儲存您的範本。</span><span class="sxs-lookup"><span data-stu-id="1adbf-123">On the **File** menu, click **Save WorkOrdersProc.sql** to save your template.</span></span>  
  
#### <a name="to-test-the-custom-template"></a><span data-ttu-id="1adbf-124">若要測試自訂範本</span><span class="sxs-lookup"><span data-stu-id="1adbf-124">To test the custom template</span></span>  
  
1.  <span data-ttu-id="1adbf-125">在範本總管中，依序展開 [預存程序]\*\*\*\* 和 [Custom]\*\*\*\*，然後按兩下 [WorkOrderProc]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1adbf-125">In Template Explorer, expand **Stored Procedure**, expand **Custom**, and then double-click **WorkOrderProc**.</span></span>  
  
2.  <span data-ttu-id="1adbf-126">在 [連接到 Database Engine]\*\*\*\* 對話方塊中，填妥連接資訊，然後按一下 [連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1adbf-126">In the **Connect to Database Engine** dialog box, complete the connection information and then click **Connect**.</span></span> <span data-ttu-id="1adbf-127">此時會開啟一個新的 [查詢編輯器] 視窗，其中含有 [WorkOrderProc]\*\*\*\* 範本的內容。</span><span class="sxs-lookup"><span data-stu-id="1adbf-127">A new Query Editor window opens, containing the contents of the **WorkOrderProc** template.</span></span>  
  
3.  <span data-ttu-id="1adbf-128">在 **[查詢]** 功能表上，按一下 **[指定範本參數的值]** 。</span><span class="sxs-lookup"><span data-stu-id="1adbf-128">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span>  
  
4.  <span data-ttu-id="1adbf-129">在 [**取代範本參數**] 對話方塊中，針對 [ `product_name` 值] 輸入**FreeWheel** (覆寫) 的預設內容，然後按一下 **[確定]** 關閉 [**取代範本參數**] 對話方塊，並在 [查詢編輯器] 中修改腳本。</span><span class="sxs-lookup"><span data-stu-id="1adbf-129">In the **Replace Template Parameters** dialog box, for the `product_name` value, type **FreeWheel** (overwriting the default contents), and then click **OK** to close the **Replace Template Parameters** dialog box and modify the script in the Query Editor.</span></span>  
  
5.  <span data-ttu-id="1adbf-130">按 F5 鍵來執行這項查詢，建立程序。</span><span class="sxs-lookup"><span data-stu-id="1adbf-130">Press F5 to execute the query, creating the procedure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="1adbf-131">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="1adbf-131">Next Task in Lesson</span></span>  
 [<span data-ttu-id="1adbf-132">將指令碼儲存成專案或方案</span><span class="sxs-lookup"><span data-stu-id="1adbf-132">Save Scripts as Projects or Solutions</span></span>](lesson-3-3-save-scripts-as-projects-or-solutions.md)  
  
  
