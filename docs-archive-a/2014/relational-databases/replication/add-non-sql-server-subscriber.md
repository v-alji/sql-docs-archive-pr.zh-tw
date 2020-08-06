---
title: 新增非 SQL Server 訂閱者 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.addnonsqlsubscriber.f1
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e36d048b11fcc71b27ab0ab2ee815b0284187c4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596667"
---
# <a name="add-non-sql-server-subscriber"></a><span data-ttu-id="d8fdd-102">加入非 SQL Server 訂閱者</span><span class="sxs-lookup"><span data-stu-id="d8fdd-102">Add Non-SQL Server Subscriber</span></span>
  <span data-ttu-id="d8fdd-103">複寫可以支援為 Oracle 和 IBM DB2 訂閱者建立快照式和交易式發行集的發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="d8fdd-103">Replication supports creating push subscriptions to snapshot and transactional publications for Oracle and IBM DB2 Subscribers.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d8fdd-104">選項。</span><span class="sxs-lookup"><span data-stu-id="d8fdd-104">Options</span></span>  
 <span data-ttu-id="d8fdd-105">**要加入的訂閱者類型**</span><span class="sxs-lookup"><span data-stu-id="d8fdd-105">**Type of Subscriber to add**</span></span>  
 <span data-ttu-id="d8fdd-106">選取 Oracle 訂閱者或 IBM DB2 訂閱者。</span><span class="sxs-lookup"><span data-stu-id="d8fdd-106">Select an Oracle Subscriber or IBM DB2 Subscriber.</span></span> <span data-ttu-id="d8fdd-107">如需這些訂閱者支援的詳細資訊，請參閱[非 SQL Server 訂閱者](non-sql/non-sql-server-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="d8fdd-107">For more information about support for these Subscribers, see [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md).</span></span>  
  
 <span data-ttu-id="d8fdd-108">**資料來源名稱**</span><span class="sxs-lookup"><span data-stu-id="d8fdd-108">**Data source name**</span></span>  
 <span data-ttu-id="d8fdd-109">在用來尋找網路上之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="d8fdd-109">The name used to locate the database on a network.</span></span> <span data-ttu-id="d8fdd-110">複寫會使用資料來源名稱，結合登入、密碼及您在此精靈的 **[散發代理程式安全性]** 頁面中指定的任何連接選項，來產生資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="d8fdd-110">Replication produces a connection string for the database using the data source name, combined with the login, password, and any connection options you specify in the **Distribution Agent Security** page in this wizard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d8fdd-111">在散發代理程式嘗試初始化訂閱之前， [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不會驗證資料來源名稱和連接字串。</span><span class="sxs-lookup"><span data-stu-id="d8fdd-111">The data source name and connection string are not validated by [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] until the Distribution Agent attempts to initialize the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8fdd-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8fdd-112">See Also</span></span>  
 <span data-ttu-id="d8fdd-113">[為非 SQL Server 訂閱者建立訂閱](create-a-subscription-for-a-non-sql-server-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="d8fdd-113">[Create a Subscription for a Non-SQL Server Subscriber](create-a-subscription-for-a-non-sql-server-subscriber.md) </span></span>  
 <span data-ttu-id="d8fdd-114">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span><span class="sxs-lookup"><span data-stu-id="d8fdd-114">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span></span>  
 [<span data-ttu-id="d8fdd-115">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="d8fdd-115">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
