---
title: 步驟 3：加入錯誤流程重新導向 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5683a45d-9e73-4cd5-83ca-fae8b26b488c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ceaea310cba05a940f310c01b52d5f912a53bea8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595178"
---
# <a name="step-3-adding-error-flow-redirection"></a><span data-ttu-id="3f3b3-102">步驟 3：新增錯誤流程重新導向</span><span class="sxs-lookup"><span data-stu-id="3f3b3-102">Step 3: Adding Error Flow Redirection</span></span>
  <span data-ttu-id="3f3b3-103">如上一項工作所示範的，當 [查閱貨幣索引鍵] 轉換試圖處理已損毀範例一般檔案 (其產生錯誤) 時，不會產生相符者。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-103">As demonstrated in the previous task, the Lookup Currency Key transformation cannot generate a match when the transformation tries to process the corrupted sample flat file, which produced an error.</span></span> <span data-ttu-id="3f3b3-104">因為轉換使用錯誤輸出的預設值，所以任何錯誤都會造成轉換失敗。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-104">Because the transformation uses the default settings for error output, any error causes the transformation to fail.</span></span> <span data-ttu-id="3f3b3-105">當轉換失敗時，封裝的其餘部分也會失敗。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-105">When the transformation fails, the rest of the package also fails.</span></span>  
  
 <span data-ttu-id="3f3b3-106">若不要讓轉換失敗，您可以設定元件利用錯誤輸出將失敗的資料列重新導向至另一個處理路徑。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-106">Instead of permitting the transformation to fail, you can configure the component to redirect the failed row to another processing path by using the error output.</span></span> <span data-ttu-id="3f3b3-107">使用個別錯誤處理路徑可讓您做一些事。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-107">Use of a separate error processing path lets you do a number of things.</span></span> <span data-ttu-id="3f3b3-108">例如，您可以試著清除資料，然後重新處理失敗的資料列。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-108">For instance, you might try to clean the data and then reprocess the failed row.</span></span> <span data-ttu-id="3f3b3-109">或者，您可以儲存失敗的資料列及其他錯誤資訊，供以後驗證及重新處理。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-109">Or, you might save the failed row along with additional error information for later verification and reprocessing.</span></span>  
  
 <span data-ttu-id="3f3b3-110">在這項工作中，您將設定查閱貨幣索引鍵轉換，將失敗的資料列重新導向至錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-110">In this task, you will configure the Lookup Currency Key transformation to redirect any rows that fail to the error output.</span></span> <span data-ttu-id="3f3b3-111">在資料流程的錯誤分支中，會將這些資料列寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-111">In the error branch of the data flow, these rows will be written to a file.</span></span>  
  
 <span data-ttu-id="3f3b3-112">根據預設，錯誤輸出中的兩個額外資料行 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ： **ErrorCode**和**ErrorColumn**，只包含代表錯誤號碼的數位代碼，以及發生錯誤的資料行識別碼。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-112">By default the two extra columns in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] error output, **ErrorCode** and **ErrorColumn**, contain only numeric codes that represent an error number, and the ID of the column in which the error occurred.</span></span> <span data-ttu-id="3f3b3-113">這些數值若無對應的錯誤描述，則用途有限。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-113">These numeric values may be of limited use without the corresponding error description.</span></span>  
  
 <span data-ttu-id="3f3b3-114">為了加強錯誤輸出的有用性，在此封裝將失敗資料列寫至檔案之前，您將使用指令碼元件來存取 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] API 及取得該錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-114">To enhance the usefulness of the error output, before the package writes the failed rows to the file, you will use a Script component to access the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] API and get a description of the error.</span></span>  
  
### <a name="to-configure-an-error-output"></a><span data-ttu-id="3f3b3-115">設定錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="3f3b3-115">To configure an error output</span></span>  
  
1.  <span data-ttu-id="3f3b3-116">在 [ **SSIS 工具箱**] 中，展開 [**一般**]，然後將 [**腳本元件**] 拖曳**至 [資料流程]** 索引標籤的設計介面上。將 [**腳本**] 放到 [**查閱貨幣索引鍵**] 轉換的右邊。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-116">In the **SSIS Toolbox**, expand **Common**, and then drag **Script Component** onto the design surface of the **Data Flow** tab. Place **Script** to the right of the **Lookup Currency Key** transformation.</span></span>  
  
2.  <span data-ttu-id="3f3b3-117">在 **[選取指令碼元件類型]** 對話方塊中，按一下 **[轉換]**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-117">In the **Select Script Component Type** dialog box, click **Transformation**, and click **OK**.</span></span>  
  
