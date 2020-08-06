---
title: 步驟 4：新增一般檔案目的地 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f4088de3-16d8-419c-96a1-a2cd005d0a5b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eff65f4a94a412d55af8055e302195f87ae4cdb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704302"
---
# <a name="step-4-adding-a-flat-file-destination"></a><span data-ttu-id="71c3c-102">步驟 4：新增一般檔案目的地</span><span class="sxs-lookup"><span data-stu-id="71c3c-102">Step 4: Adding a Flat File Destination</span></span>
  <span data-ttu-id="71c3c-103">[查閱貨幣索引鍵] 轉換的錯誤輸出，將使得查閱作業失敗的任何資料列重新導向至 [指令碼] 轉換。</span><span class="sxs-lookup"><span data-stu-id="71c3c-103">The error output of the Lookup Currency Key transformation redirects to the Script transformation any data rows that failed the lookup operation.</span></span> <span data-ttu-id="71c3c-104">為了加強所發生錯誤的相關資訊，[指令碼] 轉換執行一個取得錯誤描述的指令碼。</span><span class="sxs-lookup"><span data-stu-id="71c3c-104">To enhance information about the errors that occurred, the Script transformation runs a script that gets the description of errors.</span></span>  
  
 <span data-ttu-id="71c3c-105">在這項工作中，您將失敗資料列的所有資訊儲存至分隔檔案中供以後處理。</span><span class="sxs-lookup"><span data-stu-id="71c3c-105">In this task, you will save all this information about the failed rows to a delimited file for later processing.</span></span> <span data-ttu-id="71c3c-106">若要儲存失敗的資料列，您必須為包含該錯誤資料的文字檔加入及設定一般檔案連接管理員和一般檔案目的地。</span><span class="sxs-lookup"><span data-stu-id="71c3c-106">To save the failed rows, you must add and configure a Flat File connection manager for the text file that will contain the error data and a Flat File destination.</span></span> <span data-ttu-id="71c3c-107">透過設定「一般檔案」目的地使用之「一般檔案」連接管理員上的屬性，您可以指定「一般檔案」目的地如何格式化並寫入文字檔。</span><span class="sxs-lookup"><span data-stu-id="71c3c-107">By setting properties on the Flat File connection manager that the Flat File destination uses, you can specify how the Flat File destination formats and writes the text file.</span></span> <span data-ttu-id="71c3c-108">如需詳細資訊，請參閱一般檔案[連線管理員](connection-manager/file-connection-manager.md)和一般檔案[目的地](data-flow/flat-file-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="71c3c-108">For more information, see [Flat File Connection Manager](connection-manager/file-connection-manager.md) and [Flat File Destination](data-flow/flat-file-destination.md).</span></span>  
  
### <a name="to-add-and-configure-a-flat-file-destination"></a><span data-ttu-id="71c3c-109">加入和設定一般檔案目的地</span><span class="sxs-lookup"><span data-stu-id="71c3c-109">To add and configure a Flat File destination</span></span>  
  
1.  <span data-ttu-id="71c3c-110">按一下 **[資料流程]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="71c3c-110">Click the **Data Flow** tab.</span></span>  
  
2.  <span data-ttu-id="71c3c-111">在 **[SSIS 工具箱]** 中，展開 **[其他]**，然後將 **[一般檔案目的地]** 拖曳至 [資料流程] 設計介面中。</span><span class="sxs-lookup"><span data-stu-id="71c3c-111">In the **SSIS Toolbox**, expand **Other**, and drag **Flat File Destination** onto the data flow design surface.</span></span> <span data-ttu-id="71c3c-112">將 **[一般檔案目的地]** 直接放在 **[取得錯誤描述]** 轉換之下。</span><span class="sxs-lookup"><span data-stu-id="71c3c-112">Put the **Flat File Destination** directly underneath the **Get Error Description** transformation.</span></span>  
  
3.  <span data-ttu-id="71c3c-113">按一下 [ **取得錯誤描述** ] 轉換，然後將綠色箭頭拖曳至新的 [ **一般檔案目的地**]。</span><span class="sxs-lookup"><span data-stu-id="71c3c-113">Click the **Get Error Description** transformation, and then drag the green arrow onto the new **Flat File Destination**.</span></span>  
  
4.  <span data-ttu-id="71c3c-114">在 **[資料流程]** 設計介面中，於新加入的 **[一般檔案目的地]** 轉換中按一下 **[一般檔案目的地]** ，並將名稱變更為 **「失敗的資料列」**。</span><span class="sxs-lookup"><span data-stu-id="71c3c-114">On the **Data Flow** design surface, click **Flat File Destination** in the newly added **Flat File Destination** transformation, and change the name to **Failed Rows**.</span></span>  
  
5.  <span data-ttu-id="71c3c-115">以滑鼠右鍵按一下 **[失敗的資料列]** 轉換，然後按一下 **[編輯]**，再按一下 **[一般檔案目的地編輯器]** 中的 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="71c3c-115">Right-click the **Failed Rows** transformation, click **Edit**, and then in the **Flat File Destination Editor**, click **New**.</span></span>  
  
6.  <span data-ttu-id="71c3c-116">在 **[一般檔案格式]** 對話方塊中，確認已選取 **[使用分隔符號]** ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="71c3c-116">In the **Flat File Format** dialog box, verify that **Delimited** is selected, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="71c3c-117">在 [一般檔案**連線管理員編輯器**] 的 [**連接管理員名稱**] 方塊中，輸入 `Error Data` 。</span><span class="sxs-lookup"><span data-stu-id="71c3c-117">In the **Flat File Connection Manager Editor**, in the **Connection Manager Name** box type `Error Data`.</span></span>  
  
8.  <span data-ttu-id="71c3c-118">在 **[一般檔案連接管理員編輯器]** 對話方塊中，按一下 **[瀏覽]**，並尋找儲存該檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="71c3c-118">In the **Flat File Connection Manager Editor** dialog box, click **Browse**, and locate the folder in which to store the file.</span></span>  
  
9. <span data-ttu-id="71c3c-119">在 [**開啟**] 對話方塊中，針對 [**檔案名**] 輸入 `ErrorOutput.txt` ，然後按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="71c3c-119">In the **Open** dialog box, for **File name**, type `ErrorOutput.txt`, and then click **Open**.</span></span>  
  
10. <span data-ttu-id="71c3c-120">在 **[一般檔案連接管理員編輯器]** 對話方塊中，確認 **[地區設定]** 方塊包含 [英文 (美國)]， **[字碼頁]** 包含 1252 [ANSI - 拉丁文 1]。</span><span class="sxs-lookup"><span data-stu-id="71c3c-120">In the **Flat File Connection Manager Editor** dialog box, verify that the **Locale** box contains English (United States) and **Code page** contains 1252 (ANSI -Latin I).</span></span>  
  
11. <span data-ttu-id="71c3c-121">在 [選項] 窗格中，按一下 **[資料行]**。</span><span class="sxs-lookup"><span data-stu-id="71c3c-121">In the options pane, click **Columns**.</span></span>  
  
     <span data-ttu-id="71c3c-122">請注意，除了來源資料檔的資料行之外，還出現三個新的資料行：ErrorCode、ErrorColumn 和 ErrorDescription。</span><span class="sxs-lookup"><span data-stu-id="71c3c-122">Notice that, in addition to the columns from the source data file, three new columns are present: ErrorCode, ErrorColumn, and ErrorDescription.</span></span> <span data-ttu-id="71c3c-123">這些資料行是由 [查閱貨幣索引鍵] 轉換的錯誤輸出和 [取得錯誤描述] 轉換中的指令碼產生，而且可用來找出失敗資料列的原因並加以解決。</span><span class="sxs-lookup"><span data-stu-id="71c3c-123">These columns are generated by the error output of the Lookup Currency Key transformation and by the script in the Get Error Description transformation, and can be used to troubleshoot the cause of the failed row.</span></span>  
  
12. <span data-ttu-id="71c3c-124">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="71c3c-124">Click **OK**.</span></span>  
  
13. <span data-ttu-id="71c3c-125">在 **[一般檔案目的地編輯器]** 中，清除 **[覆寫檔案中的資料]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="71c3c-125">In the **Flat File Destination Editor**, clear the **Overwrite data in the file** check box.</span></span>  
  
     <span data-ttu-id="71c3c-126">清除這個核取方塊可保存多次封裝執行的錯誤。</span><span class="sxs-lookup"><span data-stu-id="71c3c-126">Clearing this check box persists the errors over multiple package executions.</span></span>  
  
14. <span data-ttu-id="71c3c-127">在 **[一般檔案目的地編輯器]** 中，按一下 **[對應]** 來確認所有資料行都正確。</span><span class="sxs-lookup"><span data-stu-id="71c3c-127">In the **Flat File Destination Editor**, click **Mappings** to verify that all the columns are correct.</span></span> <span data-ttu-id="71c3c-128">您可以選擇性地重新命名目的地的資料行。</span><span class="sxs-lookup"><span data-stu-id="71c3c-128">Optionally, you can rename the columns in the destination.</span></span>  
  
15. <span data-ttu-id="71c3c-129">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="71c3c-129">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="71c3c-130">後續步驟</span><span class="sxs-lookup"><span data-stu-id="71c3c-130">Next Steps</span></span>  
 [<span data-ttu-id="71c3c-131">步驟 5：測試第 4 課的教學課程封裝</span><span class="sxs-lookup"><span data-stu-id="71c3c-131">Step 5: Testing the Lesson 4 Tutorial Package</span></span>](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
  
