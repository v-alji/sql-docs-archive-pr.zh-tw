---
title: 匯入原則式管理原則 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, import policy
ms.assetid: 850b7ef9-d2b7-4754-bf04-7cb419ffb776
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d83ed589e147c61b1692447aacb17535f18a5c9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591982"
---
# <a name="import-a-policy-based-management-policy"></a><span data-ttu-id="e86e0-102">匯入原則式管理原則</span><span class="sxs-lookup"><span data-stu-id="e86e0-102">Import a Policy-Based Management Policy</span></span>
  <span data-ttu-id="e86e0-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中匯入原則式管理原則執行個體。</span><span class="sxs-lookup"><span data-stu-id="e86e0-103">This topic describes how to import a Policy-Based Management policy instance in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="e86e0-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="e86e0-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e86e0-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="e86e0-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e86e0-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="e86e0-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e86e0-107">安全性</span><span class="sxs-lookup"><span data-stu-id="e86e0-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e86e0-108">**若要使用下列項目來匯入原則執行個體：**</span><span class="sxs-lookup"><span data-stu-id="e86e0-108">**To import a policy instance, using:**</span></span>  
  
     [<span data-ttu-id="e86e0-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e86e0-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e86e0-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="e86e0-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e86e0-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="e86e0-111">Limitations and Restrictions</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e86e0-112">隨附一些可用來監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的原則。</span><span class="sxs-lookup"><span data-stu-id="e86e0-112">ships with policies that can be used to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e86e0-113">根據預設，這些原則不會安裝在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 上，但是您可以從預設位置 C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033 匯入這些原則。</span><span class="sxs-lookup"><span data-stu-id="e86e0-113">By default, these policies are not installed on the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], but they can be imported from the default location of C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e86e0-114">Security</span><span class="sxs-lookup"><span data-stu-id="e86e0-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e86e0-115">權限</span><span class="sxs-lookup"><span data-stu-id="e86e0-115">Permissions</span></span>  
 <span data-ttu-id="e86e0-116">需要 msdb 資料庫中 PolicyAdministratorRole 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="e86e0-116">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e86e0-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e86e0-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-import-a-policy-instance"></a><span data-ttu-id="e86e0-118">若要匯入原則執行個體</span><span class="sxs-lookup"><span data-stu-id="e86e0-118">To import a policy instance</span></span>  
  
1.  <span data-ttu-id="e86e0-119">在物件總管  中，按一下加號，展開新匯入之原則執行個體所在的伺服器。</span><span class="sxs-lookup"><span data-stu-id="e86e0-119">In **Object Explorer**, click the plus sign to expand the server where the newly-imported policy instance will reside.</span></span>  
  
2.  <span data-ttu-id="e86e0-120">按一下加號展開 **[管理]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e86e0-120">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="e86e0-121">按一下加號展開 **[原則管理]** 。</span><span class="sxs-lookup"><span data-stu-id="e86e0-121">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="e86e0-122">以滑鼠右鍵按一下 [原則]  資料夾，然後選取 [匯入原則]  。</span><span class="sxs-lookup"><span data-stu-id="e86e0-122">Right-click the **Policies** folder and select **Import Policy**.</span></span>  
  
5.  <span data-ttu-id="e86e0-123">在 [匯入]  對話方塊中，輸入檔案的路徑和名稱，或使用瀏覽 ( **...** ) 按鈕找出包含原則的 XML 檔案，然後選取此檔案。</span><span class="sxs-lookup"><span data-stu-id="e86e0-123">In the **Import** dialog box, type the path and name of the file; or use the Browse (**...**) button to locate the XML file that contains the policy, and then select the file.</span></span> <span data-ttu-id="e86e0-124">如需有關 **[匯入]** 對話方塊可用之選項的詳細資訊，請參閱＜ [Import Policies Dialog Box](import-policies-dialog-box.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e86e0-124">For more information on the available options in the **Import** dialog box, see [Import Policies Dialog Box](import-policies-dialog-box.md).</span></span>  
  
6.  <span data-ttu-id="e86e0-125">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="e86e0-125">When finished, click **OK**.</span></span>  
  
  
