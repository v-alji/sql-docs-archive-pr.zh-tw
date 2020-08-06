---
title: SQL Server Reporting Services Standard 和 Enterprise 之 CPU 和記憶體限制的變更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: dd553715-2b95-4119-8f58-d01de388d9ab
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: bd889344f5b0bc72320ff8467ebd6ecc654872f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593780"
---
# <a name="changes-to-cpu-and-memory-limits-for-sql-server-reporting-services-standard-and-enterprise"></a><span data-ttu-id="21f46-102">SQL Server Reporting Services Standard 和 Enterprise 之 CPU 和記憶體限制的變更</span><span class="sxs-lookup"><span data-stu-id="21f46-102">Changes to CPU and memory limits for SQL Server Reporting Services Standard and Enterprise</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="21f46-103">Reporting Services Standard 和 Enterprise 最多可支援 64 GB 的系統記憶體。</span><span class="sxs-lookup"><span data-stu-id="21f46-103">Reporting Services Standard and Enterprise supports a maximum of 64 gigabytes of system memory.</span></span>  
  
## <a name="component"></a><span data-ttu-id="21f46-104">元件</span><span class="sxs-lookup"><span data-stu-id="21f46-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
### <a name="description"></a><span data-ttu-id="21f46-105">描述</span><span class="sxs-lookup"><span data-stu-id="21f46-105">Description</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="21f46-106">Reporting Services Standard 和 Enterprise 最多可支援 64 GB 的系統記憶體。</span><span class="sxs-lookup"><span data-stu-id="21f46-106">Reporting Services Standard and Enterprise supports a maximum of 64 gigabytes of system memory.</span></span> <span data-ttu-id="21f46-107">您可能需要重新設定目前的系統設定，才能符合新的限制。</span><span class="sxs-lookup"><span data-stu-id="21f46-107">You may need to reconfigure your current system settings to align with the new limits.</span></span>  
  
 <span data-ttu-id="21f46-108">如需有關其他版本之 CPU 和記憶體限制的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[依 SQL Server 版本的計算容量限制](../compute-capacity-limits-by-edition-of-sql-server.md)和[SQL Server 版本支援的記憶體](https://go.microsoft.com/fwlink/?LinkId=212633)。</span><span class="sxs-lookup"><span data-stu-id="21f46-108">For more information about CPU and memory limits for other editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Compute Capacity Limits by Edition of SQL Server](../compute-capacity-limits-by-edition-of-sql-server.md), and [Memory Supported by the Editions of SQL Server](https://go.microsoft.com/fwlink/?LinkId=212633).</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="21f46-109">更正動作</span><span class="sxs-lookup"><span data-stu-id="21f46-109">Corrective Action</span></span>  
 <span data-ttu-id="21f46-110">您可能需要重新設定目前的系統設定，才能符合新的 CPU 和記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="21f46-110">You may need to reconfigure your current system settings to align with the new CPU and memory limits.</span></span> <span data-ttu-id="21f46-111">如需詳細資訊，請參閱[ALTER SERVER configuration &#40;transact-sql&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)和[伺服器記憶體伺服器設定選項](../../database-engine/configure-windows/server-memory-server-configuration-options.md)。</span><span class="sxs-lookup"><span data-stu-id="21f46-111">For more information, see [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql), and [Server Memory Server Configuration Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f46-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21f46-112">See Also</span></span>  
 <span data-ttu-id="21f46-113">[SQL Server 2014 版本所支援的功能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="21f46-113">[Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 [<span data-ttu-id="21f46-114">回溯相容性</span><span class="sxs-lookup"><span data-stu-id="21f46-114">Backward Compatibility</span></span>](../../../2014/getting-started/backward-compatibility.md)  
  
  