3.  <span data-ttu-id="3f3b3-118">按一下 **[查閱貨幣索引鍵]** 轉換，將紅色箭頭拖曳至新加入的 **[指令碼]** 轉換來連接兩個元件。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-118">Click the **Lookup Currency Key** transformation and then drag the red arrow onto the newly added **Script** transformation to connect the two components.</span></span>  
  
     <span data-ttu-id="3f3b3-119">紅色箭頭代表 **[查閱貨幣索引鍵]** 轉換的錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-119">The red arrow represents the error output of the **Lookup Currency Key** transformation.</span></span> <span data-ttu-id="3f3b3-120">藉由使用紅色箭頭將轉換連接到指令碼元件，您可以將任何處理錯誤重新導向至指令碼元件，然後由它處理這些錯誤並傳送到目的地。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-120">By using the red arrow to connect the transformation to the Script component, you can redirect any processing errors to the Script component, which then processes the errors and sends them to the destination.</span></span>  
  
4.  <span data-ttu-id="3f3b3-121">在 **[設定錯誤輸出]** 對話方塊的 **[錯誤]** 資料行中，選取 **[重新導向資料列]**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-121">In the **Configure Error Output** dialog box, in the **Error** column, select **Redirect row**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="3f3b3-122">在 [資料流程]\*\*\*\* 設計介面中，於新加入的 **ScriptComponent** 中按一下 [指令碼元件]\*\*\*\*，將名稱變更為**取得錯誤描述**。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-122">On the **Data Flow** design surface, click **Script Component** in the newly added **ScriptComponent**, and change the name to **Get Error Description**.</span></span>  
  
6.  <span data-ttu-id="3f3b3-123">按兩下 [取得錯誤描述]\*\*\*\* 轉換。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-123">Double-click the **Get Error Description** transformation.</span></span>  
  
7.  <span data-ttu-id="3f3b3-124">在 **[指令碼轉換編輯器]** 對話方塊的 **[輸入資料行]** 頁面上，選取 **[ErrorCode]** 資料行。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-124">In the **Script Transformation Editor** dialog box, on the **Input Columns** page, select the **ErrorCode** column.</span></span>  
  
8.  <span data-ttu-id="3f3b3-125">在 **[輸入和輸出]** 頁面，展開 **[Output 0]**，按一下 **[輸出資料行]**，然後按一下 **[加入資料行]**。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-125">On the **Inputs and Outputs** page, expand **Output 0**, click **Output Columns**, and then click **Add Column**.</span></span>  
  
9. <span data-ttu-id="3f3b3-126">在 `Name` 屬性中，輸入**ErrorDescription** ，並將 `DataType` 屬性設定為 **[Unicode 字串 [DT_WSTR]]**。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-126">In the `Name` property, type **ErrorDescription** and set the `DataType` property to **Unicode string [DT_WSTR]**.</span></span>  
  
10. <span data-ttu-id="3f3b3-127">在 [**腳本**] 頁面上，確認 `LocaleID` 屬性已設為 [**英文] ([美國]。**</span><span class="sxs-lookup"><span data-stu-id="3f3b3-127">On the **Script** page, verify that the `LocaleID` property is set to **English (United States.**</span></span>  
  
11. <span data-ttu-id="3f3b3-128">按一下 [編輯指令碼]\*\*\*\* 以開啟 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA)。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-128">Click **Edit Script** to open [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span> <span data-ttu-id="3f3b3-129">在 `Input0_ProcessInputRow` 方法中，輸入或剖析下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-129">In the `Input0_ProcessInputRow` method, type or paste the following code.</span></span>  
  
     <span data-ttu-id="3f3b3-130">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="3f3b3-130">[Visual Basic]</span></span>  
  
    ```  
    Row.ErrorDescription =   
      Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
    ```  
  
     <span data-ttu-id="3f3b3-131">[Visual C#]</span><span class="sxs-lookup"><span data-stu-id="3f3b3-131">[Visual C#]</span></span>  
  
    ```  
    Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
    ```  
  
     <span data-ttu-id="3f3b3-132">完成的副程式類似下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-132">The completed subroutine will look like the following code.</span></span>  
  
     <span data-ttu-id="3f3b3-133">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="3f3b3-133">[Visual Basic]</span></span>  
  
    ```  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
      Row.ErrorDescription =   
        Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
    End Sub  
    ```  
  
     <span data-ttu-id="3f3b3-134">[Visual C#]</span><span class="sxs-lookup"><span data-stu-id="3f3b3-134">[Visual C#]</span></span>  
  
    ```  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
        {  
  
            Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
  
        }  
    ```  
  
12. <span data-ttu-id="3f3b3-135">在 **[建置]** 功能表上，按一下 **[建置方案]** 建置指令碼並儲存您的變更，然後關閉 VSTA。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-135">On the **Build** menu, click **Build Solution** to build the script and save your changes, and then close VSTA.</span></span>  
  
13. <span data-ttu-id="3f3b3-136">按一下 **[確定]** 來關閉 **[指令碼轉換編輯器]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3f3b3-136">Click **OK** to close the **Script Transformation Editor** dialog box.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3f3b3-137">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3f3b3-137">Next Steps</span></span>  
 <span data-ttu-id="3f3b3-138">[步驟4：新增一般檔案目的地] (lesson-4-4-adding-a-flat-file-destination.md</span><span class="sxs-lookup"><span data-stu-id="3f3b3-138">[Step 4: Adding a Flat File Destination](lesson-4-4-adding-a-flat-file-destination.md</span></span>  
  
  
