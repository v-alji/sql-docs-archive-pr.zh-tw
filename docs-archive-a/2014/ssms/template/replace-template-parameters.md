---
title: 取代範本參數 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.templates.replaceparameters.f1
helpviewer_keywords:
- template parameters [Template Explorer]
- templates [Transact-SQL], replacing parameters
- Replace (Query) Template Parameters dialog box
- replacing template parameters
ms.assetid: 1234aa14-3464-4a3e-922a-5cfb8fb23627
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1d87b17a110efe118f7796487448e4d3bae30375
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597517"
---
# <a name="replace-template-parameters"></a><span data-ttu-id="1f63a-102">取代範本參數</span><span class="sxs-lookup"><span data-stu-id="1f63a-102">Replace Template Parameters</span></span>
  <span data-ttu-id="1f63a-103">範本包含每次使用範本時可由實作特定值替換的參數。</span><span class="sxs-lookup"><span data-stu-id="1f63a-103">Templates contain parameters that can be replaced by implementation-specific values each time the template is used.</span></span> <span data-ttu-id="1f63a-104">在程式碼編輯器中開啟範本之後，可以使用與您的實作相關的值替換這些參數。</span><span class="sxs-lookup"><span data-stu-id="1f63a-104">After opening a template in a code editor, you can replace the parameters with values relevant to your implementation.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="1f63a-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="1f63a-105">Before You Begin</span></span>  
 <span data-ttu-id="1f63a-106">[指定範本參數的值]  對話方塊是包含三個資料行的方格。</span><span class="sxs-lookup"><span data-stu-id="1f63a-106">The **Specify Values for Template Parameters** dialog is a grid with three columns.</span></span> <span data-ttu-id="1f63a-107">[參數]  和 [類型]  資料行是唯讀的，無法變更。</span><span class="sxs-lookup"><span data-stu-id="1f63a-107">The **Parameter** and **Type** columns are read-only and cannot be changed.</span></span> <span data-ttu-id="1f63a-108">檢閱 [值]  資料行的內容，並將任意預設值更改為適合您實作的值。</span><span class="sxs-lookup"><span data-stu-id="1f63a-108">Review the contents of the **Value** column, and change any of the defaults to values appropriate for your implementation.</span></span>  
  
 <span data-ttu-id="1f63a-109">若要使用此對話方塊，您的指令碼必須以角括弧 (`< >`) 括住參數，格式為 `<`  `,` *資料類型*`,`  `>`。</span><span class="sxs-lookup"><span data-stu-id="1f63a-109">To use this dialog box, you must have parameters in your script enclosed in angle brackets (`< >`) in the format `<`*parameter_name*`,` *data_type*`,` *default_value*`>`.</span></span>  
  
## <a name="replace-template-parameters"></a><span data-ttu-id="1f63a-110">取代範本參數</span><span class="sxs-lookup"><span data-stu-id="1f63a-110">Replace Template Parameters</span></span>  
 <span data-ttu-id="1f63a-111">在程式碼編輯器視窗中開啟範本之後：</span><span class="sxs-lookup"><span data-stu-id="1f63a-111">After opening the template in a code editor window:</span></span>  
  
1.  <span data-ttu-id="1f63a-112">在 **[查詢]** 功能表上，按一下 **[指定範本參數的值]** 。</span><span class="sxs-lookup"><span data-stu-id="1f63a-112">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span>  
  
2.  <span data-ttu-id="1f63a-113">在 [指定範本參數的值]  對話方塊中，[值]  資料行包含每一個參數的建議值。</span><span class="sxs-lookup"><span data-stu-id="1f63a-113">In the **Specify Values for Template Parameters** dialog box, the **Values** column contains a suggested value for each parameter.</span></span> <span data-ttu-id="1f63a-114">接受該值或以新的值替換。</span><span class="sxs-lookup"><span data-stu-id="1f63a-114">Accept the value or replace it with a new value.</span></span>  
  
3.  <span data-ttu-id="1f63a-115">按一下 [確定]  ，關閉 [取代範本參數]  對話方塊並在查詢編輯器中修改指令碼。</span><span class="sxs-lookup"><span data-stu-id="1f63a-115">Click **OK** to close the **Replace Template Parameters** dialog box and modify the script in the query editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f63a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f63a-116">See Also</span></span>  
 <span data-ttu-id="1f63a-117">[範本瀏覽器](template-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="1f63a-117">[Template Explorer](template-explorer.md) </span></span>  
 [<span data-ttu-id="1f63a-118">開啟範本</span><span class="sxs-lookup"><span data-stu-id="1f63a-118">Open a Template</span></span>](open-a-template.md)  
  
  
