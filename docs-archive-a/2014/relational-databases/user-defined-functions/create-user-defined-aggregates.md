---
title: 建立使用者定義彙總 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- aggregate functions [SQL Server], user-defined
- user-defined functions [CLR integration]
ms.assetid: c278b746-6323-4b32-b460-239915acc067
author: rothja
ms.author: jroth
ms.openlocfilehash: c91179cb194bbfb79e8e7a8476e9725877b88afa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708142"
---
# <a name="create-user-defined-aggregates"></a><span data-ttu-id="faa44-102">建立使用者定義彙總</span><span class="sxs-lookup"><span data-stu-id="faa44-102">Create User-defined Aggregates</span></span>
  <span data-ttu-id="faa44-103">您可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中建立資料庫物件，此功能是以 CLR 組件設計而成。</span><span class="sxs-lookup"><span data-stu-id="faa44-103">You can create a database object inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is programmed in a CLR assembly.</span></span> <span data-ttu-id="faa44-104">可以使用 CLR 提供之多種程式設計模型的資料庫物件，包括觸發程序、預存程序、函數、彙總函式和類型。</span><span class="sxs-lookup"><span data-stu-id="faa44-104">Database objects that can leverage the rich programming model provided by the CLR include triggers, stored procedures, functions, aggregate functions, and types.</span></span>  
  
 <span data-ttu-id="faa44-105">就像 [!INCLUDE[tsql](../../includes/tsql-md.md)]所提供的內建彙總函式一樣，使用者定義彙總函式會執行一組值的計算並傳回單一值。</span><span class="sxs-lookup"><span data-stu-id="faa44-105">Like the built-in aggregate functions provided in [!INCLUDE[tsql](../../includes/tsql-md.md)], user-defined aggregate functions perform a calculation on a set of values and return a single value.</span></span>  
  
 <span data-ttu-id="faa44-106">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中建立使用者定義彙總函式包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="faa44-106">Creating a user-defined aggregate function in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] involves the following steps:</span></span>  
  
-   <span data-ttu-id="faa44-107">將使用者定義彙總函式定義為以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 支援的語言寫成的類別。</span><span class="sxs-lookup"><span data-stu-id="faa44-107">Define the user-defined aggregate function as a class in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-supported language.</span></span> <span data-ttu-id="faa44-108">如需如何以 CLR 撰寫使用者定義彙總的詳細資訊，請參閱 [CLR 使用者定義彙總](../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)。</span><span class="sxs-lookup"><span data-stu-id="faa44-108">For more information about how to program user-defined aggregates in the CLR, see [CLR User-Defined Aggregates](../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md).</span></span> <span data-ttu-id="faa44-109">使用適當的語言編譯器來編譯此類別以建立 CLR 組件。</span><span class="sxs-lookup"><span data-stu-id="faa44-109">Compile this class to build a CLR assembly using the appropriate language compiler.</span></span>  
  
-   <span data-ttu-id="faa44-110">使用 CREATE ASSEMBLY 陳述式在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中登錄組件。</span><span class="sxs-lookup"><span data-stu-id="faa44-110">Register the assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the CREATE ASSEMBLY statement.</span></span> <span data-ttu-id="faa44-111">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中之組件的詳細資訊，請參閱[組件 &#40;Database Engine&#41;](../clr-integration/assemblies-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="faa44-111">For more information about assemblies in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Assemblies &#40;Database Engine&#41;](../clr-integration/assemblies-database-engine.md).</span></span>  
  
-   <span data-ttu-id="faa44-112">使用 CREATE AGGREGATE 陳述式建立參考註冊組件的使用者自訂彙總。</span><span class="sxs-lookup"><span data-stu-id="faa44-112">Create the user-defined aggregate that references the registered assembly using the CREATE AGGREGATE statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="faa44-113">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 中部署 SQL Server 專案，便會在已指定給專案的資料庫中註冊組件。</span><span class="sxs-lookup"><span data-stu-id="faa44-113">Deploying a SQL Server Project in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] registers an assembly in the database that was specified for the project.</span></span> <span data-ttu-id="faa44-114">部署專案時，也會在資料庫中為所有以 `SqlUserDefinedAggregate` 屬性註解的類別定義建立使用者自訂彙總。</span><span class="sxs-lookup"><span data-stu-id="faa44-114">Deploying the project also creates a user-defined aggregate in the database for all class definitions annotated with the `SqlUserDefinedAggregate` attribute.</span></span> <span data-ttu-id="faa44-115">如需詳細資訊，請參閱 [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="faa44-115">For more information, see [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="faa44-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行 CLR 程式碼的功能預設為關閉。</span><span class="sxs-lookup"><span data-stu-id="faa44-116">The ability of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to execute CLR code is off by default.</span></span> <span data-ttu-id="faa44-117">您可以建立、改變和卸除參考 Managed 程式碼模組的資料庫物件，但是除非使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sp_configure (Transact-SQL) [來啟用](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) [CLR 已啟用] 選項 [，否則在](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)中將無法執行這些參考。</span><span class="sxs-lookup"><span data-stu-id="faa44-117">You can create, alter and drop database objects that reference managed code modules, but these references will not execute in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unless the [clr enabled Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) is enabled using [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>  
  
 <span data-ttu-id="faa44-118">**若要建立、修改或卸除組件**</span><span class="sxs-lookup"><span data-stu-id="faa44-118">**To create, modify, or drop an assembly**</span></span>  
  
-   [<span data-ttu-id="faa44-119">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="faa44-119">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [<span data-ttu-id="faa44-120">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="faa44-120">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [<span data-ttu-id="faa44-121">DROP ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="faa44-121">DROP ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 <span data-ttu-id="faa44-122">**若要建立使用者自訂彙總**</span><span class="sxs-lookup"><span data-stu-id="faa44-122">**To create a user-defined aggregate**</span></span>  
  
-   [<span data-ttu-id="faa44-123">CREATE AGGREGATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="faa44-123">CREATE AGGREGATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-aggregate-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="faa44-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="faa44-124">See Also</span></span>  
 [<span data-ttu-id="faa44-125">Common Language Runtime &#40;CLR&#41; 整合程式設計概念</span><span class="sxs-lookup"><span data-stu-id="faa44-125">Common Language Runtime &#40;CLR&#41; Integration Programming Concepts</span></span>](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
