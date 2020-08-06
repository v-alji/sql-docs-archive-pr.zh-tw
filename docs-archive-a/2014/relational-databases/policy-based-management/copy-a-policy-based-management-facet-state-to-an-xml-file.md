---
title: 將原則式管理 Facet 狀態複製到 XML 檔案 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, copy facet state to XML file
ms.assetid: 7d604ab1-6dd6-4f8e-a79c-eba99ab106fd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7be2332d9a2507a079d85a3424bda3a387609ca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699466"
---
# <a name="copy-a-policy-based-management-facet-state-to-an-xml-file"></a><span data-ttu-id="bb135-102">將原則式管理 Facet 狀態複製到 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="bb135-102">Copy a Policy-Based Management Facet State to an XML File</span></span>
  <span data-ttu-id="bb135-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中將原則式管理 Facet 的狀態複製到 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="bb135-103">This topic describes how to how to copy the state of a Policy-Based Management facet to an XML file in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="bb135-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="bb135-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="bb135-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="bb135-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="bb135-106">安全性</span><span class="sxs-lookup"><span data-stu-id="bb135-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="bb135-107">**若要使用下列項目，將 Facet 狀態複製到 XML 檔案：**</span><span class="sxs-lookup"><span data-stu-id="bb135-107">**To copy a facet state to an XML file, using:**</span></span>  
  
     [<span data-ttu-id="bb135-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bb135-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bb135-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="bb135-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bb135-110">Security</span><span class="sxs-lookup"><span data-stu-id="bb135-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bb135-111">權限</span><span class="sxs-lookup"><span data-stu-id="bb135-111">Permissions</span></span>  
 <span data-ttu-id="bb135-112">本主題中的程序需要 msdb 資料庫的 PolicyAdministratorRole 角色成員資格。</span><span class="sxs-lookup"><span data-stu-id="bb135-112">The procedures in this topic require membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bb135-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bb135-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-copy-a-facet-state-to-an-xml-file"></a><span data-ttu-id="bb135-114">將 Facet 狀態複製到 XML 檔</span><span class="sxs-lookup"><span data-stu-id="bb135-114">To copy a facet state to an XML file</span></span>  
  
1.  <span data-ttu-id="bb135-115">在物件總管中，以滑鼠右鍵按一下 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體、執行個體物件、資料庫或資料庫物件，然後按一下 [Facet]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb135-115">In Object Explorer, right-click an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], instance object, database, or database object, and then click **Facets**.</span></span>  
  
2.  <span data-ttu-id="bb135-116">在 [檢視 Facet - _物件名稱_]\*\*\*\* 對話方塊中，按一下 [將目前狀態匯出為原則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bb135-116">In the **View Facets -**_object_name_ dialog box, click **Export Current State as Policy**.</span></span>  
  
3.  <span data-ttu-id="bb135-117">在 [匯出為原則] 對話方塊中，輸入檔案的路徑和名稱，或使用 [瀏覽] \(...) 按鈕找出檔案，然後輸入 XML 檔的名稱。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="bb135-117">In the **Export as Policy** dialog box, type the path and name of the file; or use the Browse (**...**) button to locate the file, and then type the name of the XML file.</span></span> <span data-ttu-id="bb135-118">如需有關此對話方塊可用之選項的詳細資訊，請參閱＜ [Export As Policy Dialog Box](export-as-policy-dialog-box.md)＞。</span><span class="sxs-lookup"><span data-stu-id="bb135-118">For more information on the available options in this dialog box, see [Export As Policy Dialog Box](export-as-policy-dialog-box.md)</span></span>  
  
4.  <span data-ttu-id="bb135-119">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="bb135-119">When finished, click **OK**.</span></span>  
  
  
