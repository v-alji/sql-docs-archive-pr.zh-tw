---
title: 根據商務規則驗證特定成員 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- applying business rules [Master Data Services]
- business rules [Master Data Services], applying to select members
ms.assetid: 2288ef43-5392-47ea-b651-ec25e5692a14
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 18af83146679eb77638dfbc98b31f198dc8e07b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595159"
---
# <a name="validate-specific-members-against-business-rules-master-data-services"></a><span data-ttu-id="3ea36-102">根據商務規則驗證特定成員 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3ea36-102">Validate Specific Members against Business Rules (Master Data Services)</span></span>
  <span data-ttu-id="3ea36-103">如果您想要更新或依照商務規則驗證成員子集，請在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中選擇性地套用商務規則。</span><span class="sxs-lookup"><span data-stu-id="3ea36-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], apply business rules selectively when you want to update or validate subsets of members against business rules.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ea36-104">如果您想要將商務規則套用至某版本模型中的所有成員，請參閱 [根據商務規則驗證版本 &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3ea36-104">If you want to apply business rules to all members in a version of a model, see [Validate a Version against Business Rules &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3ea36-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="3ea36-105">Prerequisites</span></span>  
 <span data-ttu-id="3ea36-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="3ea36-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="3ea36-107">您必須擁有存取 [ **Explorer** ] 功能區域的許可權。</span><span class="sxs-lookup"><span data-stu-id="3ea36-107">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="3ea36-108">針對要套用商務規則的模型物件，您必須至少擁有 **[更新]** 權限。</span><span class="sxs-lookup"><span data-stu-id="3ea36-108">You must have a minimum of **Update** permission to the model object you are applying business rules to.</span></span>  
  
### <a name="to-apply-business-rules-selectively"></a><span data-ttu-id="3ea36-109">若要選擇性地套用商務規則</span><span class="sxs-lookup"><span data-stu-id="3ea36-109">To apply business rules selectively</span></span>  
  
1.  <span data-ttu-id="3ea36-110">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 首頁上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="3ea36-110">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="3ea36-111">從 **[版本]** 清單中選取版本。</span><span class="sxs-lookup"><span data-stu-id="3ea36-111">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="3ea36-112">按一下 **[總管]**。</span><span class="sxs-lookup"><span data-stu-id="3ea36-112">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="3ea36-113">從功能表列指向 **[實體]** ，然後按一下包含要套用規則之成員的實體名稱。</span><span class="sxs-lookup"><span data-stu-id="3ea36-113">From the menu bar, point to **Entities** and click the name of the entity that contains members you want to apply rules to.</span></span>  
  
5.  <span data-ttu-id="3ea36-114">按一下 [套用商務規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ea36-114">Click **Apply business rules**.</span></span> <span data-ttu-id="3ea36-115">商務規則只套用至方格中顯示的成員。</span><span class="sxs-lookup"><span data-stu-id="3ea36-115">Business rules are applied only to the members displayed in the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ea36-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ea36-116">See Also</span></span>  
 <span data-ttu-id="3ea36-117">[根據商務規則驗證版本 &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3ea36-117">[Validate a Version against Business Rules &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md) </span></span>  
 [<span data-ttu-id="3ea36-118">商務規則 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3ea36-118">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
