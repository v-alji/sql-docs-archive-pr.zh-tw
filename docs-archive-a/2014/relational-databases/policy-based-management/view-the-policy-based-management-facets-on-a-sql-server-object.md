---
title: 檢視 SQL Server 物件的原則式管理 Facet | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view facets
ms.assetid: 5f423b9f-a6c4-41a7-9d8d-8f4926ce1fb4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9137971a79e9e5a18e0ef5d901184133a4c3eff3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593980"
---
# <a name="view-the-policy-based-management-facets-on-a-sql-server-object"></a><span data-ttu-id="9f9a4-102">檢視 SQL Server 物件的原則式管理 Facet</span><span class="sxs-lookup"><span data-stu-id="9f9a4-102">View the Policy-Based Management Facets on a SQL Server Object</span></span>
  <span data-ttu-id="9f9a4-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中檢視套用至特定 SQL Server 物件的所有原則式管理 Facet。</span><span class="sxs-lookup"><span data-stu-id="9f9a4-103">This topic describes how to view all of the Policy-Based Management facets applied to a specific SQL Server object in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="9f9a4-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="9f9a4-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9f9a4-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="9f9a4-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9f9a4-106">安全性</span><span class="sxs-lookup"><span data-stu-id="9f9a4-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9f9a4-107">**若要使用下列項目來檢視物件中的所有 Facet：**</span><span class="sxs-lookup"><span data-stu-id="9f9a4-107">**To view all of the facets in an object, using:**</span></span>  
  
     [<span data-ttu-id="9f9a4-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9f9a4-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9f9a4-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="9f9a4-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9f9a4-110">Security</span><span class="sxs-lookup"><span data-stu-id="9f9a4-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9f9a4-111">權限</span><span class="sxs-lookup"><span data-stu-id="9f9a4-111">Permissions</span></span>  
 <span data-ttu-id="9f9a4-112">需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="9f9a4-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9f9a4-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9f9a4-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-all-of-the-facets-in-an-object"></a><span data-ttu-id="9f9a4-114">若要檢視物件中的所有 Facet</span><span class="sxs-lookup"><span data-stu-id="9f9a4-114">To view all of the facets in an object</span></span>  
  
1.  <span data-ttu-id="9f9a4-115">在物件總管中，以滑鼠右鍵按一下 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體、執行個體物件、資料庫或資料庫物件，然後按一下 [Facet]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9f9a4-115">In Object Explorer, right-click an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], instance object, database, or database object, and then click **Facets**.</span></span>  
  
2.  <span data-ttu-id="9f9a4-116">在 [檢視 Facet - _物件名稱_]\*\*\*\* 對話方塊的 [Facet]\*\*\*\* 清單中，選取要檢視其屬性的 Facet。</span><span class="sxs-lookup"><span data-stu-id="9f9a4-116">In the **View Facets -**_object_name_ dialog box, in the **Facet** list, select a facet to view its properties.</span></span> <span data-ttu-id="9f9a4-117">如需有關此對話方塊可用之選項的詳細資訊，請參閱＜ [View Facets Dialog Box](view-facets-dialog-box.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9f9a4-117">For more information on the available options in this dialog box, see [View Facets Dialog Box](view-facets-dialog-box.md).</span></span>  
  
3.  <span data-ttu-id="9f9a4-118">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="9f9a4-118">When finished, click **OK**.</span></span>  
  
  
