---
title: 執行命令 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
author: rothja
ms.author: jroth
ms.openlocfilehash: 41e8da036d5a4b6469a31213247ad7d4edb7dbfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598833"
---
# <a name="executing-a-command"></a><span data-ttu-id="d2fad-102">執行命令</span><span class="sxs-lookup"><span data-stu-id="d2fad-102">Executing a Command</span></span>
  <span data-ttu-id="d2fad-103">建立資料來源的連接後，取用者會呼叫 **IDBCreateSession::CreateSession** 方法來建立工作階段。</span><span class="sxs-lookup"><span data-stu-id="d2fad-103">After the connection to a data source is established, the consumer calls the **IDBCreateSession::CreateSession** method to create a session.</span></span> <span data-ttu-id="d2fad-104">此工作階段會當做命令、資料列集或交易 Factory 運作。</span><span class="sxs-lookup"><span data-stu-id="d2fad-104">The session acts as a command, rowset, or transaction factory.</span></span>  
  
 <span data-ttu-id="d2fad-105">若要直接使用個別的資料表或索引，取用者會要求 `IOpenRowset` 介面。</span><span class="sxs-lookup"><span data-stu-id="d2fad-105">To work directly with individual tables or indexes, the consumer requests the `IOpenRowset` interface.</span></span> <span data-ttu-id="d2fad-106">`IOpenRowset::OpenRowset` 方法會從單一基底資料表或索引開啟並傳回包含所有資料列的資料列集。</span><span class="sxs-lookup"><span data-stu-id="d2fad-106">The `IOpenRowset::OpenRowset` method opens and returns a rowset that includes all rows from a single base table or index.</span></span>  
  
 <span data-ttu-id="d2fad-107">若要執行命令 (例如 SELECT \* FROM 作者) ，取用者會要求 `IDBCreateCommand` 介面。</span><span class="sxs-lookup"><span data-stu-id="d2fad-107">To execute a command (such as SELECT \* FROM Authors), the consumer requests the `IDBCreateCommand` interface.</span></span> <span data-ttu-id="d2fad-108">取用者可以執行 `IDBCreateCommand::CreateCommand` 方法來建立命令物件並要求 `ICommandText` 介面。</span><span class="sxs-lookup"><span data-stu-id="d2fad-108">The consumer can execute the `IDBCreateCommand::CreateCommand` method to create a command object and request for the `ICommandText` interface.</span></span> <span data-ttu-id="d2fad-109">`ICommandText::SetCommandText` 方法用於指定即將執行的命令。</span><span class="sxs-lookup"><span data-stu-id="d2fad-109">The `ICommandText::SetCommandText` method is used to specify the command that is to be executed.</span></span>  
  
 <span data-ttu-id="d2fad-110">`Execute` 命令用於執行命令。</span><span class="sxs-lookup"><span data-stu-id="d2fad-110">The `Execute` command is used to execute the command.</span></span> <span data-ttu-id="d2fad-111">此命令可以是任何 SQL 陳述式或程序名稱。</span><span class="sxs-lookup"><span data-stu-id="d2fad-111">The command can be any SQL statement or procedure name.</span></span> <span data-ttu-id="d2fad-112">並非所有命令都會產生結果集 (資料列集) 物件。</span><span class="sxs-lookup"><span data-stu-id="d2fad-112">Not all commands produce a result set (rowset) object.</span></span> <span data-ttu-id="d2fad-113">SELECT \* FROM Authors 之類的命令會產生結果集。</span><span class="sxs-lookup"><span data-stu-id="d2fad-113">Commands such as SELECT \* FROM Authors produce a result set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2fad-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2fad-114">See Also</span></span>  
 [<span data-ttu-id="d2fad-115">建立 SQL Server Native Client OLE DB 提供者應用程式</span><span class="sxs-lookup"><span data-stu-id="d2fad-115">Creating a SQL Server Native Client OLE DB Provider Application</span></span>](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
