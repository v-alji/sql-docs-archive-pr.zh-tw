---
title: 伺服器屬性 (其他伺服器設定頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.miscserversettings.f1
ms.assetid: b170c066-30cd-42dd-8d34-aa129ea09551
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9a82a787140141c3bfa7b18776328a813be9f41f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596897"
---
# <a name="server-properties-misc-server-settings-page"></a><span data-ttu-id="561f7-102">伺服器屬性 (其他伺服器設定頁面)</span><span class="sxs-lookup"><span data-stu-id="561f7-102">Server Properties (Misc Server Settings Page)</span></span>
  <span data-ttu-id="561f7-103">使用此頁面來檢視或修改伺服器設定。</span><span class="sxs-lookup"><span data-stu-id="561f7-103">Use this page to view or modify your server settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="561f7-104">選項。</span><span class="sxs-lookup"><span data-stu-id="561f7-104">Options</span></span>  
 <span data-ttu-id="561f7-105">**使用者的預設語言**</span><span class="sxs-lookup"><span data-stu-id="561f7-105">**Default language for users**</span></span>  
 <span data-ttu-id="561f7-106">指定所有新建立之登入的預設語言。</span><span class="sxs-lookup"><span data-stu-id="561f7-106">Specifies the default language for all newly created logins.</span></span>  
  
 <span data-ttu-id="561f7-107">**允許觸發程序引發其他觸發程序**</span><span class="sxs-lookup"><span data-stu-id="561f7-107">**Allow triggers to fire other triggers**</span></span>  
 <span data-ttu-id="561f7-108">控制觸發程序是否可以執行起始另一個觸發程序的動作。</span><span class="sxs-lookup"><span data-stu-id="561f7-108">Controls whether a trigger can perform an action that initiates another trigger.</span></span> <span data-ttu-id="561f7-109">清除此選項時，無法由另一個觸發程序來引發觸發程序。</span><span class="sxs-lookup"><span data-stu-id="561f7-109">When cleared, triggers cannot be fired by another trigger.</span></span> <span data-ttu-id="561f7-110">選取此選項時，可以由另一個觸發程序來引發觸發程序，最多可達 32 個層級。</span><span class="sxs-lookup"><span data-stu-id="561f7-110">When selected, triggers can be fired by other triggers to as many as 32 levels.</span></span>  
  
 <span data-ttu-id="561f7-111">**使用查詢管理員防止長期執行的查詢**</span><span class="sxs-lookup"><span data-stu-id="561f7-111">**Use query governor to prevent long-running queries**</span></span>  
 <span data-ttu-id="561f7-112">指定可在其中執行查詢的時間上限。</span><span class="sxs-lookup"><span data-stu-id="561f7-112">Specifies an upper limit on the time within which a query can run.</span></span> <span data-ttu-id="561f7-113">查詢成本代表在特定的硬體組態上，預估執行查詢所需的時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="561f7-113">Query cost refers to the estimated elapsed time, in seconds, required to execute a query on a specific hardware configuration.</span></span> <span data-ttu-id="561f7-114">依預設，查詢管理員會關閉而允許執行所有查詢。</span><span class="sxs-lookup"><span data-stu-id="561f7-114">By default, the query governor is turned off and all queries are allowed to run.</span></span> <span data-ttu-id="561f7-115">如果選取此選項，您必須在下面文字方塊中輸入時間限制。</span><span class="sxs-lookup"><span data-stu-id="561f7-115">If this option is selected, you must enter a time limit in the text box below.</span></span> <span data-ttu-id="561f7-116">如果指定非零的非負值，查詢若超過該值的估計成本，查詢管理員就不允許執行此查詢。</span><span class="sxs-lookup"><span data-stu-id="561f7-116">If you specify a nonzero, nonnegative value, the query governor disallows execution of any query that has an estimated cost exceeding that value.</span></span>  
  
 <span data-ttu-id="561f7-117">**將兩位數年份解譯為介於**</span><span class="sxs-lookup"><span data-stu-id="561f7-117">**Interpret a two-digit year as falling between**</span></span>  
 <span data-ttu-id="561f7-118">指定用於解譯兩位數年份值的 100 年日期範圍。</span><span class="sxs-lookup"><span data-stu-id="561f7-118">Specifies the 100-year date range for interpreting two-digit year values.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="561f7-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將參考指定範圍的年份來解譯兩位數日期值。</span><span class="sxs-lookup"><span data-stu-id="561f7-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will interpret two-digit date values to refer to the year ending in those digits that falls within the specified range.</span></span>  
  
 <span data-ttu-id="561f7-120">以結束年份設定右邊的方塊。</span><span class="sxs-lookup"><span data-stu-id="561f7-120">Set the right box with the ending year.</span></span> <span data-ttu-id="561f7-121">儲存結束年份時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將自動使用開始年份來擴展左邊的方塊。</span><span class="sxs-lookup"><span data-stu-id="561f7-121">When the ending year is saved, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will automatically populate the left box with the beginning year.</span></span>  
  
 <span data-ttu-id="561f7-122">**設定的值**</span><span class="sxs-lookup"><span data-stu-id="561f7-122">**Configured Values**</span></span>  
 <span data-ttu-id="561f7-123">針對此窗格中的選項，顯示設定的值。</span><span class="sxs-lookup"><span data-stu-id="561f7-123">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="561f7-124">如果您變更這些值，請按一下 **[執行中的值]** ，即可查看變更是否已生效。</span><span class="sxs-lookup"><span data-stu-id="561f7-124">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="561f7-125">如果變更尚未生效，必須先重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="561f7-125">If the changes have not taken effect, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restated first.</span></span>  
  
 <span data-ttu-id="561f7-126">**[執行中的值]**</span><span class="sxs-lookup"><span data-stu-id="561f7-126">**Running Values**</span></span>  
 <span data-ttu-id="561f7-127">針對此窗格中的選項，檢視目前執行中的值。</span><span class="sxs-lookup"><span data-stu-id="561f7-127">View the currently running values for the options on this pane.</span></span> <span data-ttu-id="561f7-128">這些值是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="561f7-128">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="561f7-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="561f7-129">See Also</span></span>  
 [<span data-ttu-id="561f7-130">伺服器組態選項 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="561f7-130">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
