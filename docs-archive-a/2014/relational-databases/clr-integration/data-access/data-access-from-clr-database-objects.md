---
title: 從 CLR 資料庫物件進行資料存取 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], data access
- routines [CLR integration]
- data access [CLR integration]
- ADO.NET [CLR integration]
- internal data access [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], data access
- managed code [SQL Server], database objects
- .NET Data Access Provider for SQL Server [CLR integration]
- managed code [SQL Server], data access
- SqlClient provider
- in-process data access providers [CLR integration]
ms.assetid: 9a0f4dee-71c1-42e9-a85e-52382807010f
author: rothja
ms.author: jroth
ms.openlocfilehash: d229d490a9f3a7bc6f613259ee0535218de47975
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599515"
---
# <a name="data-access-from-clr-database-objects"></a><span data-ttu-id="65c80-102">從 CLR 資料庫物件進行資料存取</span><span class="sxs-lookup"><span data-stu-id="65c80-102">Data Access from CLR Database Objects</span></span>
  <span data-ttu-id="65c80-103">Common language runtime (CLR) 常式可以輕鬆地存取儲存在其執行之實例 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] 中的資料，以及儲存在遠端實例中的資料。</span><span class="sxs-lookup"><span data-stu-id="65c80-103">A common language runtime (CLR) routine may easily access data stored in the instance of [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] in which it runs, as well as data stored in remote instances.</span></span> <span data-ttu-id="65c80-104">常式可以存取的特定資料取決於藉以執行程式碼的使用者內容。</span><span class="sxs-lookup"><span data-stu-id="65c80-104">Which particular data the routine can access is determined by the user context in which the code is running.</span></span> <span data-ttu-id="65c80-105">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 來自 managed 用戶端和仲介層應用程式之資料的 .NET Framework Data Provider，從 CLR 資料庫物件中存取資料。</span><span class="sxs-lookup"><span data-stu-id="65c80-105">Access data from within a CLR database object by using the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data from managed client and middle-tier applications.</span></span> <span data-ttu-id="65c80-106">因為這個緣故，您可以將 ADO.NET 和 `SqlClient` 的知識運用在用戶端和中間層應用程式。</span><span class="sxs-lookup"><span data-stu-id="65c80-106">Because of this, you can leverage your knowledge of ADO.NET and `SqlClient` in client and middle-tier applications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65c80-107">根據預設，執行資料存取不允許使用使用者定義型別方法與使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="65c80-107">User-defined type methods and user-defined functions are not allowed to perform data access by default.</span></span> <span data-ttu-id="65c80-108">您必須將 `DataAccess` 或 `SqlMethodAttribute` 的 `SqlFunctionAttribute` 屬性設定為 `DataAccessKind.Read` 才能使用者定義型別 (UDT) 方法或使用者定義函數進行唯讀的資料存取。</span><span class="sxs-lookup"><span data-stu-id="65c80-108">You must set the `DataAccess` property of `SqlMethodAttribute` or `SqlFunctionAttribute` to `DataAccessKind.Read` to enable read-only data access from user-defined type (UDT) methods or user-defined functions.</span></span> <span data-ttu-id="65c80-109">資料修改作業無法從 UDT 或使用者定義函數進行，如果嘗試進行，則會在執行階段擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="65c80-109">Data modification operations are not allowed from UDTs or user-defined functions, and throws exceptions at execution time if attempted.</span></span>  
  
 <span data-ttu-id="65c80-110">本節僅討論從 CLR 資料庫物件中存取資料時，功能與行為上的特定差異。</span><span class="sxs-lookup"><span data-stu-id="65c80-110">This section discusses only the specific functional and behavioral differences when accessing data from within a CLR database object.</span></span> <span data-ttu-id="65c80-111">如需有關 ADO.NET 功能的詳細資訊，請參閱隨附在 .NET Framework SDK 中的 ADO.NET 文件集。</span><span class="sxs-lookup"><span data-stu-id="65c80-111">For more information about the features and functionality of ADO.NET, see the ADO.NET documentation included in the .NET Framework SDK.</span></span>  
  
 <span data-ttu-id="65c80-112">下表列出本節的主題。</span><span class="sxs-lookup"><span data-stu-id="65c80-112">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="65c80-113">內容連接</span><span class="sxs-lookup"><span data-stu-id="65c80-113">Context Connection</span></span>](context-connection.md)  
 <span data-ttu-id="65c80-114">描述 SQL Server 的內容連接。</span><span class="sxs-lookup"><span data-stu-id="65c80-114">Describes the context connection to SQL Server.</span></span>  
  
 [<span data-ttu-id="65c80-115">連接的模擬和認證</span><span class="sxs-lookup"><span data-stu-id="65c80-115">Impersonation and Credentials for Connections</span></span>](impersonation-and-credentials-for-connections.md)  
 <span data-ttu-id="65c80-116">描述模擬連接以及連接認證。</span><span class="sxs-lookup"><span data-stu-id="65c80-116">Describes impersonating connections and connection credentials.</span></span>  
  
 [<span data-ttu-id="65c80-117">ADO.NET 的 SQL Server 同處理序特定擴充</span><span class="sxs-lookup"><span data-stu-id="65c80-117">SQL Server In-Process Specific Extensions to ADO.NET</span></span>](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
 <span data-ttu-id="65c80-118">討論同處理序的特定 `SqlPipe`、`SqlContext`、`SqlTriggerContext` 與 `SqlDataRecord` 物件。</span><span class="sxs-lookup"><span data-stu-id="65c80-118">Discusses the in-process specific `SqlPipe`, `SqlContext`, `SqlTriggerContext`, and `SqlDataRecord` objects.</span></span>  
  
 [<span data-ttu-id="65c80-119">CLR 整合和交易</span><span class="sxs-lookup"><span data-stu-id="65c80-119">CLR Integration and Transactions</span></span>](../../native-client-ole-db-transactions/transactions.md)  
 <span data-ttu-id="65c80-120">描述 System.Transactions 命名空間中提供的新交易架構如何整合 ADO.NET 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="65c80-120">Describes how the new transaction framework provided in the System.Transactions namespace integrates with ADO.NET and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR integration.</span></span>  
  
 [<span data-ttu-id="65c80-121">從 CLR 資料庫物件進行 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="65c80-121">XML Serialization from CLR Database Objects</span></span>](../../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md)  
 <span data-ttu-id="65c80-122">說明如何在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中啟用 CLR 資料庫物件的 XML 序列化案例。</span><span class="sxs-lookup"><span data-stu-id="65c80-122">Explains how to enable XML serialization scenarios of CLR database objects inside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
  
