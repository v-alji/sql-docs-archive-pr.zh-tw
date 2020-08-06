---
title: 不正確具名管道名稱可能會封鎖升級 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- invalid named pipes [SQL Server]
- named pipes
ms.assetid: 58c2199c-4fdf-4d43-ac1c-842703344b75
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: bacfd3d097d7cccb0a5780328c4db95dc5afc733
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708070"
---
# <a name="invalid-named-pipe-name-can-block-upgrade"></a><span data-ttu-id="44804-102">無效的具名管道名稱，可能會防止升級</span><span class="sxs-lookup"><span data-stu-id="44804-102">Invalid named pipe name can block upgrade</span></span>
  <span data-ttu-id="44804-103">如果具名管道通訊協定的設定不正確，升級就會失敗。</span><span class="sxs-lookup"><span data-stu-id="44804-103">Upgrade fails if the named pipes protocol is incorrectly configured.</span></span>  
  
## <a name="component"></a><span data-ttu-id="44804-104">元件</span><span class="sxs-lookup"><span data-stu-id="44804-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="44804-105">描述</span><span class="sxs-lookup"><span data-stu-id="44804-105">Description</span></span>  
 <span data-ttu-id="44804-106">在升級期間，安裝程式會啟動 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 具有共用記憶體支援的實例，這是僅接受本機連接的具名管道。</span><span class="sxs-lookup"><span data-stu-id="44804-106">During upgrade, the Setup program starts the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] instance with shared memory support, a named pipe that only accepts local connections.</span></span> <span data-ttu-id="44804-107">如果伺服器上指定的管道名稱不是空白，它必須以字串 "成 .\pipe" 開頭，才 \\ \\ \\ 會是有效的。</span><span class="sxs-lookup"><span data-stu-id="44804-107">If the pipe name specified on the server is not blank, it must begin with the string "\\\\.\pipe\\" to be valid.</span></span> <span data-ttu-id="44804-108">如果管道名稱無效，[!INCLUDE[ssDE](../../includes/ssde-md.md)] 就不會啟動，而且安裝會失敗。</span><span class="sxs-lookup"><span data-stu-id="44804-108">If the pipe name is not valid, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] will not start, and setup will fail.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="44804-109">更正動作</span><span class="sxs-lookup"><span data-stu-id="44804-109">Corrective Action</span></span>  
 <span data-ttu-id="44804-110">使用\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 網路公用程式\*\*來提供有效的管道名稱，然後執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="44804-110">Use the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Network Utility** to supply a valid pipe name, and then run Setup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44804-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44804-111">See Also</span></span>  
 <span data-ttu-id="44804-112">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="44804-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="44804-113">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="44804-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
