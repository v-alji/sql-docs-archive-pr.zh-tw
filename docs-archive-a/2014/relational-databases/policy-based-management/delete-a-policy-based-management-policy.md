---
title: 刪除原則式管理原則 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, delete policies
ms.assetid: 488f0305-190c-4223-aa5c-e9bd43b520eb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c43bc3cdf4a7a5b5d9268bbd7e68506616d1f0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686911"
---
# <a name="delete-a-policy-based-management-policy"></a><span data-ttu-id="dd03a-102">刪除原則式管理原則</span><span class="sxs-lookup"><span data-stu-id="dd03a-102">Delete a Policy-Based Management Policy</span></span>
  <span data-ttu-id="dd03a-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中刪除原則式管理原則。</span><span class="sxs-lookup"><span data-stu-id="dd03a-103">This topic describes how to delete a Policy-Based Management policy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="dd03a-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="dd03a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="dd03a-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="dd03a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="dd03a-106">安全性</span><span class="sxs-lookup"><span data-stu-id="dd03a-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="dd03a-107">**若要使用下列項目來刪除原則：**</span><span class="sxs-lookup"><span data-stu-id="dd03a-107">**To delete a policy, using:**</span></span>  
  
     [<span data-ttu-id="dd03a-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="dd03a-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="dd03a-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="dd03a-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="dd03a-110">Security</span><span class="sxs-lookup"><span data-stu-id="dd03a-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="dd03a-111">權限</span><span class="sxs-lookup"><span data-stu-id="dd03a-111">Permissions</span></span>  
 <span data-ttu-id="dd03a-112">需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="dd03a-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="dd03a-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="dd03a-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-policy"></a><span data-ttu-id="dd03a-114">刪除原則</span><span class="sxs-lookup"><span data-stu-id="dd03a-114">To delete a policy</span></span>  
  
1.  <span data-ttu-id="dd03a-115">在 [物件總管] 中，按一下加號，展開包含您想要刪除之原則式管理原則的伺服器。</span><span class="sxs-lookup"><span data-stu-id="dd03a-115">In Object Explorer, click the plus sign to expand the server that contains the Policy-Based Management policy that you want to delete.</span></span>  
  
2.  <span data-ttu-id="dd03a-116">按一下加號展開 **[管理]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="dd03a-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="dd03a-117">按一下加號展開 **[原則管理]** 。</span><span class="sxs-lookup"><span data-stu-id="dd03a-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="dd03a-118">按一下加號展開 **[原則]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="dd03a-118">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="dd03a-119">以滑鼠右鍵按一下您想要刪除的原則，然後選取 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="dd03a-119">Right-click the policy that you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="dd03a-120">在 **[刪除物件]** 對話方塊中，確定已選取正確的條件，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="dd03a-120">In the **Delete Object** dialog box, ensure that the correct condition is selected and then click **OK**.</span></span>  
  
  
