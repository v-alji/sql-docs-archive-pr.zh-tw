---
title: 結論 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b1e6fde6-c3a7-4b91-b176-fa465325dd21
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 906f9f10c541e7662d5573fd242a84f37483166e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704482"
---
# <a name="conclusion"></a><span data-ttu-id="1428f-102">結論</span><span class="sxs-lookup"><span data-stu-id="1428f-102">Conclusion</span></span>
  <span data-ttu-id="1428f-103">在本教學課程中，您已學會如何一起使用 SQL Server Integration Services (SSIS)、Master Data Services (MDS) 和 Data Quality Services (DQS) 來實作範例企業資訊管理 (EIM) 解決方案。</span><span class="sxs-lookup"><span data-stu-id="1428f-103">In this tutorial, you have learned how to use SQL Server Integration Services (SSIS), Master Data Services (MDS), and Data Quality Services (DQS) together to implement a sample Enterprise Information Management (EIM) solution.</span></span> <span data-ttu-id="1428f-104">首先，您使用 Data Quality Client 工具來建立包含供應商相關知識的 DQS 知識庫、針對知識庫清理 Excel 檔案中的供應商輸入資料，然後使用知識庫中的比對原則來比對供應商資料，以識別及移除資料中的重複項。</span><span class="sxs-lookup"><span data-stu-id="1428f-104">First, you used the Data Quality Client tool to create a DQS knowledge base with the knowledge about suppliers, cleansed the input supplier data in an excel file against the knowledge base, and then matched the supplier data by using a matching policy in the knowledge base to identify and remove duplicates in the data.</span></span> <span data-ttu-id="1428f-105">接下來，您使用適用於 Excel 的 MDS 增益集，將已清理和比對的供應商清單儲存在 MDS 中。</span><span class="sxs-lookup"><span data-stu-id="1428f-105">Next, by using the MDS Add-in for Excel, you stored the cleansed and matched supplier list in MDS.</span></span> <span data-ttu-id="1428f-106">最後，您藉由建立 SSIS 解決方案，將接收輸入資料、清理及比對資料並在 MDS 中儲存主要資料的整個過程自動化。</span><span class="sxs-lookup"><span data-stu-id="1428f-106">Finally, you automated the whole process of receiving input data, cleansing and matching the data, and storing the master data in MDS by creating an SSIS solution.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="1428f-107">其他資訊：</span><span class="sxs-lookup"><span data-stu-id="1428f-107">For more information:</span></span>  
  
 [<span data-ttu-id="1428f-108">企業資訊管理 (EIM)：結合使用 SSIS、DQS 和 MDS (影片)</span><span class="sxs-lookup"><span data-stu-id="1428f-108">Enterprise Information Management (EIM): Bringing together SSIS, DQS, and MDS (Video)</span></span>](https://go.microsoft.com/fwlink/?LinkId=258672)  
  
  
