---
title: OLE Automation 程序伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Ole Automation Procedures option
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d34615ce1f808c1015c9c3d312a38a67dba291b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687147"
---
# <a name="ole-automation-procedures-server-configuration-option"></a><span data-ttu-id="770de-102">OLE Automation 程序伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="770de-102">Ole Automation Procedures Server Configuration Option</span></span>
  <span data-ttu-id="770de-103">使用 `Ole Automation Procedures` 選項可指定 OLE Automation 物件是否可在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次內部啟動。</span><span class="sxs-lookup"><span data-stu-id="770de-103">Use the `Ole Automation Procedures` option to specify whether OLE Automation objects can be instantiated within [!INCLUDE[tsql](../../includes/tsql-md.md)] batches.</span></span> <span data-ttu-id="770de-104">您也可以使用以原則為基礎的管理或 **sp_configure** 預存程序來設定這個選項。</span><span class="sxs-lookup"><span data-stu-id="770de-104">This option can also be configured using the Policy-Based Management or the **sp_configure** stored procedure.</span></span> <span data-ttu-id="770de-105">如需詳細資訊，請參閱＜ [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)＞。</span><span class="sxs-lookup"><span data-stu-id="770de-105">For more information, see [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).</span></span>  
  
 <span data-ttu-id="770de-106">`Ole Automation Procedures` 選項可設定為下列值：</span><span class="sxs-lookup"><span data-stu-id="770de-106">The `Ole Automation Procedures` option can be set to the following values.</span></span>  
  
 <span data-ttu-id="770de-107">0</span><span class="sxs-lookup"><span data-stu-id="770de-107">0</span></span>  
 <span data-ttu-id="770de-108">停用 OLE Automation Procedures。</span><span class="sxs-lookup"><span data-stu-id="770de-108">OLE Automation Procedures are disabled.</span></span> <span data-ttu-id="770de-109">這是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]新執行個體的預設值。</span><span class="sxs-lookup"><span data-stu-id="770de-109">Default for new instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="770de-110">1</span><span class="sxs-lookup"><span data-stu-id="770de-110">1</span></span>  
 <span data-ttu-id="770de-111">啟用 OLE Automation Procedures。</span><span class="sxs-lookup"><span data-stu-id="770de-111">OLE Automation Procedures are enabled.</span></span>  
  
 <span data-ttu-id="770de-112">啟用 OLE Automation 程序時，對 **sp_OACreate** 的呼叫會啟動 OLE 共用執行環境。</span><span class="sxs-lookup"><span data-stu-id="770de-112">When OLE Automation Procedures are enabled, a call to **sp_OACreate** will start the OLE shared execution environment.</span></span>  
  
 <span data-ttu-id="770de-113">您 `Ole Automation Procedures` 可以使用**sp_configure**系統預存程式，來查看和變更選項的目前值。</span><span class="sxs-lookup"><span data-stu-id="770de-113">The current value of the `Ole Automation Procedures` option can be viewed and changed by using the **sp_configure** system stored procedure.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="770de-114">範例</span><span class="sxs-lookup"><span data-stu-id="770de-114">Examples</span></span>  
 <span data-ttu-id="770de-115">下列範例顯示如何檢視 OLE Automation Procedures 的目前設定。</span><span class="sxs-lookup"><span data-stu-id="770de-115">The following example shows how to view the current setting of OLE Automation procedures.</span></span>  
  
```  
EXEC sp_configure 'Ole Automation Procedures';  
GO  
```  
  
 <span data-ttu-id="770de-116">下列範例顯示如何啟用 OLE Automation Procedures。</span><span class="sxs-lookup"><span data-stu-id="770de-116">The following example shows how to enable OLE Automation procedures.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Ole Automation Procedures', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="770de-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="770de-117">See Also</span></span>  
 <span data-ttu-id="770de-118">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="770de-118">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="770de-119">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="770de-119">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="770de-120">[介面區組態](../../relational-databases/security/surface-area-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="770de-120">[Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md) </span></span>  
 [<span data-ttu-id="770de-121">伺服器組態選項 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="770de-121">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
