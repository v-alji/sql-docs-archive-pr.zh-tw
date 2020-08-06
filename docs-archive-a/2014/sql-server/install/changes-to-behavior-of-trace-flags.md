---
title: 追蹤旗標行為的變更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- trace flags [SQL Server], behavior changes
ms.assetid: d739df96-2659-4383-8e10-194657632526
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 11d71e8401f6b870aaeb3f64f4145b509e3a3fe0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595516"
---
# <a name="changes-to-behavior-of-trace-flags"></a><span data-ttu-id="58a5c-102">追蹤旗標之行為的變更</span><span class="sxs-lookup"><span data-stu-id="58a5c-102">Changes to behavior of trace flags</span></span>
  <span data-ttu-id="58a5c-103">工作階段所設定的全域追蹤旗標會立即在其他工作階段中生效。</span><span class="sxs-lookup"><span data-stu-id="58a5c-103">Global trace flags set by a session take effect in other sessions immediately.</span></span> <span data-ttu-id="58a5c-104">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 的某些追蹤旗標不存在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="58a5c-104">Some trace flags from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] do not exist in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="58a5c-105">元件</span><span class="sxs-lookup"><span data-stu-id="58a5c-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="58a5c-106">描述</span><span class="sxs-lookup"><span data-stu-id="58a5c-106">Description</span></span>  
 <span data-ttu-id="58a5c-107">我們建議您在升級之前停用所有追蹤旗標。</span><span class="sxs-lookup"><span data-stu-id="58a5c-107">We recommend that you disable all trace flags before you upgrade.</span></span> <span data-ttu-id="58a5c-108">修改資料庫可用性或復原模式的追蹤旗標可能會讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 無法成功升級的實例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="58a5c-108">Trace flags that modify the database availability or recovery modes might prevent the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] from successfully upgrading your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="58a5c-109">在您確認這些追蹤旗標是必要的，而且在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中仍然有效之後，就可以啟用這些追蹤旗標。</span><span class="sxs-lookup"><span data-stu-id="58a5c-109">You can enable the trace flags after you verify that the trace flags are required and are still valid in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="58a5c-110">如果您必須重新啟用追蹤旗標，就應該在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上執行其他測試。</span><span class="sxs-lookup"><span data-stu-id="58a5c-110">If you must re-enable trace flags, you should perform additional tests on your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="58a5c-111">支援全域和工作階段層級追蹤旗標。</span><span class="sxs-lookup"><span data-stu-id="58a5c-111">supports global and session level trace flags.</span></span> <span data-ttu-id="58a5c-112">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中，您可以在 DBCC TRACEON 命令中使用其他引數 (-1)，將追蹤旗標指定為本機或全域。</span><span class="sxs-lookup"><span data-stu-id="58a5c-112">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], trace flags can be specified as either local or global by using an additional argument (-1) in the DBCC TRACEON command.</span></span> <span data-ttu-id="58a5c-113">如果沒有指定這個引數，預設值就是本機。</span><span class="sxs-lookup"><span data-stu-id="58a5c-113">If this argument is not specified, the default value is local.</span></span>  
  
 <span data-ttu-id="58a5c-114">此外，在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中，在工作階段 A 中設定的旗標不會自動在已經存在的工作階段 B 中生效。相反地，只有第一次在工作階段 B 中設定追蹤旗標之後，該追蹤旗標才會生效。這個行為在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中不具決定性，而在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本中則具決定性，因為在工作階段 A 中設定的全域追蹤旗標會立即在其他並行工作階段中設定。</span><span class="sxs-lookup"><span data-stu-id="58a5c-114">Also, in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], a trace flag set in session A does not automatically take effect in an already existing session B. Instead, this trace flag takes effect only after the first time any trace flag is set in session B. This behavior is nondeterministic in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] and is deterministic in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions, where global trace flags set in session A are set immediately in other concurrent sessions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58a5c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58a5c-115">See Also</span></span>  
 <span data-ttu-id="58a5c-116">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="58a5c-116">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="58a5c-117">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="58a5c-117">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
