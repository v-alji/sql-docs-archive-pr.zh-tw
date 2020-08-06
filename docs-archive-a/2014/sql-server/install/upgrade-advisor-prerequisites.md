---
title: Upgrade Advisor 必要條件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- requirements [Upgrade Advisor]
- software [Upgrade Advisor]
- system requirements [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, prerequisites
- prerequisites [Upgrade Advisor]
- Upgrade Advisor [SQL Server], prerequisites
ms.assetid: d21a39e5-5f81-4096-a7dd-f244e4779992
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 41c97cf585d1768c7aebeec2613ee8744cb220da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595415"
---
# <a name="upgrade-advisor-prerequisites"></a><span data-ttu-id="75064-102">Upgrade Advisor 必要條件</span><span class="sxs-lookup"><span data-stu-id="75064-102">Upgrade Advisor Prerequisites</span></span>
  <span data-ttu-id="75064-103">此主題描述 Upgrade Advisor 的軟體需求。</span><span class="sxs-lookup"><span data-stu-id="75064-103">This topic describes the software requirements for Upgrade Advisor.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="75064-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="75064-104">Prerequisites</span></span>  
 <span data-ttu-id="75064-105">安裝和執行 Upgrade Advisor 的必要條件如下：</span><span class="sxs-lookup"><span data-stu-id="75064-105">The prerequisites for installing and running Upgrade Advisor are as follows:</span></span>  
  
-   [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)]<span data-ttu-id="75064-106">SP1、[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] (從 SP2 開始)、Windows 7 或 [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] R2。</span><span class="sxs-lookup"><span data-stu-id="75064-106">SP1, [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] beginning with SP2, Windows 7, or [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] R2.</span></span>  
  
-   <span data-ttu-id="75064-107">Windows Installer 4.5。</span><span class="sxs-lookup"><span data-stu-id="75064-107">Windows Installer 4.5.</span></span> <span data-ttu-id="75064-108">您可以從[Windows Installer 的網站](https://www.microsoft.com/download/details.aspx?id=8483)安裝 Windows Installer。</span><span class="sxs-lookup"><span data-stu-id="75064-108">You can install Windows Installer from the [Windows Installer Web site](https://www.microsoft.com/download/details.aspx?id=8483).</span></span>  
  
-   <span data-ttu-id="75064-109">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] (從 .NET Framework 4 開始)。</span><span class="sxs-lookup"><span data-stu-id="75064-109">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], beginning with .NET Framework 4.</span></span> <span data-ttu-id="75064-110">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]可以在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 產品媒體上取得，並從 SDK、可轉散發套件[和 Service Pack 下載網站](https://go.microsoft.com/fwlink/?LinkId=48882)取得。</span><span class="sxs-lookup"><span data-stu-id="75064-110">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] is available on the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] product media, and from the [SDK, redistributable, and service pack download Web site](https://go.microsoft.com/fwlink/?LinkId=48882).</span></span>  
  
    -   <span data-ttu-id="75064-111">若要從 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 媒體安裝 .NET Framework 4，請找出光碟機的根目錄。</span><span class="sxs-lookup"><span data-stu-id="75064-111">To install the .NET Framework 4 from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] media, locate the root of the disk drive.</span></span> <span data-ttu-id="75064-112">接著按兩下 \redist 資料夾、按兩下 DotNetFrameworks 資料夾，然後執行 dotNetFx40_Full_x86_x64.exe (適用於 32 位元和 64 位元作業系統)。</span><span class="sxs-lookup"><span data-stu-id="75064-112">Then double-click the \redist folder, double-click the DotNetFrameworks folder, and run dotNetFx40_Full_x86_x64.exe (for both 32-bit and 64-bit operating systems).</span></span>  
  
-   <span data-ttu-id="75064-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom 是安裝 upgrade advisor 的必要條件 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，而且不是由 Upgrade advisor 安裝程式所安裝。</span><span class="sxs-lookup"><span data-stu-id="75064-113">The [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom is a prerequisite for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor, and is not installed by Upgrade Advisor Setup.</span></span> <span data-ttu-id="75064-114">安裝程式會要求您 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 從 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 功能套件下載並安裝 ScriptDom。</span><span class="sxs-lookup"><span data-stu-id="75064-114">The Setup requires you to download and install the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75064-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75064-115">See Also</span></span>  
 [<span data-ttu-id="75064-116">如何：安裝升級建議程式</span><span class="sxs-lookup"><span data-stu-id="75064-116">How to: Install Upgrade Advisor</span></span>](../../../2014/sql-server/install/how-to-install-upgrade-advisor.md)  
  
  
