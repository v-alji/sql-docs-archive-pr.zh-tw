---
title: 套件角色對話方塊 UI 參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.packageroles.f1
helpviewer_keywords:
- Package Roles dialog box
ms.assetid: 63f13416-c0aa-4480-a336-ef1e6e31a860
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 389b29ddee5674af7ecd106f4f82d61bbb3a0f36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703178"
---
# <a name="package-roles-dialog-box-ui-reference"></a><span data-ttu-id="1f399-102">封裝角色對話方塊 UI 參考</span><span class="sxs-lookup"><span data-stu-id="1f399-102">Package Roles Dialog Box UI Reference</span></span>
  <span data-ttu-id="1f399-103">使用 [封裝角色]  對話方塊 (可以在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中使用)，即可指定擁有封裝之讀取權限的資料庫層級角色以及擁有封裝之寫入權限的資料庫層級角色。</span><span class="sxs-lookup"><span data-stu-id="1f399-103">Use the **Package Roles** dialog box, available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], to specify the database-level roles that have read access to the package and the database-level roles that have write access to the package.</span></span> <span data-ttu-id="1f399-104">資料庫層級角色僅適用於儲存在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **msdb** 資料庫中的套件。</span><span class="sxs-lookup"><span data-stu-id="1f399-104">Database-level roles apply only to packages that are stored in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **msdb** database.</span></span>  
  
 <span data-ttu-id="1f399-105">若要深入了解 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 資料庫層級角色及其權限，請參閱 [Integration Services 角色 &#40;SSIS 服務&#41;](security/integration-services-roles-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="1f399-105">To learn more about the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] database-level roles and their permissions, see [Integration Services Roles &#40;SSIS Service&#41;](security/integration-services-roles-ssis-service.md).</span></span>  
  
 <span data-ttu-id="1f399-106">對話方塊中所列出的角色是 **msdb** 系統資料庫的目前資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="1f399-106">The roles listed in the dialog box are the current database roles of the **msdb** system database.</span></span> <span data-ttu-id="1f399-107">如果沒有選取角色，則會套用預設 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 角色。</span><span class="sxs-lookup"><span data-stu-id="1f399-107">If no roles are selected, the default [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] roles apply.</span></span> <span data-ttu-id="1f399-108">依預設，讀取者角色包含 **db_ssisadmin**、 **db_ssisoperator**和建立封裝的使用者。</span><span class="sxs-lookup"><span data-stu-id="1f399-108">By default, the reader role includes **db_ssisadmin**, **db_ssisoperator**, and the user who created the package.</span></span> <span data-ttu-id="1f399-109">上述其中一個角色之成員或是建立封裝的使用者可以列舉、檢視、匯出和執行封裝。</span><span class="sxs-lookup"><span data-stu-id="1f399-109">A user who is a member of one of these roles or created the packages can enumerate, view, export, and run packages.</span></span> <span data-ttu-id="1f399-110">依預設，寫入者角色包含 **db_ssisadmin** 以及建立封裝的使用者。</span><span class="sxs-lookup"><span data-stu-id="1f399-110">By default, the writer role includes **db_ssisadmin** and the user who created the package.</span></span> <span data-ttu-id="1f399-111">這個角色的成員使用者以及建立封裝的使用者，可以匯入、刪除和變更封裝。</span><span class="sxs-lookup"><span data-stu-id="1f399-111">A user who is a member of this role and the user who created the packages can import, delete, and change packages.</span></span>  
  
 <span data-ttu-id="1f399-112">**sysssispackages** 資料表中的 **ownersid** 資料行列出建立封裝之使用者的唯一安全性識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f399-112">The **ownersid** column in the **sysssispackages** table lists the unique security identifier of the user who created the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1f399-113">選項。</span><span class="sxs-lookup"><span data-stu-id="1f399-113">Options</span></span>  
 <span data-ttu-id="1f399-114">**封裝名稱**</span><span class="sxs-lookup"><span data-stu-id="1f399-114">**Package Name**</span></span>  
 <span data-ttu-id="1f399-115">指定封裝的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f399-115">Specify the name of the package.</span></span>  
  
 <span data-ttu-id="1f399-116">**讀取器角色**</span><span class="sxs-lookup"><span data-stu-id="1f399-116">**Reader Role**</span></span>  
 <span data-ttu-id="1f399-117">選取清單中的角色。</span><span class="sxs-lookup"><span data-stu-id="1f399-117">Select a role in the list.</span></span>  
  
 <span data-ttu-id="1f399-118">**寫入器角色**</span><span class="sxs-lookup"><span data-stu-id="1f399-118">**Writer Role**</span></span>  
 <span data-ttu-id="1f399-119">選取清單中的角色</span><span class="sxs-lookup"><span data-stu-id="1f399-119">Select a role in the list</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f399-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f399-120">See Also</span></span>  
 <span data-ttu-id="1f399-121">[資料庫層級角色](../relational-databases/security/authentication-access/database-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="1f399-121">[Database-Level Roles](../relational-databases/security/authentication-access/database-level-roles.md) </span></span>  
 [<span data-ttu-id="1f399-122">安全性概觀 (Integration Services)</span><span class="sxs-lookup"><span data-stu-id="1f399-122">Security Overview &#40;Integration Services&#41;</span></span>](security/security-overview-integration-services.md)  
  
  
