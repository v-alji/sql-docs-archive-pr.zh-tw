---
title: CLR 使用者定義類型 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- validation [CLR integration]
- types [CLR integration]
- UserDefined serialization format [CLR integration]
- null values [CLR integration]
- serialization
- Native serialization format [CLR integration]
- databases [CLR integration]
- building database objects [CLR integration], user-defined types
- user-defined types [CLR integration]
- common language runtime [SQL Server], user-defined types
- UDTs [CLR integration]
- database objects [CLR integration], user-defined types
- turning on CLR functionality
- customizing UDT expression return types [CLR integration]
- UDTs [CLR integration], about UDTs
- comparing UDT values
- annotations [CLR integration]
- user-defined types [CLR integration], about UDTs
- variables [CLR integration]
- invoking UDT methods
- indexes [CLR integration]
ms.assetid: 27c4889b-c543-47a8-a630-ad06804f92df
author: rothja
ms.author: jroth
ms.openlocfilehash: e4e19323eeac9e0a1148924543f71aa7de5619b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606909"
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="f4c2a-102">CLR 使用者定義類型</span><span class="sxs-lookup"><span data-stu-id="f4c2a-102">CLR User-Defined Types</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f4c2a-103">提供的功能可讓您建立針對 .NET Framework Common Language Runtime (CLR) 中建立的組件來進行程式設計的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-103">gives you the ability to create database objects that are programmed against an assembly created in the.NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="f4c2a-104">資料庫物件可充分運用 CLR 所提供的豐富程式設計模型，包括觸發程序、預存程序、函數、彙總函式和類型等。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-104">Database objects that can take advantage of the rich programming model provided by the CLR include triggers, stored procedures, functions, aggregate functions, and types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4c2a-105">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，執行 CLR 程式碼的功能預設會設定為 OFF。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-105">The ability to execute CLR code is set to OFF by default in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f4c2a-106">您可以使用**sp_configure**系統預存程式來啟用 CLR。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-106">The CLR can be enabled by using the **sp_configure** system stored procedure.</span></span>  
  
 <span data-ttu-id="f4c2a-107">從開始 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ，您可以使用使用者定義型別 (udt) 來擴充伺服器的純量類型系統，以便在資料庫中儲存 CLR 物件 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-107">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], you can use user-defined types (UDTs) to extend the scalar type system of the server, enabling storage of CLR objects in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="f4c2a-108">UDT 可以包含多個元素並可以具有行為，使其有別於由單一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料類型組成的傳統別名資料類型。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-108">UDTs can contain multiple elements and can have behaviors, differentiating them from the traditional alias data types which consist of a single [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system data type.</span></span>  
  
 <span data-ttu-id="f4c2a-109">因為系統將 UDT 當做一個整體來進行存取，所以它們使用的複雜資料類型可能會對效能產生負面影響。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-109">Because UDTs are accessed by the system as a whole, their use for complex data types may negatively impact performance.</span></span> <span data-ttu-id="f4c2a-110">通常使用傳統資料列及資料表可以對複雜資料進行最佳模型化。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-110">Complex data is generally best modeled using traditional rows and tables.</span></span> <span data-ttu-id="f4c2a-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 UDT 適用於以下項目：</span><span class="sxs-lookup"><span data-stu-id="f4c2a-111">UDTs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are well suited to the following:</span></span>  
  
-   <span data-ttu-id="f4c2a-112">日期、時間、貨幣及擴充的數值類型</span><span class="sxs-lookup"><span data-stu-id="f4c2a-112">Date, time, currency, and extended numeric types</span></span>  
  
-   <span data-ttu-id="f4c2a-113">Geospatial 應用程式</span><span class="sxs-lookup"><span data-stu-id="f4c2a-113">Geospatial applications</span></span>  
  
-   <span data-ttu-id="f4c2a-114">編碼或加密的資料</span><span class="sxs-lookup"><span data-stu-id="f4c2a-114">Encoded or encrypted data</span></span>  
  
 <span data-ttu-id="f4c2a-115">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中開發 UDT 的過程包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f4c2a-115">The process of developing UDTs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consists of the following steps:</span></span>  
  
1.  <span data-ttu-id="f4c2a-116">**編寫和建立定義 UDT 的組件。**</span><span class="sxs-lookup"><span data-stu-id="f4c2a-116">**Code and build the assembly that defines the UDT.**</span></span> <span data-ttu-id="f4c2a-117">UDT 是使用會產生可驗證程式碼之 .NET Framework Common Language Runtime (CLR) 支援的任何語言所定義。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-117">UDTs are defined using any of the languages supported by the.NET Framework common language runtime (CLR) that produce verifiable code.</span></span> <span data-ttu-id="f4c2a-118">這包括 Visual C# 和 Visual Basic .NET。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-118">This includes Visual C# and Visual Basic .NET.</span></span> <span data-ttu-id="f4c2a-119">資料會公開為 .NET Framework 類別或結構的欄位及屬性，並且其行為是由類別或結構的方法所定義。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-119">The data is exposed as fields and properties of a .NET Framework class or structure, and behaviors are defined by methods of the class or structure.</span></span>  
  
2.  <span data-ttu-id="f4c2a-120">**註冊組件。**</span><span class="sxs-lookup"><span data-stu-id="f4c2a-120">**Register the assembly.**</span></span> <span data-ttu-id="f4c2a-121">Udt 可以透過資料庫專案中的 Visual Studio 使用者介面來部署，或藉由使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY 語句，將包含類別或結構的元件複製到資料庫中。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-121">UDTs can be deployed through the Visual Studio user interface in a database project, or by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY statement, which copies the assembly containing the class or structure into a database.</span></span>  
  
3.  <span data-ttu-id="f4c2a-122">**在 SQL Server 中建立 UDT。**</span><span class="sxs-lookup"><span data-stu-id="f4c2a-122">**Create the UDT in SQL Server.**</span></span> <span data-ttu-id="f4c2a-123">將元件載入到主機資料庫之後，您可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE 語句來建立 udt，並將類別或結構的成員公開為 UDT 的成員。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-123">Once an assembly is loaded into a host database, you use the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE statement to create a UDT and expose the members of the class or structure as members of the UDT.</span></span> <span data-ttu-id="f4c2a-124">UDT 僅存在於單一資料庫的內容中，並且一旦註冊後，就不再與建立它們的外部檔案具有相依性。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-124">UDTs exist only in the context of a single database, and, once registered, have no dependencies on the external files from which they were created.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f4c2a-125">在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 之前，不支援從 .NET Framework 組件建立的 UDT。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-125">Before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], UDTs created from .NET Framework assemblies were not supported.</span></span> <span data-ttu-id="f4c2a-126">不過，您仍然可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sp_addtype**來使用別名資料類型。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-126">However, you can still use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alias data types by using **sp_addtype**.</span></span> <span data-ttu-id="f4c2a-127">CREATE TYPE 語法可用來建立原生 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者定義資料類型及 UDT。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-127">The CREATE TYPE syntax can be used for creating both native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user-defined data types and UDTs.</span></span>  
  
