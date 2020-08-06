---
title: 設定原則式管理的一般屬性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.PolicyManagement.f1
helpviewer_keywords:
- Policy-Based Management, configure properties
ms.assetid: 6d1e0e37-29ea-408a-a055-384984d884be
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a2efb37fafa29bcb043dedbcfa8719d0092b1c77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699472"
---
# <a name="configure-the-general-properties-of-policy-based-management"></a><span data-ttu-id="a2f99-102">設定原則式管理的一般屬性</span><span class="sxs-lookup"><span data-stu-id="a2f99-102">Configure the General Properties of Policy-Based Management</span></span>
  <span data-ttu-id="a2f99-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中設定原則式管理的屬性。</span><span class="sxs-lookup"><span data-stu-id="a2f99-103">This topic describes how to configure the properties for Policy-Based Management in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a2f99-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="a2f99-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a2f99-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="a2f99-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a2f99-106">安全性</span><span class="sxs-lookup"><span data-stu-id="a2f99-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a2f99-107">**若要使用下列項目設定原則式管理：**</span><span class="sxs-lookup"><span data-stu-id="a2f99-107">**To configure Policy-Based Management, using:**</span></span>  
  
     [<span data-ttu-id="a2f99-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a2f99-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a2f99-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a2f99-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a2f99-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="a2f99-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a2f99-111">Security</span><span class="sxs-lookup"><span data-stu-id="a2f99-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a2f99-112">權限</span><span class="sxs-lookup"><span data-stu-id="a2f99-112">Permissions</span></span>  
 <span data-ttu-id="a2f99-113">需要 PolicyAdministratorRole 固定資料庫角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="a2f99-113">Requires membership in the PolicyAdministratorRole fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a2f99-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a2f99-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-policy-based-management"></a><span data-ttu-id="a2f99-115">設定以原則為基礎的管理</span><span class="sxs-lookup"><span data-stu-id="a2f99-115">To configure Policy-Based Management</span></span>  
  
1.  <span data-ttu-id="a2f99-116">在物件總管\*\*\*\* 中，按一下加號，展開您想要設定原則式管理屬性的伺服器。</span><span class="sxs-lookup"><span data-stu-id="a2f99-116">In **Object Explorer**, click the plus sign to expand the server where you want to configure Policy-Based Management properties.</span></span>  
  
2.  <span data-ttu-id="a2f99-117">按一下加號展開 **[管理]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="a2f99-117">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="a2f99-118">以滑鼠右鍵按一下 [原則管理]\*\*\*\*，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a2f99-118">Right-click **Policy Management** and select **Properties**.</span></span>  
  
     <span data-ttu-id="a2f99-119">**[原則管理屬性]** 對話方塊有下列選項。</span><span class="sxs-lookup"><span data-stu-id="a2f99-119">The following options are available in **Policy Management Properties** dialog box.</span></span>  
  
     <span data-ttu-id="a2f99-120">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="a2f99-120">**Enabled**</span></span>  
     <span data-ttu-id="a2f99-121">指定是否啟用以原則為基礎的管理。</span><span class="sxs-lookup"><span data-stu-id="a2f99-121">Specifies whether Policy-Based Management is enabled.</span></span>  
  
     <span data-ttu-id="a2f99-122">**HistoryRetentionInDays**</span><span class="sxs-lookup"><span data-stu-id="a2f99-122">**HistoryRetentionInDays**</span></span>  
     <span data-ttu-id="a2f99-123">指定原則評估記錄應保留的天數。</span><span class="sxs-lookup"><span data-stu-id="a2f99-123">Specifies the number of days that policy evaluation history should be retained.</span></span> <span data-ttu-id="a2f99-124">如果這個值為 0 (預設值)，將不會自動移除記錄。</span><span class="sxs-lookup"><span data-stu-id="a2f99-124">If this value is 0 (the default), the history will not be automatically removed.</span></span>  
  
     <span data-ttu-id="a2f99-125">**LogOnSuccess**</span><span class="sxs-lookup"><span data-stu-id="a2f99-125">**LogOnSuccess**</span></span>  
     <span data-ttu-id="a2f99-126">指定以原則為基礎的管理是否會記錄成功的原則評估。</span><span class="sxs-lookup"><span data-stu-id="a2f99-126">Specifies whether Policy-Based Management logs successful policy evaluations.</span></span>  
  
    -   <span data-ttu-id="a2f99-127">當這個值為 false (預設值) 時，只會記錄失敗的原則評估。</span><span class="sxs-lookup"><span data-stu-id="a2f99-127">When this value is false (the default), only failed policy evaluations are logged.</span></span>  
  
    -   <span data-ttu-id="a2f99-128">當這個值為 true 時，成功和失敗的原則評估都會記錄下來。</span><span class="sxs-lookup"><span data-stu-id="a2f99-128">When this value is true, both successful and failed policy evaluations are logged.</span></span>  
  
4.  <span data-ttu-id="a2f99-129">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="a2f99-129">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a2f99-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a2f99-130">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-policy-based-management"></a><span data-ttu-id="a2f99-131">設定以原則為基礎的管理</span><span class="sxs-lookup"><span data-stu-id="a2f99-131">To configure Policy-Based Management</span></span>  
  
1.  <span data-ttu-id="a2f99-132">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a2f99-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a2f99-133">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="a2f99-133">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a2f99-134">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="a2f99-134">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- enables Policy-Based Management   
    USE msdb;  
    GO  
    EXEC dbo.sp_syspolicy_configure   
         @name = N'Enabled',   
         @value = 1;  
    GO  
    ```  
  
 <span data-ttu-id="a2f99-135">如需詳細資訊，請參閱 [sp_syspolicy_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a2f99-135">For more information, see [sp_syspolicy_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql).</span></span>  
  
  
