---
title: 授與處理資料庫許可權 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 69ba952e-09ae-49a9-9297-00e32e8e89a8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6ada30e3fb509bd1ffd210485ce0e34b7bf86fb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584788"
---
# <a name="granting-process-database-permissions"></a><span data-ttu-id="5d02e-102">授與處理資料庫權限</span><span class="sxs-lookup"><span data-stu-id="5d02e-102">Granting Process Database Permissions</span></span>
  <span data-ttu-id="5d02e-103">當您安裝 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]的執行個體之後，該執行個體中 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 伺服器管理員角色的所有成員都會具有伺服器範圍權限，可在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]執行個體內執行任何工作。</span><span class="sxs-lookup"><span data-stu-id="5d02e-103">After you install an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], all members of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server administrator role in that instance have server-wide permissions to perform any task within the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="5d02e-104">依預設，其他使用者都無權管理或檢視 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]執行個體中的任何物件。</span><span class="sxs-lookup"><span data-stu-id="5d02e-104">By default, no other users have any permission to administer or view any objects in the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>

 <span data-ttu-id="5d02e-105">伺服器管理員角色的成員可在整個伺服器範圍，讓他們成為角色的成員，以授與使用者管理存取權。</span><span class="sxs-lookup"><span data-stu-id="5d02e-105">A member of the server administrator role can grant users administrative access on a server-wide basis by making them members of the role.</span></span> <span data-ttu-id="5d02e-106">伺服器管理員角色的成員也可以在資料庫層級授與使用者有限或完整的管理權或存取權，藉此授與使用者比較有限的存取權。</span><span class="sxs-lookup"><span data-stu-id="5d02e-106">A member of the server administrator role can also grant users access on a more limited basis by granting them limited or complete administrative or access permissions at the database level.</span></span> <span data-ttu-id="5d02e-107">有限的管理員權限包括在資料庫、Cube 或維度層級的處理或讀取定義權限。</span><span class="sxs-lookup"><span data-stu-id="5d02e-107">Limited administrative permissions include process or read definition permissions at the database, cube, or dimension level.</span></span>

 <span data-ttu-id="5d02e-108">在本主題的工作中，您要定義處理資料庫物件安全性角色，這個角色會授權讓角色成員處理所有的資料庫物件，但不讓他們有權檢視資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="5d02e-108">In the tasks in this topic, you will define a Process Database Objects security role that grants members of the role permission to process all database objects, but no permission to view data within the database.</span></span>

## <a name="defining-a-process-database-objects-security-role"></a><span data-ttu-id="5d02e-109">定義處理資料庫物件安全性角色</span><span class="sxs-lookup"><span data-stu-id="5d02e-109">Defining a Process Database Objects Security Role</span></span>

1.  <span data-ttu-id="5d02e-110">在方案總管中，以滑鼠右鍵按一下 [角色]\*\*\*\*，然後按一下 [新增角色]\*\*\*\* 以開啟 [角色設計師]。</span><span class="sxs-lookup"><span data-stu-id="5d02e-110">In Solution Explorer, right-click **Roles** and then click **New Role** to open the Role Designer.</span></span>

2.  <span data-ttu-id="5d02e-111">按一下 [處理資料庫]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5d02e-111">Click the **Process database** check box.</span></span>

3.  <span data-ttu-id="5d02e-112">在 [屬性視窗中，將這個新角色的 [**名稱**] 屬性變更為 `Process Database Objects Role` 。</span><span class="sxs-lookup"><span data-stu-id="5d02e-112">In the Properties window, change the **Name** property for this new role to `Process Database Objects Role`.</span></span>

     <span data-ttu-id="5d02e-113">![角色設計師](../../2014/tutorials/media/l10-security-1.png "角色設計師")</span><span class="sxs-lookup"><span data-stu-id="5d02e-113">![Role Designer](../../2014/tutorials/media/l10-security-1.png "Role Designer")</span></span>

4.  <span data-ttu-id="5d02e-114">切換到 [角色設計師] 的 [成員資格]\*\*\*\* 索引標籤，然後按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5d02e-114">Switch to the **Membership** tab of Role Designer and click **Add**.</span></span>

5.  <span data-ttu-id="5d02e-115">輸入 Windows 網域使用者或群組的帳戶，他們將成為這個角色的成員。</span><span class="sxs-lookup"><span data-stu-id="5d02e-115">Enter the accounts of the Windows domain users or groups who will be members of this role.</span></span> <span data-ttu-id="5d02e-116">按一下 [檢查名稱]\*\*\*\* 來確認帳戶資訊，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5d02e-116">Click **Check Names** to verify the account information, and then click **OK**.</span></span>

6.  <span data-ttu-id="5d02e-117">切換到 [角色設計師] 的 [Cube]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5d02e-117">Switch to the **Cubes** tab of Role Designer.</span></span>

     <span data-ttu-id="5d02e-118">請注意，雖然這個角色的成員有權處理這個資料庫，但是無權存取 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 中的資料，也沒有本機 Cube/鑽研存取權，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="5d02e-118">Notice that members of this role have permissions to process this database, but have no permission to access the data in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube and have no local cube/drillthrough access, as shown in the following image.</span></span>

     <span data-ttu-id="5d02e-119">![角色設計師的 Cube 索引標籤](../../2014/tutorials/media/l10-security-2.png "角色設計師的 Cube 索引標籤")</span><span class="sxs-lookup"><span data-stu-id="5d02e-119">![Cubes tab of Role Designer](../../2014/tutorials/media/l10-security-2.png "Cubes tab of Role Designer")</span></span>

7.  <span data-ttu-id="5d02e-120">切換到 [角色設計師] 的 [維度]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5d02e-120">Switch to the **Dimensions** tab of Role Designer.</span></span>

     <span data-ttu-id="5d02e-121">請注意，這個角色的成員有權處理這個資料庫中的所有維度物件，而且依預設，也有權讀取 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程資料庫中的每一個維度物件。</span><span class="sxs-lookup"><span data-stu-id="5d02e-121">Notice that members of this role have permissions to process all dimension objects in this database, and, by default, have read permissions to access each dimension object in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial database.</span></span>

8.  <span data-ttu-id="5d02e-122">在 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5d02e-122">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

     <span data-ttu-id="5d02e-123">現在您已經順利定義和部署處理資料庫物件安全性角色了。</span><span class="sxs-lookup"><span data-stu-id="5d02e-123">You have now successfully defined and deployed the Process Database Objects security role.</span></span> <span data-ttu-id="5d02e-124">當您把 Cube 部署到實際環境之後，部署 Cube 的管理員就可以根據需要，把使用者加入這個角色中，將處理責任委託給特定的使用者。</span><span class="sxs-lookup"><span data-stu-id="5d02e-124">After a cube is deployed to the production environment, the administrators of the deployed cube can add users to this role as required to delegate processing responsibilities to specific users.</span></span>

> [!NOTE]
>  <span data-ttu-id="5d02e-125">您可以下載並安裝範例，取得完成第 10 課的專案。</span><span class="sxs-lookup"><span data-stu-id="5d02e-125">A completed project for Lesson 10 is available by downloading and installing the samples.</span></span> <span data-ttu-id="5d02e-126">如需詳細資訊，請參閱[安裝 Analysis Services 多維度模型化教學課程的範例資料和專案](install-sample-data-and-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="5d02e-126">For more information, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5d02e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d02e-127">See Also</span></span>
 [<span data-ttu-id="5d02e-128">角色與權限 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="5d02e-128">Roles and Permissions &#40;Analysis Services&#41;</span></span>](multidimensional-models/roles-and-permissions-analysis-services.md)


