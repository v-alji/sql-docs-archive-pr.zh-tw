---
title: 刪除原則式管理條件 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, delete policy conditions
ms.assetid: e04148b8-f6dd-4c50-a5ef-c650b71dbf4d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f02a5294ecb53db4d8baa4f3dae0a232d9551a13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585338"
---
# <a name="delete-a-policy-based-management-condition"></a><span data-ttu-id="e4015-102">刪除原則式管理條件</span><span class="sxs-lookup"><span data-stu-id="e4015-102">Delete a Policy-Based Management Condition</span></span>
  <span data-ttu-id="e4015-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中刪除原則式管理條件。</span><span class="sxs-lookup"><span data-stu-id="e4015-103">This topic describes how to delete a Policy-based Management condition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="e4015-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="e4015-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e4015-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="e4015-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e4015-106">安全性</span><span class="sxs-lookup"><span data-stu-id="e4015-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e4015-107">**若要使用下列項目來刪除條件：**</span><span class="sxs-lookup"><span data-stu-id="e4015-107">**To delete a condition, using:**</span></span>  
  
     [<span data-ttu-id="e4015-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e4015-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e4015-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="e4015-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e4015-110">Security</span><span class="sxs-lookup"><span data-stu-id="e4015-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e4015-111">權限</span><span class="sxs-lookup"><span data-stu-id="e4015-111">Permissions</span></span>  
 <span data-ttu-id="e4015-112">需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="e4015-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e4015-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e4015-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-condition"></a><span data-ttu-id="e4015-114">若要刪除條件</span><span class="sxs-lookup"><span data-stu-id="e4015-114">To delete a condition</span></span>  
  
1.  <span data-ttu-id="e4015-115">在 **[物件總管]** 中，按一下加號，展開包含您想要刪除之條件的伺服器。</span><span class="sxs-lookup"><span data-stu-id="e4015-115">In **Object Explorer**, click the plus sign to expand the server that contains the condition that you want to delete.</span></span>  
  
2.  <span data-ttu-id="e4015-116">按一下加號展開 **[管理]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e4015-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="e4015-117">按一下加號展開 **[原則管理]** 。</span><span class="sxs-lookup"><span data-stu-id="e4015-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="e4015-118">按一下加號展開 **[條件]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e4015-118">Click the plus sign to expand the **Conditions** folder.</span></span>  
  
5.  <span data-ttu-id="e4015-119">以滑鼠右鍵按一下您想要刪除的條件，然後選取 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="e4015-119">Right-click the condition that you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="e4015-120">在 **[刪除物件]** 對話方塊中，確定已選取正確的條件，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="e4015-120">In the **Delete Object** dialog box, ensure that the correct condition is selected and then click **OK**.</span></span>  
  
  
