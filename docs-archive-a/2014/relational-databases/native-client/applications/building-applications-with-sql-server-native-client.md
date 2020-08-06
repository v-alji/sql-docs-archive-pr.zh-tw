---
title: 使用 SQL Server Native Client 建立應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], building applications
- SQLNCLI, building applications
- applications [SQL Server Native Client]
- SQL Server Native Client, building applications
ms.assetid: 254a2b48-f0e3-43b5-a48d-3d666c2a779f
author: rothja
ms.author: jroth
ms.openlocfilehash: d08fe1042ab1a79f6b48648f5a774b4fbac49ead
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597079"
---
# <a name="building-applications-with-sql-server-native-client"></a><span data-ttu-id="a98f4-102">使用 SQL Server Native Client 建立應用程式</span><span class="sxs-lookup"><span data-stu-id="a98f4-102">Building Applications with SQL Server Native Client</span></span>
  <span data-ttu-id="a98f4-103">當您開發使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 程式庫的應用程式時，會遇到一些問題。</span><span class="sxs-lookup"><span data-stu-id="a98f4-103">When developing an application that uses the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client library, there are a number of issues that come into play.</span></span> <span data-ttu-id="a98f4-104">本章節的主題將討論其中的許多問題，包括從 MDAC 升級到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 標頭檔和程式庫檔案)，以及可搭配 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 使用的各種連接字串概觀。</span><span class="sxs-lookup"><span data-stu-id="a98f4-104">The topics in this section discuss many of these issues including upgrading from MDAC to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client header and library files, and an overview of the various connection strings that can be used with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a98f4-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="a98f4-105">In This Section</span></span>  
 [<span data-ttu-id="a98f4-106">安裝 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="a98f4-106">Installing SQL Server Native Client</span></span>](installing-sql-server-native-client.md)  
 <span data-ttu-id="a98f4-107">討論如何安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client、各種元件的安裝位置，以及如何解除安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="a98f4-107">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client is installed, the locations that various components are installed to, and how to uninstall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 [<span data-ttu-id="a98f4-108">SQL Server Native Client 的元件</span><span class="sxs-lookup"><span data-stu-id="a98f4-108">Components of SQL Server Native Client</span></span>](components-of-sql-server-native-client.md)  
 <span data-ttu-id="a98f4-109">討論組成 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 的元件，包括程式庫、資源、說明和標頭檔案。</span><span class="sxs-lookup"><span data-stu-id="a98f4-109">Discusses the components that make up [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client including library, resource, help, and header files.</span></span>  
  
 [<span data-ttu-id="a98f4-110">搭配 SQL Server Native Client 使用連接字串關鍵字</span><span class="sxs-lookup"><span data-stu-id="a98f4-110">Using Connection String Keywords with SQL Server Native Client</span></span>](using-connection-string-keywords-with-sql-server-native-client.md)  
 <span data-ttu-id="a98f4-111">討論當透過 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 連接到資料庫時，可以使用之各種類型的連接字串。</span><span class="sxs-lookup"><span data-stu-id="a98f4-111">Discusses the various types of connection strings that can be used when connecting to a database through [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 [<span data-ttu-id="a98f4-112">使用 SQL Server Native Client 標頭檔與程式庫檔案</span><span class="sxs-lookup"><span data-stu-id="a98f4-112">Using the SQL Server Native Client Header and Library Files</span></span>](using-the-sql-server-native-client-header-and-library-files.md)  
 <span data-ttu-id="a98f4-113">討論如何在應用程式內使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 標頭檔和程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="a98f4-113">Discusses how to use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client header and library files within an application.</span></span>  
  
 [<span data-ttu-id="a98f4-114">從 MDAC 將應用程式更新至 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="a98f4-114">Updating an Application to SQL Server Native Client from MDAC</span></span>](updating-an-application-to-sql-server-native-client-from-mdac.md)  
 <span data-ttu-id="a98f4-115">討論 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 與 MDAC 之間的差異以及從 MDAC 升級到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 時所應該考量的問題。</span><span class="sxs-lookup"><span data-stu-id="a98f4-115">Discusses the differences between [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client and MDAC and issues that should be considered when upgrading from MDAC to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 [<span data-ttu-id="a98f4-116">從 SQL Server 2005 Native Client 更新應用程式</span><span class="sxs-lookup"><span data-stu-id="a98f4-116">Updating an Application from SQL Server 2005 Native Client</span></span>](updating-an-application-from-sql-server-2005-native-client.md)  
 <span data-ttu-id="a98f4-117">討論從 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client 升級到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client 時所應該考量的問題。</span><span class="sxs-lookup"><span data-stu-id="a98f4-117">Discusses issues that should be considered when upgrading from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span>  
  
 [<span data-ttu-id="a98f4-118">使用 ADO 搭配 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="a98f4-118">Using ADO with SQL Server Native Client</span></span>](using-ado-with-sql-server-native-client.md)  
 <span data-ttu-id="a98f4-119">討論 ADO 要如何使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 來存取及使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="a98f4-119">Discusses how ADO can use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to access and use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] functionality.</span></span>  
  
 [<span data-ttu-id="a98f4-120">SQL Server Native Client 的支援原則</span><span class="sxs-lookup"><span data-stu-id="a98f4-120">Support Policies for SQL Server Native Client</span></span>](support-policies-for-sql-server-native-client.md)  
 <span data-ttu-id="a98f4-121">討論要如何搭配不同版本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 使用各種資料存取元件。</span><span class="sxs-lookup"><span data-stu-id="a98f4-121">Discusses how various data-access components can be used with different versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 [<span data-ttu-id="a98f4-122">使用 SQL Server Native Client 連線到 Azure SQL Database</span><span class="sxs-lookup"><span data-stu-id="a98f4-122">Connecting to an Azure SQL Database Using SQL Server Native Client</span></span>](connecting-to-a-windows-azure-sql-database-using-sql-server-native-client.md)  
 <span data-ttu-id="a98f4-123">討論如何使用 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] Native Client 連接至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a98f4-123">Discusses how to connect to a [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a98f4-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a98f4-124">See Also</span></span>  
 <span data-ttu-id="a98f4-125">[SQL Server Native Client 程式設計](../sql-server-native-client-programming.md) </span><span class="sxs-lookup"><span data-stu-id="a98f4-125">[SQL Server Native Client Programming](../sql-server-native-client-programming.md) </span></span>  
 <span data-ttu-id="a98f4-126">[ODBC 的使用說明主題](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="a98f4-126">[ODBC How-to Topics](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span></span>  
 [<span data-ttu-id="a98f4-127">OLE DB 的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="a98f4-127">OLE DB How-to Topics</span></span>](../../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
