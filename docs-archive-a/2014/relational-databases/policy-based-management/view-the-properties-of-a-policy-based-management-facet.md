---
title: 檢視原則式管理 Facet 的屬性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view facet properties
ms.assetid: 022a244c-c2e7-4467-b9a2-c7a27859be22
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea24ff2768ecaeec426a8689455912d848b54813
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593979"
---
# <a name="view-the-properties-of-a-policy-based-management-facet"></a><span data-ttu-id="e3db7-102">檢視原則式管理 Facet 的屬性</span><span class="sxs-lookup"><span data-stu-id="e3db7-102">View the Properties of a Policy-Based Management Facet</span></span>
  <span data-ttu-id="e3db7-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中檢視原則式管理 Facet 的屬性。</span><span class="sxs-lookup"><span data-stu-id="e3db7-103">This topic describes how to view the properties of a Policy-Based Management facet in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="e3db7-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="e3db7-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e3db7-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="e3db7-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e3db7-106">安全性</span><span class="sxs-lookup"><span data-stu-id="e3db7-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e3db7-107">**若要使用下列項目來檢視 Facet 的屬性：**</span><span class="sxs-lookup"><span data-stu-id="e3db7-107">**To view the properties of a facet, using:**</span></span>  
  
     [<span data-ttu-id="e3db7-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e3db7-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e3db7-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="e3db7-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e3db7-110">Security</span><span class="sxs-lookup"><span data-stu-id="e3db7-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e3db7-111">權限</span><span class="sxs-lookup"><span data-stu-id="e3db7-111">Permissions</span></span>  
 <span data-ttu-id="e3db7-112">需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="e3db7-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e3db7-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e3db7-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-properties-of-a-facet"></a><span data-ttu-id="e3db7-114">若要檢視 Facet 的屬性</span><span class="sxs-lookup"><span data-stu-id="e3db7-114">To view the properties of a facet</span></span>  
  
1.  <span data-ttu-id="e3db7-115">在 **[物件總管]** 中，按一下加號，展開包含您想要檢視其屬性之 Facet 的伺服器。</span><span class="sxs-lookup"><span data-stu-id="e3db7-115">In **Object Explorer**, click the plus sign to expand the server that contains the facet whose properties you want to view.</span></span>  
  
2.  <span data-ttu-id="e3db7-116">按一下加號展開 **[管理]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e3db7-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="e3db7-117">按一下加號展開 **[原則管理]**。</span><span class="sxs-lookup"><span data-stu-id="e3db7-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="e3db7-118">按一下加號展開 **[Facet]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e3db7-118">Click the plus sign to expand the **Facets** folder.</span></span>  
  
5.  <span data-ttu-id="e3db7-119">以滑鼠右鍵按一下您想要檢視其屬性的 Facet，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3db7-119">Right-click the facet whose properties you want to view and select **Properties**.</span></span> <span data-ttu-id="e3db7-120">如需有關 [Facet 屬性 - _Facet 名稱_]\*\*\*\* 對話方塊中可用選項的詳細資訊，請參閱 [Facet 屬性對話方塊，一般頁面](../../integration-services/general-page-of-integration-services-designers-options.md)、[Facet 屬性對話方塊，相依原則頁面](facet-properties-dialog-box-dependent-policies-page.md)和 [Facet 屬性對話方塊，相依條件頁面](facet-properties-dialog-box-dependent-conditions-page.md)。</span><span class="sxs-lookup"><span data-stu-id="e3db7-120">For more information on the available options in the **Facet Properties -**_facet_name_ dialog box, see [Facet Properties Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md), [Facet Properties Dialog Box, Dependent Policies Page](facet-properties-dialog-box-dependent-policies-page.md), and [Facet Properties Dialog Box, Dependent Conditions Page](facet-properties-dialog-box-dependent-conditions-page.md).</span></span>  
  
6.  <span data-ttu-id="e3db7-121">完成後，請按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="e3db7-121">When finished, click **Close**.</span></span>  
  
  
