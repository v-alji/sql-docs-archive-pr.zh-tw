---
title: 多點傳送轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multicasttrans.f1
helpviewer_keywords:
- multiple outputs
- Multicast transformation
- datasets [Integration Services], multiple outputs
- multiple transformations
ms.assetid: 32194784-1684-40cd-9f91-1aba4d8360d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7b5c0a38c966c89f426a213f302b45c390b77cfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710786"
---
# <a name="multicast-transformation"></a><span data-ttu-id="48a6b-102">多點傳送轉換</span><span class="sxs-lookup"><span data-stu-id="48a6b-102">Multicast Transformation</span></span>
  <span data-ttu-id="48a6b-103">「多點傳送」轉換會將其輸入散發至一個或多個輸出。</span><span class="sxs-lookup"><span data-stu-id="48a6b-103">The Multicast transformation distributes its input to one or more outputs.</span></span> <span data-ttu-id="48a6b-104">此轉換與「條件式分割」轉換類似。</span><span class="sxs-lookup"><span data-stu-id="48a6b-104">This transformation is similar to the Conditional Split transformation.</span></span> <span data-ttu-id="48a6b-105">這兩種轉換都會將輸入導向多個輸出，</span><span class="sxs-lookup"><span data-stu-id="48a6b-105">Both transformations direct an input to multiple outputs.</span></span> <span data-ttu-id="48a6b-106">兩者的差異在於「多點傳送」轉換會將每個資料列導向每個輸出，而「條件式分割」會將一個資料列導向單一輸出。</span><span class="sxs-lookup"><span data-stu-id="48a6b-106">The difference between the two is that the Multicast transformation directs every row to every output, and the Conditional Split directs a row to a single output.</span></span> <span data-ttu-id="48a6b-107">如需詳細資訊，請參閱 [Conditional Split Transformation](conditional-split-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="48a6b-107">For more information, see [Conditional Split Transformation](conditional-split-transformation.md).</span></span>  
  
 <span data-ttu-id="48a6b-108">您可加入輸出以設定「多點傳送」轉換。</span><span class="sxs-lookup"><span data-stu-id="48a6b-108">You configure the Multicast transformation by adding outputs.</span></span>  
  
 <span data-ttu-id="48a6b-109">使用「多點傳送」轉換時，封裝可建立資料的邏輯副本。</span><span class="sxs-lookup"><span data-stu-id="48a6b-109">Using the Multicast transformation, a package can create logical copies of data.</span></span> <span data-ttu-id="48a6b-110">當封裝需要將多組轉換套用至相同資料時，此功能會很有用。</span><span class="sxs-lookup"><span data-stu-id="48a6b-110">This capability is useful when the package needs to apply multiple sets of transformations to the same data.</span></span> <span data-ttu-id="48a6b-111">例如，彙總一份資料副本且只將摘要資訊載入其目的地，但是以查閱值和衍生的資料行擴充另一份資料副本，再將其載入目的地。</span><span class="sxs-lookup"><span data-stu-id="48a6b-111">For example, one copy of the data is aggregated and only the summary information is loaded into its destination, while another copy of the data is extended with lookup values and derived columns before it is loaded into its destination.</span></span>  
  
 <span data-ttu-id="48a6b-112">此轉換有一個輸入和多個輸出，</span><span class="sxs-lookup"><span data-stu-id="48a6b-112">This transformation has one input and multiple outputs.</span></span> <span data-ttu-id="48a6b-113">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="48a6b-113">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-multicast-transformation"></a><span data-ttu-id="48a6b-114">設定多點傳送轉換</span><span class="sxs-lookup"><span data-stu-id="48a6b-114">Configuration of the Multicast Transformation</span></span>  
 <span data-ttu-id="48a6b-115">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="48a6b-115">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="48a6b-116">如需有關可在 **[多點傳送轉換編輯器]** 對話方塊中設定之屬性的詳細資訊，請參閱＜ [Multicast Transformation Editor](../../multicast-transformation-editor.md)＞。</span><span class="sxs-lookup"><span data-stu-id="48a6b-116">For information about the properties that you can set in the **Multicast Transformation Editor** dialog box, see [Multicast Transformation Editor](../../multicast-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="48a6b-117">如需有關可以程式設計方式設定之屬性的詳細資訊，請參閱＜ [Common Properties](../../common-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="48a6b-117">For information about the properties that you can set programmatically, see [Common Properties](../../common-properties.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="48a6b-118">相關工作</span><span class="sxs-lookup"><span data-stu-id="48a6b-118">Related Tasks</span></span>  
 <span data-ttu-id="48a6b-119">如需如何設定此元件屬性的資訊，請參閱 [設定資料流程元件的屬性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="48a6b-119">For information about how to set properties of this component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a6b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48a6b-120">See Also</span></span>  
 <span data-ttu-id="48a6b-121">[資料流程](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="48a6b-121">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="48a6b-122">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="48a6b-122">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
