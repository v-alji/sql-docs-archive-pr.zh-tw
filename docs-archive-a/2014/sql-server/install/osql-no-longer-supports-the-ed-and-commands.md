---
title: osql 不再支援 ED 和 !! 命令 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- ED command
- osql utility [SQL Server]
- '!! command'
ms.assetid: 7cc2852f-94e8-4292-9326-c3f1a1acd281
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1ad92a32c47002c8f56e56a5b3695d42d3bdd671
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596446"
---
# <a name="osql-no-longer-supports-the-ed-and--commands"></a><span data-ttu-id="ecd3e-103">osql 不再支援 ED 和 !!</span><span class="sxs-lookup"><span data-stu-id="ecd3e-103">osql no longer supports the ED and !!</span></span> <span data-ttu-id="ecd3e-104">命令</span><span class="sxs-lookup"><span data-stu-id="ecd3e-104">commands</span></span>
  <span data-ttu-id="ecd3e-105">**Osql**公用程式不支援**ED**和 **！！**</span><span class="sxs-lookup"><span data-stu-id="ecd3e-105">The **osql** utility does not support the **ED** and **!!**</span></span> <span data-ttu-id="ecd3e-106">指令.</span><span class="sxs-lookup"><span data-stu-id="ecd3e-106">commands.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="ecd3e-107">更正動作</span><span class="sxs-lookup"><span data-stu-id="ecd3e-107">Corrective Action</span></span>  
 <span data-ttu-id="ecd3e-108">移除**ED**和 **！！** 的參考</span><span class="sxs-lookup"><span data-stu-id="ecd3e-108">Remove references to the **ED** and **!!**</span></span> <span data-ttu-id="ecd3e-109">腳本中的命令。</span><span class="sxs-lookup"><span data-stu-id="ecd3e-109">commands from your scripts.</span></span>  
  
 <span data-ttu-id="ecd3e-110">如果您想要使用**ED**和 **！！**</span><span class="sxs-lookup"><span data-stu-id="ecd3e-110">If you want to use the **ED** and **!!**</span></span> <span data-ttu-id="ecd3e-111">命令，請使用**sqlcmd**公用程式，而不是**osql**。</span><span class="sxs-lookup"><span data-stu-id="ecd3e-111">commands, use the **sqlcmd** utility instead of **osql**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecd3e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecd3e-112">See Also</span></span>  
 <span data-ttu-id="ecd3e-113">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="ecd3e-113">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="ecd3e-114">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="ecd3e-114">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
