---
title: 重新啟用成員或集合 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], reactivating
- consolidated members [Master Data Services], reactivating
- reactivating members [Master Data Services]
- members [Master Data Services], reactivating
- reactivating collections [Master Data Services]
- leaf members [Master Data Services], reactivating
ms.assetid: bb4884c0-3658-4763-92d1-636804278b1c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c449a5a277128bbca6ae24e848bcf12cb0881968
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598495"
---
# <a name="reactivate-a-member-or-collection-master-data-services"></a><span data-ttu-id="28d3d-102">重新啟用成員或集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="28d3d-102">Reactivate a Member or Collection (Master Data Services)</span></span>
  <span data-ttu-id="28d3d-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以重新啟用以下成員：</span><span class="sxs-lookup"><span data-stu-id="28d3d-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can reactivate a member that was either:</span></span>  
  
-   <span data-ttu-id="28d3d-104">已透過暫存處理序停用。</span><span class="sxs-lookup"><span data-stu-id="28d3d-104">Deactivated by the staging process.</span></span>  
  
-   <span data-ttu-id="28d3d-105">已在 MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]中予以刪除。</span><span class="sxs-lookup"><span data-stu-id="28d3d-105">Deleted in the MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
-   <span data-ttu-id="28d3d-106">已在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式中予以刪除。</span><span class="sxs-lookup"><span data-stu-id="28d3d-106">Deleted in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
 <span data-ttu-id="28d3d-107">當您重新啟用成員時，即會還原成員在階層和集合中的屬性及其成員資格。</span><span class="sxs-lookup"><span data-stu-id="28d3d-107">When you reactivate a member, its attributes and its membership in hierarchies and collections are restored.</span></span>  
  
 <span data-ttu-id="28d3d-108">您也可以重新啟用集合。</span><span class="sxs-lookup"><span data-stu-id="28d3d-108">You can also reactivate collections.</span></span> <span data-ttu-id="28d3d-109">當您這麼做時，會還原集合的屬性以及屬於該集合的成員。</span><span class="sxs-lookup"><span data-stu-id="28d3d-109">When you do, the collection's attributes and the members that belong to the collection are restored.</span></span>  
  
 <span data-ttu-id="28d3d-110">重新啟用集合或成員時，會還原先前所有的交易。</span><span class="sxs-lookup"><span data-stu-id="28d3d-110">When either a collection or member is reactivated, all previous transactions are restored.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="28d3d-111">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="28d3d-111">Prerequisites</span></span>  
 <span data-ttu-id="28d3d-112">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="28d3d-112">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="28d3d-113">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 中，您必須具有 [版本管理]\*\*\*\* 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="28d3d-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], you must have permission to the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="28d3d-114">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="28d3d-114">You must be a model administrator.</span></span> <span data-ttu-id="28d3d-115">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="28d3d-115">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-reactivate-a-member-or-collection"></a><span data-ttu-id="28d3d-116">若要重新啟用成員或集合</span><span class="sxs-lookup"><span data-stu-id="28d3d-116">To reactivate a member or collection</span></span>  
  
1.  <span data-ttu-id="28d3d-117">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 首頁上，按一下 [版本管理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="28d3d-117">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="28d3d-118">在功能表列上，按一下 [交易]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="28d3d-118">On the menu bar, click **Transactions**.</span></span>  
  
3.  <span data-ttu-id="28d3d-119">在 [交易]\*\*\*\* 頁面上，選取 [模型]\*\*\*\* 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="28d3d-119">On the **Transactions** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="28d3d-120">從 **[版本]** 清單中選取版本。</span><span class="sxs-lookup"><span data-stu-id="28d3d-120">From the **Version** list, select a version.</span></span>  
  
5.  <span data-ttu-id="28d3d-121">在 [交易]\*\*\*\* 窗格中，按一下您要重新啟用之成員或集合的資料列。</span><span class="sxs-lookup"><span data-stu-id="28d3d-121">In the **Transactions** pane, click the row for the member or collection you want to reactivate.</span></span> <span data-ttu-id="28d3d-122">此資料列應該在 [先前的值]\*\*\*\* 資料行中顯示 [Active]\*\*\*\*，並在 [新值]\*\*\*\* 資料行中顯示 [De-Activated]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="28d3d-122">This row should have **Active** displayed in the **Prior Value** column and **De-Activated** in the **New Value** column.</span></span>  
  
6.  <span data-ttu-id="28d3d-123">按一下 [反轉交易]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="28d3d-123">Click **Reverse Transaction**.</span></span>  
  
7.  <span data-ttu-id="28d3d-124">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="28d3d-124">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="28d3d-125">即會加入新交易，在 [新值]\*\*\*\* 資料行中顯示 [Active]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="28d3d-125">A new transaction is added, showing **Active** in the **New Value** column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28d3d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28d3d-126">See Also</span></span>  
 <span data-ttu-id="28d3d-127">[使用暫存進程停用或刪除成員 &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="28d3d-127">[Deactivate or Delete Members by Using the Staging Process &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md) </span></span>  
 <span data-ttu-id="28d3d-128">[&#40;Master Data Services 刪除成員或集合&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="28d3d-128">[Delete a Member or Collection &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md) </span></span>  
 <span data-ttu-id="28d3d-129">[成員 &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="28d3d-129">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 [<span data-ttu-id="28d3d-130">集合 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="28d3d-130">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)  
  
  
