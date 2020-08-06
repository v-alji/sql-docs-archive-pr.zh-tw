---
title: 安裝 Upgrade Advisor |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: 1b7d6eca-1df1-47df-bbba-0fc485706a95
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 40f214b01f3e2066708a060c5f3ad1e8aa4a0a23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688449"
---
# <a name="installing-upgrade-advisor"></a><span data-ttu-id="b156a-102">安裝 Upgrade Advisor</span><span class="sxs-lookup"><span data-stu-id="b156a-102">Installing Upgrade Advisor</span></span>
  <span data-ttu-id="b156a-103">安裝 SQL Server 2014 Upgrade Advisor 的位置會因您要分析的項目而不同。</span><span class="sxs-lookup"><span data-stu-id="b156a-103">Where you install SQL Server 2014 Upgrade Advisor depends on what you will be analyzing.</span></span> <span data-ttu-id="b156a-104">Upgrade Advisor 支援所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件的遠端分析，但 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]除外。</span><span class="sxs-lookup"><span data-stu-id="b156a-104">Upgrade Advisor supports remote analysis of all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components except [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="b156a-105">如果您未掃描的實例 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，您可以在任何可連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 且符合[Upgrade advisor 必要條件](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)的電腦上安裝 Upgrade Advisor。</span><span class="sxs-lookup"><span data-stu-id="b156a-105">If you are not scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can install Upgrade Advisor on any computer that can connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and that meets the [Upgrade Advisor Prerequisites](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md).</span></span> <span data-ttu-id="b156a-106">如果您要掃描 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的執行個體，則必須將 Upgrade Advisor 安裝在報表伺服器上。</span><span class="sxs-lookup"><span data-stu-id="b156a-106">If you are scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must install Upgrade Advisor on the report server.</span></span>  
  
 <span data-ttu-id="b156a-107">執行 **SQLUA.msi** 檔，以便安裝 Upgrade Advisor。</span><span class="sxs-lookup"><span data-stu-id="b156a-107">Run the **SQLUA.msi** file to install Upgrade Advisor.</span></span> <span data-ttu-id="b156a-108">您可以從命令提示字元進行自主式且自動化安裝。</span><span class="sxs-lookup"><span data-stu-id="b156a-108">You can install from the command prompt for unattended and automated installations.</span></span> <span data-ttu-id="b156a-109">請參閱＜ [Installing Upgrade Advisor from the Command Prompt](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md) ＞，以取得語法和範例。</span><span class="sxs-lookup"><span data-stu-id="b156a-109">See [Installing Upgrade Advisor from the Command Prompt](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md) for syntax and examples.</span></span>  
  
 <span data-ttu-id="b156a-110">取得 SQLUA.msi：</span><span class="sxs-lookup"><span data-stu-id="b156a-110">Get SQLUA.msi:</span></span>  
  
-   <span data-ttu-id="b156a-111">在 **產品媒體的** redist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b156a-111">In the **redist** folder of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] product media.</span></span>  
  
-   <span data-ttu-id="b156a-112">作為 [SQL 2014 功能套件下載](https://www.microsoft.com/download/details.aspx?id=42295)的一部分。</span><span class="sxs-lookup"><span data-stu-id="b156a-112">As part of the [SQL 2014 Feature Pack download](https://www.microsoft.com/download/details.aspx?id=42295).</span></span>  
  
## <a name="uninstalling-upgrade-advisor"></a><span data-ttu-id="b156a-113">解除安裝 Upgrade Advisor</span><span class="sxs-lookup"><span data-stu-id="b156a-113">Uninstalling Upgrade Advisor</span></span>  
 <span data-ttu-id="b156a-114">您可以使用 **[新增或移除程式]** 來解除安裝 Upgrade Advisor。</span><span class="sxs-lookup"><span data-stu-id="b156a-114">You can uninstall Upgrade Advisor by using **Add or Remove Programs**.</span></span> <span data-ttu-id="b156a-115">命令提示字元語法也支援移除/解除安裝。</span><span class="sxs-lookup"><span data-stu-id="b156a-115">The command prompt syntax also supports removal/uninstall.</span></span>  
  
  
