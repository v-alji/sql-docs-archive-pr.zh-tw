---
title: 變更屬性名稱 (Master Data Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], changing name
ms.assetid: d348f238-f59d-41c7-ad20-3ccd55bfd9e5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: abbe5f666daed42b25b46f02e954343b57446145
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703058"
---
# <a name="change-an-attribute-name-master-data-services"></a><span data-ttu-id="1ae5e-102">變更屬性名稱 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1ae5e-102">Change an Attribute Name (Master Data Services)</span></span>
  <span data-ttu-id="1ae5e-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以變更屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="1ae5e-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can change the name of an attribute.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1ae5e-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="1ae5e-104">Prerequisites</span></span>  
 <span data-ttu-id="1ae5e-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="1ae5e-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="1ae5e-106">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="1ae5e-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="1ae5e-107">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="1ae5e-107">You must be a model administrator.</span></span> <span data-ttu-id="1ae5e-108">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae5e-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-change-an-attribute-name"></a><span data-ttu-id="1ae5e-109">若要變更屬性名稱</span><span class="sxs-lookup"><span data-stu-id="1ae5e-109">To change an attribute name</span></span>  
  
1.  <span data-ttu-id="1ae5e-110">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="1ae5e-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="1ae5e-111">在 **[模型檢視]** 頁面上，從功能表列指向 **[管理]** ，然後按一下 **[實體]**。</span><span class="sxs-lookup"><span data-stu-id="1ae5e-111">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="1ae5e-112">在 **[實體維護]** 頁面上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="1ae5e-112">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="1ae5e-113">按一下實體的資料列，該實體包含您想要變更名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="1ae5e-113">Click the row for the entity that contains the attribute with the name you want to change.</span></span>  
  
5.  <span data-ttu-id="1ae5e-114">按一下 **[編輯選取的實體]**。</span><span class="sxs-lookup"><span data-stu-id="1ae5e-114">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="1ae5e-115">在 [**編輯實體**] 頁面上，按一下您想要變更名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="1ae5e-115">On the **Edit Entity** page, click the attribute with the name you want to change.</span></span>  
  
7.  <span data-ttu-id="1ae5e-116">按一下 [**編輯選取的屬性**]。</span><span class="sxs-lookup"><span data-stu-id="1ae5e-116">Click **Edit selected attribute**.</span></span>  
  
8.  <span data-ttu-id="1ae5e-117">在 [名稱]\*\*\*\* 方塊中，輸入屬性的更新名稱。</span><span class="sxs-lookup"><span data-stu-id="1ae5e-117">In the **Name** box, type the updated name of the attribute.</span></span> <span data-ttu-id="1ae5e-118">如需不應當做屬性名稱使用的字組清單，請參閱[保留字 &#40;Master Data Services&#41;](reserved-words-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae5e-118">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="1ae5e-119">按一下 **[儲存屬性]**。</span><span class="sxs-lookup"><span data-stu-id="1ae5e-119">Click **Save attribute**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ae5e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ae5e-120">See Also</span></span>  
 <span data-ttu-id="1ae5e-121">[建立 &#40;Master Data Services&#41;的文字屬性](create-a-text-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="1ae5e-121">[Create a Text Attribute &#40;Master Data Services&#41;](create-a-text-attribute-master-data-services.md) </span></span>  
 <span data-ttu-id="1ae5e-122">[刪除屬性 &#40;Master Data Services&#41;](delete-an-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="1ae5e-122">[Delete an Attribute &#40;Master Data Services&#41;](delete-an-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="1ae5e-123">屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1ae5e-123">Attributes &#40;Master Data Services&#41;</span></span>](attributes-master-data-services.md)  
  
  