4.  <span data-ttu-id="f4c2a-128">**使用 UDT 建立資料表、變數或參數**從開始 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ，使用者定義型別可用來當做資料表的資料行定義、批次中的變數 [!INCLUDE[tsql](../../includes/tsql-md.md)] ，或當做 [!INCLUDE[tsql](../../includes/tsql-md.md)] 函數或預存程式的引數。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-128">**Create tables, variables, or parameters using the UDT** Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], a user-defined type can be used as the column definition of a table, as a variable in a [!INCLUDE[tsql](../../includes/tsql-md.md)] batch, or as an argument of a [!INCLUDE[tsql](../../includes/tsql-md.md)] function or stored procedure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f4c2a-129">本節內容</span><span class="sxs-lookup"><span data-stu-id="f4c2a-129">In This Section</span></span>  
 [<span data-ttu-id="f4c2a-130">建立使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="f4c2a-130">Creating a User-Defined Type</span></span>](creating-user-defined-types.md)  
 <span data-ttu-id="f4c2a-131">描述如何建立 UDT。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-131">Describes how to create UDTs.</span></span>  
  
 [<span data-ttu-id="f4c2a-132">在 SQL Server 中註冊使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="f4c2a-132">Registering User-Defined Types in SQL Server</span></span>](registering-user-defined-types-in-sql-server.md)  
 <span data-ttu-id="f4c2a-133">描述如何在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中註冊及管理 UDT。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-133">Describes how to register and manage UDTs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="f4c2a-134">在 SQL Server 中使用使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="f4c2a-134">Working with User-Defined Types in SQL Server</span></span>](working-with-user-defined-types-in-sql-server.md)  
 <span data-ttu-id="f4c2a-135">描述如何使用 UDT 建立查詢。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-135">Describes how to create queries using UDTs.</span></span>  
  
 [<span data-ttu-id="f4c2a-136">存取 ADO.NET 中的使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="f4c2a-136">Accessing User-Defined Types in ADO.NET</span></span>](accessing-user-defined-types-in-ado-net.md)  
 <span data-ttu-id="f4c2a-137">描述如何在 ADO.NET 中，使用 .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 來處理 UDT。</span><span class="sxs-lookup"><span data-stu-id="f4c2a-137">Describes how to work with UDTs using the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in ADO.NET.</span></span>  
  
  
