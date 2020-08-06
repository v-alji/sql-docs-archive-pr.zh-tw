---
title: SAP BW 來源編輯器 (資料行頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c2ec8bb7-be9b-4783-ad88-32512de784b0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ba605360d01abc520cedfbc457dd89319ed83c52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706610"
---
# <a name="sap-bw-source-editor-columns-page"></a><span data-ttu-id="374bf-102">SAP BW 來源編輯器 (資料行頁面)</span><span class="sxs-lookup"><span data-stu-id="374bf-102">SAP BW Source Editor (Columns Page)</span></span>
  <span data-ttu-id="374bf-103">使用 [SAP BW 來源編輯器] 的 [資料行] 頁面可以將輸出資料行對應至每個外部 (來源) 資料行。</span><span class="sxs-lookup"><span data-stu-id="374bf-103">Use the **Columns** page of the **SAP BW Source Editor** to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="374bf-104">若要深入了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 來源元件，請參閱 [SAP BW 來源](sap-bw-source.md)。</span><span class="sxs-lookup"><span data-stu-id="374bf-104">To learn more about the SAP BW source component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Source](sap-bw-source.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="374bf-105">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="374bf-105">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="374bf-106">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="374bf-106">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="374bf-107">擷取 SAP Netweaver BW 中的資料需要額外的 SAP 授權。</span><span class="sxs-lookup"><span data-stu-id="374bf-107">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="374bf-108">請洽詢 SAP 以確認這些需求。</span><span class="sxs-lookup"><span data-stu-id="374bf-108">Check with SAP to verify these requirements.</span></span>  
  
 <span data-ttu-id="374bf-109">**開啟資料行頁面**</span><span class="sxs-lookup"><span data-stu-id="374bf-109">**To open the Columns page**</span></span>  
  
1.  <span data-ttu-id="374bf-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 來源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="374bf-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW source.</span></span>  
  
2.  <span data-ttu-id="374bf-111">在 [資料流程]  索引標籤上，按兩下 SAP BW 來源。</span><span class="sxs-lookup"><span data-stu-id="374bf-111">On the **Data Flow** tab, double-click the SAP BW source.</span></span>  
  
3.  <span data-ttu-id="374bf-112">在 **[SAP BW 來源編輯器]** 中，按一下 **[資料行]** 開啟編輯器的 **[資料行]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="374bf-112">In the **SAP BW Source Editor**, click **Columns** to open the **Columns** page of the editor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="374bf-113">選項。</span><span class="sxs-lookup"><span data-stu-id="374bf-113">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="374bf-114">如果您不知道設定來源的所有必要值，可能必須詢問 SAP 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="374bf-114">If you do not know all the values that are required to configure the source, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="374bf-115">**可用的外部資料行**</span><span class="sxs-lookup"><span data-stu-id="374bf-115">**Available External Columns**</span></span>  
 <span data-ttu-id="374bf-116">檢視資料來源中可用的外部資料行清單，然後選取要包含在資料流程中的資料行。</span><span class="sxs-lookup"><span data-stu-id="374bf-116">View the list of available external columns in the data source, and then select the columns to be included in the data flow.</span></span>  
  
 <span data-ttu-id="374bf-117">若要在資料流程中包含資料行，請選取對應至該資料行的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="374bf-117">To include a column in the data flow, select the check box that corresponds to that column.</span></span> <span data-ttu-id="374bf-118">您選取核取方塊的順序會決定資料行的輸出順序。</span><span class="sxs-lookup"><span data-stu-id="374bf-118">The order in which you select the check boxes determines the order in which columns will be output.</span></span> <span data-ttu-id="374bf-119">也就是說，您所選取的第一個核取方塊就是第一個輸出資料行，第二個核取方塊就是第二個輸出資料行，依此類推。</span><span class="sxs-lookup"><span data-stu-id="374bf-119">That is, the first check box that you select will be the first output column, the second check box will be the second output columns, and so on.</span></span>  
  
 <span data-ttu-id="374bf-120">**[外部資料行]**</span><span class="sxs-lookup"><span data-stu-id="374bf-120">**External Column**</span></span>  
 <span data-ttu-id="374bf-121">檢視選取的外部 (來源) 資料行。</span><span class="sxs-lookup"><span data-stu-id="374bf-121">View the selected external (source) columns.</span></span> <span data-ttu-id="374bf-122">當您設定從這個來源取用資料的下游元件時，選取的資料行會按照其對應輸出資料行的顯示順序出現。</span><span class="sxs-lookup"><span data-stu-id="374bf-122">The selected columns appear in the order in which you will see their corresponding output columns when you configure downstream components that consume data from this source.</span></span>  
  
 <span data-ttu-id="374bf-123">若要變更資料行的順序，請在 **[可用的外部資料行]** 清單中，清除所有資料行的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="374bf-123">To change the order of the columns, in the **Available External Columns** list, clear the check boxes for all columns.</span></span> <span data-ttu-id="374bf-124">然後，按照您想要讓資料行出現的順序選取資料行。</span><span class="sxs-lookup"><span data-stu-id="374bf-124">Then, select the columns in the order that you want them to appear.</span></span>  
  
 <span data-ttu-id="374bf-125">**輸出資料行**</span><span class="sxs-lookup"><span data-stu-id="374bf-125">**Output Column**</span></span>  
 <span data-ttu-id="374bf-126">為每個輸出資料行提供唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="374bf-126">Provide a unique name for each output column.</span></span> <span data-ttu-id="374bf-127">預設值是選取之外部 (來源) 資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="374bf-127">The default is the name of the selected external (source) column.</span></span> <span data-ttu-id="374bf-128">不過，您可以輸入任何唯一的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="374bf-128">However, you can enter any unique, descriptive name.</span></span> [!INCLUDE[ssIS](../../includes/ssis-md.md)] <span data-ttu-id="374bf-129">設計師將會顯示這些資料行的 **輸出資料行** 名稱。</span><span class="sxs-lookup"><span data-stu-id="374bf-129">Designer will display the **Output Column** names for the columns when you configure downstream components that consume data from this source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="374bf-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="374bf-130">See Also</span></span>  
 <span data-ttu-id="374bf-131">[SAP BW 來源編輯器 &#40;連線管理員頁面&#41;](sap-bw-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="374bf-131">[SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="374bf-132">[SAP BW 來源編輯器 &#40;錯誤輸出頁面&#41;](sap-bw-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="374bf-132">[SAP BW Source Editor &#40;Error Output Page&#41;](sap-bw-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="374bf-133">[SAP BW 來源編輯器 &#40;進階頁面&#41;](sap-bw-source-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="374bf-133">[SAP BW Source Editor &#40;Advanced Page&#41;](sap-bw-source-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="374bf-134">Microsoft Connector 1.1 for SAP BW F1 說明</span><span class="sxs-lookup"><span data-stu-id="374bf-134">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
