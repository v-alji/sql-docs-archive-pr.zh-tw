---
title: xp_cmdshell 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- xp_cmdshell
ms.assetid: c147c9e1-b81d-49c8-b800-3019f4d86a13
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a7feec1765cf6ffaa3e46a300a5155ae73fb13db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607076"
---
# <a name="xp_cmdshell-server-configuration-option"></a><span data-ttu-id="61af8-102">xp_cmdshell 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="61af8-102">xp_cmdshell Server Configuration Option</span></span>
  <span data-ttu-id="61af8-103">**xp_cmdshell** 選項是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 伺服器組態選項，可讓系統管理員控制 **xp_cmdshell** 擴充預存程序是否可在系統上執行。</span><span class="sxs-lookup"><span data-stu-id="61af8-103">The **xp_cmdshell** option is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server configuration option that enables system administrators to control whether the **xp_cmdshell** extended stored procedure can be executed on a system.</span></span> <span data-ttu-id="61af8-104">根據預設， **xp_cmdshell** 選項會在新安裝上停用，而且可以使用原則式管理或執行 **sp_configure** 系統預存程序來啟用，如下列程式碼範例所示：</span><span class="sxs-lookup"><span data-stu-id="61af8-104">By default, the **xp_cmdshell** option is disabled on new installations and can be enabled by using the Policy-Based Management or by running the **sp_configure** system stored procedure as shown in the following code example:</span></span>  
  
```  
-- To allow advanced options to be changed.  
EXEC sp_configure 'show advanced options', 1;  
GO  
-- To update the currently configured value for advanced options.  
RECONFIGURE;  
GO  
-- To enable the feature.  
EXEC sp_configure 'xp_cmdshell', 1;  
GO  
-- To update the currently configured value for this feature.  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="61af8-105">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61af8-105">See Also</span></span>  
 <span data-ttu-id="61af8-106">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="61af8-106">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="61af8-107">使用原則式管理來管理伺服器</span><span class="sxs-lookup"><span data-stu-id="61af8-107">Administer Servers by Using Policy-Based Management</span></span>](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
