---
title: 開發人員&#39;s 指南 (資料庫引擎) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- developer's guide [SQL Server Database Engine]
- Database Engine [SQL Server], development
ms.assetid: 7638f46c-9e66-48e6-9a9b-425e0b788311
author: rothja
ms.author: jroth
ms.openlocfilehash: e1f8c8022422def83229b72c6b6a061f12755328
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606366"
---
# <a name="developer39s-guide-database-engine"></a><span data-ttu-id="cf970-102">開發人員&#39;s 指南 (資料庫引擎) </span><span class="sxs-lookup"><span data-stu-id="cf970-102">Developer&#39;s Guide (Database Engine)</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="cf970-103">提供一組豐富的工具來開發、管理與控制資料庫應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf970-103">provides a rich set of tools for developing, administering, and controlling database applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf970-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="cf970-104">In This Section</span></span>  
 [<span data-ttu-id="cf970-105">Common Language Runtime &#40;CLR&#41; 整合程式設計概念</span><span class="sxs-lookup"><span data-stu-id="cf970-105">Common Language Runtime &#40;CLR&#41; Integration Programming Concepts</span></span>](clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
 <span data-ttu-id="cf970-106">描述將 .NET Framework for [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 之 Common Language Runtime (CLR) 元件整合到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="cf970-106">Describes the integration of the common language runtime (CLR) component of the .NET Framework for [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cf970-107">這表示您可以使用任何 .NET Framework 語言 (包括 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic .NET 及 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#)，撰寫預存程序、觸發程序、使用者定義型別、使用者定義函數、使用者定義彙總及資料流資料表值函數。</span><span class="sxs-lookup"><span data-stu-id="cf970-107">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic .NET and [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.</span></span>  
  
 [<span data-ttu-id="cf970-108">SQL Server Native Client 程式設計</span><span class="sxs-lookup"><span data-stu-id="cf970-108">SQL Server Native Client Programming</span></span>](native-client/sql-server-native-client-programming.md)  
 <span data-ttu-id="cf970-109">描述如何使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client 建立新的應用程式，或者加強需要利用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 新功能 (例如，Multiple Active Result Set (MARS)、使用者定義資料類型 (UDT)、查詢通知、快照集隔離和 XML 資料類型支援) 的現有應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf970-109">Describes how [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client can be used to create new applications or enhance existing applications to take advantage of new [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] features such as multiple active result sets (MARS), user-defined data types (UDT), query notifications, snapshot isolation, and XML data type support.</span></span>  
  
 [<span data-ttu-id="cf970-110">SQLXML 4.0 程式設計概念</span><span class="sxs-lookup"><span data-stu-id="cf970-110">SQLXML 4.0 Programming Concepts</span></span>](sqlxml/sqlxml-4-0-programming-concepts.md)  
 <span data-ttu-id="cf970-111">描述最新版的 SQLXML，提供與 SQLXML 3.0 相同的功能以及其他更新來配合 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] 所推出的新功能，例如 xml 資料類型。</span><span class="sxs-lookup"><span data-stu-id="cf970-111">Describes the latest version of SQLXML, which delivers the same functionality as SQLXML 3.0 as well as additional updates to accommodate new features introduced in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], such as the xml data type.</span></span>  
  
 [<span data-ttu-id="cf970-112">組態管理的 WMI 提供者概念</span><span class="sxs-lookup"><span data-stu-id="cf970-112">WMI Provider for Configuration Management Concepts</span></span>](wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
 <span data-ttu-id="cf970-113">說明與 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 適用于 Microsoft Management Console (MMC) 和 Configuration Manager 的 Configuration Manager 嵌入式管理單元搭配使用的已發佈層 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cf970-113">Describes a published layer that is used with the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager snap-in for Microsoft Management Console (MMC) and the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="cf970-114">它會提供統一的方式來協助您連結管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 組態管理員所要求之登錄作業的 API 呼叫，並在選取的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服務上，提供增強的控制和操作功能。</span><span class="sxs-lookup"><span data-stu-id="cf970-114">It provides a unified way for interfacing with the API calls that manage the registry operations requested by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager and provides enhanced control and manipulation over the selected [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] services.</span></span>  
  
 [<span data-ttu-id="cf970-115">伺服器事件的 WMI 提供者概念</span><span class="sxs-lookup"><span data-stu-id="cf970-115">WMI Provider for Server Events Concepts</span></span>](wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)  
 <span data-ttu-id="cf970-116">描述如何使用 Windows Management Instrumentation (WMI) 來監視 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體中的事件。</span><span class="sxs-lookup"><span data-stu-id="cf970-116">Describes how to use Windows Management Instrumentation (WMI) to monitor events in an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="cf970-117">SQL Server 管理物件 &#40;SMO&#41; 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cf970-117">SQL Server Management Objects &#40;SMO&#41; Programming Guide</span></span>](server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
 <span data-ttu-id="cf970-118">包含 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Objects (SMO) 的相關資訊，也就是針對管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 之所有層面進行程式設計所設計的物件集合相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cf970-118">Contains information about [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Objects (SMO), a collection of objects that are designed for programming all aspects of managing [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="cf970-119">資料庫引擎擴充預存程序程式設計</span><span class="sxs-lookup"><span data-stu-id="cf970-119">Database Engine Extended Stored Procedure Programming</span></span>](database-engine-extended-stored-procedure-programming.md)  
 <span data-ttu-id="cf970-120">描述如何使用擴充預存程序，以 C 之類的程式語言建立您自己的外部常式。</span><span class="sxs-lookup"><span data-stu-id="cf970-120">Describes how to use extended stored procedures to create your own external routines in a programming language such as C.</span></span>  
  
 [<span data-ttu-id="cf970-121">資料收集器程式設計</span><span class="sxs-lookup"><span data-stu-id="cf970-121">Data Collector Programming</span></span>](../database-engine/dev-guide/data-collector-programming.md)  
 <span data-ttu-id="cf970-122">描述資料收集器物件模型。</span><span class="sxs-lookup"><span data-stu-id="cf970-122">Describes the Data Collector object model.</span></span>  
  
 [<span data-ttu-id="cf970-123">例外狀況訊息方塊程式設計</span><span class="sxs-lookup"><span data-stu-id="cf970-123">Exception Message Box Programming</span></span>](../database-engine/dev-guide/exception-message-box-programming.md)  
 <span data-ttu-id="cf970-124">描述如何在應用程式中使用例外狀況訊息方塊程式介面，讓您更有效地控制訊息經驗，以便讓使用者選擇要儲存錯誤訊息內容以供日後參考，或是取得訊息的說明。</span><span class="sxs-lookup"><span data-stu-id="cf970-124">Describes how you can use the exception message box programmatic interface in your applications to provide more control over the messaging experience, to give your users the option to save error message content for later reference, and to get help with messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf970-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf970-125">See Also</span></span>  
 <span data-ttu-id="cf970-126">[資料採礦程式設計](../analysis-services/dev-guide/data-mining-programming.md) </span><span class="sxs-lookup"><span data-stu-id="cf970-126">[Data Mining Programming](../analysis-services/dev-guide/data-mining-programming.md) </span></span>  
 <span data-ttu-id="cf970-127">[開發人員指南 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/analysis-services-developer-documentation) </span><span class="sxs-lookup"><span data-stu-id="cf970-127">[Developer's Guide &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/analysis-services-developer-documentation) </span></span>  
 <span data-ttu-id="cf970-128">[開發人員指南 &#40;Integration Services&#41;](../integration-services/integration-services-developer-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="cf970-128">[Developer's Guide &#40;Integration Services&#41;](../integration-services/integration-services-developer-documentation.md) </span></span>  
 <span data-ttu-id="cf970-129">[&#40;複寫&#41;的開發人員指南](replication/concepts/replication-developer-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="cf970-129">[Developer's Guide &#40;Replication&#41;](replication/concepts/replication-developer-documentation.md) </span></span>  
 [<span data-ttu-id="cf970-130">開發人員指南 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cf970-130">Developer's Guide &#40;Reporting Services&#41;</span></span>](../reporting-services/reporting-services-developer-documentation.md)  
  
  
