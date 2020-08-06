---
title: Web 伺服器資訊 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.webserverinformation.f1
ms.assetid: 86d72275-45c7-459f-98cf-f5a366ed279c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f7b461ed26b3e234f083add3312e256e164efc9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594473"
---
# <a name="web-server-information"></a><span data-ttu-id="409ea-102">Web 伺服器資訊</span><span class="sxs-lookup"><span data-stu-id="409ea-102">Web Server Information</span></span>
  <span data-ttu-id="409ea-103">使用合併式複寫的 Web 同步處理選項時，需要有 Web 伺服器資訊。</span><span class="sxs-lookup"><span data-stu-id="409ea-103">Web server information is required to use the Web synchronization option for merge replication.</span></span> <span data-ttu-id="409ea-104">如需設定 Web 同步處理的資訊，請參閱[設定 Web 同步處理](configure-web-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="409ea-104">For information about configuring Web synchronization, see [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="409ea-105">選項。</span><span class="sxs-lookup"><span data-stu-id="409ea-105">Options</span></span>  
 <span data-ttu-id="409ea-106">**Web 伺服器位址**</span><span class="sxs-lookup"><span data-stu-id="409ea-106">**Web server address**</span></span>  
 <span data-ttu-id="409ea-107">如果您在 [發行集屬性]  對話方塊的 [FTP 快照集和網際網路]  頁面中，指定了 Web 伺服器位址，該位址就會在此文字方塊中顯示為預設值。</span><span class="sxs-lookup"><span data-stu-id="409ea-107">If you specified a Web server address in the **FTP Snapshot andInternet** page of the **Publication Properties** dialog box, it appears in this text box as a default.</span></span> <span data-ttu-id="409ea-108">接受預設值，或輸入同步處理此訂閱的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) 伺服器之完整 Web 伺服器位址。</span><span class="sxs-lookup"><span data-stu-id="409ea-108">Either accept the default or enter a fully qualified Web server address for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) server that synchronizes this subscription.</span></span>  
  
 <span data-ttu-id="409ea-109">**每一個訂閱者如何連接到 Web 伺服器？**</span><span class="sxs-lookup"><span data-stu-id="409ea-109">**How will each Subscriber connect to the Web server?**</span></span>  
 <span data-ttu-id="409ea-110">指定用於連接到 Web 伺服器的驗證類型。</span><span class="sxs-lookup"><span data-stu-id="409ea-110">Specify the type of authentication used to connect to the Web server.</span></span> <span data-ttu-id="409ea-111">針對 IIS 伺服器連接，建議使用基本驗證搭配安全通訊端層 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="409ea-111">It is recommended to use Basic Authentication for connections to the IIS server in conjunction with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="409ea-112">如果您選取基本驗證，請輸入從訂閱者連接到 IIS 伺服器時所使用的登入名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="409ea-112">If you select Basic Authentication, enter the login and password that will be used to connect from the Subscriber to the IIS server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="409ea-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="409ea-113">See Also</span></span>  
 <span data-ttu-id="409ea-114">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="409ea-114">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="409ea-115">[檢視及修改提取訂閱屬性](view-and-modify-pull-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="409ea-115">[View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md) </span></span>  
 <span data-ttu-id="409ea-116">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span><span class="sxs-lookup"><span data-stu-id="409ea-116">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span></span>  
 <span data-ttu-id="409ea-117">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="409ea-117">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 [<span data-ttu-id="409ea-118">合併式複寫的 Web 同步處理</span><span class="sxs-lookup"><span data-stu-id="409ea-118">Web Synchronization for Merge Replication</span></span>](web-synchronization-for-merge-replication.md)  
  
  
