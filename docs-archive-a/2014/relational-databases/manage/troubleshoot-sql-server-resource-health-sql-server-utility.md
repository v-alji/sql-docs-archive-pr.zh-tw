---
title: 針對 SQL Server 資源健全情況 (SQL Server 公用程式) 進行疑難排解 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 614f07b5-f221-4013-9f8d-22964cf42270
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 182225dd618dd1e9e058c549bdc07818813ba764
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592686"
---
# <a name="troubleshoot-sql-server-resource-health-sql-server-utility"></a><span data-ttu-id="153b8-102">疑難排解 SQL Server 資源健全情況 (SQL Server 公用程式)</span><span class="sxs-lookup"><span data-stu-id="153b8-102">Troubleshoot SQL Server Resource Health (SQL Server Utility)</span></span>
  <span data-ttu-id="153b8-103">疑難排解 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP 找到的資源健全狀況問題可能包括改善電腦或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體中 CPU 的過度使用，或是改善資料層應用程式的 CPU 過度使用。</span><span class="sxs-lookup"><span data-stu-id="153b8-103">Troubleshooting resource health issues identified by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP might include mitigating overutilized CPU on a computer or on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or mitigating overutilized CPU for a data-tier application.</span></span> <span data-ttu-id="153b8-104">其他問題可能還包括解決資料庫檔案的檔案空間過度使用，或是解決存放磁碟區中配置磁碟空間的過度使用。</span><span class="sxs-lookup"><span data-stu-id="153b8-104">Other issues might include resolving overutilized file space for database files or resolving overutilization of allocated disk space on a storage volume.</span></span>  
  
 <span data-ttu-id="153b8-105">請注意，如果資料庫處於「緊急」狀態，則健康狀態會顯示記錄檔空間過度使用。</span><span class="sxs-lookup"><span data-stu-id="153b8-105">Note that if a database is in "emergency" state, the health state will display overutilized log file space.</span></span>  
  
 <span data-ttu-id="153b8-106">如需 UCP 上受管理的執行個體清單檢視中，因資料收集失敗導致灰色狀態圖示的詳細資訊，請參閱 [疑難排解 SQL Server 公用程式](../../database-engine/troubleshoot-the-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="153b8-106">For more information about failed data collection resulting in gray status icons in the managed instance list view on a UCP, see [Troubleshoot the SQL Server Utility](../../database-engine/troubleshoot-the-sql-server-utility.md).</span></span> <span data-ttu-id="153b8-107">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式入門的詳細資訊，請參閱 [SQL Server 公用程式的功能與工作](sql-server-utility-features-and-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="153b8-107">For more information about getting started with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
 <span data-ttu-id="153b8-108">如需改善 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP 所確認之特定資源健全狀況問題的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="153b8-108">For more information about mitigating specific resource health issues identified by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP, see the following topics:</span></span>  
  
-   [<span data-ttu-id="153b8-109">如何識別 SQL Server 版本與版本類型</span><span class="sxs-lookup"><span data-stu-id="153b8-109">How to identify your SQL Server version and edition</span></span>](https://go.microsoft.com/fwlink/?LinkID=178504)  
  
-   [<span data-ttu-id="153b8-110">疑難排解 SQL Server 2008 的效能問題</span><span class="sxs-lookup"><span data-stu-id="153b8-110">Troubleshooting Performance Problems in SQL Server 2008</span></span>](https://go.microsoft.com/fwlink/?LinkId=151354)  
  
  
