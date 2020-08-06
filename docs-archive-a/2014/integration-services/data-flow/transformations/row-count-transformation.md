---
title: 資料列計數轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rowcounttrans.f1
helpviewer_keywords:
- updating variables
- Row Count transformation
- number of rows
- variables [Integration Services], updating
- counting rows
ms.assetid: b68293b9-a68c-40be-9d81-77342da1be29
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b0940d608aeaa96b7ec43fa4486944ce0f887e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710773"
---
# <a name="row-count-transformation"></a><span data-ttu-id="e744f-102">資料列計數轉換</span><span class="sxs-lookup"><span data-stu-id="e744f-102">Row Count Transformation</span></span>
  <span data-ttu-id="e744f-103">「資料列計數」轉換會在資料列通過資料流程時計算其數目，並將最後計數儲存到變數中。</span><span class="sxs-lookup"><span data-stu-id="e744f-103">The Row Count transformation counts rows as they pass through a data flow and stores the final count in a variable.</span></span>  
  
 <span data-ttu-id="e744f-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 套件可使用資料列計數更新指令碼、運算式和屬性運算式中使用的變數</span><span class="sxs-lookup"><span data-stu-id="e744f-104">A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package can use row counts to update the variables used in scripts, expressions, and property expressions.</span></span> <span data-ttu-id="e744f-105">(例如，儲存資料列計數的變數可更新電子郵件訊息中的訊息文字，以便加入資料列數)。「資料列計數」轉換使用的變數必須已存在，且必須在擁有「資料列計數」轉換的資料流程所屬的「資料流程」工作範圍內。</span><span class="sxs-lookup"><span data-stu-id="e744f-105">(For example, the variable that stores the row count can update the message text in an e-mail message to include the number of rows.) The variable that the Row Count transformation uses must already exist, and it must be in the scope of the Data Flow task to which the data flow with the Row Count transformation belongs.</span></span>  
  
 <span data-ttu-id="e744f-106">此轉換只會在最後一個資料列傳遞至轉換之後，才使用變數儲存資料列計數值。</span><span class="sxs-lookup"><span data-stu-id="e744f-106">The transformation stores the row count value in the variable only after the last row has passed through the transformation.</span></span> <span data-ttu-id="e744f-107">因此，變數的值不會及時更新為使用資料流程中包含「資料列計數」轉換的更新值。</span><span class="sxs-lookup"><span data-stu-id="e744f-107">Therefore, the value of the variable is not updated in time to use the updated value in the data flow that contains the Row Count transformation.</span></span> <span data-ttu-id="e744f-108">您可以在個別的資料流程中使用更新的變數。</span><span class="sxs-lookup"><span data-stu-id="e744f-108">You can use the updated variable in a separate data flow.</span></span>  
  
 <span data-ttu-id="e744f-109">此轉換有一個輸入和一個輸出。</span><span class="sxs-lookup"><span data-stu-id="e744f-109">This transformation has one input and one output.</span></span> <span data-ttu-id="e744f-110">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="e744f-110">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-row-count-transformation"></a><span data-ttu-id="e744f-111">資料列計數轉換的組態</span><span class="sxs-lookup"><span data-stu-id="e744f-111">Configuration of the Row Count Transformation</span></span>  
 <span data-ttu-id="e744f-112">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="e744f-112">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="e744f-113">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="e744f-113">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="e744f-114">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="e744f-114">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="e744f-115">Common Properties</span><span class="sxs-lookup"><span data-stu-id="e744f-115">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="e744f-116">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="e744f-116">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="e744f-117">相關工作</span><span class="sxs-lookup"><span data-stu-id="e744f-117">Related Tasks</span></span>  
 <span data-ttu-id="e744f-118">如需如何設定此元件屬性的資訊，請參閱 [設定資料流程元件的屬性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="e744f-118">For information about how to set the properties of this component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e744f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e744f-119">See Also</span></span>  
 <span data-ttu-id="e744f-120">[Integration Services &#40;SSIS&#41; 變數](../../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="e744f-120">[Integration Services &#40;SSIS&#41; Variables](../../integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="e744f-121">[資料流程](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="e744f-121">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="e744f-122">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="e744f-122">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
