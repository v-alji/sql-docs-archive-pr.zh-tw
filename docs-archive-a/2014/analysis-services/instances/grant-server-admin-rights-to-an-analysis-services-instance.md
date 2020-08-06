---
title: 授與伺服器管理員許可權 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- administrator rights [Analysis Services]
- server-wide administrative permissions [Analysis Services]
ms.assetid: 20d1234b-a457-4a84-ae08-fe356870c466
author: minewiskan
ms.author: owend
ms.openlocfilehash: 822227ae89f4f219a055bcc0d6d6b0a228f7964b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700474"
---
# <a name="grant-server-administrator-permissions-analysis-services"></a><span data-ttu-id="02f25-102">授與伺服器管理員權限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="02f25-102">Grant Server Administrator Permissions (Analysis Services)</span></span>
  <span data-ttu-id="02f25-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體內伺服器管理員角色的成員對於該執行個體中的所有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件和資料具有不受限制的存取權。</span><span class="sxs-lookup"><span data-stu-id="02f25-103">Members of the Server administrator role within an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] have unrestricted access to all [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects and data in that instance.</span></span> <span data-ttu-id="02f25-104">使用者必須是伺服器管理員角色的成員，才能執行整個伺服器範圍的工作，例如建立資料庫或處理資料庫、修改伺服器屬性或啟動追蹤 (但處理事件不算)。</span><span class="sxs-lookup"><span data-stu-id="02f25-104">A user must be a member of the Server administrator role to perform any server-wide task, such as creating or processing a database, modifying server properties, or launching a trace (other than for processing events).</span></span>

 <span data-ttu-id="02f25-105">在安裝 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 時，會建立角色成員資格。</span><span class="sxs-lookup"><span data-stu-id="02f25-105">Role membership is established when [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is installed.</span></span> <span data-ttu-id="02f25-106">在提供伺服器時，執行安裝程式的使用者可將本身加入角色或加入其他使用者。</span><span class="sxs-lookup"><span data-stu-id="02f25-106">The user running the Setup program can add him or herself to the role, or add another user, when provisioning the server.</span></span> <span data-ttu-id="02f25-107">您可以使用下列程序，以後續安裝工作的形式修改角色成員資格。</span><span class="sxs-lookup"><span data-stu-id="02f25-107">You can modify role membership as a post-installation task using the following procedure.</span></span>

## <a name="modify-server-role-membership"></a><span data-ttu-id="02f25-108">修改伺服器角色成員資格</span><span class="sxs-lookup"><span data-stu-id="02f25-108">Modify Server Role Membership</span></span>

1.  <span data-ttu-id="02f25-109">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的執行個體，然後以滑鼠右鍵按一下物件總管中的執行個體名稱，再按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="02f25-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], and then right-click the instance name in Object Explorer and then click **Properties**.</span></span>

2.  <span data-ttu-id="02f25-110">按一下 **[選取頁面]** 窗格中的 **[安全性]** ，然後按一下頁面底部的 **[加入]** ，以將一個或多個 Windows 使用者或群組加入至伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="02f25-110">Click **Security** in the **Select a Page** pane, and then click **Add** at the bottom of the page to add one or more Windows users or groups to the server role.</span></span>

     <span data-ttu-id="02f25-111">![Management Studio 中的 [加入使用者] 對話方塊](../media/ssas-serveradminadd.png "Management Studio 中的 [加入使用者] 對話方塊")</span><span class="sxs-lookup"><span data-stu-id="02f25-111">![Add users dialog box in management studio](../media/ssas-serveradminadd.png "Add users dialog box in management studio")</span></span>

 <span data-ttu-id="02f25-112">在安裝期間，SQL Server 安裝程式會要求您至少指定一個使用者帳戶做為 Analysis Services 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="02f25-112">At installation time, SQL Server Setup requires that you specify at least one user account as the Analysis Services system administrator.</span></span>

 <span data-ttu-id="02f25-113">依預設，也會將 Analysis Server 的管理權限授與本機 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="02f25-113">By default, members of the local Administrators group are also granted administrative rights in Analysis Server.</span></span> <span data-ttu-id="02f25-114">雖然本機群組未明確授與 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器管理員角色的成員資格，但本機管理員可以建立資料庫，新增使用者和權限，以及執行系統管理員可執行的其他工作。</span><span class="sxs-lookup"><span data-stu-id="02f25-114">Although the local group is not explicitly granted membership in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server administrator role, local administrators can create databases, add users and permissions, and perform any other task allowed to system administrators.</span></span> <span data-ttu-id="02f25-115">這個行為是可設定的，</span><span class="sxs-lookup"><span data-stu-id="02f25-115">This behavior is configurable.</span></span> <span data-ttu-id="02f25-116">它是由 `BuiltinAdminsAreServerAdmins` 伺服器屬性所決定，預設會設定為**true** 。</span><span class="sxs-lookup"><span data-stu-id="02f25-116">It is determined by the `BuiltinAdminsAreServerAdmins` server property, which is set to **true** by default.</span></span> <span data-ttu-id="02f25-117">您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中變更這個屬性。</span><span class="sxs-lookup"><span data-stu-id="02f25-117">You can change this property in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="02f25-118">如需詳細資訊，請參閱 [Security Properties](../server-properties/security-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="02f25-118">For more information, see [Security Properties](../server-properties/security-properties.md).</span></span>

 <span data-ttu-id="02f25-119">您也可以使用分析管理物件 (AMO) 來管理伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="02f25-119">You can also manage server roles by using Analysis Management Objects (AMO).</span></span> <span data-ttu-id="02f25-120">如需詳細資訊，請參閱[使用分析管理物件 &#40;AMO&#41; 來開發](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)。</span><span class="sxs-lookup"><span data-stu-id="02f25-120">For more information, see [Developing with Analysis Management Objects &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo).</span></span>

## <a name="see-also"></a><span data-ttu-id="02f25-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02f25-121">See Also</span></span>
 <span data-ttu-id="02f25-122">[&#40;Analysis Services&#41;安全性角色來授權物件和作業的存取權](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md) [&#40;Analysis Services 多維度資料&#41;](../multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="02f25-122">[Authorizing access to objects and operations &#40;Analysis Services&#41;](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md) [Security Roles  &#40;Analysis Services - Multidimensional Data&#41;](../multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)</span></span>


