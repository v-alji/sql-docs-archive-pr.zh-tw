---
title: 步驟 3：修改一般檔案連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 459e3995-2116-4f15-aaa2-32f26113869c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b897f9412a8f2978ebe4137e3e79bf1d28c97844
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592116"
---
# <a name="step-3-modifying-the-flat-file-connection-manager"></a><span data-ttu-id="50042-102">步驟 3：修改一般檔案連線管理員</span><span class="sxs-lookup"><span data-stu-id="50042-102">Step 3: Modifying the Flat File Connection Manager</span></span>
  <span data-ttu-id="50042-103">在這項工作中，您將會修改您在第 1 課建立及設定的一般檔案連接管理員。</span><span class="sxs-lookup"><span data-stu-id="50042-103">In this task, you will modify the Flat File connection manager that you created and configured in Lesson 1.</span></span> <span data-ttu-id="50042-104">一開始建立時，已設定一般檔案連接管理員來以靜態方式載入單一檔案。</span><span class="sxs-lookup"><span data-stu-id="50042-104">When originally created, the Flat File connection manager was configured to statically load a single file.</span></span> <span data-ttu-id="50042-105">若要讓一般檔案連線管理員反覆載入檔案，您必須修改連線管理員的 ConnectionString 屬性來接受使用者定義變數 `User:varFileName`，這個變數包含在執行階段要載入的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="50042-105">To enable the Flat File connection manager to iteratively load files, you must modify the ConnectionString property of the connection manager to accept the user-defined variable `User:varFileName`, which contains the path of the file to be loaded at run time.</span></span>  
  
 <span data-ttu-id="50042-106">透過將連線管理員修改為使用該使用者定義變數 `User::varFileName`的值，來擴展連線管理員的 ConnectionString 屬性，使連線管理員能夠連接到不同的一般檔案。</span><span class="sxs-lookup"><span data-stu-id="50042-106">By modifying the connection manager to use the value of the user-defined variable, `User::varFileName`, to populate the ConnectionString property of the connection manager, the connection manager will be able to connect to different flat files.</span></span> <span data-ttu-id="50042-107">在執行階段，Foreach 迴圈容器的每一個反覆運算將動態更新 `User::varFileName` 變數。</span><span class="sxs-lookup"><span data-stu-id="50042-107">At run time, each iteration of the Foreach Loop container will dynamically update the `User::varFileName` variable.</span></span> <span data-ttu-id="50042-108">更新這個變數會造成連接管理員連接到不同的一般檔案，並使資料流程工作處理不同的資料集。</span><span class="sxs-lookup"><span data-stu-id="50042-108">Updating the variable, in turn, causes the connection manager to connect to a different flat file, and the data flow task to process a different set of data.</span></span>  
  
### <a name="to-configure-the-flat-file-connection-manager-to-use-a-variable-for-the-connection-string"></a><span data-ttu-id="50042-109">若要設定一般檔案連接管理員使用連接字串的變數</span><span class="sxs-lookup"><span data-stu-id="50042-109">To configure the Flat File connection manager to use a variable for the connection string</span></span>  
  
1.  <span data-ttu-id="50042-110">在 **[連接管理員]** 窗格中，以滑鼠右鍵按一下 **[範例一般檔案來源資料]** ，並選取 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="50042-110">In the **Connection Managers** pane, right-click **Sample Flat File Source Data**, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="50042-111">在 [屬性視窗中，針對 [**運算式**] 按一下空白儲存格，然後按一下省略號按鈕 [ \*\* (] ) \*\*。</span><span class="sxs-lookup"><span data-stu-id="50042-111">In the Properties window, for **Expressions**, click in the empty cell, and then click the ellipsis button **(...)**.</span></span>  
  
3.  <span data-ttu-id="50042-112">在 [**屬性運算式編輯器**] 對話方塊的 [**屬性**] 資料行中，輸入或選取 `ConnectionString` 。</span><span class="sxs-lookup"><span data-stu-id="50042-112">In the **Property Expressions Editor** dialog box, in the **Property** column, type or select `ConnectionString`.</span></span>  
  
4.  <span data-ttu-id="50042-113">在 [**運算式**] 資料行中，按一下省略號按鈕\*\* ( ...] ) **開啟 [**運算式\*\*產生器] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="50042-113">In the **Expression** column, click the ellipsis button **(...)** to open the **Expression Builder** dialog box.</span></span>  
  
5.  <span data-ttu-id="50042-114">在 **[運算式產生器]** 對話方塊中，展開 **[變數]** 節點。</span><span class="sxs-lookup"><span data-stu-id="50042-114">In the **Expression Builder** dialog box, expand the **Variables** node.</span></span>  
  
6.  <span data-ttu-id="50042-115">將變數 [ **User：： varfilename 拖曳**] 拖曳到 [**運算式**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="50042-115">Drag the variable, **User::varFileName**, into the **Expression** box.</span></span>  
  
7.  <span data-ttu-id="50042-116">按一下 **[確定]** 來關閉 **[運算式產生器]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="50042-116">Click **OK** to close the **Expression Builder** dialog box.</span></span>  
  
8.  <span data-ttu-id="50042-117">再按一下 **[確定]** 來關閉 **[屬性運算式編輯器]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="50042-117">Click **OK** again to close the **Property Expressions Editor** dialog box.</span></span>  
  
## <a name="next-lesson-task"></a><span data-ttu-id="50042-118">下一課的工作</span><span class="sxs-lookup"><span data-stu-id="50042-118">Next Lesson Task</span></span>  
 [<span data-ttu-id="50042-119">步驟 4：測試第 2 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="50042-119">Step 4: Testing the Lesson 2 Tutorial Package</span></span>](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
  
