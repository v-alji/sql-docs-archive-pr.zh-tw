---
title: 使用範本設定資源管理員 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, templates
ms.assetid: f342dec2-d1d6-483e-b44e-98eb7d168b5e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 62edb23cf55a953cb0fef54f002f8eaaa16f58ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599468"
---
# <a name="configure-resource-governor-using-a-template"></a><span data-ttu-id="434f5-102">使用範本來設定資源管理員</span><span class="sxs-lookup"><span data-stu-id="434f5-102">Configure Resource Governor Using a Template</span></span>
  <span data-ttu-id="434f5-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]所提供的範本來設定資源管理員。</span><span class="sxs-lookup"><span data-stu-id="434f5-103">You can configure Resource Governor by using a template that is provided in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="434f5-104">**開始之前：** [權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="434f5-104">**Before you begin:**  [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="434f5-105">**若要建立工作負載群組，請使用：** [範本](#ConfRGTemplate)</span><span class="sxs-lookup"><span data-stu-id="434f5-105">**To create a workload group, using:**  [a template](#ConfRGTemplate)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="434f5-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="434f5-106">Before You Begin</span></span>  
 <span data-ttu-id="434f5-107">使用下列步驟即可開啟和修改建立資源集區與集區之工作負載群組的範本。</span><span class="sxs-lookup"><span data-stu-id="434f5-107">Use the following steps to open and modify a template that creates a resource pool and a workload group for the pool.</span></span> <span data-ttu-id="434f5-108">此外，這個範本可讓您建立使用者定義的分類函數，以便將新的連接路由傳送至預設群組或您所建立的工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="434f5-108">In addition, this template enables you to create a classifier user-defined function that routes new connections to either the default group or the workload group that you create.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="434f5-109">權限</span><span class="sxs-lookup"><span data-stu-id="434f5-109">Permissions</span></span>  
 <span data-ttu-id="434f5-110">範本中的資源管理員 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式需要 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="434f5-110">The resource governor [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the template require CONTROL SERVER permission.</span></span>  
  
##  <a name="configure-resource-governor-using-a-template"></a><a name="ConfRGTemplate"></a> <span data-ttu-id="434f5-111">使用範本來設定資源管理員</span><span class="sxs-lookup"><span data-stu-id="434f5-111">Configure Resource Governor Using a Template</span></span>  
 <span data-ttu-id="434f5-112">**若要使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="434f5-112">**To configure resource governor by using a template in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="434f5-113">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 [檢視]  功能表上，按一下 [範本總管] 。</span><span class="sxs-lookup"><span data-stu-id="434f5-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="434f5-114">在 [範本總管] 中，展開 [Resource Governor]，然後按兩下 [設定 Resource Governor]。</span><span class="sxs-lookup"><span data-stu-id="434f5-114">In **Template Explorer**, expand **Resource Governor**, and then double-click **Configure Resource Governor**.</span></span>  
  
3.  <span data-ttu-id="434f5-115">在 **[連接到 Database Engine]** 中，輸入必要資訊，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="434f5-115">In **Connect to Database Engine**, enter the required information, and then click **OK**.</span></span> <span data-ttu-id="434f5-116">此時，[查詢編輯器] 就會提供 Configure Resource Governor.sql 範本。</span><span class="sxs-lookup"><span data-stu-id="434f5-116">The template Configure Resource Governor.sql is provided in the Query Editor.</span></span> <span data-ttu-id="434f5-117">您可以使用此範本來建立並設定資源集區、工作負載群組和分類函數。</span><span class="sxs-lookup"><span data-stu-id="434f5-117">Use this template to create and configure a resource pool, a workload group, and a classifier function.</span></span>  
  
4.  <span data-ttu-id="434f5-118">若要變更範本中的值，請按下 CTRL+SHIFT+M。</span><span class="sxs-lookup"><span data-stu-id="434f5-118">To change the values in the template, press CTRL+SHIFT+M.</span></span> <span data-ttu-id="434f5-119">在 **[指定範本參數的值]** 視窗中，輸入您想要使用的值。</span><span class="sxs-lookup"><span data-stu-id="434f5-119">In the **Specify Values for Template Parameters** window, enter the values that you want to use.</span></span>  
  
5.  <span data-ttu-id="434f5-120">若要儲存您對範本所做的變更，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="434f5-120">To save the changes that you make to the template, click **OK**.</span></span>  
  
6.  <span data-ttu-id="434f5-121">若要執行查詢，請按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="434f5-121">To run the query, click **Execute**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="434f5-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="434f5-122">See Also</span></span>  
 <span data-ttu-id="434f5-123">[資源管理員](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="434f5-123">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="434f5-124">[啟用資源管理員](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="434f5-124">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="434f5-125">[資源管理員資源集區](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="434f5-125">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="434f5-126">[資源管理員工作負載群組](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="434f5-126">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="434f5-127">[資源管理員分類函數](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="434f5-127">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="434f5-128">[檢視資源管理員屬性](view-resource-governor-properties.md) </span><span class="sxs-lookup"><span data-stu-id="434f5-128">[View Resource Governor Properties](view-resource-governor-properties.md) </span></span>  
 <span data-ttu-id="434f5-129">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="434f5-129">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="434f5-130">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="434f5-130">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="434f5-131">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="434f5-131">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span></span>  
 [<span data-ttu-id="434f5-132">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="434f5-132">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
