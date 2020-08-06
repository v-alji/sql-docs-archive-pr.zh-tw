---
title: SQL Server ADO.NET 的同進程特定延伸模組 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
author: rothja
ms.author: jroth
ms.openlocfilehash: 37d8aedc1d8f93739c2e9386665adfc67b43e312
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606372"
---
# <a name="sql-server-in-process-specific-extensions-to-adonet"></a><span data-ttu-id="f2be4-102">ADO.NET 的 SQL Server 同處理序特定擴充</span><span class="sxs-lookup"><span data-stu-id="f2be4-102">SQL Server In-Process Specific Extensions to ADO.NET</span></span>
  <span data-ttu-id="f2be4-103">ADO.NET 有四個專門用於同處理序的主要功能擴充。</span><span class="sxs-lookup"><span data-stu-id="f2be4-103">There are four main functional extensions to ADO.NET that are specifically for in-process use.</span></span> <span data-ttu-id="f2be4-104">下列主題將詳細說明這些擴充功能。</span><span class="sxs-lookup"><span data-stu-id="f2be4-104">The following topics will cover these extensions in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f2be4-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="f2be4-105">In This Section</span></span>  
 [<span data-ttu-id="f2be4-106">SqlContext 物件</span><span class="sxs-lookup"><span data-stu-id="f2be4-106">SqlContext Object</span></span>](sqlcontext-object.md)  
 <span data-ttu-id="f2be4-107">此類別會摘要執行 Managed 程式碼同處理序之 SQL Server 常式呼叫者的內容，藉以存取其他延伸模組。</span><span class="sxs-lookup"><span data-stu-id="f2be4-107">This class provides access to the other extensions by abstracting the context of a caller of a SQL Server routine that executes managed code in-process.</span></span>  
  
 [<span data-ttu-id="f2be4-108">SqlPipe 物件</span><span class="sxs-lookup"><span data-stu-id="f2be4-108">SqlPipe Object</span></span>](sqlpipe-object.md)  
 <span data-ttu-id="f2be4-109">此類別包含可將表格式結果和訊息傳送到用戶端的常式。</span><span class="sxs-lookup"><span data-stu-id="f2be4-109">This class contains routines to send tabular results and messages to the client.</span></span>  
  
 [<span data-ttu-id="f2be4-110">SqlTriggerContext 物件</span><span class="sxs-lookup"><span data-stu-id="f2be4-110">SqlTriggerContext Object</span></span>](sqltriggercontext-object.md)  
 <span data-ttu-id="f2be4-111">此類別提供執行觸發程序之內容的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f2be4-111">This class provides information on the context in which a trigger is run.</span></span>  
  
 [<span data-ttu-id="f2be4-112">SqlDataRecord 物件</span><span class="sxs-lookup"><span data-stu-id="f2be4-112">SqlDataRecord Object</span></span>](sqldatarecord-object.md)  
 <span data-ttu-id="f2be4-113">SqlDataRecord 類別會要求單一資料列的資料及其相關的中繼資料，並允許預存程序將自訂結果集傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="f2be4-113">The SqlDataRecord class represents a single row of data, along with its related metadata, and allows stored procedures to return custom result sets to the client.</span></span>  
  
  
