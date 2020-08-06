---
title: ADO.NET 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], ADO.NET
- ADO.NET connection manager [Integration Services]
- connections [Integration Services], ADO.NET
ms.assetid: fc5daa2f-0159-4bda-9402-c87f1035a96f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9bdc25eeeae93fe0bd85deb55bfc86c55ab91ee5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596232"
---
# <a name="adonet-connection-manager"></a><span data-ttu-id="4622e-102">ADO.NET 連接管理員</span><span class="sxs-lookup"><span data-stu-id="4622e-102">ADO.NET Connection Manager</span></span>
  <span data-ttu-id="4622e-103">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連接管理員可讓封裝使用 .NET 提供者來存取資料來源。</span><span class="sxs-lookup"><span data-stu-id="4622e-103">An [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager enables a package to access data sources by using a .NET provider.</span></span> <span data-ttu-id="4622e-104">此連線管理員通常用於存取資料來源（例如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ），以及透過使用 c # 這類語言以 managed 程式碼撰寫之自訂工作中的 OLE DB 和 XML 公開的資料來源。</span><span class="sxs-lookup"><span data-stu-id="4622e-104">This connection manager is typically used to access data sources such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and also data sources exposed through OLE DB and XML in custom tasks that are written in managed code by using a language such C#.</span></span>  
  
 <span data-ttu-id="4622e-105">當您將 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員加入封裝時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會建立在執行時間解析為連接的連線管理員 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 、設定連線管理員屬性，並將連線管理員加入 `Connections` 封裝上的集合。</span><span class="sxs-lookup"><span data-stu-id="4622e-105">When you add an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to a package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that is resolved as an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="4622e-106">連接管理員的 `ConnectionManagerType` 屬性會設為 `ADO.NET`。</span><span class="sxs-lookup"><span data-stu-id="4622e-106">The `ConnectionManagerType` property of the connection manager is set to `ADO.NET`.</span></span> <span data-ttu-id="4622e-107">系統會限定 `ConnectionManagerType` 的值，以包含連接管理員使用之 .NET 提供者的名稱。</span><span class="sxs-lookup"><span data-stu-id="4622e-107">The value of `ConnectionManagerType` is qualified to include the name of the .NET provider that the connection manager uses.</span></span>  
  
## <a name="adonet-connection-manager-troubleshooting"></a><span data-ttu-id="4622e-108">ADO.NET 連接管理員疑難排解</span><span class="sxs-lookup"><span data-stu-id="4622e-108">ADO.NET Connection Manager Troubleshooting</span></span>  
 <span data-ttu-id="4622e-109">您可以記錄 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連接管理員對外部資料提供者執行的呼叫。</span><span class="sxs-lookup"><span data-stu-id="4622e-109">You can log the calls that the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager makes to external data providers.</span></span> <span data-ttu-id="4622e-110">您可以使用這項記錄功能，疑難排解 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連接管理員對外部資料來源執行的連接。</span><span class="sxs-lookup"><span data-stu-id="4622e-110">You can use this logging capability to troubleshoot the connections that the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager makes to external data sources.</span></span> <span data-ttu-id="4622e-111">若要記錄 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員對外部資料提供者執行的呼叫，請啟用封裝記錄，然後在封裝層級選取 [診斷]\*\*\*\* 事件。</span><span class="sxs-lookup"><span data-stu-id="4622e-111">To log the calls that the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="4622e-112">如需詳細資訊，請參閱 [封裝執行的疑難排解工具](../troubleshooting/troubleshooting-tools-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="4622e-112">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
 <span data-ttu-id="4622e-113">由 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員讀取時，某些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期資料類型的資料將會產生如下表所示的結果。</span><span class="sxs-lookup"><span data-stu-id="4622e-113">When being read by an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager, data of certain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date data types will generate the results shown in the following table.</span></span>  
  
|<span data-ttu-id="4622e-114">SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="4622e-114">SQL Server data type</span></span>|<span data-ttu-id="4622e-115">結果</span><span class="sxs-lookup"><span data-stu-id="4622e-115">Result</span></span>|  
|--------------------------|------------|  
|<span data-ttu-id="4622e-116">`time`, `datetimeoffset`</span><span class="sxs-lookup"><span data-stu-id="4622e-116">`time`, `datetimeoffset`</span></span>|<span data-ttu-id="4622e-117">除非封裝使用參數化 SQL 命令，否則封裝會失敗。</span><span class="sxs-lookup"><span data-stu-id="4622e-117">The package fails unless the package uses parameterized SQL commands.</span></span> <span data-ttu-id="4622e-118">若要使用參數化 SQL 命令，請在封裝中使用「執行 SQL 工作」。</span><span class="sxs-lookup"><span data-stu-id="4622e-118">To use parameterized SQL commands, use the Execute SQL Task in your package.</span></span> <span data-ttu-id="4622e-119">如需詳細資訊，請參閱 [執行 SQL 工作](../control-flow/execute-sql-task.md) 和 [執行 SQL 工作中的參數和傳回碼](../parameters-and-return-codes-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="4622e-119">For more information, see [Execute SQL Task](../control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>|  
|`datetime2`|<span data-ttu-id="4622e-120">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連接管理員會截斷毫秒值。</span><span class="sxs-lookup"><span data-stu-id="4622e-120">The [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager truncates the millisecond value.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="4622e-121">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型以及如何將其對應到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料類型的詳細資訊，請參閱[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) 和 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="4622e-121">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types and how they map to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) and [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="adonet-connection-manager-configuration"></a><span data-ttu-id="4622e-122">ADO.NET 連接管理員組態</span><span class="sxs-lookup"><span data-stu-id="4622e-122">ADO.NET Connection Manager Configuration</span></span>  
 <span data-ttu-id="4622e-123">您可以利用下列方式設定 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員：</span><span class="sxs-lookup"><span data-stu-id="4622e-123">You can configure an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager in the following ways:</span></span>  
  
 <span data-ttu-id="4622e-124">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="4622e-124">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
-   <span data-ttu-id="4622e-125">提供設定的特定連接字串，以符合所選 .NET 提供者的需求。</span><span class="sxs-lookup"><span data-stu-id="4622e-125">Provide a specific connection string configured to meet the requirements of the selected .NET provider.</span></span>  
  
-   <span data-ttu-id="4622e-126">視提供者而定，包含要連接的資料來源名稱。</span><span class="sxs-lookup"><span data-stu-id="4622e-126">Depending on the provider, include the name of the data source to connect to.</span></span>  
  
-   <span data-ttu-id="4622e-127">為所選的提供者提供適當的安全性認證。</span><span class="sxs-lookup"><span data-stu-id="4622e-127">Provide security credentials as appropriate for the selected provider.</span></span>  
  
-   <span data-ttu-id="4622e-128">指示是否在執行階段保留從連接管理員建立的連接。</span><span class="sxs-lookup"><span data-stu-id="4622e-128">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
 <span data-ttu-id="4622e-129">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員的許多組態選項依存於連線管理員使用的 .NET 提供者。</span><span class="sxs-lookup"><span data-stu-id="4622e-129">Many of configuration options of the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager depend on the .NET provider that the connection manager uses.</span></span>  
  
 <span data-ttu-id="4622e-130">如需可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="4622e-130">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click one of the following topic:</span></span>  
  
-   [<span data-ttu-id="4622e-131">設定 ADO.NET 連線管理員</span><span class="sxs-lookup"><span data-stu-id="4622e-131">Configure ADO.NET Connection Manager</span></span>](../configure-ado-net-connection-manager.md)  
  
 <span data-ttu-id="4622e-132">如需以程式設計方式設定連線管理員的資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以程式設計方式加入連接](../building-packages-programmatically/adding-connections-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="4622e-132">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4622e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4622e-133">See Also</span></span>  
 [<span data-ttu-id="4622e-134">Integration Services &#40;SSIS&#41; 連接</span><span class="sxs-lookup"><span data-stu-id="4622e-134">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
