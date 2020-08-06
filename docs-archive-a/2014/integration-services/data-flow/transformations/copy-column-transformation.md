---
title: 複製資料行轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.copycolumntrans.f1
helpviewer_keywords:
- columns [Integration Services], copying
- copying columns
- Copy Column transformation
ms.assetid: 1c72a313-9026-46bc-a57f-c6b3f47346f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fd2745070a92ab71e89f3bfa9edd8673b676632b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597240"
---
# <a name="copy-column-transformation"></a><span data-ttu-id="3cdde-102">複製資料行轉換</span><span class="sxs-lookup"><span data-stu-id="3cdde-102">Copy Column Transformation</span></span>
  <span data-ttu-id="3cdde-103">「複製資料行」轉換會複製輸入資料行，並將新資料行加入轉換輸出，以建立新資料行。</span><span class="sxs-lookup"><span data-stu-id="3cdde-103">The Copy Column transformation creates new columns by copying input columns and adding the new columns to the transformation output.</span></span> <span data-ttu-id="3cdde-104">稍後在資料流程中，可將不同的轉換套用至資料行副本。</span><span class="sxs-lookup"><span data-stu-id="3cdde-104">Later in the data flow, different transformations can be applied to the column copies.</span></span> <span data-ttu-id="3cdde-105">例如，您可以使用「複製資料行」轉換建立資料行複本，然後使用「字元對應」轉換將複製的資料轉換為大寫字元，或使用「彙總」轉換將彙總套用至新資料行。</span><span class="sxs-lookup"><span data-stu-id="3cdde-105">For example, you can use the Copy Column transformation to create a copy of a column and then convert the copied data to uppercase characters by using the Character Map transformation, or apply aggregations to the new column by using the Aggregate transformation.</span></span>  
  
## <a name="configuration-of-the-copy-column-transformation"></a><span data-ttu-id="3cdde-106">設定複製資料行轉換</span><span class="sxs-lookup"><span data-stu-id="3cdde-106">Configuration of the Copy Column Transformation</span></span>  
 <span data-ttu-id="3cdde-107">您可將輸入資料行指定為複製，以設定「複製資料行」轉換。</span><span class="sxs-lookup"><span data-stu-id="3cdde-107">You configure the Copy Column transformation by specifying the input columns to copy.</span></span> <span data-ttu-id="3cdde-108">您可以在一個作業中建立資料行的多份副本，或是建立多個資料行的副本。</span><span class="sxs-lookup"><span data-stu-id="3cdde-108">You can create multiple copies of a column, or create copies of multiple columns in one operation.</span></span>  
  
 <span data-ttu-id="3cdde-109">此轉換有一個輸入和一個輸出。</span><span class="sxs-lookup"><span data-stu-id="3cdde-109">This transformation has one input and one output.</span></span> <span data-ttu-id="3cdde-110">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="3cdde-110">It does not support an error output.</span></span>  
  
 <span data-ttu-id="3cdde-111">您可以透過「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="3cdde-111">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="3cdde-112">如需可在 **[複製資料行轉換編輯器]** 對話方塊中設定之屬性的詳細資訊，請參閱＜ [Copy Column Transformation Editor](../../copy-column-transformation-editor.md)＞。</span><span class="sxs-lookup"><span data-stu-id="3cdde-112">For more information about the properties that you can set in the **Copy Column Transformation Editor** dialog box, see [Copy Column Transformation Editor](../../copy-column-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="3cdde-113">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="3cdde-113">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="3cdde-114">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="3cdde-114">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="3cdde-115">Common Properties</span><span class="sxs-lookup"><span data-stu-id="3cdde-115">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="3cdde-116">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="3cdde-116">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="3cdde-117">如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="3cdde-117">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cdde-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cdde-118">See Also</span></span>  
 <span data-ttu-id="3cdde-119">[資料流程](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="3cdde-119">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="3cdde-120">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="3cdde-120">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
