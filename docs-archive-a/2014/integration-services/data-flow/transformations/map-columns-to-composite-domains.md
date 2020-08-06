---
title: 將資料行對應到複合定義域 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d9422412-8a3d-45ae-af7f-072c902a09ba
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6a665b2096579c9da35a1b69be46c4ba6103610f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599095"
---
# <a name="map-columns-to-composite-domains"></a><span data-ttu-id="e6de9-102">將資料行對應到複合定義域</span><span class="sxs-lookup"><span data-stu-id="e6de9-102">Map Columns to Composite Domains</span></span>
  <span data-ttu-id="e6de9-103">複合定義域是由兩個以上的單一定義域所組成。</span><span class="sxs-lookup"><span data-stu-id="e6de9-103">A composite domain consists of two or more single domains.</span></span> <span data-ttu-id="e6de9-104">您可以將多個資料行對應到定義域，也可將具有分隔值的單一資料行對應到定義域。</span><span class="sxs-lookup"><span data-stu-id="e6de9-104">You can map multiple columns to the domain, or you can map a single column with delimited values to the domain.</span></span>  
  
 <span data-ttu-id="e6de9-105">當您有多個資料行時，資料行必須個別對應到複合定義域中的每一個單一定義域，以將複合定義域規則套用於資料清理。</span><span class="sxs-lookup"><span data-stu-id="e6de9-105">When you have multiple columns, you must map a column to each single domain in the composite domain to apply the composite domain rules to data cleansing.</span></span> <span data-ttu-id="e6de9-106">您將在 Data Quality Client 中選取複合定義域內所容納的單一定義域。</span><span class="sxs-lookup"><span data-stu-id="e6de9-106">You select the single domains contained in the composite domain, in the Data Quality Client.</span></span> <span data-ttu-id="e6de9-107">如需相關資訊，請參閱 [建立複合定義域](../../../data-quality-services/create-a-composite-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="e6de9-107">For more information, see [Create a Composite Domain](../../../data-quality-services/create-a-composite-domain.md).</span></span>  
  
 <span data-ttu-id="e6de9-108">若為具有分隔值的單一資料行，則必須將該單一資料行對應到複合定義域。</span><span class="sxs-lookup"><span data-stu-id="e6de9-108">When you have a single column with delimited values, you must map the single column to the composite domain.</span></span> <span data-ttu-id="e6de9-109">各個值出現的順序務必與單一定義域出現在複合定義域中的順序相同。</span><span class="sxs-lookup"><span data-stu-id="e6de9-109">The values must appear in the same order as the single domains appear in the composite domain.</span></span> <span data-ttu-id="e6de9-110">資料來源中的分隔符號必須與用以剖析複合定義域值的分隔符號一致。</span><span class="sxs-lookup"><span data-stu-id="e6de9-110">The delimiter in the data source must match the delimiter that is used to parse the composite domain values.</span></span> <span data-ttu-id="e6de9-111">您將在 Data Quality Client 中為複合定義域選取分隔符號，並且設定其他屬性。</span><span class="sxs-lookup"><span data-stu-id="e6de9-111">You select the delimiter for the composite domain, as well as set other properties, in the Data Quality Client.</span></span> <span data-ttu-id="e6de9-112">如需相關資訊，請參閱 [建立複合定義域](../../../data-quality-services/create-a-composite-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="e6de9-112">For more information, see [Create a Composite Domain](../../../data-quality-services/create-a-composite-domain.md).</span></span>  
  
### <a name="to-map-multiple-columns-to-a-composite-domain"></a><span data-ttu-id="e6de9-113">若要將多個資料行對應到複合定義域</span><span class="sxs-lookup"><span data-stu-id="e6de9-113">To map multiple columns to a composite domain</span></span>  
  
1.  <span data-ttu-id="e6de9-114">以滑鼠右鍵按一下 DQS 清理轉換，然後按一下 [編輯]  。</span><span class="sxs-lookup"><span data-stu-id="e6de9-114">Right-click the DQS Cleansing transformation, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="e6de9-115">在 **[連接管理員]** 索引標籤上，確認複合定義域出現在可用的定義域清單中。</span><span class="sxs-lookup"><span data-stu-id="e6de9-115">On the **Connection Manager** tab, confirm that the composite domain appears in the list of available domains.</span></span>  
  
3.  <span data-ttu-id="e6de9-116">在 **[對應]** 索引標籤上，從 **[可用的輸入資料行]** 區域內選取資料行。</span><span class="sxs-lookup"><span data-stu-id="e6de9-116">On the **Mapping** tab, select the columns in the **Available Input Columns** area.</span></span>  
  
4.  <span data-ttu-id="e6de9-117">針對 **[輸入資料行]** 欄位中所列的每一個資料行，從 **[定義域]** 欄位中選取個別的單一定義域。</span><span class="sxs-lookup"><span data-stu-id="e6de9-117">For each column listed in the **Input Column** field, select a single domain in the **Domain** field.</span></span> <span data-ttu-id="e6de9-118">務必只選取位於複合定義域內的單一定義域。</span><span class="sxs-lookup"><span data-stu-id="e6de9-118">Select only single domains that are in the composite domain.</span></span>  
  
5.  <span data-ttu-id="e6de9-119">視需要修改 **[來源別名]** 、 **[輸出別名]** 和 **[狀態別名]** 欄位中所顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="e6de9-119">As needed, modify the names that appear in the **Source Alias**, **Output Alias**, and **Status Alias** fields.</span></span>  
  
6.  <span data-ttu-id="e6de9-120">視需要在 **[進階]** 索引標籤上設定屬性。如需這些屬性的詳細資訊，請參閱＜ [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e6de9-120">As needed, set properties on the **Advanced** tab. For more information about the properties, see [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md).</span></span>  
  
### <a name="to-map-a-column-with-delimited-values-to-a-composite-domain"></a><span data-ttu-id="e6de9-121">若要將具有分隔值的資料行對應到複合定義網域</span><span class="sxs-lookup"><span data-stu-id="e6de9-121">To map a column with delimited values to a composite domain</span></span>  
  
1.  <span data-ttu-id="e6de9-122">以滑鼠右鍵按一下 DQS 清理轉換，然後按一下 [編輯]  。</span><span class="sxs-lookup"><span data-stu-id="e6de9-122">Right-click the DQS Cleansing transformation, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="e6de9-123">在 **[連接管理員]** 索引標籤上，確認複合定義域出現在可用的定義域清單中。</span><span class="sxs-lookup"><span data-stu-id="e6de9-123">On the **Connection Manager** tab, confirm that the composite domain appears in the list of available domains.</span></span>  
  
3.  <span data-ttu-id="e6de9-124">在 **[對應]** 索引標籤上，從 **[可用的輸入資料行]** 區域內選取該資料行。</span><span class="sxs-lookup"><span data-stu-id="e6de9-124">On the **Mapping** tab, select the column in the **Available Input Columns** area.</span></span>  
  
4.  <span data-ttu-id="e6de9-125">針對 **[輸入資料行]** 欄位中所列的資料行，從 **[定義域]** 欄位中選取複合定義域。</span><span class="sxs-lookup"><span data-stu-id="e6de9-125">For the column listed in the **Input Column** field, select the composite domain in the **Domain** field.</span></span>  
  
5.  <span data-ttu-id="e6de9-126">視需要修改 **[來源別名]** 、 **[輸出別名]** 和 **[狀態別名]** 欄位中所顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="e6de9-126">As needed, modify the names that appear in the **Source Alias**, **Output Alias**, and **Status Alias** fields.</span></span>  
  
6.  <span data-ttu-id="e6de9-127">視需要在 **[進階]** 索引標籤上設定屬性。如需這些屬性的詳細資訊，請參閱＜ [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e6de9-127">As needed, set properties on the **Advanced** tab. For more information about the properties, see [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6de9-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6de9-128">See Also</span></span>  
 [<span data-ttu-id="e6de9-129">DQS 清理轉換</span><span class="sxs-lookup"><span data-stu-id="e6de9-129">DQS Cleansing Transformation</span></span>](dqs-cleansing-transformation.md)  
  
  
