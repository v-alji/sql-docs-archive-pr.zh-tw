---
title: EKM provider enabled 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- external encryption provider
helpviewer_keywords:
- EKM provider enabled option
ms.assetid: da58ed50-3a13-4172-9065-960559d8f383
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1b44e7f5e0801bb370a98abe79a6ea449c6f7409
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708605"
---
# <a name="ekm-provider-enabled-server-configuration-option"></a><span data-ttu-id="8d4a6-102">EKM provider enabled 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="8d4a6-102">EKM provider enabled Server Configuration Option</span></span>
  <span data-ttu-id="8d4a6-103">`EKM provider enabled` 選項可控制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的可延伸金鑰管理裝置支援。</span><span class="sxs-lookup"><span data-stu-id="8d4a6-103">The `EKM provider enabled` option controls Extensible Key Management device support in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8d4a6-104">根據預設，這個選項是關閉的。</span><span class="sxs-lookup"><span data-stu-id="8d4a6-104">By default this option is off.</span></span>  
  
 <span data-ttu-id="8d4a6-105">若要啟用或停用此功能，請發出下列其中一個 `sp_configure` 命令：</span><span class="sxs-lookup"><span data-stu-id="8d4a6-105">To enable or disable the feature, issue one of the following `sp_configure` commands:</span></span>  
  
```  
/* Enable the external encryption provider option */  
sp_configure 'EKM provider enabled', 1  
/* Disable the external encryption provider option */  
sp_configure 'EKM provider enabled', 0  
```  
  
> [!NOTE]  
>  <span data-ttu-id="8d4a6-106">並非每個 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本都會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="8d4a6-106">This option is not enabled in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8d4a6-107">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="8d4a6-107">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d4a6-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d4a6-108">See Also</span></span>  
 <span data-ttu-id="8d4a6-109">[可延伸金鑰管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md) </span><span class="sxs-lookup"><span data-stu-id="8d4a6-109">[Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md) </span></span>  
 <span data-ttu-id="8d4a6-110">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8d4a6-110">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="8d4a6-111">[監視資源使用量 &#40;系統監視器&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="8d4a6-111">[Monitor Resource Usage &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="8d4a6-112">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8d4a6-112">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="8d4a6-113">RECONFIGURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8d4a6-113">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
