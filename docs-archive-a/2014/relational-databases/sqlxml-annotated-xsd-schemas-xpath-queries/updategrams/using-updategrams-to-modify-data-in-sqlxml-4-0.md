---
title: 使用 Updategram 來修改 SQLXML 4.0 中的資料 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, updategrams
- data insertions [SQLXML]
- data deletions [SQLXML]
- updating data [SQLXML]
- modifying data [SQLXML]
- OPENXML function
- updategrams [SQLXML]
- database modifications [SQLXML]
- data updates [SQLXML]
- modifying databases
- data modifications [SQLXML]
- deleting data
- inserting data
ms.assetid: b8b3b892-cb73-41d0-b945-bce148d81d9b
author: rothja
ms.author: jroth
ms.openlocfilehash: a4a2397668ed08df91377cc35dea22fd52788580
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597733"
---
# <a name="using-updategrams-to-modify-data-in-sqlxml-40"></a><span data-ttu-id="4c338-102">使用 Updategram 來修改 SQLXML 4.0 中的資料</span><span class="sxs-lookup"><span data-stu-id="4c338-102">Using Updategrams to Modify Data in SQLXML 4.0</span></span>
  <span data-ttu-id="4c338-103">您可以 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用 UPDATEGRAM 或 OPENXML 函數，從現有的 XML 檔修改中的資料庫)  (插入、更新或刪除 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4c338-103">You can modify (insert, update, or delete) a database in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from an existing XML document by using an updategram or the OPENXML [!INCLUDE[tsql](../../../includes/tsql-md.md)] function.</span></span>  
  
 <span data-ttu-id="4c338-104">本節提供有關 Updategram 及其使用範例的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c338-104">This section provides information about updategrams and examples of their usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c338-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="4c338-105">In This Section</span></span>  
 [<span data-ttu-id="4c338-106">Updategram &#40;SQLXML 4.0&#41;簡介</span><span class="sxs-lookup"><span data-stu-id="4c338-106">Introduction to Updategrams &#40;SQLXML 4.0&#41;</span></span>](introduction-to-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="4c338-107">提供 Updategram 的基本資訊和範例。</span><span class="sxs-lookup"><span data-stu-id="4c338-107">Provides basic information and examples of updategrams.</span></span>  
  
 [<span data-ttu-id="4c338-108">在 Updategram 中指定批註式對應架構 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4c338-108">Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;</span></span>](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)  
 <span data-ttu-id="4c338-109">說明與提供 Updategram 中的註解式對應結構描述範例。</span><span class="sxs-lookup"><span data-stu-id="4c338-109">Explains and provides examples of annotated mapping schemas in updategrams.</span></span>  
  
 [<span data-ttu-id="4c338-110">Null 處理 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4c338-110">NULL Handling &#40;SQLXML 4.0&#41;</span></span>](null-handling-sqlxml-4-0.md)  
 <span data-ttu-id="4c338-111">描述如何針對元素和屬性值指定 NULL。</span><span class="sxs-lookup"><span data-stu-id="4c338-111">Describes how to specify NULL for element and attribute values.</span></span>  
  
 [<span data-ttu-id="4c338-112">使用 XML Updategram 插入資料 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4c338-112">Inserting Data Using XML Updategrams &#40;SQLXML 4.0&#41;</span></span>](inserting-data-using-xml-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="4c338-113">描述與提供使用 Updategram 插入資料的範例。</span><span class="sxs-lookup"><span data-stu-id="4c338-113">Describes and provides examples of using updategrams to insert data.</span></span>  
  
 [<span data-ttu-id="4c338-114">使用 XML Updategram 刪除資料 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4c338-114">Deleting Data Using XML Updategrams &#40;SQLXML 4.0&#41;</span></span>](deleting-data-using-xml-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="4c338-115">描述與提供使用 Updategram 刪除資料的範例。</span><span class="sxs-lookup"><span data-stu-id="4c338-115">Describes and provides examples of using updategrams to delete data.</span></span>  
  
 [<span data-ttu-id="4c338-116">使用 XML Updategram 更新資料 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4c338-116">Updating Data Using XML Updategrams &#40;SQLXML 4.0&#41;</span></span>](updating-data-using-xml-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="4c338-117">描述與提供使用 Updategram 修改現有資料的範例。</span><span class="sxs-lookup"><span data-stu-id="4c338-117">Describes and provides examples of using updategrams to modify existing data.</span></span>  
  
 [<span data-ttu-id="4c338-118">將參數傳遞至 Updategram &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4c338-118">Passing Parameters to Updategrams &#40;SQLXML 4.0&#41;</span></span>](passing-parameters-to-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="4c338-119">描述與提供將參數傳遞到 Updategram 的範例。</span><span class="sxs-lookup"><span data-stu-id="4c338-119">Describes and provides examples of passing parameters to updategrams.</span></span>  
  
 [<span data-ttu-id="4c338-120">處理 Updategram 中的資料庫並行問題 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4c338-120">Handling Database Concurrency Issues in Updategrams &#40;SQLXML 4.0&#41;</span></span>](handling-database-concurrency-issues-in-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="4c338-121">描述在 Updategram 中處理並行問題的各種可能保護等級，並提供範例。</span><span class="sxs-lookup"><span data-stu-id="4c338-121">Describes the various levels of protection possible for handling concurrency issues in updategrams, and provides examples.</span></span>  
  
 [<span data-ttu-id="4c338-122">Updategram 範例應用程式 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4c338-122">Updategram Sample Applications &#40;SQLXML 4.0&#41;</span></span>](../../../database-engine/dev-guide/updategram-sample-applications-sqlxml-4-0.md)  
 <span data-ttu-id="4c338-123">提供使用 Updategram 的範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="4c338-123">Provides sample applications that use updategrams.</span></span>  
  
 [<span data-ttu-id="4c338-124">XML Updategram 的指導方針和限制 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4c338-124">Guidelines and Limitations of XML Updategrams &#40;SQLXML 4.0&#41;</span></span>](guidelines-and-limitations-of-xml-updategrams-sqlxml-4-0.md)  
 <span data-ttu-id="4c338-125">列出使用 Updategram 時要注意的事項。</span><span class="sxs-lookup"><span data-stu-id="4c338-125">Lists some things to remember when working with updategrams.</span></span>  
  
  
