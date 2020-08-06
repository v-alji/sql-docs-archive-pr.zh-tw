---
title: 建立版本旗標 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating version flags [Master Data Services]
- version flags [Master Data Services], creating
- versions [Master Data Services], creating flags
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f04c93f8315ccd5b53e07db169783da53afe0156
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597890"
---
# <a name="create-a-version-flag-master-data-services"></a><span data-ttu-id="d9562-102">建立版本旗標 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d9562-102">Create a Version Flag (Master Data Services)</span></span>
  <span data-ttu-id="d9562-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，建立要指派給版本的版本旗標。</span><span class="sxs-lookup"><span data-stu-id="d9562-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a version flag to assign to a version.</span></span> <span data-ttu-id="d9562-104">此旗標可以指出使用者或訂閱系統應該使用的版本。</span><span class="sxs-lookup"><span data-stu-id="d9562-104">The flag can indicate the version that users or subscribing systems should use.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d9562-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="d9562-105">Prerequisites</span></span>  
 <span data-ttu-id="d9562-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="d9562-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d9562-107">您必須擁有存取 **[版本管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="d9562-107">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="d9562-108">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="d9562-108">You must be a model administrator.</span></span> <span data-ttu-id="d9562-109">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d9562-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-version-flag"></a><span data-ttu-id="d9562-110">若要建立版本旗標</span><span class="sxs-lookup"><span data-stu-id="d9562-110">To create a version flag</span></span>  
  
1.  <span data-ttu-id="d9562-111">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[版本管理]**。</span><span class="sxs-lookup"><span data-stu-id="d9562-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="d9562-112">在 **[管理版本]** 頁面上，從功能表列指向 **[管理]** ，然後按一下 **[旗標]**。</span><span class="sxs-lookup"><span data-stu-id="d9562-112">On the **Manage Versions** page, from the menu bar, point to **Manage** and then click **Flags**.</span></span>  
  
3.  <span data-ttu-id="d9562-113">在 **[管理版本旗標]** 頁面上，從 **[模型]** 欄位選取您要建立旗標的模型。</span><span class="sxs-lookup"><span data-stu-id="d9562-113">On the **Manage Version Flags** page, from the **Model** field, select the model for which you want to create a flag.</span></span>  
  
4.  <span data-ttu-id="d9562-114">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="d9562-114">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="d9562-115">在 **[名稱]** 方塊中，輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="d9562-115">In the **Name** box, type a name.</span></span>  
  
6.  <span data-ttu-id="d9562-116">在 **[描述]** 方塊中，輸入描述。</span><span class="sxs-lookup"><span data-stu-id="d9562-116">In the **Description** box, type a description.</span></span>  
  
7.  <span data-ttu-id="d9562-117">在 **[僅限認可的版本]** 欄位中，選取 **[True]** 表示旗標只能指派給狀態為 **[已認可]** 的版本。</span><span class="sxs-lookup"><span data-stu-id="d9562-117">In the **Committed Versions Only** field, select **True** to indicate that the flag can be assigned to versions with a status of **Committed** only.</span></span> <span data-ttu-id="d9562-118">選取 **[False]** 表示旗標可以指派給任何狀態的版本。</span><span class="sxs-lookup"><span data-stu-id="d9562-118">Select **False** to indicate that the flag can be assigned to versions with any status.</span></span>  
  
8.  <span data-ttu-id="d9562-119">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="d9562-119">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d9562-120">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d9562-120">Next Steps</span></span>  
  
-   [<span data-ttu-id="d9562-121">將旗標指派給版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d9562-121">Assign a Flag to a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="d9562-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9562-122">See Also</span></span>  
 <span data-ttu-id="d9562-123">[版本 &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d9562-123">[Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span></span>  
 [<span data-ttu-id="d9562-124">變更版本旗標名稱 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d9562-124">Change a Version Flag Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-version-flag-name-master-data-services.md)  
  
  
