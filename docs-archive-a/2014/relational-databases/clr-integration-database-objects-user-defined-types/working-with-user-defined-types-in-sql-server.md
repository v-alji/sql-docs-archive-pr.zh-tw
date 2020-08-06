---
title: 在 SQL Server 中使用使用者自訂類型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- user-defined types [CLR integration], queries
- UDTs [CLR integration], queries
- user-defined types [CLR integration], Transact-SQL
- UDTs [CLR integration], Transact-SQL
- queries [CLR integration]
ms.assetid: 807376fb-1f1a-4f2a-8cf8-a622c5858634
author: rothja
ms.author: jroth
ms.openlocfilehash: c9fed9ad4e73102eadd1374ff87d2a46d0ff4126
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698317"
---
# <a name="working-with-user-defined-types-in-sql-server"></a><span data-ttu-id="943e0-102">使用 SQL Server 中的使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="943e0-102">Working with User-Defined Types in SQL Server</span></span>
  <span data-ttu-id="943e0-103">您可以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 使用一般查詢語法，從語言中的 (UDT) 功能來存取使用者定義型別。</span><span class="sxs-lookup"><span data-stu-id="943e0-103">You can access user-defined type (UDT) functionality in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[tsql](../../includes/tsql-md.md)] language by using regular query syntax.</span></span> <span data-ttu-id="943e0-104">在資料庫物件定義中，UDT 可當做 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次、函數及預存程序中的變數，以及函數及預存程序中的引數使用。</span><span class="sxs-lookup"><span data-stu-id="943e0-104">UDTs can be used in the definition of database objects, as variables in [!INCLUDE[tsql](../../includes/tsql-md.md)] batches, in functions and stored procedures, and as arguments in functions and stored procedures.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="943e0-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="943e0-105">In This Section</span></span>  
 [<span data-ttu-id="943e0-106">定義 UDT 資料表及資料行</span><span class="sxs-lookup"><span data-stu-id="943e0-106">Defining UDT Tables and Columns</span></span>](working-with-user-defined-types-defining-udt-tables-and-columns.md)  
 <span data-ttu-id="943e0-107">描述如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 建立資料表中的 UDT 資料行。</span><span class="sxs-lookup"><span data-stu-id="943e0-107">Describes how to use [!INCLUDE[tsql](../../includes/tsql-md.md)] to create a UDT column in a table.</span></span>  
  
 [<span data-ttu-id="943e0-108">操作 UDT 資料</span><span class="sxs-lookup"><span data-stu-id="943e0-108">Manipulating UDT Data</span></span>](working-with-user-defined-types-manipulating-udt-data.md)  
 <span data-ttu-id="943e0-109">描述如何透過 [!INCLUDE[tsql](../../includes/tsql-md.md)] 使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 UDT 資料。</span><span class="sxs-lookup"><span data-stu-id="943e0-109">Describes how to use [!INCLUDE[tsql](../../includes/tsql-md.md)] to work with UDT data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="943e0-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="943e0-110">See Also</span></span>  
 [<span data-ttu-id="943e0-111">CLR 使用者定義類型</span><span class="sxs-lookup"><span data-stu-id="943e0-111">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
  
  
