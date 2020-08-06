---
title: 支援的 .NET Framework 程式庫 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], .NET Framework libraries
- .NET Framework [CLR Integration]
ms.assetid: 417544ff-c25c-496e-add4-2f278f8a4911
author: rothja
ms.author: jroth
ms.openlocfilehash: 22f92e3eadccc869452cf35534f786724c8e259a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584575"
---
# <a name="supported-net-framework-libraries"></a><span data-ttu-id="96d28-102">支援的 .NET Framework 程式庫</span><span class="sxs-lookup"><span data-stu-id="96d28-102">Supported .NET Framework Libraries</span></span>
  <span data-ttu-id="96d28-103">利用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中裝載的 Common Language Runtime (CLR)，您能夠以 Managed 程式碼撰寫預存程序、觸發程序、使用者定義函數、使用者定義型別及使用者定義彙總。</span><span class="sxs-lookup"><span data-stu-id="96d28-103">With the common language runtime (CLR) hosted in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="96d28-104">藉由 .NET Framework 類別庫所提供的功能，您可以存取預先建立的類別，這些類別可提供字串操作、進階數學運算、檔案存取、加密等多項功能。</span><span class="sxs-lookup"><span data-stu-id="96d28-104">With the functionality found in the .NET Framework class libraries, you have access to pre-built classes that provide functionality for string manipulation, advanced math operations, file access, cryptography, and more.</span></span> <span data-ttu-id="96d28-105">您可以透過任何 Managed 預存程序、使用者定義型別、觸發程序、使用者定義函數或使用者定義彙總來存取這些類別。</span><span class="sxs-lookup"><span data-stu-id="96d28-105">These classes can be accessed from any managed stored procedure, user-defined type, trigger, user-defined function, or user-defined aggregate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="96d28-106">如果您在全域組件快取中服務或升級不支援的元件 (GAC) ，您的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="96d28-106">If you service or upgrade unsupported assemblies in the global assembly cache (GAC), your [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="96d28-107">如果元件同時存在於 CLR 整合中，則為 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="96d28-107">If an assembly exists both in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR integration.</span></span> <span data-ttu-id="96d28-108">如果您在 GAC 中服務或升級的組件也已在資料庫中註冊 (包括不受支援的 .NET Framework 組件)，請務必也在您的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫中藉由 `ALTER ASSEMBLY` 陳述式來服務或升級該組件的副本。</span><span class="sxs-lookup"><span data-stu-id="96d28-108">If you service or upgrade any assemblies in the GAC that are also registered in the database, including unsupported .NET Framework assemblies, make sure to also service or upgrade the copy of the assembly inside your [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases with the `ALTER ASSEMBLY` statement.</span></span> <span data-ttu-id="96d28-109">如需詳細資訊，請參閱[知識庫文章 949080](https://support.microsoft.com/kb/949080)。</span><span class="sxs-lookup"><span data-stu-id="96d28-109">For more information, see [Knowledge Base article 949080](https://support.microsoft.com/kb/949080).</span></span>  
  
## <a name="supported-libraries"></a><span data-ttu-id="96d28-110">支援的程式庫</span><span class="sxs-lookup"><span data-stu-id="96d28-110">Supported Libraries</span></span>  
 <span data-ttu-id="96d28-111">從開始 [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] ，有一份支援的 .NET Framework 程式庫清單，其已進行測試，以確保它們符合與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 直接從全域組件快取 (GAC) 載入它們的互動可靠性和安全性標準。</span><span class="sxs-lookup"><span data-stu-id="96d28-111">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] has a list of supported .NET Framework libraries, which have been tested to ensure that they meet reliability and security standards for interaction with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] loads them directly from the Global Assembly Cache (GAC).</span></span>  
  
 <span data-ttu-id="96d28-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的 CLR 整合所支援的程式庫/命名空間是：</span><span class="sxs-lookup"><span data-stu-id="96d28-112">The libraries/namespaces supported by CLR integration in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] are:</span></span>  
  
-   <span data-ttu-id="96d28-113">CustomMarshalers</span><span class="sxs-lookup"><span data-stu-id="96d28-113">CustomMarshalers</span></span>  
  
-   <span data-ttu-id="96d28-114">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="96d28-114">Microsoft.VisualBasic</span></span>  
  
-   <span data-ttu-id="96d28-115">Microsoft.VisualC</span><span class="sxs-lookup"><span data-stu-id="96d28-115">Microsoft.VisualC</span></span>  
  
-   <span data-ttu-id="96d28-116">mscorlib</span><span class="sxs-lookup"><span data-stu-id="96d28-116">mscorlib</span></span>  
  
-   <span data-ttu-id="96d28-117">系統</span><span class="sxs-lookup"><span data-stu-id="96d28-117">System</span></span>  
  
-   <span data-ttu-id="96d28-118">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="96d28-118">System.Configuration</span></span>  
  
-   <span data-ttu-id="96d28-119">System.Data</span><span class="sxs-lookup"><span data-stu-id="96d28-119">System.Data</span></span>  
  
-   <span data-ttu-id="96d28-120">System.Data.OracleClient</span><span class="sxs-lookup"><span data-stu-id="96d28-120">System.Data.OracleClient</span></span>  
  
-   <span data-ttu-id="96d28-121">System.Data.SqlXml</span><span class="sxs-lookup"><span data-stu-id="96d28-121">System.Data.SqlXml</span></span>  
  
-   <span data-ttu-id="96d28-122">System.Deployment</span><span class="sxs-lookup"><span data-stu-id="96d28-122">System.Deployment</span></span>  
  
-   <span data-ttu-id="96d28-123">System.Security</span><span class="sxs-lookup"><span data-stu-id="96d28-123">System.Security</span></span>  
  
-   <span data-ttu-id="96d28-124">System.Transactions</span><span class="sxs-lookup"><span data-stu-id="96d28-124">System.Transactions</span></span>  
  
-   <span data-ttu-id="96d28-125">System.Web.Services</span><span class="sxs-lookup"><span data-stu-id="96d28-125">System.Web.Services</span></span>  
  
-   <span data-ttu-id="96d28-126">System.Xml</span><span class="sxs-lookup"><span data-stu-id="96d28-126">System.Xml</span></span>  
  
-   <span data-ttu-id="96d28-127">System.Core.dll</span><span class="sxs-lookup"><span data-stu-id="96d28-127">System.Core.dll</span></span>  
  
-   <span data-ttu-id="96d28-128">System.Xml.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="96d28-128">System.Xml.Linq.dll</span></span>  
  
## <a name="unsupported-libraries"></a><span data-ttu-id="96d28-129">不支援的程式庫</span><span class="sxs-lookup"><span data-stu-id="96d28-129">Unsupported Libraries</span></span>  
 <span data-ttu-id="96d28-130">不支援的程式庫仍可以從 Managed 預存程序、觸發程序、使用者定義函數、使用者定義型別和使用者定義彙總加以呼叫。</span><span class="sxs-lookup"><span data-stu-id="96d28-130">Unsupported libraries can still be called from your managed stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates.</span></span> <span data-ttu-id="96d28-131">您必須先使用 `CREATE ASSEMBLY` 陳述式在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫中註冊不支援的程式庫，才能在程式碼中使用該程式庫。</span><span class="sxs-lookup"><span data-stu-id="96d28-131">The unsupported library must first be registered in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, using the `CREATE ASSEMBLY` statement, before it can be used in your code.</span></span> <span data-ttu-id="96d28-132">為了確保安全性和可靠性，任何在伺服器上註冊及執行的不支援程式庫都應該經過檢閱和測試。</span><span class="sxs-lookup"><span data-stu-id="96d28-132">Any unsupported library that is registered and run on the server should be reviewed and tested for security and reliability.</span></span>  
  
 <span data-ttu-id="96d28-133">例如，`System.DirectoryServices` 命名空間並不受支援。</span><span class="sxs-lookup"><span data-stu-id="96d28-133">For example, the `System.DirectoryServices` namespace is not supported.</span></span> <span data-ttu-id="96d28-134">您必須使用 `UNSAFE` 權限註冊 System.DirectoryServices.dll 組件，才能從程式碼中加以呼叫。</span><span class="sxs-lookup"><span data-stu-id="96d28-134">You must register the System.DirectoryServices.dll assembly with `UNSAFE` permissions before you can call it from your code.</span></span> <span data-ttu-id="96d28-135">`UNSAFE` 權限是必要的，因為 `System.DirectoryServices` 命名空間中的類別並不符合 `SAFE` 或 `EXTERNAL_ACCESS` 的需求。</span><span class="sxs-lookup"><span data-stu-id="96d28-135">The `UNSAFE` permission is necessary because classes in the `System.DirectoryServices` namespace do not meet the requirements for `SAFE` or `EXTERNAL_ACCESS`.</span></span> <span data-ttu-id="96d28-136">如需詳細資訊，請參閱[Clr 整合程式設計模型限制](clr-integration-programming-model-restrictions.md)和[clr 整合代碼啟用安全性](../security/clr-integration-code-access-security.md)。</span><span class="sxs-lookup"><span data-stu-id="96d28-136">For more information, see [CLR Integration Programming Model Restrictions](clr-integration-programming-model-restrictions.md) and [CLR Integration Code Access Security](../security/clr-integration-code-access-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96d28-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96d28-137">See Also</span></span>  
 <span data-ttu-id="96d28-138">[建立元件](../assemblies/creating-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="96d28-138">[Creating an Assembly](../assemblies/creating-an-assembly.md) </span></span>  
 <span data-ttu-id="96d28-139">[CLR 整合代碼啟用安全性](../security/clr-integration-code-access-security.md) </span><span class="sxs-lookup"><span data-stu-id="96d28-139">[CLR Integration Code Access Security](../security/clr-integration-code-access-security.md) </span></span>  
 [<span data-ttu-id="96d28-140">CLR 整合程式設計模型限制</span><span class="sxs-lookup"><span data-stu-id="96d28-140">CLR Integration Programming Model Restrictions</span></span>](clr-integration-programming-model-restrictions.md)  
  
  
