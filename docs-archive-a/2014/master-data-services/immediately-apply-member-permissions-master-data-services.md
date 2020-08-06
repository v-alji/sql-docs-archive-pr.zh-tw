---
title: 立即套用成員權限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members [Master Data Services], applying permissions immediately
- permissions [Master Data Services], applying member permissions immediately
ms.assetid: 5b16de66-5c39-49f5-992f-402a9eb319aa
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e960ad06213b7c5057a6249b72ce225a6abe35e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597176"
---
# <a name="immediately-apply-member-permissions-master-data-services"></a><span data-ttu-id="00124-102">立即套用成員權限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="00124-102">Immediately Apply Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="00124-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以立即套用成員權限，不等候成員安全性於固定間隔套用。</span><span class="sxs-lookup"><span data-stu-id="00124-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], instead of waiting for member security to be applied at regular intervals, you can apply member permissions immediately.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="00124-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="00124-104">Prerequisites</span></span>  
 <span data-ttu-id="00124-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="00124-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="00124-106">您必須在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫中擁有執行 mdm.udpSecurityMemberProcessRebuildModel 預存程序的權限。</span><span class="sxs-lookup"><span data-stu-id="00124-106">You must have permission to execute the mdm.udpSecurityMemberProcessRebuildModel stored procedure in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="00124-107">如需詳細資訊，請參閱[資料庫物件安全性 &#40;Master Data Services&#41;](database-object-security-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="00124-107">For more information, see [Database Object Security &#40;Master Data Services&#41;](database-object-security-master-data-services.md).</span></span>  
  
### <a name="to-immediately-apply-hierarchy-member-permissions"></a><span data-ttu-id="00124-108">若要立即套用階層成員權限</span><span class="sxs-lookup"><span data-stu-id="00124-108">To immediately apply hierarchy member permissions</span></span>  
  
1.  <span data-ttu-id="00124-109">開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 並且連接到 [!INCLUDE[ssDE](../includes/ssde-md.md)] 資料庫的 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="00124-109">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] instance for your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="00124-110">建立新的查詢。</span><span class="sxs-lookup"><span data-stu-id="00124-110">Create a new query.</span></span>  
  
3.  <span data-ttu-id="00124-111">輸入下列文字，以您的資料庫名稱取代 *database* ，並以模型名稱取代 *Model_Name* 。</span><span class="sxs-lookup"><span data-stu-id="00124-111">Type the following text, replacing *database* with the name of your database and *Model_Name* with the name of the model.</span></span>  
  
    ```  
    USE [database];  
    GO  
  
    DECLARE @Model_ID INT;  
    SELECT @Model_ID = ID FROM mdm.tblModel WHERE [Name] = N'Model_Name';  
    EXEC [mdm].[udpSecurityMemberProcessRebuildModel] @Model_ID=@Model_ID, @ProcessNow=1;  
    GO  
    ```  
  
4.  <span data-ttu-id="00124-112">執行查詢。</span><span class="sxs-lookup"><span data-stu-id="00124-112">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00124-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00124-113">See Also</span></span>  
 <span data-ttu-id="00124-114">[指派階層成員許可權 &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="00124-114">[Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="00124-115">階層成員權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="00124-115">Hierarchy Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
