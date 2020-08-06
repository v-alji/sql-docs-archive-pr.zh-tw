---
title: 使用交易 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
author: stevestein
ms.author: sstein
ms.openlocfilehash: a075719c8ed31ffcc1c34f2d013a8beb0ae40dae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597065"
---
# <a name="using-transactions"></a><span data-ttu-id="76d6f-102">使用交易</span><span class="sxs-lookup"><span data-stu-id="76d6f-102">Using Transactions</span></span>
  <span data-ttu-id="76d6f-103">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理物件 (SMO) 中，交易處理是藉由使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件，透過與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的連接而達成。</span><span class="sxs-lookup"><span data-stu-id="76d6f-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), transaction processing is achieved through the connection to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span> <span data-ttu-id="76d6f-104">物件 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 是在 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 建立連接時由物件的屬性所參考 <xref:Microsoft.SqlServer.Management.Smo.Server> 。</span><span class="sxs-lookup"><span data-stu-id="76d6f-104">The <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object is referenced by the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server> object when the connection is established.</span></span> <span data-ttu-id="76d6f-105"><xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>、<xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A> 和 <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A> 之類的方法屬於 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 物件屬性。</span><span class="sxs-lookup"><span data-stu-id="76d6f-105">Methods such as <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A>, and <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A> belong to the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> object property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76d6f-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76d6f-106">See Also</span></span>  
 [<span data-ttu-id="76d6f-107">建立 SMO 程式</span><span class="sxs-lookup"><span data-stu-id="76d6f-107">Creating SMO Programs</span></span>](creating-smo-programs.md)  
  
  
