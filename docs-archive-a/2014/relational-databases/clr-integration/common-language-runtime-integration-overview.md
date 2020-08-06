---
title: Common Language Runtime (CLR) 整合總覽 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- managed code [SQL Server]
- common language runtime [SQL Server], about CLR integration
- cross-language integration
- integrating CLR [SQL Server]
- .NET Framework [SQL Server], common language runtime
- code access security [CLR integration]
- managed code [SQL Server], CLR integration
ms.assetid: 7be9e644-36a2-48fc-9206-faf59fdff4d7
author: rothja
ms.author: jroth
ms.openlocfilehash: 25345fd39fb8a77f62e4e352b75629a98cb9d7af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595121"
---
# <a name="common-language-runtime-clr-integration-overview"></a><span data-ttu-id="37efa-102">Common Language Runtime (CLR) 整合概觀</span><span class="sxs-lookup"><span data-stu-id="37efa-102">Common Language Runtime (CLR) Integration Overview</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="37efa-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]現在功能整合了 common language runtime (CLR) 元件的 .NET Framework [!INCLUDE[msCoName](../../../includes/msconame-md.md)]時段.</span><span class="sxs-lookup"><span data-stu-id="37efa-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] now features the integration of the common language runtime (CLR) component of the .NET Framework for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows.</span></span> <span data-ttu-id="37efa-104">CLR 提供含有如跨語言整合、程式碼存取安全性、物件存留期間管理，以及偵錯和設定檔作業支援的 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="37efa-104">The CLR supplies managed code with services such as cross-language integration, code access security, object lifetime management, and debugging and profiling support.</span></span> <span data-ttu-id="37efa-105">對於 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用者和應用程式開發人員，CLR 整合意味著您現在可以使用任何 .NET Framework 語言 (包括 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET 和 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#) 撰寫預存程序、觸發程序、使用者定義型別、使用者定義函數 (純量和資料表值) 和使用者定義彙總函式。</span><span class="sxs-lookup"><span data-stu-id="37efa-105">For [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] users and application developers, CLR integration means that you can now write stored procedures, triggers, user-defined types, user-defined functions (scalar and table-valued), and user-defined aggregate functions using any .NET Framework language, including [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="37efa-106">包含預先安裝的 .NET Framework 版本 4。</span><span class="sxs-lookup"><span data-stu-id="37efa-106">includes the .NET Framework version 4 pre-installed.</span></span>  
  
 <span data-ttu-id="37efa-107">這項整合的主要優點包括：</span><span class="sxs-lookup"><span data-stu-id="37efa-107">Among the major benefits of this integration are:</span></span>  
  
-   <span data-ttu-id="37efa-108">**程式設計模型更好。**</span><span class="sxs-lookup"><span data-stu-id="37efa-108">**A better programming model.**</span></span> <span data-ttu-id="37efa-109">.NET Framework 語言在許多方面比 Transact-SQL 豐富，可提供先前未提供給 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 開發人員的建構與功能。</span><span class="sxs-lookup"><span data-stu-id="37efa-109">The .NET Framework languages are in many respects richer than Transact-SQL, offering constructs and capabilities previously not available to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] developers.</span></span> <span data-ttu-id="37efa-110">開發人員也可以運用提供一組廣大類別的 .NET Framework 程式庫功能，可用於快速而有效率地解決程式設計問題。</span><span class="sxs-lookup"><span data-stu-id="37efa-110">Developers may also leverage the power of the .NET Framework Library, which provides an extensive set of classes that can be used to quickly and efficiently solve programming problems.</span></span>  
  
