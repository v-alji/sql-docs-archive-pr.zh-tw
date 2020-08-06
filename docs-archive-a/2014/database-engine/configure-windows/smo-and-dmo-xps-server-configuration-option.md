---
title: SMO 和 DMO XPs 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f18fc6fafcf033113c983f990700158a10aec92a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707849"
---
# <a name="smo-and-dmo-xps-server-configuration-option"></a><span data-ttu-id="9a6f0-102">SMO 和 DMO XPs 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="9a6f0-102">SMO and DMO XPs Server Configuration Option</span></span>
  <span data-ttu-id="9a6f0-103">使用 SMO 和 DMO XP 選項可啟用此伺服器上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object (SMO) 擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="9a6f0-103">Use the SMO and DMO XPs option to enable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object (SMO) extended stored procedures on this server.</span></span>  
  
 <span data-ttu-id="9a6f0-104">請注意，從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]開始，已經從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中移除 DMO。</span><span class="sxs-lookup"><span data-stu-id="9a6f0-104">Note than beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], DMO has been removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9a6f0-105">下表說明可用的值：</span><span class="sxs-lookup"><span data-stu-id="9a6f0-105">The possible values are described in the following table:</span></span>  
  
|<span data-ttu-id="9a6f0-106">值</span><span class="sxs-lookup"><span data-stu-id="9a6f0-106">Value</span></span>|<span data-ttu-id="9a6f0-107">意義</span><span class="sxs-lookup"><span data-stu-id="9a6f0-107">Meaning</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="9a6f0-108">0</span><span class="sxs-lookup"><span data-stu-id="9a6f0-108">0</span></span>|<span data-ttu-id="9a6f0-109">無法使用 SMO XP。</span><span class="sxs-lookup"><span data-stu-id="9a6f0-109">SMO XPs are not available.</span></span>|  
|<span data-ttu-id="9a6f0-110">1</span><span class="sxs-lookup"><span data-stu-id="9a6f0-110">1</span></span>|<span data-ttu-id="9a6f0-111">可使用 SMO XP。</span><span class="sxs-lookup"><span data-stu-id="9a6f0-111">SMO XPs are available.</span></span> <span data-ttu-id="9a6f0-112">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="9a6f0-112">This is the default.</span></span>|  
  
 <span data-ttu-id="9a6f0-113">設定會立即生效。</span><span class="sxs-lookup"><span data-stu-id="9a6f0-113">The setting takes effect immediately.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9a6f0-114">範例</span><span class="sxs-lookup"><span data-stu-id="9a6f0-114">Examples</span></span>  
 <span data-ttu-id="9a6f0-115">下列範例會啟用 SMO 擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="9a6f0-115">The following example enables SMO extended stored procedures.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'SMO and DMO XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a6f0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a6f0-116">See Also</span></span>  
 [<span data-ttu-id="9a6f0-117">SQL Server 管理物件 &#40;SMO&#41; 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9a6f0-117">SQL Server Management Objects &#40;SMO&#41; Programming Guide</span></span>](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  
