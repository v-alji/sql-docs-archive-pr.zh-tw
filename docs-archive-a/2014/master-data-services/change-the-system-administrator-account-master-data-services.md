---
title: 變更系統管理員帳戶 (Master Data Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], changing
ms.assetid: cf30312e-4338-49a7-90f0-6e4f7b431ff8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1d13cdc19c70c9e16c92dfd290393739d7e4f5e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703054"
---
# <a name="change-the-system-administrator-account-master-data-services"></a><span data-ttu-id="f9428-102">變更系統管理員帳戶 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f9428-102">Change the System Administrator Account (Master Data Services)</span></span>
  <span data-ttu-id="f9428-103">您可以變更指定為系統管理員的使用者帳戶 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f9428-103">You can change the user account that is designated as the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system administrator.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="f9428-104">當您完成這個程序時，先前的系統管理員使用者帳戶會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="f9428-104">When you complete this procedure, the former system administrator user account is deleted.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f9428-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f9428-105">Prerequisites</span></span>  
 <span data-ttu-id="f9428-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="f9428-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="f9428-107">您必須將新的系統管理員使用者名稱加入 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 使用者清單。</span><span class="sxs-lookup"><span data-stu-id="f9428-107">You must add the new administrator's user name to the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Users list.</span></span> <span data-ttu-id="f9428-108">如需詳細資訊，請參閱[Add a User &#40;Master Data Services&#41;](add-a-user-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f9428-108">For more information, see [Add a User &#40;Master Data Services&#41;](add-a-user-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="f9428-109">您必須在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫中擁有檢視 mdm.tblUser 及執行 mdm.udpSecurityMemberProcessRebuildModel 預存程序的權限。</span><span class="sxs-lookup"><span data-stu-id="f9428-109">You must have permission to view mdm.tblUser and to execute the mdm.udpSecurityMemberProcessRebuildModel stored procedure in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="f9428-110">如需詳細資訊，請參閱[資料庫物件安全性 &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f9428-110">For more information, see [Database Object Security &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md).</span></span>  
  
### <a name="to-change-the-administrator-account"></a><span data-ttu-id="f9428-111">若要變更系統管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="f9428-111">To change the administrator account</span></span>  
  
1.  <span data-ttu-id="f9428-112">開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 並且連接到 [!INCLUDE[ssDE](../includes/ssde-md.md)] 資料庫的 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="f9428-112">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] instance for your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="f9428-113">在 [tblUser] 中，尋找將成為新系統管理員的使用者，並複製資料行中的值 `SID` 。</span><span class="sxs-lookup"><span data-stu-id="f9428-113">In mdm.tblUser, find the user that will be the new administrator and copy the value in the `SID` column.</span></span>  
  
3.  <span data-ttu-id="f9428-114">建立新的查詢。</span><span class="sxs-lookup"><span data-stu-id="f9428-114">Create a new query.</span></span>  
  
4.  <span data-ttu-id="f9428-115">輸入下列文字，以新的系統管理員的使用者名稱和*SID*取代*DOMAIN \ user_name* ，並使用您在步驟2中複製的值。</span><span class="sxs-lookup"><span data-stu-id="f9428-115">Type the following text, replacing *DOMAIN\user_name* with the new administrator's user name and *SID* with the value you copied in step 2.</span></span>  
  
    ```  
    EXEC [mdm].[udpSecuritySetAdministrator] @UserName='DOMAIN\user_name', @SID = 'SID', @PromoteNonAdmin = 1  
    ```  
  
5.  <span data-ttu-id="f9428-116">執行查詢。</span><span class="sxs-lookup"><span data-stu-id="f9428-116">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9428-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9428-117">See Also</span></span>  
 [<span data-ttu-id="f9428-118">管理員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f9428-118">Administrators &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/administrators-master-data-services.md)  
  
  
