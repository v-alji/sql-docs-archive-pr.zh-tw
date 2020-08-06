---
title: 建立分葉成員 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- leaf members [Master Data Services], creating
- creating leaf members [Master Data Services]
- members [Master Data Services], creating leaf members
ms.assetid: 0499d3b3-d508-4d43-a740-19cf53ade9f1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fe0245dd30019e1cb9112754bd8b8eeafed93aa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584624"
---
# <a name="create-a-leaf-member-master-data-services"></a><span data-ttu-id="941a7-102">建立分葉成員 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="941a7-102">Create a Leaf Member (Master Data Services)</span></span>
  <span data-ttu-id="941a7-103">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]當您想要在系統中加入主要資料，而不是使用臨時表或匯入資料時，可以在中建立分葉成員 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="941a7-103">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], create a leaf member when you want to add master data to your system and are not using staging tables or the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] to import data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="941a7-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="941a7-104">Prerequisites</span></span>  
 <span data-ttu-id="941a7-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="941a7-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="941a7-106">您必須擁有存取 [ **Explorer** ] 功能區域的許可權。</span><span class="sxs-lookup"><span data-stu-id="941a7-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="941a7-107">針對要加入成員之實體的分葉模型物件，您至少必須擁有 [**更新**] 許可權。</span><span class="sxs-lookup"><span data-stu-id="941a7-107">You must have a minimum of **Update** permission to the leaf model object for the entity you are adding a member to.</span></span>  
  
### <a name="to-create-a-leaf-member"></a><span data-ttu-id="941a7-108">若要建立分葉成員</span><span class="sxs-lookup"><span data-stu-id="941a7-108">To create a leaf member</span></span>  
  
1.  <span data-ttu-id="941a7-109">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 首頁上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="941a7-109">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="941a7-110">如果您是使用者，請從 [版本]\*\*\*\* 清單中選取開啟的版本。</span><span class="sxs-lookup"><span data-stu-id="941a7-110">If you are a user, select an open version from the **Version** list.</span></span> <span data-ttu-id="941a7-111">如果您是系統管理員，請從 [版本]\*\*\*\* 清單中選取狀態為開啟或鎖定的版本。</span><span class="sxs-lookup"><span data-stu-id="941a7-111">If you are an administrator, select a version with open or locked status from the **Version** list.</span></span>  
  
3.  <span data-ttu-id="941a7-112">按一下 **[總管]**。</span><span class="sxs-lookup"><span data-stu-id="941a7-112">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="941a7-113">從功能表列指向 [實體]\*\*\*\*，然後按一下要新增成員的實體名稱。</span><span class="sxs-lookup"><span data-stu-id="941a7-113">From the menu bar, point to **Entities** and click the name of the entity you want to add a member to.</span></span>  
  
5.  <span data-ttu-id="941a7-114">按一下 [**新增成員**]。</span><span class="sxs-lookup"><span data-stu-id="941a7-114">Click **Add member**.</span></span>  
  
6.  <span data-ttu-id="941a7-115">填妥 [詳細資料]\*\*\*\* 窗格中的欄位。</span><span class="sxs-lookup"><span data-stu-id="941a7-115">In the **Details** pane, complete the fields.</span></span>  
  
7.  <span data-ttu-id="941a7-116">選擇性。</span><span class="sxs-lookup"><span data-stu-id="941a7-116">Optional.</span></span> <span data-ttu-id="941a7-117">在 **[註解]** 方塊中，輸入有關加入此成員之原因的註解。</span><span class="sxs-lookup"><span data-stu-id="941a7-117">In the **Annotations** box, type a comment about why the member was added.</span></span> <span data-ttu-id="941a7-118">可存取成員的所有使用者都可以檢視註解。</span><span class="sxs-lookup"><span data-stu-id="941a7-118">All users who have access to the member can view the annotation.</span></span>  
  
8.  <span data-ttu-id="941a7-119">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="941a7-119">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="941a7-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="941a7-120">See Also</span></span>  
 <span data-ttu-id="941a7-121">[使用暫存進程在 Master Data Services 中載入或更新成員](add-update-and-delete-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="941a7-121">[Load or Update Members in Master Data Services by Using the Staging Process](add-update-and-delete-data-master-data-services.md) </span></span>  
 <span data-ttu-id="941a7-122">[建立合併成員 &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="941a7-122">[Create a Consolidated Member &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md) </span></span>  
 [<span data-ttu-id="941a7-123">成員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="941a7-123">Members &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/members-master-data-services.md)  
  
  
