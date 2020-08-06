---
title: 資料錄集目的地 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.recordsetdest.f1
helpviewer_keywords:
- Recordset destination
- ADO recordsets [Integration Services]
- destinations [Integration Services], Recordset
- in-memory ADO recordsets [Integration Services]
ms.assetid: be973cf1-c4ff-49f8-987e-314c08ef98e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c1acc29c904e9020721e8ac62dff09a8ec29a392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593458"
---
# <a name="recordset-destination"></a><span data-ttu-id="77c10-102">資料錄集目的地</span><span class="sxs-lookup"><span data-stu-id="77c10-102">Recordset Destination</span></span>
  <span data-ttu-id="77c10-103">資料錄集目的地可建立和擴展記憶體中的 ADO 資料錄集。</span><span class="sxs-lookup"><span data-stu-id="77c10-103">The Recordset destination creates and populates an in-memory ADO recordset.</span></span> <span data-ttu-id="77c10-104">資料錄集的形狀，是由設計階段時對「資料錄集」目的地的輸入所定義。</span><span class="sxs-lookup"><span data-stu-id="77c10-104">The shape of the recordset is defined by the input to the Recordset destination at design time.</span></span>  
  
## <a name="configuration-of-the-recordset-destination"></a><span data-ttu-id="77c10-105">資料錄集目的地的組態</span><span class="sxs-lookup"><span data-stu-id="77c10-105">Configuration of the Recordset Destination</span></span>  
 <span data-ttu-id="77c10-106">藉由指定儲存 ADO 資料錄集的變數，您可以設定「資料錄集」目的地。</span><span class="sxs-lookup"><span data-stu-id="77c10-106">You configure the Recordset destination by specifying the variable that stores the ADO recordset.</span></span>  
  
 <span data-ttu-id="77c10-107">在執行階段，ADO 資料錄集會被寫入「資料錄集」目的地之 VariableName 屬性中指定的 [物件] 變數類型。</span><span class="sxs-lookup"><span data-stu-id="77c10-107">At run time, an ADO recordset is written to the variable of type, Object, that is specified in the VariableName property of the Recordset destination.</span></span> <span data-ttu-id="77c10-108">然後，該變數會使「資料錄集」在資料流程外部可用，指令碼及其他封裝元素會在此處使用該資料錄集。</span><span class="sxs-lookup"><span data-stu-id="77c10-108">The variable then makes the Recordset available outside the data flow, where it can be used by scripts and other package elements.</span></span>  
  
 <span data-ttu-id="77c10-109">此來源具有一個輸入。</span><span class="sxs-lookup"><span data-stu-id="77c10-109">This source has one input.</span></span> <span data-ttu-id="77c10-110">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="77c10-110">It does not support an error output.</span></span>  
  
 <span data-ttu-id="77c10-111">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="77c10-111">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="77c10-112">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="77c10-112">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="77c10-113">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="77c10-113">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="77c10-114">Common Properties</span><span class="sxs-lookup"><span data-stu-id="77c10-114">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="77c10-115">資料錄集目的地自訂屬性</span><span class="sxs-lookup"><span data-stu-id="77c10-115">Recordset Destination Custom Properties</span></span>](recordset-destination-custom-properties.md)  
  
 <span data-ttu-id="77c10-116">如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="77c10-116">For more information about how to set the properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="77c10-117">相關工作</span><span class="sxs-lookup"><span data-stu-id="77c10-117">Related Tasks</span></span>  
 [<span data-ttu-id="77c10-118">使用資料錄集目的地</span><span class="sxs-lookup"><span data-stu-id="77c10-118">Use a Recordset Destination</span></span>](recordset-destination.md)  
  
  
