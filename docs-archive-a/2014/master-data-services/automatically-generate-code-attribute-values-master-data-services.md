---
title: 自動產生 Code 屬性值 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 19b354ee-2906-4cc7-ba2f-32b4543bddcf
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6c442f37ffe322985ba55b29b2c4cd539b8a3e05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599049"
---
# <a name="automatically-generate-code-attribute-values-master-data-services"></a><span data-ttu-id="40b0a-102">自動產生 Code 屬性值 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="40b0a-102">Automatically Generate Code Attribute Values (Master Data Services)</span></span>
  <span data-ttu-id="40b0a-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中，當您希望每次建立新成員時，自動將整數指派給 Code 值，請自動為實體的 Code 屬性產生值。</span><span class="sxs-lookup"><span data-stu-id="40b0a-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], automatically generate values for an entity's Code attribute when you want an integer to be automatically assigned to the Code value each time a new member is created.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="40b0a-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="40b0a-104">Prerequisites</span></span>  
 <span data-ttu-id="40b0a-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="40b0a-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="40b0a-106">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="40b0a-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="40b0a-107">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="40b0a-107">You must be a model administrator.</span></span> <span data-ttu-id="40b0a-108">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="40b0a-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="40b0a-109">實體必須存在。</span><span class="sxs-lookup"><span data-stu-id="40b0a-109">The entity must exist.</span></span> <span data-ttu-id="40b0a-110">如需詳細資訊，請參閱[建立實體 &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="40b0a-110">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-automatically-generate-code-values"></a><span data-ttu-id="40b0a-111">若要自動產生值字碼</span><span class="sxs-lookup"><span data-stu-id="40b0a-111">To automatically generate Code values</span></span>  
  
1.  <span data-ttu-id="40b0a-112">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="40b0a-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="40b0a-113">在 [**模型瀏覽器**] 頁面上，從功能表列指向 [**管理**]，然後按一下 [**實體**]。</span><span class="sxs-lookup"><span data-stu-id="40b0a-113">On the **Model Explorer** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="40b0a-114">在 **[實體維護]** 頁面上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="40b0a-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="40b0a-115">選取要產生其字碼之實體的資料列。</span><span class="sxs-lookup"><span data-stu-id="40b0a-115">Select the row for the entity that you want to generate codes for.</span></span>  
  
5.  <span data-ttu-id="40b0a-116">按一下 **[編輯選取的實體]**。</span><span class="sxs-lookup"><span data-stu-id="40b0a-116">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="40b0a-117">選取 **[自動建立字碼值]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="40b0a-117">Select the **Create Code values automatically** check box.</span></span>  
  
7.  <span data-ttu-id="40b0a-118">在 **[開始]** 方塊中，輸入開始遞增的數字。</span><span class="sxs-lookup"><span data-stu-id="40b0a-118">In the **Start with** box, type a number to begin incrementing.</span></span> <span data-ttu-id="40b0a-119">如果成員已存在，則將根據最大的現有值設定 Code。</span><span class="sxs-lookup"><span data-stu-id="40b0a-119">If members already exist, the Code will be set based on the highest existing value.</span></span> <span data-ttu-id="40b0a-120">例如，若最大的現有 Code 值為 299，則下一個成員的 Code 值將設為 300。</span><span class="sxs-lookup"><span data-stu-id="40b0a-120">For example, if the highest existing Code value is 299, the next member's Code value will be set to 300.</span></span>  
  
8.  <span data-ttu-id="40b0a-121">按一下 [**儲存實體**]。</span><span class="sxs-lookup"><span data-stu-id="40b0a-121">Click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40b0a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40b0a-122">See Also</span></span>  
 <span data-ttu-id="40b0a-123">[自動建立程式碼 &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="40b0a-123">[Automatic Code Creation &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md) </span></span>  
 [<span data-ttu-id="40b0a-124">自動產生 Code 以外的屬性值 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="40b0a-124">Automatically Generate Attribute Values Other Than Code &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)  
  
  
