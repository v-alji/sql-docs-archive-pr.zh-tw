---
title: 查看暫存進程期間發生的錯誤 (Master Data Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], viewing errors
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3b39d039b29090f3021c764126ebb782ce25cbfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699877"
---
# <a name="view-errors-that-occur-during-the-staging-process-master-data-services"></a><span data-ttu-id="d45cb-102">檢視暫存處理序期間發生的錯誤 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d45cb-102">View Errors that Occur During the Staging Process (Master Data Services)</span></span>
  <span data-ttu-id="d45cb-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以檢視暫存處理序期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d45cb-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can view errors that occur during the staging process.</span></span> <span data-ttu-id="d45cb-104">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫提供下列兩個用來顯示錯誤的檢視：</span><span class="sxs-lookup"><span data-stu-id="d45cb-104">In the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database, there are two views that show errors:</span></span>  
  
-   <span data-ttu-id="d45cb-105">分葉或合併成員更新適用的 stg.viw_name_MemberErrorDetails。</span><span class="sxs-lookup"><span data-stu-id="d45cb-105">stg.viw_name_MemberErrorDetails for leaf or consolidated member updates.</span></span>  
  
-   <span data-ttu-id="d45cb-106">階層關聯性更新適用的 stg.viw_name_RelationshipErrorDetails。</span><span class="sxs-lookup"><span data-stu-id="d45cb-106">stg.viw_name_RelationshipErrorDetails for hierarchy relationship updates.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d45cb-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="d45cb-107">Prerequisites</span></span>  
 <span data-ttu-id="d45cb-108">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="d45cb-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d45cb-109">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫中，您必須具有 stg.viw_name_MemberErrorDetails 或 stg.viw_name_RelationshipErrorDetails 檢視的 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="d45cb-109">In the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database, you must have SELECT permissions to either the stg.viw_name_MemberErrorDetails or stg.viw_name_RelationshipErrorDetails view.</span></span>  
  
-   <span data-ttu-id="d45cb-110">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="d45cb-110">You must be a model administrator.</span></span> <span data-ttu-id="d45cb-111">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d45cb-111">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-view-staging-errors"></a><span data-ttu-id="d45cb-112">檢視暫存錯誤</span><span class="sxs-lookup"><span data-stu-id="d45cb-112">To view staging errors</span></span>  
  
1.  <span data-ttu-id="d45cb-113">開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 並且連接到 [!INCLUDE[ssDE](../includes/ssde-md.md)] 資料庫的 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d45cb-113">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] instance for your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="d45cb-114">開啟新的查詢。</span><span class="sxs-lookup"><span data-stu-id="d45cb-114">Open a new query.</span></span>  
  
3.  <span data-ttu-id="d45cb-115">輸入下列文字，以您的暫存資料表名稱取代名稱，例如 viw_Product_MemberErrorDetails。</span><span class="sxs-lookup"><span data-stu-id="d45cb-115">Type the following text, replacing name with the name of your staging table, for example, viw_Product_MemberErrorDetails.</span></span>  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  <span data-ttu-id="d45cb-116">執行查詢。</span><span class="sxs-lookup"><span data-stu-id="d45cb-116">Excecute the query.</span></span> <span data-ttu-id="d45cb-117">錯誤詳細資料會顯示在 **ErrorDescription** 欄位中。</span><span class="sxs-lookup"><span data-stu-id="d45cb-117">Error details are displayed in the **ErrorDescription** field.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d45cb-118">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d45cb-118">Next Steps</span></span>  
 <span data-ttu-id="d45cb-119">如需錯誤訊息的詳細資訊，請參閱[暫存處理序錯誤 &#40;Master Data Services&#41;](../../2014/master-data-services/staging-process-errors-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d45cb-119">For more details on error messages, see [Staging Process Errors &#40;Master Data Services&#41;](../../2014/master-data-services/staging-process-errors-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d45cb-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d45cb-120">See Also</span></span>  
 <span data-ttu-id="d45cb-121">[資料匯入 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d45cb-121">[Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md) </span></span>  
 [<span data-ttu-id="d45cb-122">暫存處理序疑難排解 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d45cb-122">Troubleshooting the Staging Process (Master Data Services)</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  
