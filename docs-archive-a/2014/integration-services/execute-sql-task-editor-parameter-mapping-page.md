---
title: '[執行 SQL 工作編輯器] ([參數對應] 頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.parametermapping.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: 8ebe020a-7921-46b2-8823-398748f379b2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cfbb4468cb69947dfa54fb519b7698286393d578
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594125"
---
# <a name="execute-sql-task-editor-parameter-mapping-page"></a><span data-ttu-id="fe9f5-102">執行 SQL 工作編輯器 (參數對應頁面)</span><span class="sxs-lookup"><span data-stu-id="fe9f5-102">Execute SQL Task Editor (Parameter Mapping Page)</span></span>
  <span data-ttu-id="fe9f5-103">使用 [執行 SQL 工作編輯器]  對話方塊的 [參數對應]  頁面，即可將變數對應到 SQL 陳述式中的參數。</span><span class="sxs-lookup"><span data-stu-id="fe9f5-103">Use the **Parameter Mapping** page of the **Execute SQL Task Editor** dialog box to map variables to parameters in the SQL statement.</span></span>  
  
 <span data-ttu-id="fe9f5-104">若要了解這項工作，請參閱[執行 SQL 工作](control-flow/execute-sql-task.md)和[執行 SQL 工作中的參數和傳回碼](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="fe9f5-104">To learn about this task, see [Execute SQL Task](control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="fe9f5-105">選項。</span><span class="sxs-lookup"><span data-stu-id="fe9f5-105">Options</span></span>  
 <span data-ttu-id="fe9f5-106">**變數名稱**</span><span class="sxs-lookup"><span data-stu-id="fe9f5-106">**Variable Name**</span></span>  
 <span data-ttu-id="fe9f5-107">按一下 [新增] 新增參數對應之後，請從清單中選取系統或使用者定義變數，或按一下 \<**New variable...**> 以使用 [新增變數] 對話方塊新增新的變數。</span><span class="sxs-lookup"><span data-stu-id="fe9f5-107">After you have added a parameter mapping by clicking **Add**, select a system or user-defined variable from the list or click \<**New variable...**> to add a new variable by using the **Add Variable** dialog box.</span></span>  
  
 <span data-ttu-id="fe9f5-108">**相關主題：** [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)</span><span class="sxs-lookup"><span data-stu-id="fe9f5-108">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md)</span></span>  
  
 <span data-ttu-id="fe9f5-109">**方向**</span><span class="sxs-lookup"><span data-stu-id="fe9f5-109">**Direction**</span></span>  
 <span data-ttu-id="fe9f5-110">選取參數的方向。</span><span class="sxs-lookup"><span data-stu-id="fe9f5-110">Select the direction of the parameter.</span></span> <span data-ttu-id="fe9f5-111">將每個變數對應到輸入參數、輸出參數或傳回碼。</span><span class="sxs-lookup"><span data-stu-id="fe9f5-111">Map each variable to an input parameter, output parameter, or a return code.</span></span>  
  
 <span data-ttu-id="fe9f5-112">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="fe9f5-112">**Data Type**</span></span>  
 <span data-ttu-id="fe9f5-113">選取參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="fe9f5-113">Select the data type of the parameter.</span></span> <span data-ttu-id="fe9f5-114">在工作所使用之連接管理員中選取的提供者，各有其專用的可用資料類型清單。</span><span class="sxs-lookup"><span data-stu-id="fe9f5-114">The list of available data types is specific to the provider selected in the connection manager used by the task.</span></span>  
  
 <span data-ttu-id="fe9f5-115">**參數名稱**</span><span class="sxs-lookup"><span data-stu-id="fe9f5-115">**Parameter Name**</span></span>  
 <span data-ttu-id="fe9f5-116">提供參數名稱。</span><span class="sxs-lookup"><span data-stu-id="fe9f5-116">Provide a parameter name.</span></span>  
  
 <span data-ttu-id="fe9f5-117">您必須根據工作所使用的連接管理員類型，來使用數字或參數名稱。</span><span class="sxs-lookup"><span data-stu-id="fe9f5-117">Depending on the connection manager type that the task uses, you must use numbers or parameter names.</span></span> <span data-ttu-id="fe9f5-118">某些連線管理員類型要求參數名稱的第一個字元是 \@ 符號、特定名稱 (如 \@Param1) 或資料行名稱作為參數名稱。</span><span class="sxs-lookup"><span data-stu-id="fe9f5-118">Some connection manager types require that the first character of the parameter name is the \@ sign , specific names like \@Param1, or column names as parameter names.</span></span>  
  
 <span data-ttu-id="fe9f5-119">**相關主題：** [在執行 SQL 工作中設定參數和傳回碼](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)</span><span class="sxs-lookup"><span data-stu-id="fe9f5-119">**Related Topics:** [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)</span></span>  
  
 <span data-ttu-id="fe9f5-120">**參數大小**</span><span class="sxs-lookup"><span data-stu-id="fe9f5-120">**Parameter Size**</span></span>  
 <span data-ttu-id="fe9f5-121">提供具有可變長度之參數的大小，例如字串和二進位欄位。</span><span class="sxs-lookup"><span data-stu-id="fe9f5-121">Provide the size of parameters that have variable length, such as strings and binary fields.</span></span>  
  
 <span data-ttu-id="fe9f5-122">此設計可確保提供者能為可變長度的參數值配置足夠的空間。</span><span class="sxs-lookup"><span data-stu-id="fe9f5-122">This setting ensures that the provider allocates sufficient space for variable-length parameter values.</span></span>  
  
 <span data-ttu-id="fe9f5-123">**加入**</span><span class="sxs-lookup"><span data-stu-id="fe9f5-123">**Add**</span></span>  
 <span data-ttu-id="fe9f5-124">按一下即可加入參數對應。</span><span class="sxs-lookup"><span data-stu-id="fe9f5-124">Click to add a parameter mapping.</span></span>  
  
 <span data-ttu-id="fe9f5-125">**移除**</span><span class="sxs-lookup"><span data-stu-id="fe9f5-125">**Remove**</span></span>  
 <span data-ttu-id="fe9f5-126">在清單中選取參數對應，然後按一下 [移除]  。</span><span class="sxs-lookup"><span data-stu-id="fe9f5-126">Select a parameter mapping in the list and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe9f5-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe9f5-127">See Also</span></span>  
 <span data-ttu-id="fe9f5-128">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fe9f5-128">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="fe9f5-129">[&#40;一般頁面&#41;執行 SQL 工作編輯器](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="fe9f5-129">[Execute SQL Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="fe9f5-130">[[執行 SQL 工作編輯器] &#40;[結果集] 頁面&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md) </span><span class="sxs-lookup"><span data-stu-id="fe9f5-130">[Execute SQL Task Editor &#40;Result Set Page&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md) </span></span>  
 [<span data-ttu-id="fe9f5-131">Transact-SQL 參考 &#40;資料庫引擎41;</span><span class="sxs-lookup"><span data-stu-id="fe9f5-131">Transact-SQL Reference &#40;Database Engine&#41;</span></span>](/sql/t-sql/language-reference)  
  
  
