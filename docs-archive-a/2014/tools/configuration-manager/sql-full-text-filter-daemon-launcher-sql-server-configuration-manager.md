---
title: SQL 全文檢索篩選精靈啟動器 (SQL Server 設定管理員) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: d0dc03db-5f76-4558-b041-1ac7b9b5bb16
author: stevestein
ms.author: sstein
ms.openlocfilehash: 45194c893db048151cdb03d33f1419ef42246d69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584931"
---
# <a name="sql-full-text-filter-daemon-launcher-sql-server-configuration-manager"></a><span data-ttu-id="9e591-102">SQL 全文檢索篩選背景程式啟動器 (SQL Server 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="9e591-102">SQL Full-text Filter Daemon Launcher (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="9e591-103">從 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]開始， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文檢索搜尋就會使用 SQL 全文檢索篩選背景程式啟動器 (FDHOST 啟動器) 服務來啟動篩選背景程式主機處理序，以便處理全文檢索搜尋篩選和斷詞。</span><span class="sxs-lookup"><span data-stu-id="9e591-103">Beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the SQL Full-text Filter Daemon Launcher (FDHOST Launcher) service is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text search to start the filter daemon host process, which handles full-text search filtering and word breaking.</span></span> <span data-ttu-id="9e591-104">若要使用全文檢索搜尋，您必須執行這個服務。</span><span class="sxs-lookup"><span data-stu-id="9e591-104">This service must be running to use full-text search.</span></span> <span data-ttu-id="9e591-105">FDHOST 啟動器服務是一個與特定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體有關的執行個體感知服務。</span><span class="sxs-lookup"><span data-stu-id="9e591-105">The FDHOST Launcher service is an instance-aware service that is associated with a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9e591-106">FDHOST 啟動器服務會將服務帳戶資訊傳播至啟動的每個篩選背景程式主機處理序。</span><span class="sxs-lookup"><span data-stu-id="9e591-106">The FDHOST Launcher service propagates the service account information to each filter daemon host process started.</span></span> <span data-ttu-id="9e591-107">如需有關篩選背景程式主機處理序的詳細資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜全文檢索搜尋架構＞。</span><span class="sxs-lookup"><span data-stu-id="9e591-107">For information about the filter daemon host processes, see "Full-Text Search Architecture" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
  
