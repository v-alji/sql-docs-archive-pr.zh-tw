---
title: 設定「For 迴圈」容器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], For Loop
- For Loop containers
ms.assetid: b9cd7ea7-b198-4a35-8b16-6acf09611ca5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9cb33ea5b7f3f59baad3c94f6bc845c281613ec9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592171"
---
# <a name="configure-a-for-loop-container"></a><span data-ttu-id="c1d2a-102">設定 For 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="c1d2a-102">Configure a For Loop Container</span></span>
  <span data-ttu-id="c1d2a-103">此程序描述如何使用 [For 迴圈編輯器]  對話方塊設定「For 迴圈」容器。</span><span class="sxs-lookup"><span data-stu-id="c1d2a-103">This procedure describes how to configure a For Loop container by using the **For Loop Editor** dialog box.</span></span>  
  
### <a name="to-configure-the-for-loop-container"></a><span data-ttu-id="c1d2a-104">設定 For 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="c1d2a-104">To configure the For Loop container</span></span>  
  
1.  <span data-ttu-id="c1d2a-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，按兩下「For 迴圈」容器以開啟 [For 迴圈編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="c1d2a-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], double-click the For Loop container to open the **For Loop Editor**.</span></span>  
  
2.  <span data-ttu-id="c1d2a-106">(選擇性) 修改「For 迴圈」容器的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="c1d2a-106">Optionally, modify the name and description of the For Loop container.</span></span>  
  
3.  <span data-ttu-id="c1d2a-107">(選擇性) 在 [InitExpression]  文字方塊中輸入初始化運算式。</span><span class="sxs-lookup"><span data-stu-id="c1d2a-107">Optionally, type an initialization expression in the **InitExpression** text box.</span></span>  
  
4.  <span data-ttu-id="c1d2a-108">在 [EvalExpression]  文字方塊中輸入評估運算式。</span><span class="sxs-lookup"><span data-stu-id="c1d2a-108">Type an evaluation expression in the **EvalExpression** text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c1d2a-109">運算式必須評估為布林。</span><span class="sxs-lookup"><span data-stu-id="c1d2a-109">The expression must evaluate to a Boolean.</span></span> <span data-ttu-id="c1d2a-110">如果運算式的評估為 `false`，迴圈將停止執行。</span><span class="sxs-lookup"><span data-stu-id="c1d2a-110">When the expression evaluates to `false`, the loop stops running.</span></span>  
  
5.  <span data-ttu-id="c1d2a-111">(選擇性) 在 [AssignExpression]  文字方塊中輸入指派運算式。</span><span class="sxs-lookup"><span data-stu-id="c1d2a-111">Optionally, type an assignment expression in the **AssignExpression** text box.</span></span>  
  
6.  <span data-ttu-id="c1d2a-112">(選擇性) 按一下 [運算式]  ，然後在 [運算式]  頁面上建立「For 迴圈」容器之屬性的屬性運算式。</span><span class="sxs-lookup"><span data-stu-id="c1d2a-112">Optionally, click **Expressions** and, on the **Expressions** page, create property expressions for the properties of the For Loop container.</span></span> <span data-ttu-id="c1d2a-113">如需詳細資訊，請參閱[加入或變更屬性運算式](expressions/add-or-change-a-property-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="c1d2a-113">For more information, see [Add or Change a Property Expression](expressions/add-or-change-a-property-expression.md).</span></span>  
  
7.  <span data-ttu-id="c1d2a-114">按一下 [確定]  ，以關閉 [For 迴圈編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="c1d2a-114">Click **OK** to close the **For Loop Editor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1d2a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1d2a-115">See Also</span></span>  
 <span data-ttu-id="c1d2a-116">[For 迴圈容器](control-flow/for-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="c1d2a-116">[For Loop Container](control-flow/for-loop-container.md) </span></span>  
 <span data-ttu-id="c1d2a-117">[Integration Services &#40;SSIS&#41; 運算式](expressions/integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="c1d2a-117">[Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md) </span></span>  
 [<span data-ttu-id="c1d2a-118">在封裝中使用屬性運算式</span><span class="sxs-lookup"><span data-stu-id="c1d2a-118">Use Property Expressions in Packages</span></span>](expressions/use-property-expressions-in-packages.md)  
  
  
