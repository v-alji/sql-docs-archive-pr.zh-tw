---
title: 將資料品質規則套用至資料來源 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d59e6fb5ffb752b3346d40740e0b841bf574344e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687064"
---
# <a name="apply-data-quality-rules-to-data-source"></a><span data-ttu-id="c1989-102">將資料品質規則套用至資料來源</span><span class="sxs-lookup"><span data-stu-id="c1989-102">Apply Data Quality Rules to Data Source</span></span>
  <span data-ttu-id="c1989-103">您可以使用 Data Quality Services (DQS) 修正封裝資料流程中的資料，方法是將 DQS 清理轉換連接至資料來源。</span><span class="sxs-lookup"><span data-stu-id="c1989-103">You can use Data Quality Services (DQS) to correct data in the package data flow by connecting the DQS Cleansing transformation to the data source.</span></span> <span data-ttu-id="c1989-104">如需有關 DQS 的詳細資訊，請參閱＜ [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md)＞。</span><span class="sxs-lookup"><span data-stu-id="c1989-104">For more information about DQS, see [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md).</span></span> <span data-ttu-id="c1989-105">如需此轉換的詳細資訊，請參閱＜ [DQS Cleansing Transformation](dqs-cleansing-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="c1989-105">For more information about the transformation, see [DQS Cleansing Transformation](dqs-cleansing-transformation.md).</span></span>  
  
 <span data-ttu-id="c1989-106">當您使用 DQS 清理轉換處理資料時，會在資料品質伺服器上建立資料品質專案。</span><span class="sxs-lookup"><span data-stu-id="c1989-106">When you process data with the DQS Cleansing transformation, a data quality project is created on the Data Quality Server.</span></span> <span data-ttu-id="c1989-107">您可以使用 Data Quality Client 管理專案。</span><span class="sxs-lookup"><span data-stu-id="c1989-107">You use the Data Quality Client to manage the project.</span></span> <span data-ttu-id="c1989-108">如需詳細資訊，請參閱[管理 &#40;開啟、解除鎖定、重新命名和刪除&#41; 資料品質專案](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)。</span><span class="sxs-lookup"><span data-stu-id="c1989-108">For more information, see [Manage &#40;Open, Unlock, Rename, and Delete&#41; a Data Quality Project](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md).</span></span>  
  
### <a name="to-correct-data-in-the-data-flow"></a><span data-ttu-id="c1989-109">若要更正資料流程中的資料</span><span class="sxs-lookup"><span data-stu-id="c1989-109">To correct data in the data flow</span></span>  
  
1.  <span data-ttu-id="c1989-110">建立封裝。</span><span class="sxs-lookup"><span data-stu-id="c1989-110">Create a package.</span></span>  
  
2.  <span data-ttu-id="c1989-111">加入並設定 DQS 清理轉換。</span><span class="sxs-lookup"><span data-stu-id="c1989-111">Add and configure the DQS Cleansing transformation.</span></span> <span data-ttu-id="c1989-112">如需相關資訊，請參閱 [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="c1989-112">For more information, see [DQS Cleansing Transformation Editor Dialog Box](../../dqs-cleansing-transformation-editor-dialog-box.md).</span></span>  
  
3.  <span data-ttu-id="c1989-113">將 DQS 清理轉換連接至資料來源。</span><span class="sxs-lookup"><span data-stu-id="c1989-113">Connect the DQS Cleansing transformation to a data source.</span></span>  
  
  
