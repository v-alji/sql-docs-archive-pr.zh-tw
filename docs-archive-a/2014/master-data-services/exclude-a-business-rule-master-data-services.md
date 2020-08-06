---
title: 排除商務規則 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], excluding
ms.assetid: bdbc9df0-23f7-40b9-8aba-4445c1482580
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 317964dcbc7b2cbe212c415b3aa4f9f1a0743301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699946"
---
# <a name="exclude-a-business-rule-master-data-services"></a><span data-ttu-id="f3d7b-102">排除商務規則 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f3d7b-102">Exclude a Business Rule (Master Data Services)</span></span>
  <span data-ttu-id="f3d7b-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，當您不想要永久刪除商務規則，但是也不想使用它來驗證資料時，可排除此商務規則。</span><span class="sxs-lookup"><span data-stu-id="f3d7b-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], exclude a business rule when you do not want to delete the rule permanently, but you do not want to validate data against it.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f3d7b-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f3d7b-104">Prerequisites</span></span>  
 <span data-ttu-id="f3d7b-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="f3d7b-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="f3d7b-106">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="f3d7b-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="f3d7b-107">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="f3d7b-107">You must be a model administrator.</span></span> <span data-ttu-id="f3d7b-108">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f3d7b-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-exclude-a-business-rule"></a><span data-ttu-id="f3d7b-109">若要排除商務規則</span><span class="sxs-lookup"><span data-stu-id="f3d7b-109">To exclude a business rule</span></span>  
  
1.  <span data-ttu-id="f3d7b-110">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="f3d7b-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="f3d7b-111">從功能表列，指向 **[管理]** ，然後按一下 **[商務規則]**。</span><span class="sxs-lookup"><span data-stu-id="f3d7b-111">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="f3d7b-112">在 [商務規則維護]\*\*\*\* 頁面上，選取 [模型]\*\*\*\* 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="f3d7b-112">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="f3d7b-113">從 [實體]\*\*\*\* 清單中選取實體。</span><span class="sxs-lookup"><span data-stu-id="f3d7b-113">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="f3d7b-114">從 [**成員類型**] 清單中，選取成員的類型。</span><span class="sxs-lookup"><span data-stu-id="f3d7b-114">From the **Member Type** list, select a type of member.</span></span>  
  
6.  <span data-ttu-id="f3d7b-115">從 [屬性]\*\*\*\* 清單中，選取屬性或保留預設值 [全部]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f3d7b-115">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="f3d7b-116">在方格中，于商務規則的資料列中，選取 [**排除**] 資料行中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f3d7b-116">In the grid, in the row for the business rule, select the check box in the **Exclude** column.</span></span> <span data-ttu-id="f3d7b-117">[**狀態**] 資料行中的值為 [**排除暫**止]。</span><span class="sxs-lookup"><span data-stu-id="f3d7b-117">The value in the **Status** column is **Exclusion pending**.</span></span>  
  
8.  <span data-ttu-id="f3d7b-118">按一下 [發行商務規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f3d7b-118">Click **Publish business rules**.</span></span>  
  
9. <span data-ttu-id="f3d7b-119">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f3d7b-119">In the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="f3d7b-120">[**狀態**] 資料行中的值已**排除**。</span><span class="sxs-lookup"><span data-stu-id="f3d7b-120">The value in the **Status** column is **Excluded**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3d7b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3d7b-121">See Also</span></span>  
 <span data-ttu-id="f3d7b-122">[刪除商務規則 &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-business-rule-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f3d7b-122">[Delete a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-business-rule-master-data-services.md) </span></span>  
 <span data-ttu-id="f3d7b-123">[建立和發佈商務規則 &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f3d7b-123">[Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md) </span></span>  
 [<span data-ttu-id="f3d7b-124">商務規則 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f3d7b-124">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
