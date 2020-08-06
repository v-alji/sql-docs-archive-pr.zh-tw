---
title: 建立新的原則式管理條件 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, creating policy conditions
ms.assetid: 8a612f7e-6c70-49db-a4de-48431e097cc5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e4fe206c9a82b69101508f6f0a760ca9c1bc423d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596676"
---
# <a name="create-a-new-policy-based-management-condition"></a><span data-ttu-id="88b0d-102">建立新的原則式管理條件</span><span class="sxs-lookup"><span data-stu-id="88b0d-102">Create a New Policy-Based Management Condition</span></span>
  <span data-ttu-id="88b0d-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中建立原則式管理條件。</span><span class="sxs-lookup"><span data-stu-id="88b0d-103">This topic describes how to create a Policy-based Management condition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="88b0d-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="88b0d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="88b0d-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="88b0d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="88b0d-106">安全性</span><span class="sxs-lookup"><span data-stu-id="88b0d-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="88b0d-107">**若要使用下列項目來建立條件：**</span><span class="sxs-lookup"><span data-stu-id="88b0d-107">**To create a condition, using:**</span></span>  
  
     [<span data-ttu-id="88b0d-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="88b0d-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="88b0d-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="88b0d-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="88b0d-110">Security</span><span class="sxs-lookup"><span data-stu-id="88b0d-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="88b0d-111">權限</span><span class="sxs-lookup"><span data-stu-id="88b0d-111">Permissions</span></span>  
 <span data-ttu-id="88b0d-112">需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="88b0d-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="88b0d-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="88b0d-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-condition"></a><span data-ttu-id="88b0d-114">建立條件</span><span class="sxs-lookup"><span data-stu-id="88b0d-114">To create a condition</span></span>  
  
1.  <span data-ttu-id="88b0d-115">在物件總管  中，按一下加號，展開您想要建立原則式管理條件的伺服器。</span><span class="sxs-lookup"><span data-stu-id="88b0d-115">In **Object Explorer**, click the plus sign to expand the server where you want to create a Policy-based Management condition.</span></span>  
  
2.  <span data-ttu-id="88b0d-116">按一下加號展開 **[管理]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="88b0d-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="88b0d-117">按一下加號展開 **[原則管理]** 。</span><span class="sxs-lookup"><span data-stu-id="88b0d-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="88b0d-118">按一下加號展開 **[Facet]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="88b0d-118">Click the plus sign to expand the **Facets** folder.</span></span>  
  
5.  <span data-ttu-id="88b0d-119">以滑鼠右鍵按一下您想要建立新條件的 Facet，然後選取 [新增條件]  。</span><span class="sxs-lookup"><span data-stu-id="88b0d-119">Right-click the facet in which you want to create a new condition and select **New Condition**.</span></span>  
  
6.  <span data-ttu-id="88b0d-120">在 **[建立新條件]** 對話方塊的 **[名稱]** 方塊中，輸入新條件的名稱。</span><span class="sxs-lookup"><span data-stu-id="88b0d-120">In the **Create New Condition** dialog box, in the **Name** box, type the name of the new condition.</span></span>  
  
7.  <span data-ttu-id="88b0d-121">在 **[Facet]** 清單中，確認正確的 Facet，或選取不同的 Facet。</span><span class="sxs-lookup"><span data-stu-id="88b0d-121">Confirm the correct facet in the **Facet** list, or select a different facet.</span></span>  
  
8.  <span data-ttu-id="88b0d-122">在 **[運算式]** 底下的 **[欄位]** 方塊中選取 Facet 屬性及其相關聯的運算子和值，藉以建構條件運算式。</span><span class="sxs-lookup"><span data-stu-id="88b0d-122">Under **Expression**, construct condition expressions by selecting a facet property in the **Field** box, together with its associated operator and value.</span></span> <span data-ttu-id="88b0d-123">當您加入多個運算式時，可以使用 **[及]** 或 **[或]** 來聯結運算式。</span><span class="sxs-lookup"><span data-stu-id="88b0d-123">When you add multiple expressions, the expressions can be joined by using **And** or **Or**.</span></span> <span data-ttu-id="88b0d-124">如需此對話方塊可用之選項的詳細資訊，請參閱[建立新條件或開啟條件對話方塊，一般頁面](../../integration-services/general-page-of-integration-services-designers-options.md)、[建立新條件或開啟條件對話方塊，描述頁面](create-new-condition-or-open-condition-dialog-box-description-page.md)和[進階編輯 &#40;條件&#41; 對話方塊](advanced-edit-condition-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="88b0d-124">For more information on the available options in this dialog box, see [Create New Condition or Open Condition Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md), [Create New Condition or Open Condition Dialog Box, Description Page](create-new-condition-or-open-condition-dialog-box-description-page.md), and [Advanced Edit &#40;Condition&#41; Dialog Box](advanced-edit-condition-dialog-box.md).</span></span>  
  
9. <span data-ttu-id="88b0d-125">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="88b0d-125">When finished, click **OK**.</span></span>  
  
  
