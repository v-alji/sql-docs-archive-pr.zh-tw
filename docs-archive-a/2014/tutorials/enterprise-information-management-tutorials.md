---
title: 公司資訊管理教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8745dc80-193d-4de0-9f17-ba648ab1e81c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b8cde162479645ab13a6ae000cc46e42e3c10e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598084"
---
# <a name="enterprise-information-management-tutorials"></a><span data-ttu-id="75912-102">企業資訊管理教學課程</span><span class="sxs-lookup"><span data-stu-id="75912-102">Enterprise Information Management Tutorials</span></span>
  <span data-ttu-id="75912-103">本章節包含的教學課程是有關使用 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 中所包含的企業資訊管理 (EIM) 技術來管理企業中的資訊。</span><span class="sxs-lookup"><span data-stu-id="75912-103">This section contains tutorials for managing information in an enterprise by using Enterprise Information Management (EIM) technologies that are included in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span> <span data-ttu-id="75912-104">企業資訊管理 (EIM) 提供一套解決方案組合，可讓組織信任其資料的可信度和一致性，以便他們做出重要的商業決策。</span><span class="sxs-lookup"><span data-stu-id="75912-104">Enterprise Integration Management (EIM) provides a portfolio of solutions that enable organizations to trust the credibility and consistency of their data so they can make critical business decisions.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="75912-105">具有以下技術，可協助您在企業中實作 EIM 解決方案。</span><span class="sxs-lookup"><span data-stu-id="75912-105">has the following technologies that help you implement EIM solutions in your enterprise.</span></span>  
  
-   <span data-ttu-id="75912-106">SQL Server Integration Services (SSIS)。</span><span class="sxs-lookup"><span data-stu-id="75912-106">SQL Server Integration Services (SSIS).</span></span> <span data-ttu-id="75912-107">SSIS 提供了功能強大而且可擴充的平台，透過全面性擷取、轉換和載入 (ETL) 解決方案從各種不同的來源整合資料，這個解決方案可支援商務工作流程、資料倉儲或主要資料管理。</span><span class="sxs-lookup"><span data-stu-id="75912-107">SSIS provides a powerful, extensible platform for integrating data from various sources in a comprehensive extract, transform, and load (ETL) solution that supports business workflows, a data warehouse, or master data management.</span></span>  
  
-   <span data-ttu-id="75912-108">SQL Server Data Quality Services (DQS)。</span><span class="sxs-lookup"><span data-stu-id="75912-108">SQL Server Data Quality Services (DQS).</span></span> <span data-ttu-id="75912-109">DQS 可讓您清理、比對、標準化及充實資料，好讓您可以針對商業智慧、資料倉儲和交易處理工作負載傳遞可靠的資訊。</span><span class="sxs-lookup"><span data-stu-id="75912-109">DQS enables you to cleanse, match, standardize, and enrich data, so you can deliver trusted information for business intelligence, a data warehouse, and transaction processing workloads.</span></span>  
  
-   <span data-ttu-id="75912-110">SQL Server Master Data Services (MDS)。</span><span class="sxs-lookup"><span data-stu-id="75912-110">SQL Server Master Data Services (MDS).</span></span> <span data-ttu-id="75912-111">MDS 提供一個資料中樞，可確保資訊的完整性和資料的一致性在不同應用程式之間都保持不變。</span><span class="sxs-lookup"><span data-stu-id="75912-111">MDS provides a central data hub that ensures that the integrity of information and consistency of data is constant across different applications.</span></span>  
  
 [<span data-ttu-id="75912-112">使用 SSIS、MDS 和 DQS 一起管理公司資訊 &#91;教學課程&#93;</span><span class="sxs-lookup"><span data-stu-id="75912-112">Enterprise Information Management using SSIS, MDS, and DQS Together &#91;Tutorial&#93;</span></span>](../../2014/tutorials/enterprise-information-management-using-ssis-mds-and-dqs-together-[tutorial].md)  
 <span data-ttu-id="75912-113">在本教學課程中，您會學習如何一起使用 SSIS、MDS 和 DQS 來實作範例企業資訊管理 (EIM) 解決方案。</span><span class="sxs-lookup"><span data-stu-id="75912-113">In this tutorial, you learn how to use SSIS, MDS, and DQS together to implement a sample Enterprise Information Management (EIM) solution.</span></span> <span data-ttu-id="75912-114">首先，您會使用 DQS 來建立包含供應商資料 (中繼資料) 相關知識的知識庫、針對知識庫清理 Excel 檔案中的資料，並且比對資料來識別及移除資料的重複項。</span><span class="sxs-lookup"><span data-stu-id="75912-114">First, you use DQS to create a knowledgebase with the knowledge about the supplier data (metadata), cleanse the data in an Excel file against the knowledge base, and match the data to identify and remove duplicates in the data.</span></span> <span data-ttu-id="75912-115">接下來，您會使用適用於 Excel 的 MDS 增益集，將已清理和比對的資料上傳至 MDS。</span><span class="sxs-lookup"><span data-stu-id="75912-115">Next, you use the MDS Add-in for Excel to upload the cleansed and matched data to MDS.</span></span> <span data-ttu-id="75912-116">然後，您會使用 SSIS 解決方案自動化整個程序。</span><span class="sxs-lookup"><span data-stu-id="75912-116">Then, you automate the whole process by using an SSIS solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75912-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75912-117">See Also</span></span>  
 [<span data-ttu-id="75912-118">公司資訊管理-Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="75912-118">Enterprise Information Management - Microsoft SQL Server</span></span>](https://go.microsoft.com/fwlink/?LinkId=270871)  
  
  
