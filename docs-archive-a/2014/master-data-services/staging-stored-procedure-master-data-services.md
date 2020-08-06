---
title: 暫存預存程序 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9259352350a099db5d9b18411ad4da06dfb19819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606948"
---
# <a name="staging-stored-procedure-master-data-services"></a><span data-ttu-id="0cf67-102">暫存預存程序 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0cf67-102">Staging Stored Procedure (Master Data Services)</span></span>
  <span data-ttu-id="0cf67-103">從 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]起始暫存處理序時，可以使用下列三個預存程序其中之一：</span><span class="sxs-lookup"><span data-stu-id="0cf67-103">When initiating the staging process from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], you use one of three stored procedures.</span></span>  
  
-   <span data-ttu-id="0cf67-104">stg.udp_name_Leaf</span><span class="sxs-lookup"><span data-stu-id="0cf67-104">stg.udp_name_Leaf</span></span>  
  
-   <span data-ttu-id="0cf67-105">stg.udp_name_Consolidated</span><span class="sxs-lookup"><span data-stu-id="0cf67-105">stg.udp_name_Consolidated</span></span>  
  
-   <span data-ttu-id="0cf67-106">stg.udp_name_Relationship</span><span class="sxs-lookup"><span data-stu-id="0cf67-106">stg.udp_name_Relationship</span></span>  
  
 <span data-ttu-id="0cf67-107">其中 name 是建立實體時所指定之暫存資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="0cf67-107">Where name is the name of the staging table that was specified when the entity was created.</span></span>  
  
## <a name="staging-process-stored-procedure-parameters"></a><span data-ttu-id="0cf67-108">暫存處理序預存程序參數</span><span class="sxs-lookup"><span data-stu-id="0cf67-108">Staging Process Stored Procedure Parameters</span></span>  
 <span data-ttu-id="0cf67-109">下表列出這些預存程序的參數。</span><span class="sxs-lookup"><span data-stu-id="0cf67-109">The following table lists the parameters of these stored procedures.</span></span>  
  
|<span data-ttu-id="0cf67-110">參數</span><span class="sxs-lookup"><span data-stu-id="0cf67-110">Parameter</span></span>|<span data-ttu-id="0cf67-111">描述</span><span class="sxs-lookup"><span data-stu-id="0cf67-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0cf67-112">**VersionName**</span><span class="sxs-lookup"><span data-stu-id="0cf67-112">**VersionName**</span></span><br /><br /> <span data-ttu-id="0cf67-113">必要</span><span class="sxs-lookup"><span data-stu-id="0cf67-113">Required</span></span>|<span data-ttu-id="0cf67-114">版本的名稱。</span><span class="sxs-lookup"><span data-stu-id="0cf67-114">The name of the version.</span></span> <span data-ttu-id="0cf67-115">是否區分大小寫取決於您的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 集合設定。</span><span class="sxs-lookup"><span data-stu-id="0cf67-115">This may or may not be case-sensitive, depending on your [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] collation setting.</span></span>|  
|<span data-ttu-id="0cf67-116">**LogFlag**</span><span class="sxs-lookup"><span data-stu-id="0cf67-116">**LogFlag**</span></span><br /><br /> <span data-ttu-id="0cf67-117">必要</span><span class="sxs-lookup"><span data-stu-id="0cf67-117">Required</span></span>|<span data-ttu-id="0cf67-118">決定是否在暫存處理序期間記錄交易。</span><span class="sxs-lookup"><span data-stu-id="0cf67-118">Determines whether transactions are logged during the staging process.</span></span> <span data-ttu-id="0cf67-119">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="0cf67-119">Possible values are:</span></span><br /><br /> <span data-ttu-id="0cf67-120">**0**：不記錄交易。</span><span class="sxs-lookup"><span data-stu-id="0cf67-120">**0**: Do not log transactions.</span></span><br /><span data-ttu-id="0cf67-121">**1**：記錄交易。</span><span class="sxs-lookup"><span data-stu-id="0cf67-121">**1**: Log transactions.</span></span><br /><br /> <br /><br /> <span data-ttu-id="0cf67-122">如需交易的詳細資訊，請參閱[交易 &#40;Master Data Services&#41;](transactions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0cf67-122">For more information about transactions, see [Transactions &#40;Master Data Services&#41;](transactions-master-data-services.md).</span></span>|  
|<span data-ttu-id="0cf67-123">**BatchTag**</span><span class="sxs-lookup"><span data-stu-id="0cf67-123">**BatchTag**</span></span><br /><br /> <span data-ttu-id="0cf67-124">必要項，只有 Web 服務不需要</span><span class="sxs-lookup"><span data-stu-id="0cf67-124">Required, except by web service</span></span>|<span data-ttu-id="0cf67-125">**BatchTag** 值，依暫存資料表中所指定。</span><span class="sxs-lookup"><span data-stu-id="0cf67-125">The **BatchTag** value as specified in the staging table.</span></span>|  
|<span data-ttu-id="0cf67-126">**Batch_ID**</span><span class="sxs-lookup"><span data-stu-id="0cf67-126">**Batch_ID**</span></span><br /><br /> <span data-ttu-id="0cf67-127">只有 Web 服務需要</span><span class="sxs-lookup"><span data-stu-id="0cf67-127">Required by web service only</span></span>|<span data-ttu-id="0cf67-128">**Batch_ID** 值，依暫存資料表中所指定。</span><span class="sxs-lookup"><span data-stu-id="0cf67-128">The **Batch_ID** value as specified in the staging table.</span></span>|  
  
### <a name="staging-process-stored-procedure-example"></a><span data-ttu-id="0cf67-129">暫存處理序預存程序範例</span><span class="sxs-lookup"><span data-stu-id="0cf67-129">Staging Process Stored Procedure Example</span></span>  
 <span data-ttu-id="0cf67-130">下列範例顯示如何使用暫存預存程序啟動暫存處理序。</span><span class="sxs-lookup"><span data-stu-id="0cf67-130">The following example shows how to start the staging process by using the staging stored procedure.</span></span>  
  
```  
USE [DATABASE_NAME]  
GO  
  
EXEC[stg].[udp_name_Leaf]  
      @VersionName = N'VERSION_1',  
@LogFlag = 1,  
@BatchTag = N'batch1'  
  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cf67-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cf67-131">See Also</span></span>  
 <span data-ttu-id="0cf67-132">[驗證預存程式 &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="0cf67-132">[Validation Stored Procedure &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md) </span></span>  
 <span data-ttu-id="0cf67-133">[使用暫存進程在 Master Data Services 中載入或更新成員](add-update-and-delete-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="0cf67-133">[Load or Update Members in Master Data Services by Using the Staging Process](add-update-and-delete-data-master-data-services.md) </span></span>  
 [<span data-ttu-id="0cf67-134">查看暫存進程期間發生的錯誤 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0cf67-134">View Errors that Occur During the Staging Process &#40;Master Data Services&#41;</span></span>](view-errors-that-occur-during-staging-master-data-services.md)  
  
  
