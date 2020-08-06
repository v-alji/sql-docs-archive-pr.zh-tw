---
title: 將成員新增至集合 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], adding members
ms.assetid: 1a7155e6-2d4a-4ed1-a72c-edb37fa1a46b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce2038f3bc90a2f17506b0aadaaf9707fa911896
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606397"
---
# <a name="add-members-to-a-collection-master-data-services"></a><span data-ttu-id="b232c-102">將成員加入至集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b232c-102">Add Members to a Collection (Master Data Services)</span></span>
  <span data-ttu-id="b232c-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以將分葉成員和合併成員加入至集合中。</span><span class="sxs-lookup"><span data-stu-id="b232c-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can add leaf and consolidated members to a collection.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b232c-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="b232c-104">Prerequisites</span></span>  
 <span data-ttu-id="b232c-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="b232c-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="b232c-106">您必須擁有存取 [ **Explorer** ] 功能區域的許可權。</span><span class="sxs-lookup"><span data-stu-id="b232c-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="b232c-107">針對要加入成員的集合模型物件，您至少必須擁有 **[更新]** 權限。</span><span class="sxs-lookup"><span data-stu-id="b232c-107">You must have a minimum of **Update** permission to the collection model object that you are adding members to.</span></span>  
  
-   <span data-ttu-id="b232c-108">集合必須存在。</span><span class="sxs-lookup"><span data-stu-id="b232c-108">A collection must exist.</span></span> <span data-ttu-id="b232c-109">如需詳細資訊，請參閱[建立集合 &#40;Master Data Services&#41;](create-a-collection-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b232c-109">For more information, see [Create a Collection &#40;Master Data Services&#41;](create-a-collection-master-data-services.md).</span></span>  
  
### <a name="to-add-members-to-a-collection"></a><span data-ttu-id="b232c-110">若要將成員加入至集合</span><span class="sxs-lookup"><span data-stu-id="b232c-110">To add members to a collection</span></span>  
  
1.  <span data-ttu-id="b232c-111">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 首頁上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="b232c-111">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="b232c-112">從 **[版本]** 清單中選取版本。</span><span class="sxs-lookup"><span data-stu-id="b232c-112">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="b232c-113">按一下 **[總管]**。</span><span class="sxs-lookup"><span data-stu-id="b232c-113">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="b232c-114">從功能表列指向 [集合]\*\*\*\*，然後按一下 *entity_name*。</span><span class="sxs-lookup"><span data-stu-id="b232c-114">From the menu bar, point to **Collections** and click *entity_name*.</span></span>  
  
5.  <span data-ttu-id="b232c-115">在方格中，按一下您想要在其中加入成員之集合的資料列。</span><span class="sxs-lookup"><span data-stu-id="b232c-115">In the grid, click the row for the collection you want to add members to.</span></span>  
  
6.  <span data-ttu-id="b232c-116">按一下 **[集合成員]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b232c-116">Click the **Collection Members** tab.</span></span>  
  
7.  <span data-ttu-id="b232c-117">按一下 **[編輯成員]**。</span><span class="sxs-lookup"><span data-stu-id="b232c-117">Click **Edit Members**.</span></span>  
  
8.  <span data-ttu-id="b232c-118">若要篩選可用成員的清單，請從左側的清單中選取。</span><span class="sxs-lookup"><span data-stu-id="b232c-118">To filter the list of available members, select from the list on the left.</span></span>  
  
9. <span data-ttu-id="b232c-119">按一下包含您想要加入之成員的資料列，然後按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="b232c-119">Click the row with the member you want to add and click **Add**.</span></span>  
  
10. <span data-ttu-id="b232c-120">或者，按一下 **[向上]** 或 **[向下]**，重新排列集合成員。</span><span class="sxs-lookup"><span data-stu-id="b232c-120">Optionally, rearrange collection members by clicking **Up** or **Down**.</span></span>  
  
11. <span data-ttu-id="b232c-121">或者，按一下 **[加權]** 資料行中的值來設定加權值。</span><span class="sxs-lookup"><span data-stu-id="b232c-121">Optionally, set weight values by clicking the value in the **Weight** column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b232c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b232c-122">See Also</span></span>  
 [<span data-ttu-id="b232c-123">集合 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b232c-123">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)  
  
  
