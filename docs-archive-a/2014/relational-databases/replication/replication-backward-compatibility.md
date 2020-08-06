---
title: 複寫回溯相容性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, backward compatibility
- backward compatibility [SQL Server replication]
- merge replication backward compatibility [SQL Server replication]
- replication [SQL Server], backward compatibility
- backward compatibility [SQL Server], replication
- snapshot replication [SQL Server], backward compatibility
- compatibility [SQL Server replication]
ms.assetid: 091c51dc-8b32-4b4f-847e-b317456c8394
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b9cc81d957c754eb792ca589d445f32f2bcd076b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585275"
---
# <a name="replication-backward-compatibility"></a><span data-ttu-id="4b199-102">複寫回溯相容性</span><span class="sxs-lookup"><span data-stu-id="4b199-102">Replication Backward Compatibility</span></span>
  <span data-ttu-id="4b199-103">「回溯相容性」一節中的主題描述複寫版本之間行為上的變更 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4b199-103">Topics in the backward compatibility section describe changes in behavior between versions of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="4b199-104">如果您要升級，或是複寫拓撲中有不只一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本，則一定要了解回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="4b199-104">It is important to understand backward compatibility if you are upgrading or if you have more than one version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a replication topology.</span></span>  
  
 [<span data-ttu-id="4b199-105">SQL Server 複寫中已被取代的功能</span><span class="sxs-lookup"><span data-stu-id="4b199-105">Deprecated Features in SQL Server Replication</span></span>](deprecated-features-in-sql-server-replication.md)  
 <span data-ttu-id="4b199-106">為了 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 與舊版相容而保留的複寫功能，將在未來的版本中移除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4b199-106">Replication features that have been retained in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] for backward compatibility, but which will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="4b199-107">SQL Server 複寫中的重大變更</span><span class="sxs-lookup"><span data-stu-id="4b199-107">Breaking Changes in SQL Server Replication</span></span>](breaking-changes-in-sql-server-replication.md)  
 <span data-ttu-id="4b199-108">需要對應用程式做一些改變的複寫功能變更。</span><span class="sxs-lookup"><span data-stu-id="4b199-108">Replication feature changes that might require changes to applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b199-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b199-109">See Also</span></span>  
 [<span data-ttu-id="4b199-110">升級複寫的資料庫</span><span class="sxs-lookup"><span data-stu-id="4b199-110">Upgrade Replicated Databases</span></span>](../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
  
