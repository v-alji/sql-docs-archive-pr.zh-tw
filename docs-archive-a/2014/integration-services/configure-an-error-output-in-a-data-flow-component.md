---
title: 在資料流程元件中設定錯誤輸出 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- errors [Integration Services], data flow components
- components [Integration Services], data flow
- error outputs [Integration Services]
ms.assetid: 53d7eeea-927d-4b45-8ea9-084e65ad5390
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ebd44383e27daa465576bb056a67f6dacad87b0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708557"
---
# <a name="configure-an-error-output-in-a-data-flow-component"></a><span data-ttu-id="2292a-102">在資料流程元件中設定錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="2292a-102">Configure an Error Output in a Data Flow Component</span></span>
  <span data-ttu-id="2292a-103">許多資料流程元件都支援錯誤輸出，因元件的不同， [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師會以不同的方式設定錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="2292a-103">Many data flow components support error outputs, and depending on the component, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer provides different ways to configure an error output.</span></span> <span data-ttu-id="2292a-104">除了設定錯誤輸出以外，您也可以設定錯誤輸出的資料行。</span><span class="sxs-lookup"><span data-stu-id="2292a-104">In addition to configuring an error output, you can also configure the columns of an error output.</span></span> <span data-ttu-id="2292a-105">其中包括設定此元件所加入的 **ErrorCode** 和 **ErrorColumn** 資料行。</span><span class="sxs-lookup"><span data-stu-id="2292a-105">This includes configuring the **ErrorCode** and **ErrorColumn** columns that are added by the component.</span></span>  
  
## <a name="configuring-an-error-output"></a><span data-ttu-id="2292a-106">設定錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="2292a-106">Configuring an Error Output</span></span>  
 <span data-ttu-id="2292a-107">若要設定錯誤輸出，您有兩個選項：</span><span class="sxs-lookup"><span data-stu-id="2292a-107">To configure an error output, you have two options:</span></span>  
  
-   <span data-ttu-id="2292a-108">使用 [設定錯誤輸出]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2292a-108">Use the **Configure Error Output** dialog box.</span></span> <span data-ttu-id="2292a-109">您可以使用此對話方塊，在支援錯誤輸出的任何資料流程元件中設定錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="2292a-109">You can use this dialog box to configure an error output on any data flow component that supports an error output.</span></span>  
  
-   <span data-ttu-id="2292a-110">請針對此元件使用編輯器對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2292a-110">Use the editor dialog box for the component.</span></span> <span data-ttu-id="2292a-111">某些元件可讓您直接從它們的編輯器對話方塊設定錯誤輸出；</span><span class="sxs-lookup"><span data-stu-id="2292a-111">Some components let you configure error outputs directly from their editor dialog box.</span></span> <span data-ttu-id="2292a-112">但如果是 ADO NET 來源、匯入資料行轉換、OLE DB 命令轉換或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 目的地，您便無法從編輯器對話方塊設定錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="2292a-112">However, you cannot configure error outputs from the editor dialog box for the ADO NET source, the Import Column transformation, the OLE DB Command transformation, or the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact destination.</span></span>  
  
 <span data-ttu-id="2292a-113">下列程序描述如何使用這些對話方塊來設定錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="2292a-113">The following procedures describe how to use these dialog boxes to configure error outputs.</span></span>  
  
#### <a name="to-configure-an-error-output-using-the-configure-error-output-dialog-box"></a><span data-ttu-id="2292a-114">若要使用 [設定錯誤輸出] 對話方塊設定錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="2292a-114">To configure an error output using the Configure Error Output dialog box</span></span>  
  
1.  <span data-ttu-id="2292a-115">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="2292a-115">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="2292a-116">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="2292a-116">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="2292a-117">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師中，按一下 [資料流程]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2292a-117">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Data Flow** tab.</span></span>  
  
4.  <span data-ttu-id="2292a-118">將錯誤輸出 (以紅色箭頭表示) 從錯誤來源元件拖曳到資料流程中的另一個元件。</span><span class="sxs-lookup"><span data-stu-id="2292a-118">Drag the error output, represented by the red arrow, from the component that is the source of the errors to another component in the data flow.</span></span>  
  
5.  <span data-ttu-id="2292a-119">在 [設定錯誤輸出]  對話方塊中，針對元件輸入中的每個資料行，在 [錯誤]  和 [截斷]  資料行中選取動作。</span><span class="sxs-lookup"><span data-stu-id="2292a-119">In the **Configure Error Output** dialog box, select an action in the **Error** and **Truncation** columns for each column in the component input.</span></span>  
  
6.  <span data-ttu-id="2292a-120">若要儲存已更新的封裝，請按一下 [檔案]  功能表上的 [儲存選取項目]  。</span><span class="sxs-lookup"><span data-stu-id="2292a-120">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
#### <a name="to-add-an-error-output-using-the-editor-dialog-box-for-the-component"></a><span data-ttu-id="2292a-121">針對此元件使用編輯器對話方塊來加入錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="2292a-121">To add an error output using the editor dialog box for the component</span></span>  
  
1.  <span data-ttu-id="2292a-122">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="2292a-122">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="2292a-123">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="2292a-123">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="2292a-124">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師中，按一下 [資料流程]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2292a-124">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Data Flow** tab.</span></span>  
  
4.  <span data-ttu-id="2292a-125">按兩下要在其中設定錯誤輸出的資料流程元件，並依據此元件，執行下列其中一個步驟：</span><span class="sxs-lookup"><span data-stu-id="2292a-125">Double-click the data flow components in which you want to configure an error output and, depending on the component, do one of the following steps:</span></span>  
  
    -   <span data-ttu-id="2292a-126">按一下 [設定錯誤輸出]  。</span><span class="sxs-lookup"><span data-stu-id="2292a-126">Click **Configure Error Output**.</span></span>  
  
    -   <span data-ttu-id="2292a-127">按一下 [錯誤輸出]  。</span><span class="sxs-lookup"><span data-stu-id="2292a-127">Click **Error Output**.</span></span>  
  
5.  <span data-ttu-id="2292a-128">為每個資料行設定 [錯誤]  選項。</span><span class="sxs-lookup"><span data-stu-id="2292a-128">Set the **Error** option for each column.</span></span>  
  
6.  <span data-ttu-id="2292a-129">為每個資料行設定 [截斷]  選項。</span><span class="sxs-lookup"><span data-stu-id="2292a-129">Set the **Truncation** option for each column.</span></span>  
  
7.  <span data-ttu-id="2292a-130">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="2292a-130">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="2292a-131">若要儲存已更新的封裝，請按一下 [檔案]  功能表上的 [儲存選取項目]  。</span><span class="sxs-lookup"><span data-stu-id="2292a-131">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="configuring-error-output-columns"></a><span data-ttu-id="2292a-132">設定錯誤輸出資料行</span><span class="sxs-lookup"><span data-stu-id="2292a-132">Configuring Error Output Columns</span></span>  
 <span data-ttu-id="2292a-133">若要設定錯誤輸出資料行，您必須使用 [進階編輯器]  對話方塊的 [輸入與輸出屬性]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2292a-133">To configure the error output columns, you have to use the **Input and Output Properties** tab of the **Advanced Editor** dialog box.</span></span>  
  
#### <a name="to-configure-error-output-columns"></a><span data-ttu-id="2292a-134">設定錯誤輸出資料行</span><span class="sxs-lookup"><span data-stu-id="2292a-134">To configure error output columns</span></span>  
  
1.  <span data-ttu-id="2292a-135">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="2292a-135">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="2292a-136">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="2292a-136">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="2292a-137">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師中，按一下 [資料流程]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2292a-137">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Data Flow** tab.</span></span>  
  
4.  <span data-ttu-id="2292a-138">以滑鼠右鍵按一下要設定其錯誤輸出資料行的元件，並按一下 [顯示進階編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="2292a-138">Right-click the component whose error output columns you want to configure and click **Show Advanced Editor**.</span></span>  
  
5.  <span data-ttu-id="2292a-139">按一下 [輸入與輸出屬性] 索引標籤，並展開 [\<component name> 錯誤輸出]，然後展開 [輸出資料行]。</span><span class="sxs-lookup"><span data-stu-id="2292a-139">Click the **Input and Output Properties** tab and expand **\<component name> Error Output** and then expand **Output Columns**.</span></span>  
  
6.  <span data-ttu-id="2292a-140">按一下資料行並更新其屬性。</span><span class="sxs-lookup"><span data-stu-id="2292a-140">Click a column and update its properties.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2292a-141">資料行的清單包括元件輸入中的資料行、上一個錯誤輸出加入的 **ErrorCode** 和 **ErrorColumn** 資料行，以及此元件加入的 **ErrorCode** 和 **ErrorColumn** 資料行。</span><span class="sxs-lookup"><span data-stu-id="2292a-141">The list of columns includes the columns in the component input, the **ErrorCode** and **ErrorColumn** columns added by previous error outputs, and the **ErrorCode** and **ErrorColumn** columns added by this component.</span></span>  
  
7.  <span data-ttu-id="2292a-142">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="2292a-142">Click **OK.**</span></span>  
  
8.  <span data-ttu-id="2292a-143">若要儲存已更新的封裝，請按一下 [檔案]  功能表上的 [儲存選取項目]  。</span><span class="sxs-lookup"><span data-stu-id="2292a-143">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2292a-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2292a-144">See Also</span></span>  
 [<span data-ttu-id="2292a-145">資料中的錯誤處理</span><span class="sxs-lookup"><span data-stu-id="2292a-145">Error Handling in Data</span></span>](data-flow/error-handling-in-data.md)  
  
  
