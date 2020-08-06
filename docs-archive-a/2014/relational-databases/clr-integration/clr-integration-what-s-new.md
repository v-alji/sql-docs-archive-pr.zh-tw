---
title: CLR 整合的新功能&#39;|Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
ms.openlocfilehash: b51eb5d8bee5ff8e514f294d5e9facca93a30bfa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595122"
---
# <a name="what39s-new-in-clr-integration"></a><span data-ttu-id="3db01-102">CLR 整合的新功能&#39;</span><span class="sxs-lookup"><span data-stu-id="3db01-102">What&#39;s New in CLR Integration</span></span>
  <span data-ttu-id="3db01-103">以下是 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中 CLR 整合的新功能：</span><span class="sxs-lookup"><span data-stu-id="3db01-103">The following are new features in CLR integration in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:</span></span>  
  
-   <span data-ttu-id="3db01-104">在 CLR 的版本 4 中，CLR 資料庫物件不再攔截損壞的狀態例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3db01-104">In version 4 of the CLR, CLR database objects no longer catch corrupted state exceptions.</span></span> <span data-ttu-id="3db01-105">這些例外狀況現在會在 CLR 整合裝載層中攔截。</span><span class="sxs-lookup"><span data-stu-id="3db01-105">These exceptions are now caught in the CLR integration hosting layer.</span></span> <span data-ttu-id="3db01-106">CLR 資料庫元件仍然會攔截這些例外狀況，方法是設定 ([ \<legacyCorruptedStateExceptionsPolicy> 元素](https://go.microsoft.com/fwlink/?LinkId=204954)) 的程式碼屬性。</span><span class="sxs-lookup"><span data-stu-id="3db01-106">These exceptions can still be caught by the CLR database components by setting a code attribute ([\<legacyCorruptedStateExceptionsPolicy> Element](https://go.microsoft.com/fwlink/?LinkId=204954)).</span></span> <span data-ttu-id="3db01-107">但是不建議您這樣做，因為當發生損壞的狀態例外狀況時，結果就不可靠。</span><span class="sxs-lookup"><span data-stu-id="3db01-107">However, this is not recommended because results are not reliable when a corrupted state exception occurs.</span></span>  
  
-   <span data-ttu-id="3db01-108">由於 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 的安全性要求很嚴格，所以 CLR 資料庫元件將會繼續使用 CLR 2.0 版中所定義的程式碼存取安全性模型。</span><span class="sxs-lookup"><span data-stu-id="3db01-108">Due to the strict security requirements of [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], CLR database components will continue to use the Code Access Security model defined in CLR version 2.0.</span></span>  
  
-   <span data-ttu-id="3db01-109">在 CLR 版本 4 中，`System.TimeSpan` 值的格式錯誤將會產生 `System.FormatExceptions`。</span><span class="sxs-lookup"><span data-stu-id="3db01-109">In CLR version 4, a format error in a `System.TimeSpan` value will generate a `System.FormatExceptions`.</span></span> <span data-ttu-id="3db01-110">在 CLR 的版本 4 之前，`System.TimeSpan` 值的格式錯誤會被忽略。</span><span class="sxs-lookup"><span data-stu-id="3db01-110">Prior to version 4 of the CLR, a format error in a `System.TimeSpan` value was ignored.</span></span> <span data-ttu-id="3db01-111">依賴 CLR 版本 4 之前行為的資料庫應用程式應該要以資料庫相容性層級 (`ALTER DATABASE Compatibility Level`) 100 或更低的層級來執行。</span><span class="sxs-lookup"><span data-stu-id="3db01-111">Database applications that rely on the behavior prior to version 4 of the CLR should run with a database compatibility level (`ALTER DATABASE Compatibility Level`) of 100 or lower.</span></span> <span data-ttu-id="3db01-112">如需詳細資訊，請參閱[<TimeSpan_LegacyFormatMode> 元素](https://go.microsoft.com/fwlink/?LinkId=205109)。</span><span class="sxs-lookup"><span data-stu-id="3db01-112">For more information, see [<TimeSpan_LegacyFormatMode> Element](https://go.microsoft.com/fwlink/?LinkId=205109).</span></span>  
  
-   <span data-ttu-id="3db01-113">版本 4 的 CLR 支援 Unicode 5.1。</span><span class="sxs-lookup"><span data-stu-id="3db01-113">Version 4 of the CLR supports Unicode 5.1.</span></span> <span data-ttu-id="3db01-114">涉及一些腔調字標記和符號的排序作業將得以改善。</span><span class="sxs-lookup"><span data-stu-id="3db01-114">Sort operations involving some accent marks and symbols will be improved.</span></span> <span data-ttu-id="3db01-115">如果您的應用程式依賴舊版的排序行為，可能會發生相容性問題。</span><span class="sxs-lookup"><span data-stu-id="3db01-115">Compatibility problems may occur if your application relies on legacy sorting behavior.</span></span> <span data-ttu-id="3db01-116">若要啟用舊版排序，資料庫相容性層級 (`ALTER DATABASE Compatibility Level`) 必須設定為 100 或更低的值。</span><span class="sxs-lookup"><span data-stu-id="3db01-116">To enable legacy sorting, the database compatibility level (`ALTER DATABASE Compatibility Level`) must be set to 100 or lower.</span></span> <span data-ttu-id="3db01-117">為了支援這項處理，[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 會將 sort00001000.dll 安裝在 .NET Framework 4 目錄中 (C:\Windows\Microsoft.NET\Framework\v4.0.30319)。</span><span class="sxs-lookup"><span data-stu-id="3db01-117">To support this, [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] will install sort00001000.dll in the .NET Framework 4 directory (C:\Windows\Microsoft.NET\Framework\v4.0.30319).</span></span> <span data-ttu-id="3db01-118">如需詳細資訊，請參閱[ \<CompatSortNLSVersion> 元素](https://go.microsoft.com/fwlink/?LinkId=205110)。</span><span class="sxs-lookup"><span data-stu-id="3db01-118">For more information, see [\<CompatSortNLSVersion> Element](https://go.microsoft.com/fwlink/?LinkId=205110).</span></span>  
  
-   <span data-ttu-id="3db01-119">下列資料行已加入至[sys. dm_clr_appdomains](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql)： `total_processor_time_ms` 、 `total_allocated_memory_kb` 和 `survived_memory_kb` 。</span><span class="sxs-lookup"><span data-stu-id="3db01-119">The following columns have been added to [sys.dm_clr_appdomains](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql): `total_processor_time_ms`, `total_allocated_memory_kb`, and `survived_memory_kb`.</span></span>  
  
  
