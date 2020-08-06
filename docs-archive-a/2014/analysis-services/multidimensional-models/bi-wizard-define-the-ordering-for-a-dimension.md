---
title: 定義維度的順序 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OrderBy property
- dimensions [Analysis Services], ordering
- Business Intelligence enhancements [Analysis Services], ordering
- dimensions [Analysis Services], Business Intelligence enhancements
- ordering dimensions [Analysis Services]
- OrderByAttributeID property
ms.assetid: c42fbd58-244d-4e0a-b715-6f919cbc3ad9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8cd5ea148e374c18c530ba0a15c80dbb23983020
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593665"
---
# <a name="define-the-ordering-for-a-dimension"></a><span data-ttu-id="7f1da-102">定義維度的排序方式</span><span class="sxs-lookup"><span data-stu-id="7f1da-102">Define the Ordering for a Dimension</span></span>
  <span data-ttu-id="7f1da-103">將屬性排序方式增強功能加入至 Cube 或維度，即可指定如何排序屬性的成員。</span><span class="sxs-lookup"><span data-stu-id="7f1da-103">Add the attribute ordering enhancement to a cube or dimension to specify how the members of an attribute are ordered.</span></span> <span data-ttu-id="7f1da-104">您可以依名稱或屬性的索引鍵來排序成員，或是依名稱或另一個屬性 (根據屬性關聯性) 的索引鍵來排序成員。</span><span class="sxs-lookup"><span data-stu-id="7f1da-104">Members can be ordered by the name or the key of the attribute, or by the name or the key of another attribute (based on an attribute relationship).</span></span> <span data-ttu-id="7f1da-105">依預設，會依名稱來排序成員。</span><span class="sxs-lookup"><span data-stu-id="7f1da-105">By default, members are ordered by the name.</span></span> <span data-ttu-id="7f1da-106">這項增強功能會在維度中變更屬性的 `OrderBy` 和 `OrderByAttributeID` 屬性設定。</span><span class="sxs-lookup"><span data-stu-id="7f1da-106">This enhancement changes the `OrderBy` and `OrderByAttributeID` property settings for attributes in a dimension.</span></span>  
  
 <span data-ttu-id="7f1da-107">若要加入屬性排序，您可使用 [商業智慧精靈]，並於 [選擇增強功能]\*\*\*\* 頁面上選取 [指定屬性排列方式]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="7f1da-107">To add attribute ordering, you use the Business Intelligence Wizard, and select the **Specify attribute ordering** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="7f1da-108">然後，此精靈會引導您逐步完成選取要套用屬性排序方式的維度，並指定如何為選取的維度排序屬性。</span><span class="sxs-lookup"><span data-stu-id="7f1da-108">This wizard then guides you through the steps of selecting a dimension to which you want to apply attribute ordering and specifying how to order the attributes for the selected dimension.</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="7f1da-109">選取維度</span><span class="sxs-lookup"><span data-stu-id="7f1da-109">Selecting a Dimension</span></span>  
 <span data-ttu-id="7f1da-110">在精靈的第一個 [指定屬性排列方式]\*\*\*\* 頁面上，您指定要套用屬性排列方式的維度。</span><span class="sxs-lookup"><span data-stu-id="7f1da-110">On the first **Specify Attribute Ordering** page of the wizard, you specify the dimension to which you want to apply attribute ordering.</span></span> <span data-ttu-id="7f1da-111">加入到此選取維度的屬性排列方式增強功能，會造成維度的變更。</span><span class="sxs-lookup"><span data-stu-id="7f1da-111">The attribute ordering enhancement added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="7f1da-112">包含選取之維度的所有 Cube，都會繼承這些變更。</span><span class="sxs-lookup"><span data-stu-id="7f1da-112">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
## <a name="specifying-ordering"></a><span data-ttu-id="7f1da-113">指定排列方式</span><span class="sxs-lookup"><span data-stu-id="7f1da-113">Specifying Ordering</span></span>  
 <span data-ttu-id="7f1da-114">在精靈的第二個 [指定屬性排列方式]\*\*\*\* 頁面上，您指定如何排序維度中的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="7f1da-114">On the second **Specify Attribute Ordering** page of the wizard, you specify how all the attributes in the dimension will be ordered.</span></span>  
  
 <span data-ttu-id="7f1da-115">在 [排序屬性]\*\*\*\* 資料行中，您可變更用於執行排序的屬性。</span><span class="sxs-lookup"><span data-stu-id="7f1da-115">In the **Ordering Attribute** column, you can change the attribute used to do the ordering.</span></span> <span data-ttu-id="7f1da-116">如果您要用來排序成員的屬性不在清單中，請在清單中向下移動，然後選取 **\<New attribute...>** 以開啟 [**選取資料行**] 對話方塊，您可以在其中選取維度資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="7f1da-116">If the attribute that you want to use to order members is not in the list, scroll down the list, and then select **\<New attribute...>** to open the **Select a Column** dialog box, where you can select a column in a dimension table.</span></span> <span data-ttu-id="7f1da-117">使用 [選取資料行]\*\*\*\* 對話方塊選取資料行會建立一個額外的屬性，可用它來排序屬性的成員。</span><span class="sxs-lookup"><span data-stu-id="7f1da-117">Selecting a column by using the **Select a Column** dialog box creates an additional attribute with which to order members of an attribute.</span></span>  
  
 <span data-ttu-id="7f1da-118">在 [準則]\*\*\*\* 資料行中，您可選取要依 [索引鍵]\*\*\*\* 或 [名稱]\*\*\*\* 來排序屬性的成員。</span><span class="sxs-lookup"><span data-stu-id="7f1da-118">In the **Criteria** column, you can then select whether to order the members of the attribute by either **Key** or **Name**.</span></span>  
  
  
