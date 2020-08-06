---
title: 檢查磁片輸入輸出子系統的讀取重試問題 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: cedf4097-5b73-4964-9935-74a101847019
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19809b1554e435600eb4eeae424bed17dc27bdbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686919"
---
# <a name="check-disk-input-output-subsystem-for-read-retry-problems"></a><span data-ttu-id="a5f3e-102">檢查磁碟輸入輸出子系統的讀取重試問題</span><span class="sxs-lookup"><span data-stu-id="a5f3e-102">Check Disk Input Output Subsystem for Read Retry Problems</span></span>
  <span data-ttu-id="a5f3e-103">這個規則會檢查事件記錄檔中是否有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤訊息 825。</span><span class="sxs-lookup"><span data-stu-id="a5f3e-103">This rule checks the event log for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error message 825.</span></span> <span data-ttu-id="a5f3e-104">此訊息表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 無法在第一次嘗試時讀取磁碟上的資料。</span><span class="sxs-lookup"><span data-stu-id="a5f3e-104">This message indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] was unable to read data from the disk on the first try.</span></span> <span data-ttu-id="a5f3e-105">此訊息表示磁碟 I/O 子系統發生重大問題。</span><span class="sxs-lookup"><span data-stu-id="a5f3e-105">This message indicates a major problem with the disk I/O subsystem.</span></span> <span data-ttu-id="a5f3e-106">此訊息目前並不表示有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 問題。</span><span class="sxs-lookup"><span data-stu-id="a5f3e-106">This message does not currently indicate a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] problem.</span></span> <span data-ttu-id="a5f3e-107">但是，磁碟問題若沒有解決，可能會導致資料遺失或資料庫損毀。</span><span class="sxs-lookup"><span data-stu-id="a5f3e-107">However, the disk problem could cause data loss or database corruption if it is not resolved.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="a5f3e-108">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="a5f3e-108">Best Practices Recommendations</span></span>  
 <span data-ttu-id="a5f3e-109">下列動作可協助您找出並解決根本硬體問題：</span><span class="sxs-lookup"><span data-stu-id="a5f3e-109">The following actions might help you discover and resolve the underlying hardware problem:</span></span>  
  
-   <span data-ttu-id="a5f3e-110">檢閱錯誤記錄檔和此訊息中的變數文字，找出能夠解釋問題的線索。</span><span class="sxs-lookup"><span data-stu-id="a5f3e-110">Review the error log and the variable text in this message for clues that explain the problem.</span></span>  
  
-   <span data-ttu-id="a5f3e-111">檢查磁碟系統。</span><span class="sxs-lookup"><span data-stu-id="a5f3e-111">Check the disk system.</span></span> <span data-ttu-id="a5f3e-112">問題可能與磁碟、磁碟控制卡、陣列卡，或磁碟驅動程式有關。</span><span class="sxs-lookup"><span data-stu-id="a5f3e-112">The problem could be related to the disks, the disk controllers, array cards, or disk drivers.</span></span>  
  
-   <span data-ttu-id="a5f3e-113">連絡磁碟製造廠商，取得最新的公用程式來檢查磁碟系統的狀態。</span><span class="sxs-lookup"><span data-stu-id="a5f3e-113">Contact the disk manufacturer for the latest utilities for checking the status of the disk system.</span></span>  
  
-   <span data-ttu-id="a5f3e-114">連絡磁碟製造廠商，取得最新的驅動程式更新。</span><span class="sxs-lookup"><span data-stu-id="a5f3e-114">Contact the disk manufacturer for the latest driver updates.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="a5f3e-115">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="a5f3e-115">For More Information</span></span>  
 [<span data-ttu-id="a5f3e-116">MSSQLSERVER_825</span><span class="sxs-lookup"><span data-stu-id="a5f3e-116">MSSQLSERVER_825</span></span>](../errors-events/mssqlserver-825-database-engine-error.md)  
  
 <span data-ttu-id="a5f3e-117">[SQL Server I/O 基本概念，第 2 章](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="a5f3e-117">[SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))</span></span>  
  
  
