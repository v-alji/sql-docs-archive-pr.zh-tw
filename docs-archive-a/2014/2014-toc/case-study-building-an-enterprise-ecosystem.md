---
title: 案例研究：使用 Microsoft Dynamics ERP 和 SQL Server 2014 複寫來建立企業生態系統，以提供擴充性和效能 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 2b0b5ab7-4e08-431a-bd59-360177c4565c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: dfde59b5e3e12746aa6dbaf975b079cfe32a3718
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584861"
---
# <a name="case-study-building-an-enterprise-ecosystem-with-microsoft-dynamics-erp-and-sql-server-2014-replication-for-scalability-and-performance"></a><span data-ttu-id="176e2-102">案例研究：使用 Microsoft Dynamics ERP 和 SQL Server 2014 複寫建置具有延展性和效能的企業生態系統。</span><span class="sxs-lookup"><span data-stu-id="176e2-102">Case Study: Building an Enterprise Ecosystem with Microsoft Dynamics ERP and SQL Server 2014 Replication for Scalability and Performance</span></span>

  <span data-ttu-id="176e2-103">**摘要：** 本白皮書涵蓋下列案例：</span><span class="sxs-lookup"><span data-stu-id="176e2-103">**Summary:** This paper covers the following scenarios:</span></span>  
<span data-ttu-id="176e2-104">如何使用 SQL Server 2014 中的異動複寫，將 Dynamics AX 用戶端之間的交易散發到多個節點。</span><span class="sxs-lookup"><span data-stu-id="176e2-104">How to use transactional replication in SQL Server 2014 to distribute the transactions from Dynamics AX clients across multiple nodes.</span></span> <span data-ttu-id="176e2-105">因為資料為跨節點進行即時維護，所以異動複寫提供資料備援來增加資料的可用性，包含可用來讓效能分析更有效率的資料。</span><span class="sxs-lookup"><span data-stu-id="176e2-105">Because data is maintained across the nodes in real-time, transactional replication provides data redundancy, which increases the availability of data, includes data available for more efficient performance analysis.</span></span>  
<span data-ttu-id="176e2-106">如何在運用異動複寫來建置 Microsoft Dynamics ERP 中高擴充性的企業生態系統時，了解所涉及的詳細規格。</span><span class="sxs-lookup"><span data-stu-id="176e2-106">How to understand the specifics involved while leveraging transactional replication to build highly scalable Enterprise ecosystems in Microsoft Dynamics ERP.</span></span> <span data-ttu-id="176e2-107">提供高效能和延展性，且不需自訂 AX 的立即可用功能。</span><span class="sxs-lookup"><span data-stu-id="176e2-107">Deliver high performance and scalability without customizing the AX out-of-box features.</span></span>  
  
 <span data-ttu-id="176e2-108">異動複寫一般用於需要高輸送量的伺服器對伺服器工作流程中。</span><span class="sxs-lookup"><span data-stu-id="176e2-108">Transactional replication is typically used in server-to-server workflows that require high throughput.</span></span> <span data-ttu-id="176e2-109">這些包含案例，例如提升延展性和可用性、資料倉儲和報表、整合多個站台的資料、整合異質資料，以及卸載批次處理。</span><span class="sxs-lookup"><span data-stu-id="176e2-109">These include scenarios, such as improving scalability and availability, data warehousing and reporting, integrating data from multiple sites, integrating heterogeneous data, and offloading batch processing.</span></span> <span data-ttu-id="176e2-110">這份技術白皮書描述一個相異案例及相關聯的模式，內容為在 Microsoft Dynamics ERP 中運用異動複寫。</span><span class="sxs-lookup"><span data-stu-id="176e2-110">This white paper describes a distinct scenario and associated patterns where transactional replication is leveraged in Microsoft Dynamics ERP.</span></span> <span data-ttu-id="176e2-111">其還包含在考慮以異動複寫建置企業資源規劃 (ERP) 特定的企業解決方案時，所會遇到的挑戰和最佳作法，以及不同階段的效能分析。</span><span class="sxs-lookup"><span data-stu-id="176e2-111">It also covers the challenges and best practices when considering transactional replication to build enterprise solutions specific to Enterprise Resource Planning (ERP), as well as the performance analysis at different stages.</span></span>  
  
 <span data-ttu-id="176e2-112">此內容適用於開發人員、架構設計人員和資料庫管理員。</span><span class="sxs-lookup"><span data-stu-id="176e2-112">This content is suitable for developers, architects, and database administrators.</span></span> <span data-ttu-id="176e2-113">這是假設這份技術白皮書的讀者具備 SQL Server 2008、2012 或 2014 以及 SQL Server 管理經驗的基本知識。</span><span class="sxs-lookup"><span data-stu-id="176e2-113">It is assumed that readers of this white paper have basic knowledge of SQL Server 2008, 2012, or 2014 as well as SQL Server administration experience.</span></span>  
  
 <span data-ttu-id="176e2-114">**寫入器：** Prabhakaran Sethuraman (PRAB) ，Microsoft</span><span class="sxs-lookup"><span data-stu-id="176e2-114">**Writer:** Prabhakaran Sethuraman (PRAB), Microsoft</span></span>  
  
 <span data-ttu-id="176e2-115">**技術審核者：** Prabhakaran Sethuraman (PRAB) ，Microsoft;Santosh Padhy，Microsoft;Pavel Majstrov，Microsoft;Karthik Sankaranarayanan，Microsoft;Jon Acone，Microsoft;David Stahlkopf，Microsoft;Kent Oldenburger，Microsoft;Mandi Ohlinger，Microsoft;Jason Roth，Microsoft</span><span class="sxs-lookup"><span data-stu-id="176e2-115">**Technical Reviewers:** Prabhakaran Sethuraman (PRAB), Microsoft; Santosh Padhy, Microsoft; Pavel Majstrov, Microsoft; Karthik Sankaranarayanan, Microsoft; Jon Acone, Microsoft; David Stahlkopf, Microsoft;Kent Oldenburger, Microsoft; Mandi Ohlinger, Microsoft; Jason Roth, Microsoft</span></span>  
  
 <span data-ttu-id="176e2-116">**已發行：** 2015年10月</span><span class="sxs-lookup"><span data-stu-id="176e2-116">**Published:** October 2015</span></span>  
  
 <span data-ttu-id="176e2-117">**適用物件：** SQL Server 2008、SQL Server 2012 及 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="176e2-117">**Applies to:** SQL Server 2008, SQL Server 2012, and SQL Server 2014</span></span>  
  
 <span data-ttu-id="176e2-118">若要查看檔，請下載</span><span class="sxs-lookup"><span data-stu-id="176e2-118">To review the document, please download the</span></span>  
        <span data-ttu-id="176e2-119">[案例研究：使用 Microsoft DYNAMICS ERP 和 SQL Server 2014 複寫來建立企業生態系統，以提供擴充性和效能](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/A%20Case%20Study%20Using%20Replication%20to%20Build%20an%20Enterprise%20Ecosystem%20in%20Microsoft%20Dynamics%20ERP%20for%20Scalability%20and%20Performance.docx)Word 檔。</span><span class="sxs-lookup"><span data-stu-id="176e2-119">[Case Study: Building an Enterprise Ecosystem with Microsoft Dynamics ERP and SQL Server 2014 Replication for Scalability and Performance](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/A%20Case%20Study%20Using%20Replication%20to%20Build%20an%20Enterprise%20Ecosystem%20in%20Microsoft%20Dynamics%20ERP%20for%20Scalability%20and%20Performance.docx) Word document.</span></span>  
  
  