-   <span data-ttu-id="37efa-111">**可增進安全和安全性。**</span><span class="sxs-lookup"><span data-stu-id="37efa-111">**Improved safety and security.**</span></span> <span data-ttu-id="37efa-112">Managed 程式碼會在 Database Engine 主控的 Common Language Run-time 環境下執行。</span><span class="sxs-lookup"><span data-stu-id="37efa-112">Managed code runs in a common language run-time environment, hosted by the Database Engine.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="37efa-113">會運用此環境提供更安全的替代方式給舊版 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 所提供的擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="37efa-113">leverages this to provide a safer and more secure alternative to the extended stored procedures available in earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="37efa-114">**能夠定義資料類型和彙總函式。**</span><span class="sxs-lookup"><span data-stu-id="37efa-114">**Ability to define data types and aggregate functions.**</span></span> <span data-ttu-id="37efa-115">使用者定義型別和使用者定義彙總是兩個新的 Managed 資料庫物件，它們可以擴充 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的儲存和查詢功能。</span><span class="sxs-lookup"><span data-stu-id="37efa-115">User defined types and user defined aggregates are two new managed database objects which expand the storage and querying capabilities of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="37efa-116">**透過標準化環境簡化的開發。**</span><span class="sxs-lookup"><span data-stu-id="37efa-116">**Streamlined development through a standardized environment.**</span></span> <span data-ttu-id="37efa-117">資料庫開發會整合到後續版本的  Visual Studio .NET 開發環境中。</span><span class="sxs-lookup"><span data-stu-id="37efa-117">Database development is integrated into future releases of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio .NET development environment.</span></span> <span data-ttu-id="37efa-118">開發人員用來開發與偵錯資料庫物件和指令碼的工具，與他們用來撰寫中介層或用戶層的 .NET Framework 元件和服務的工具是一樣的。</span><span class="sxs-lookup"><span data-stu-id="37efa-118">Developers use the same tools for developing and debugging database objects and scripts as they use to write middle-tier or client-tier .NET Framework components and services.</span></span>  
  
-   <span data-ttu-id="37efa-119">**增進效能和延展性的可能性。**</span><span class="sxs-lookup"><span data-stu-id="37efa-119">**Potential for improved performance and scalability.**</span></span> <span data-ttu-id="37efa-120">在許多情況下，.NET Framework 語言編譯和執行模型會透過 Transact-SQL 提供改善的效能。</span><span class="sxs-lookup"><span data-stu-id="37efa-120">In many situations, the .NET Framework language compilation and execution models deliver improved performance over Transact-SQL.</span></span>  
  
 <span data-ttu-id="37efa-121">下表列出本節中的主題。</span><span class="sxs-lookup"><span data-stu-id="37efa-121">This following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="37efa-122">CLR 整合的概觀</span><span class="sxs-lookup"><span data-stu-id="37efa-122">Overview of CLR Integration</span></span>](clr-integration-overview.md)  
 <span data-ttu-id="37efa-123">描述可以使用 CLR 整合建立的物件種類，並檢閱使用 CLR 整合建立資料庫物件的需求。</span><span class="sxs-lookup"><span data-stu-id="37efa-123">Describes the kinds of objects that can be built using CLR integration, and reviews the requirements for building database objects using CLR integration.</span></span>  
  
 [<span data-ttu-id="37efa-124">CLR 整合的新功能</span><span class="sxs-lookup"><span data-stu-id="37efa-124">What's New in CLR Integration</span></span>](clr-integration-what-s-new.md)  
 <span data-ttu-id="37efa-125">描述這個版本的新功能。</span><span class="sxs-lookup"><span data-stu-id="37efa-125">Describes the new features in this release.</span></span>  
  
 [<span data-ttu-id="37efa-126">CLR 整合的架構</span><span class="sxs-lookup"><span data-stu-id="37efa-126">Architecture of CLR Integration</span></span>](../../database-engine/dev-guide/architecture-of-clr-integration.md)  
 <span data-ttu-id="37efa-127">描述 CLR 整合的設計目標。</span><span class="sxs-lookup"><span data-stu-id="37efa-127">Describes the design goals of CLR integration.</span></span>  
  
 [<span data-ttu-id="37efa-128">啟用 CLR 整合</span><span class="sxs-lookup"><span data-stu-id="37efa-128">Enabling CLR Integration</span></span>](clr-integration-enabling.md)  
 <span data-ttu-id="37efa-129">說明如何啟用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="37efa-129">Describes how to enable CLR integration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37efa-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37efa-130">See Also</span></span>  
 <span data-ttu-id="37efa-131">[安裝 .NET Framework](https://technet.microsoft.com/library/ms166014\(v=SQL.105\).aspx) </span><span class="sxs-lookup"><span data-stu-id="37efa-131">[Installing the .NET Framework](https://technet.microsoft.com/library/ms166014\(v=SQL.105\).aspx) </span></span>  
 [<span data-ttu-id="37efa-132">CLR 整合的效能</span><span class="sxs-lookup"><span data-stu-id="37efa-132">Performance of CLR Integration</span></span>](clr-integration-architecture-performance.md)  
  
  
