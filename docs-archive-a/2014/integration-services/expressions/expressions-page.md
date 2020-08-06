---
title: 運算式頁面 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.expressionspage.f1
helpviewer_keywords:
- Expressions Page dialog box
ms.assetid: c9016ec6-11c1-4ebd-b2a7-0fa6631fd9e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ba4e73ea495456e8f9e452108ab09106a65543ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595217"
---
# <a name="expressions-page"></a><span data-ttu-id="409e4-102">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="409e4-102">Expressions Page</span></span>
  <span data-ttu-id="409e4-103">使用 [運算式]  頁面，即可編輯屬性運算式，並存取 [屬性運算式編輯器]  和 [屬性運算式產生器]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="409e4-103">Use the **Expressions** page to edit property expressions and to access the **Property Expressions Editor** and **Property Expression Builder** dialog boxes.</span></span>  
  
 <span data-ttu-id="409e4-104">屬性運算式會在執行封裝時更新屬性值。</span><span class="sxs-lookup"><span data-stu-id="409e4-104">Property expressions update the values of properties when the package is run.</span></span> <span data-ttu-id="409e4-105">屬性運算式可與封裝、工作、容器、連接管理員以及一些資料流程元件的屬性一起使用。</span><span class="sxs-lookup"><span data-stu-id="409e4-105">Property expressions can be used with the properties of packages, tasks, containers, connection managers, as well as some data flow components.</span></span> <span data-ttu-id="409e4-106">會評估這些運算式並使用其結果，但不會使用您在設定封裝和封裝物件時所設定的屬性值。</span><span class="sxs-lookup"><span data-stu-id="409e4-106">The expressions are evaluated and their results are used instead of the values to which you set the properties when you configured the package and package objects.</span></span> <span data-ttu-id="409e4-107">運算式可以包含變數以及運算式語言提供的函數與運算子。</span><span class="sxs-lookup"><span data-stu-id="409e4-107">The expressions can include variables and the functions and operators that the expression language provides.</span></span> <span data-ttu-id="409e4-108">例如，您可以將包含字串 "Weather forecast for " 的變數值與 GETDATE() 函數的傳回結果，串連成字串 "Weather forecast for 4/5/2006"，以產生「傳送郵件」工作的主旨列。</span><span class="sxs-lookup"><span data-stu-id="409e4-108">For example, you can generate the subject line for the Send Mail task by concatenating the value of a variable that contains the string "Weather forecast for " and the return results of the GETDATE() function to make the string "Weather forecast for 4/5/2006".</span></span>  
  
 <span data-ttu-id="409e4-109">若要深入了解撰寫運算式以及使用屬性運算式，請參閱 [Integration Services &#40;SSIS&#41; 運算式](integration-services-ssis-expressions.md) 和 [在封裝中使用屬性運算式](use-property-expressions-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="409e4-109">To learn more about writing expressions and using property expressions, see [Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md) and [Use Property Expressions in Packages](use-property-expressions-in-packages.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="409e4-110">選項。</span><span class="sxs-lookup"><span data-stu-id="409e4-110">Options</span></span>  
 <span data-ttu-id="409e4-111">**運算式 (...)**</span><span class="sxs-lookup"><span data-stu-id="409e4-111">**Expressions (...)**</span></span>  
 <span data-ttu-id="409e4-112">按一下省略符號，即可開啟 **屬性運算式編輯器** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="409e4-112">Click the ellipsis to open the **Property Expressions Editor** dialog box.</span></span> <span data-ttu-id="409e4-113">如需詳細資訊，請參閱 [屬性運算式編輯器](property-expressions-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="409e4-113">For more information, see [Property Expressions Editor](property-expressions-editor.md).</span></span>  
  
 **\<property name>**  
 <span data-ttu-id="409e4-114">按一下省略符號，即可開啟 **[運算式產生器]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="409e4-114">Click the ellipsis to open the **Expression Builder** dialog box.</span></span> <span data-ttu-id="409e4-115">如需詳細資訊，請參閱 [Expression Builder](expression-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="409e4-115">For more information, see [Expression Builder](expression-builder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="409e4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="409e4-116">See Also</span></span>  
 <span data-ttu-id="409e4-117">[Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="409e4-117">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="409e4-118">[系統變數](../system-variables.md) </span><span class="sxs-lookup"><span data-stu-id="409e4-118">[System Variables](../system-variables.md) </span></span>  
 [<span data-ttu-id="409e4-119">Integration Services &#40;SSIS&#41; 運算式</span><span class="sxs-lookup"><span data-stu-id="409e4-119">Integration Services &#40;SSIS&#41; Expressions</span></span>](integration-services-ssis-expressions.md)  
  
  
