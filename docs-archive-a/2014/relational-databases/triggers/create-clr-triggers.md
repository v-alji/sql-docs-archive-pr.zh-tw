---
title: 建立 CLR 觸發程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- CRL triggers
- DML triggers, CLR triggers
- DDL triggers, CLR triggers
ms.assetid: 31f41703-134d-49fc-9850-76c297351c2c
author: rothja
ms.author: jroth
ms.openlocfilehash: 3afd841b4f1f9ca567a93c0a20c0a7609a5b45e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606152"
---
# <a name="create-clr-triggers"></a><span data-ttu-id="b39ce-102">建立 CLR 觸發程序</span><span class="sxs-lookup"><span data-stu-id="b39ce-102">Create CLR Triggers</span></span>
  <span data-ttu-id="b39ce-103">您可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中建立資料庫物件，這些物件是透過使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Common Language Runtime (CLR) 建立的組件所撰寫。</span><span class="sxs-lookup"><span data-stu-id="b39ce-103">You can create a database object inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is programmed in an assembly created in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language runtime (CLR).</span></span> <span data-ttu-id="b39ce-104">可以使用 CLR 所提供之豐富程式設計模型的資料庫物件，包括 DML 觸發程序、DDL 觸發程序、預存程序、函數、彙總函式以及類型。</span><span class="sxs-lookup"><span data-stu-id="b39ce-104">Database objects that can leverage the rich programming model provided by the CLR include DML triggers, DDL triggers, stored procedures, functions, aggregate functions, and types.</span></span>  
  
 <span data-ttu-id="b39ce-105">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中建立 CLR 觸發程序 (DML 或 DDL) 包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b39ce-105">Creating a CLR trigger (DML or DDL) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] involves the following steps:</span></span>  
  
-   <span data-ttu-id="b39ce-106">以 .NET Framework 支援的語言，將觸發程序定義為類別。</span><span class="sxs-lookup"><span data-stu-id="b39ce-106">Define the trigger as a class in a .NET Framework-supported language.</span></span> <span data-ttu-id="b39ce-107">如需如何在 CLR 中設計觸發程序的程式的詳細資訊，請參閱 [CLR 觸發程序](../../database-engine/dev-guide/clr-triggers.md)。</span><span class="sxs-lookup"><span data-stu-id="b39ce-107">For more information about how to program triggers in the CLR, see [CLR Triggers](../../database-engine/dev-guide/clr-triggers.md).</span></span> <span data-ttu-id="b39ce-108">然後，使用適當的語言編譯器編譯類別，在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 中建立組件。</span><span class="sxs-lookup"><span data-stu-id="b39ce-108">Then, compile the class to build an assembly in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] using the appropriate language compiler.</span></span>  
  
-   <span data-ttu-id="b39ce-109">使用 CREATE ASSEMBLY 陳述式在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中登錄組件。</span><span class="sxs-lookup"><span data-stu-id="b39ce-109">Register the assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the CREATE ASSEMBLY statement.</span></span> <span data-ttu-id="b39ce-110">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中之組件的詳細資訊，請參閱[組件 &#40;Database Engine&#41;](../clr-integration/assemblies-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="b39ce-110">For more information about assemblies in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Assemblies &#40;Database Engine&#41;](../clr-integration/assemblies-database-engine.md).</span></span>  
  
-   <span data-ttu-id="b39ce-111">建立參考所登錄之組件的觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b39ce-111">Create the trigger that references the registered assembly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b39ce-112">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 中部署 SQL Server 專案，便會在已指定給專案的資料庫中註冊組件。</span><span class="sxs-lookup"><span data-stu-id="b39ce-112">Deploying a SQL Server Project in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] registers an assembly in the database that was specified for the project.</span></span> <span data-ttu-id="b39ce-113">部署專案也會在資料庫中，為所有以 `SqlTrigger` 屬性註解的方法建立 CLR 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b39ce-113">Deploying the project also creates CLR triggers in the database for all methods annotated with the `SqlTrigger` attribute.</span></span> <span data-ttu-id="b39ce-114">如需詳細資訊，請參閱 [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="b39ce-114">For more information, see [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b39ce-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行 CLR 程式碼的功能預設為關閉。</span><span class="sxs-lookup"><span data-stu-id="b39ce-115">The ability of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to execute CLR code is off by default.</span></span> <span data-ttu-id="b39ce-116">您可以建立、修改和卸除參考 Managed 程式碼模組的物件，但是除非使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sp_configure (Transact-SQL) [來啟用](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) clr enabled 選項 [，否則在](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)中將無法執行這些參考。</span><span class="sxs-lookup"><span data-stu-id="b39ce-116">You can create, alter, and drop database objects that reference managed code modules, but these references will not execute in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unless the [clr enabled Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) is enabled using [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>  
  
 <span data-ttu-id="b39ce-117">**若要建立、修改或卸除組件**</span><span class="sxs-lookup"><span data-stu-id="b39ce-117">**To create, modify, or drop an assembly**</span></span>  
  
-   [<span data-ttu-id="b39ce-118">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b39ce-118">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [<span data-ttu-id="b39ce-119">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b39ce-119">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [<span data-ttu-id="b39ce-120">DROP ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b39ce-120">DROP ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 <span data-ttu-id="b39ce-121">**若要建立 CLR 觸發程序**</span><span class="sxs-lookup"><span data-stu-id="b39ce-121">**To create a CLR trigger**</span></span>  
  
-   [<span data-ttu-id="b39ce-122">CREATE TRIGGER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b39ce-122">CREATE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-trigger-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="b39ce-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b39ce-123">See Also</span></span>  
 <span data-ttu-id="b39ce-124">[DML 觸發程序](dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="b39ce-124">[DML Triggers](dml-triggers.md) </span></span>  
 <span data-ttu-id="b39ce-125">[Common Language Runtime &#40;CLR&#41; 整合程式設計概念](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="b39ce-125">[Common Language Runtime &#40;CLR&#41; Integration Programming Concepts](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md) </span></span>  
 [<span data-ttu-id="b39ce-126">從 CLR 資料庫物件進行資料存取</span><span class="sxs-lookup"><span data-stu-id="b39ce-126">Data Access from CLR Database Objects</span></span>](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
