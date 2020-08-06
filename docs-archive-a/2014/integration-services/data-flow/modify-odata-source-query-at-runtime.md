---
title: 在執行時間修改 OData 來源查詢 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: bcbba7f4-6e5d-46e6-a73a-3f17d3ff376a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b3dbc4d27f2d11537a9d66980ef6ca59b80811b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708505"
---
# <a name="modify-odata-source-query-at-runtime"></a><span data-ttu-id="6b0a7-102">在執行階段修改 OData 來源查詢</span><span class="sxs-lookup"><span data-stu-id="6b0a7-102">Modify OData Source Query at Runtime</span></span>
  <span data-ttu-id="6b0a7-103">您可以在執行階段修改 OData 來源查詢，修改的方式是將「運算式」  加入資料流程工作的 [OData Source].[Query] 屬性。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-103">You can modify the OData Source query at runtime by adding an expression to the **[OData Source].[Query]** property of the Data Flow task.</span></span>  
  
 <span data-ttu-id="6b0a7-104">請注意，資料行必須維持與設計階段所使用的內容相同，否則您在執行封裝時將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-104">Note that the columns must remain the same as what was used at design time; otherwise you will get an error when the package is executed.</span></span> <span data-ttu-id="6b0a7-105">在使用 $select 查詢選項時，請務必指定相同的資料行 (以相同順序)。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-105">Be sure to specify the same columns (in the same order) when using the $select query option.</span></span> <span data-ttu-id="6b0a7-106">使用 $select 選項有一個更安全的替代方法，也就是直接從來源元件 UI 取消選取您不想要的資料行。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-106">A safer alternative to using the $select option is to deselect the columns you don't want directly from the Source Component UI.</span></span>  
  
 <span data-ttu-id="6b0a7-107">有幾個不同的方式可以在執行階段動態設定查詢值。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-107">There are a few different ways of dynamically setting the query value at runtime.</span></span> <span data-ttu-id="6b0a7-108">底下是一些較為常見的方法。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-108">Below are some of the more common methods.</span></span>  
  
## <a name="exposing-the-query-as-a-parameter"></a><span data-ttu-id="6b0a7-109">將查詢公開為參數</span><span class="sxs-lookup"><span data-stu-id="6b0a7-109">Exposing the Query as a Parameter</span></span>  
 <span data-ttu-id="6b0a7-110">下列程序的步驟會將 OData 來源元件所使用的查詢公開為封裝的參數。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-110">The following procedure has steps to expose query used by an OData Source component as a parameter to the package.</span></span>  
  
1.  <span data-ttu-id="6b0a7-111">以滑鼠右鍵按一下 [資料流程工作]  ，然後選取 [參數化...]  選項。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-111">Right click on the **Data Flow task** and select the **Parameterize...** option.</span></span>  
  
2.  <span data-ttu-id="6b0a7-112">在 [參數化] 對話方塊中，針對 [屬性] 選取 [\<Name of the OData Source Component>].[Query]。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-112">In the **Parameterize** dialog, select **[\<Name of the OData Source Component>].[Query]** for **Property**.</span></span>  
  
3.  <span data-ttu-id="6b0a7-113">選擇是要 [建立新的參數]  還是 [使用現有的參數]  。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-113">Choose whether to **create new parameter** or **use an existing parameter**.</span></span>  
  
4.  <span data-ttu-id="6b0a7-114">如果您選取 [建立新的參數]\*\*\*\*，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6b0a7-114">If you select **Create new parameter**, do the following:</span></span>  
  
    1.  <span data-ttu-id="6b0a7-115">輸入參數的 [名稱]  和 [描述]  。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-115">Enter **name** and **description** for the parameter.</span></span>  
  
    2.  <span data-ttu-id="6b0a7-116">指定參數的預設 [值]  。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-116">Specify default **value** for the parameter.</span></span>  
  
    3.  <span data-ttu-id="6b0a7-117">為參數指定 [範圍]  ([封裝]  或 [專案]  )。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-117">Specify the **scope** (**package** or **project**) for the parameter.</span></span>  
  
    4.  <span data-ttu-id="6b0a7-118">指定參數是否為 [必要]</span><span class="sxs-lookup"><span data-stu-id="6b0a7-118">Specify whether the parameter is **required** or not</span></span>  
  
5.  <span data-ttu-id="6b0a7-119">按一下 **[確定]** ，關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-119">Click **OK** to close the dialog box.</span></span>  
  
## <a name="using-an-expression"></a><span data-ttu-id="6b0a7-120">使用運算式</span><span class="sxs-lookup"><span data-stu-id="6b0a7-120">Using an Expression</span></span>  
 <span data-ttu-id="6b0a7-121">當您想要在執行階段以動態方式建構查詢字串時，此方法相當實用。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-121">This method is useful when you want to dynamically construct query string at runtime.</span></span> <span data-ttu-id="6b0a7-122">在此範例中，MaxRows 變數將會透過其他方式 (指令碼、參數等等) 設定。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-122">In this example, MaxRows variable will be set through other means (script, parameter, etc).</span></span>  
  
1.  <span data-ttu-id="6b0a7-123">選取包含您的 [OData 來源]\*\*\*\* 的 [資料流程工作]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-123">Select the **Data Flow Task** which contains your **OData Source**.</span></span>  
  
2.  <span data-ttu-id="6b0a7-124">在 [屬性]  視窗中，反白顯示 [運算式]  屬性。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-124">In the **Properties** window, highlight the **Expressions** property.</span></span>  
  
3.  <span data-ttu-id="6b0a7-125">按一下 [...] (省略號) ] 按鈕，以顯示 [**屬性運算式編輯器**]。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-125">Click the ... (ellipses) button to bring up the **Property Expressions Editor**.</span></span>  
  
4.  <span data-ttu-id="6b0a7-126">選取 **[OData Source].[Query]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-126">Select the **[OData Source].[Query]** property.</span></span>  
  
5.  <span data-ttu-id="6b0a7-127">按一下 [**運算式**] (省略號) ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-127">Click the ... (ellipses) button for **Expression**.</span></span>  
  
6.  <span data-ttu-id="6b0a7-128">輸入 [運算式]  。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-128">Enter the **expression**.</span></span>  
  
7.  <span data-ttu-id="6b0a7-129">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-129">Click **OK**.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="6b0a7-130">請注意，當您使用這種方法時，您必須確定設定的值具有正確的 URL 編碼。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-130">Note that when using this approach you need to ensure that the values set are properly URL encoded.</span></span> <span data-ttu-id="6b0a7-131">當從使用者輸入接受值時 (例如，從參數設定個別查詢選項值)，您必須確定這些值已經過驗證，以免可能發生 SQL 資料隱碼類型的攻擊。</span><span class="sxs-lookup"><span data-stu-id="6b0a7-131">When receiving values from user input (for example, setting individual query option values from a parameter), you must ensure that the values are validated to avoid potential SQL injection-type attacks.</span></span>  
  
  
