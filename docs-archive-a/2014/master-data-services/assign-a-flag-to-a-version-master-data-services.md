---
title: 將旗標指派給版本 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- version flags [Master Data Services], assigning flags
- versions [Master Data Services], assigning flags
ms.assetid: 6629ec7e-32e7-4a1e-8b31-eb43c5923766
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2de0d0d8d8ea96814e13b9123fe4fcd4782d6bef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606394"
---
# <a name="assign-a-flag-to-a-version-master-data-services"></a><span data-ttu-id="5be73-102">將旗標指派給版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="5be73-102">Assign a Flag to a Version (Master Data Services)</span></span>
  <span data-ttu-id="5be73-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，將旗標指派給版本，指出使用者或訂閱系統應該使用的版本。</span><span class="sxs-lookup"><span data-stu-id="5be73-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], assign a flag to a version to indicate the version that users or subscribing systems should use.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5be73-104">版本旗標一次只能指派給一個版本。</span><span class="sxs-lookup"><span data-stu-id="5be73-104">Version flags can be assigned to only one version at a time.</span></span> <span data-ttu-id="5be73-105">如果指派的旗標已指派給另一個版本，該旗標會移至選取的版本。</span><span class="sxs-lookup"><span data-stu-id="5be73-105">If you assign a flag that is already assigned to another version, the flag is moved to the version you selected.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5be73-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="5be73-106">Prerequisites</span></span>  
 <span data-ttu-id="5be73-107">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="5be73-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="5be73-108">您必須擁有存取 **[版本管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="5be73-108">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="5be73-109">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="5be73-109">You must be a model administrator.</span></span> <span data-ttu-id="5be73-110">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="5be73-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="5be73-111">您必須已建立要指派的版本旗標。</span><span class="sxs-lookup"><span data-stu-id="5be73-111">You must have created a version flag to assign.</span></span> <span data-ttu-id="5be73-112">如需詳細資訊，請參閱 [建立版本旗標 &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md)(管理員 (Master Data Services))。</span><span class="sxs-lookup"><span data-stu-id="5be73-112">For more information, see [Create a Version Flag &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md).</span></span>  
  
### <a name="to-assign-a-flag-to-a-version"></a><span data-ttu-id="5be73-113">若要將旗標指派給版本</span><span class="sxs-lookup"><span data-stu-id="5be73-113">To assign a flag to a version</span></span>  
  
1.  <span data-ttu-id="5be73-114">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[版本管理]**。</span><span class="sxs-lookup"><span data-stu-id="5be73-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="5be73-115">在 [管理版本]\*\*\*\* 頁面上，於您要指派旗標之版本的資料列，按兩下 [旗標]\*\*\*\* 資料行中的資料格。</span><span class="sxs-lookup"><span data-stu-id="5be73-115">On the **Manage Versions** page, in the row for the version to which you want to assign a flag, double-click the cell in the **Flag** column.</span></span>  
  
3.  <span data-ttu-id="5be73-116">從清單中選取您要指派的旗標。</span><span class="sxs-lookup"><span data-stu-id="5be73-116">From the list, select the flag you want to assign.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5be73-117">如果您要的旗標無法使用，此旗標可能只適用於 [已認可]\*\*\*\* 版本。</span><span class="sxs-lookup"><span data-stu-id="5be73-117">If the flag you want is not available, the flag might be available for **Committed** versions only.</span></span> <span data-ttu-id="5be73-118">若要確認，請移至 [管理版本旗標]\*\*\*\* 頁面並檢視旗標的 [僅限認可的版本]\*\*\*\* 欄位。</span><span class="sxs-lookup"><span data-stu-id="5be73-118">To confirm, go to the **Manage Version Flags** page and view the **Committed Versions Only** field for the flag.</span></span>  
  
4.  <span data-ttu-id="5be73-119">按下 ENTER 鍵儲存變更。</span><span class="sxs-lookup"><span data-stu-id="5be73-119">Press ENTER to save the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5be73-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5be73-120">See Also</span></span>  
 <span data-ttu-id="5be73-121">[建立 &#40;Master Data Services 的版本旗標&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="5be73-121">[Create a Version Flag &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md) </span></span>  
 [<span data-ttu-id="5be73-122">版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="5be73-122">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
  
