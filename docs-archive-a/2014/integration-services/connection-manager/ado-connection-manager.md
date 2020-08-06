---
title: ADO 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], ADO
- connection managers [Integration Services], ADO
- ADO connection manager [Integration Services]
ms.assetid: 490418bc-5ef1-41b8-a9c8-de38aa96e0f6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fb4b667733f81eebbaf2b6a2ab9b205c09fe2c66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599148"
---
# <a name="ado-connection-manager"></a><span data-ttu-id="dddc2-102">ADO 連接管理員</span><span class="sxs-lookup"><span data-stu-id="dddc2-102">ADO Connection Manager</span></span>
  <span data-ttu-id="dddc2-103">ADO 連接管理員可讓封裝連接到 ActiveX Data Objects (ADO) 物件，例如資料錄集。</span><span class="sxs-lookup"><span data-stu-id="dddc2-103">An ADO connection manager enables a package to connect to ActiveX Data Objects (ADO) objects, such as a recordset.</span></span> <span data-ttu-id="dddc2-104">這個連接管理員一般用在以舊版語言 (例如 Microsoft Visual Basic 6.0) 所撰寫的自訂工作中，或用於做為使用 ADO 連接到資料來源之現有應用程式一部份的自訂工作中。</span><span class="sxs-lookup"><span data-stu-id="dddc2-104">This connection manager is typically used in custom tasks written in an earlier version of a language, such as Microsoft Visual Basic 6.0, or in custom tasks that are part of an existing application that uses ADO to connect to a data source.</span></span>  
  
 <span data-ttu-id="dddc2-105">當您將 ADO 連線管理員加入封裝時， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會建立在執行時間解析為 ADO 連接的連線管理員、設定連線管理員屬性，並將連線管理員加入 `Connections` 封裝上的集合。</span><span class="sxs-lookup"><span data-stu-id="dddc2-105">When you add an ADO connection manager to a package, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an ADO connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="dddc2-106">連接管理員的 `ConnectionManagerType` 屬性會設為 `ADO`。</span><span class="sxs-lookup"><span data-stu-id="dddc2-106">The `ConnectionManagerType` property of the connection manager is set to `ADO`.</span></span>  
  
## <a name="troubleshooting-the-ado-connection-manager"></a><span data-ttu-id="dddc2-107">疑難排解 ADO 連接管理員</span><span class="sxs-lookup"><span data-stu-id="dddc2-107">Troubleshooting the ADO Connection Manager</span></span>  
 <span data-ttu-id="dddc2-108">由 ADO 連接管理員讀取時，某些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期資料類型會產生如下表所示結果。</span><span class="sxs-lookup"><span data-stu-id="dddc2-108">When being read by an ADO connection manager, certain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date data types will generate the results shown in the following table.</span></span>  
  
|<span data-ttu-id="dddc2-109">SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="dddc2-109">SQL Server Data type</span></span>|<span data-ttu-id="dddc2-110">結果</span><span class="sxs-lookup"><span data-stu-id="dddc2-110">Result</span></span>|  
|--------------------------|------------|  
|<span data-ttu-id="dddc2-111">`time`, `datetimeoffset`</span><span class="sxs-lookup"><span data-stu-id="dddc2-111">`time`, `datetimeoffset`</span></span>|<span data-ttu-id="dddc2-112">除非封裝使用參數化 SQL 命令，否則封裝會失敗。</span><span class="sxs-lookup"><span data-stu-id="dddc2-112">The package fails unless the package uses parameterized SQL commands.</span></span> <span data-ttu-id="dddc2-113">若要使用參數化 SQL 命令，請在封裝中使用「執行 SQL 工作」。</span><span class="sxs-lookup"><span data-stu-id="dddc2-113">To use parameterized SQL commands, use the Execute SQL Task in your package.</span></span> <span data-ttu-id="dddc2-114">如需詳細資訊，請參閱 [執行 SQL 工作](../control-flow/execute-sql-task.md) 和 [執行 SQL 工作中的參數和傳回碼](../parameters-and-return-codes-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="dddc2-114">For more information, see [Execute SQL Task](../control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>|  
|`datetime2`|<span data-ttu-id="dddc2-115">ADO 連接管理員會截斷毫秒值。</span><span class="sxs-lookup"><span data-stu-id="dddc2-115">The ADO connection manager truncates the millisecond value.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="dddc2-116">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型以及如何將其對應到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料類型的詳細資訊，請參閱[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) 和 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="dddc2-116">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types and how they map to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) and [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="configuring-the-ado-connection-manager"></a><span data-ttu-id="dddc2-117">設定 ADO 連接管理員</span><span class="sxs-lookup"><span data-stu-id="dddc2-117">Configuring the ADO Connection Manager</span></span>  
 <span data-ttu-id="dddc2-118">您可以利用下列方式設定 ADO 連接管理員：</span><span class="sxs-lookup"><span data-stu-id="dddc2-118">You can configure an ADO connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="dddc2-119">提供設定的特定連接字串，以符合所選取提供者的需求。</span><span class="sxs-lookup"><span data-stu-id="dddc2-119">Provide a specific connection string configured to meet the requirements of the selected provider.</span></span>  
  
-   <span data-ttu-id="dddc2-120">視提供者而定，包含要連接的資料來源名稱。</span><span class="sxs-lookup"><span data-stu-id="dddc2-120">Depending on the provider, include the name of the data source to connect to.</span></span>  
  
-   <span data-ttu-id="dddc2-121">為所選的提供者提供適當的安全性認證。</span><span class="sxs-lookup"><span data-stu-id="dddc2-121">Provide security credentials as appropriate for the selected provider.</span></span>  
  
-   <span data-ttu-id="dddc2-122">指示是否在執行階段保留從連接管理員建立的連接。</span><span class="sxs-lookup"><span data-stu-id="dddc2-122">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
 <span data-ttu-id="dddc2-123">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="dddc2-123">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="dddc2-124">如需有關可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="dddc2-124">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="dddc2-125">設定 OLE DB 連線管理員</span><span class="sxs-lookup"><span data-stu-id="dddc2-125">Configure OLE DB Connection Manager</span></span>](ole-db-connection-manager.md)  
  
 <span data-ttu-id="dddc2-126">如需以程式設計方式設定連線管理員的資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以程式設計方式加入連接](../building-packages-programmatically/adding-connections-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="dddc2-126">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dddc2-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dddc2-127">See Also</span></span>  
 [<span data-ttu-id="dddc2-128">Integration Services &#40;SSIS&#41; 連接</span><span class="sxs-lookup"><span data-stu-id="dddc2-128">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
