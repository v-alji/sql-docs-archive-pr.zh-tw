---
title: 刪除屬性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], deleting
- deleting attributes [Master Data Services]
ms.assetid: ec3e66f7-0e35-43d7-a80d-64899948ebfe
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 96db56dac9356b1131e722fc7f6b779c93305bb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687015"
---
# <a name="delete-an-attribute-master-data-services"></a><span data-ttu-id="30f84-102">刪除屬性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="30f84-102">Delete an Attribute (Master Data Services)</span></span>
  <span data-ttu-id="30f84-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，如果您想要永久刪除某個屬性以及所有關聯的屬性值，請刪除此屬性。</span><span class="sxs-lookup"><span data-stu-id="30f84-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete an attribute when you want to permanently delete the attribute and all associated attribute values.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="30f84-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="30f84-104">Prerequisites</span></span>  
 <span data-ttu-id="30f84-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="30f84-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="30f84-106">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="30f84-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="30f84-107">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="30f84-107">You must be a model administrator.</span></span> <span data-ttu-id="30f84-108">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="30f84-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-an-attribute"></a><span data-ttu-id="30f84-109">若要刪除屬性</span><span class="sxs-lookup"><span data-stu-id="30f84-109">To delete an attribute</span></span>  
  
1.  <span data-ttu-id="30f84-110">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="30f84-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="30f84-111">在 **[模型檢視]** 頁面上，從功能表列指向 **[管理]** ，然後按一下 **[實體]**。</span><span class="sxs-lookup"><span data-stu-id="30f84-111">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="30f84-112">在 **[實體維護]** 頁面上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="30f84-112">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="30f84-113">針對包含要刪除之屬性的實體選取資料列。</span><span class="sxs-lookup"><span data-stu-id="30f84-113">Select the row for the entity that contains the attribute you want to delete.</span></span>  
  
5.  <span data-ttu-id="30f84-114">按一下 **[編輯選取的實體]**。</span><span class="sxs-lookup"><span data-stu-id="30f84-114">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="30f84-115">在 [**編輯實體**] 頁面上，按一下您想要刪除的屬性。</span><span class="sxs-lookup"><span data-stu-id="30f84-115">On the **Edit Entity** page, click the attribute you want to delete.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="30f84-116">您不能刪除 Name 或 Code 屬性。</span><span class="sxs-lookup"><span data-stu-id="30f84-116">You cannot delete the Name or Code attributes.</span></span>  
  
7.  <span data-ttu-id="30f84-117">按一下 [**刪除選取的屬性**]。</span><span class="sxs-lookup"><span data-stu-id="30f84-117">Click **Delete selected attribute**.</span></span>  
  
8.  <span data-ttu-id="30f84-118">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="30f84-118">In the confirmation dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="30f84-119">在另一個確認對話方塊中按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30f84-119">In the additional confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30f84-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30f84-120">See Also</span></span>  
 <span data-ttu-id="30f84-121">[Master Data Services &#40;的屬性&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="30f84-121">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="30f84-122">[以網域為基礎的屬性 &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="30f84-122">[Domain-Based Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="30f84-123">[建立 &#40;Master Data Services&#41;的文字屬性](../../2014/master-data-services/create-a-text-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="30f84-123">[Create a Text Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="30f84-124">建立網域屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="30f84-124">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  
