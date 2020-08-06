---
title: 匯出原則式管理原則 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, export policy
ms.assetid: f0001b33-9078-4432-8460-496736fb325a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 15f554aeeebfd47c3fa1ea13b100fbe6bcfcc055
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596669"
---
# <a name="export-a-policy-based-management-policy"></a><span data-ttu-id="ce6ed-102">匯出原則式管理原則</span><span class="sxs-lookup"><span data-stu-id="ce6ed-102">Export a Policy-Based Management Policy</span></span>
  <span data-ttu-id="ce6ed-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中匯出原則式管理原則。</span><span class="sxs-lookup"><span data-stu-id="ce6ed-103">This topic describes how to export a Policy-Based Management policy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="ce6ed-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="ce6ed-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ce6ed-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="ce6ed-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ce6ed-106">安全性</span><span class="sxs-lookup"><span data-stu-id="ce6ed-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ce6ed-107">**若要使用下列項目來匯出原則：**</span><span class="sxs-lookup"><span data-stu-id="ce6ed-107">**To export a policy, using:**</span></span>  
  
     [<span data-ttu-id="ce6ed-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ce6ed-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ce6ed-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="ce6ed-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ce6ed-110">Security</span><span class="sxs-lookup"><span data-stu-id="ce6ed-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ce6ed-111">權限</span><span class="sxs-lookup"><span data-stu-id="ce6ed-111">Permissions</span></span>  
 <span data-ttu-id="ce6ed-112">需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="ce6ed-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ce6ed-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ce6ed-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-export-a-policy"></a><span data-ttu-id="ce6ed-114">若要匯出原則</span><span class="sxs-lookup"><span data-stu-id="ce6ed-114">To export a policy</span></span>  
  
1.  <span data-ttu-id="ce6ed-115">在 [物件總管] 中，按一下加號，展開包含您想要匯出之原則式管理原則的伺服器。</span><span class="sxs-lookup"><span data-stu-id="ce6ed-115">In Object Explorer, click the plus sign to expand the server that contains the Policy-Based Management policy that you want to export.</span></span>  
  
2.  <span data-ttu-id="ce6ed-116">按一下加號展開 **[管理]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ce6ed-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="ce6ed-117">按一下加號展開 **[原則管理]** 。</span><span class="sxs-lookup"><span data-stu-id="ce6ed-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="ce6ed-118">按一下加號展開 **[原則]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ce6ed-118">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="ce6ed-119">以滑鼠右鍵按一下您想要匯出的原則，然後選取 [匯出原則]  。</span><span class="sxs-lookup"><span data-stu-id="ce6ed-119">Right-click the policy that you want to export and select **Export Policy**.</span></span>  
  
6.  <span data-ttu-id="ce6ed-120">在 **[匯出原則]** 對話方塊的位址列中，輸入檔案的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="ce6ed-120">In the **Export Policy** dialog box, type the path and name of the file in the address bar.</span></span> <span data-ttu-id="ce6ed-121">或者，在對話方塊的導覽窗格中尋找適當的檔案位置，然後在 **[檔案名稱]** 方塊中輸入 XML 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="ce6ed-121">Alternately, find a suitable location for the file in the dialog box's navigation pane, and then type the name of the XML file in the **File Name** box.</span></span>  
  
7.  <span data-ttu-id="ce6ed-122">完成時，按一下 [儲存]  。</span><span class="sxs-lookup"><span data-stu-id="ce6ed-122">When finished, click **Save**.</span></span>  
  
  
