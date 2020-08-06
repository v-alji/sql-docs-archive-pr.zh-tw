---
title: 變更商務規則名稱 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], changing name
ms.assetid: cffcae43-a208-443f-9f43-a0ec9e05f79c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0e99047ffe27332aaed4514394ca2357942a1297
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606966"
---
# <a name="change-a-business-rule-name-master-data-services"></a><span data-ttu-id="5bfb9-102">變更商務規則名稱 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="5bfb9-102">Change a Business Rule Name (Master Data Services)</span></span>
  <span data-ttu-id="5bfb9-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，當指派的商務規則名稱不符合業務需求時，變更此名稱。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], change a business rule name when the name assigned does not meet your business needs.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5bfb9-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="5bfb9-104">Prerequisites</span></span>  
 <span data-ttu-id="5bfb9-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="5bfb9-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="5bfb9-106">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="5bfb9-107">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-107">You must be a model administrator.</span></span> <span data-ttu-id="5bfb9-108">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="5bfb9-109">商務規則必須存在。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-109">A business rule must exist.</span></span> <span data-ttu-id="5bfb9-110">如需詳細資訊，請參閱[建立及發行商務規則 &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-110">For more information, see [Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).</span></span>  
  
### <a name="to-change-the-name-of-a-business-rule"></a><span data-ttu-id="5bfb9-111">若要變更商務規則的名稱</span><span class="sxs-lookup"><span data-stu-id="5bfb9-111">To change the name of a business rule</span></span>  
  
1.  <span data-ttu-id="5bfb9-112">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="5bfb9-113">從功能表列，指向 **[管理]** ，然後按一下 **[商務規則]**。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-113">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="5bfb9-114">在 [商務規則維護]\*\*\*\* 頁面上，選取 [模型]\*\*\*\* 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-114">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="5bfb9-115">從 [實體]\*\*\*\* 清單中選取實體。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-115">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="5bfb9-116">從 [**成員類型**] 清單中，選取成員的類型。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-116">From the **Member Type** list, select a type of member.</span></span>  
  
6.  <span data-ttu-id="5bfb9-117">從 [屬性]\*\*\*\* 清單中，選取屬性或保留預設值 [全部]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-117">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="5bfb9-118">在方格中，按兩下商務規則的資料列中的 [**名稱**] 欄位。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-118">In the grid, in the row for the business rule, double-click the **Name** field.</span></span>  
  
8.  <span data-ttu-id="5bfb9-119">輸入商務規則的名稱。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-119">Type a name for the business rule.</span></span>  
  
9. <span data-ttu-id="5bfb9-120">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-120">Press ENTER.</span></span>  
  
10. <span data-ttu-id="5bfb9-121">按一下 [發行商務規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-121">Click **Publish business rules**.</span></span>  
  
11. <span data-ttu-id="5bfb9-122">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-122">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="5bfb9-123">規則狀態會變更為 [作用中]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5bfb9-123">The rule's status changes to **Active**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bfb9-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bfb9-124">See Also</span></span>  
 [<span data-ttu-id="5bfb9-125">商務規則 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="5bfb9-125">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
