---
title: MSSQLSERVER_12304 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 12304 (Database Engine error)
ms.assetid: a2c252c2-e815-4ac8-a101-7af5b32e3233
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2347fc46fe5ab83ef2ff46b81500cd737ed02d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597161"
---
# <a name="mssqlserver_12304"></a><span data-ttu-id="fbbc7-102">MSSQLSERVER_12304</span><span class="sxs-lookup"><span data-stu-id="fbbc7-102">MSSQLSERVER_12304</span></span>
    
## <a name="details"></a><span data-ttu-id="fbbc7-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fbbc7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fbbc7-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="fbbc7-104">Product Name</span></span>|<span data-ttu-id="fbbc7-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="fbbc7-105">SQL Server</span></span>|  
|<span data-ttu-id="fbbc7-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fbbc7-106">Event ID</span></span>|<span data-ttu-id="fbbc7-107">12304</span><span class="sxs-lookup"><span data-stu-id="fbbc7-107">12304</span></span>|  
|<span data-ttu-id="fbbc7-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="fbbc7-108">Event Source</span></span>|<span data-ttu-id="fbbc7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="fbbc7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="fbbc7-110">元件</span><span class="sxs-lookup"><span data-stu-id="fbbc7-110">Component</span></span>|<span data-ttu-id="fbbc7-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="fbbc7-111">SQLEngine</span></span>|  
|<span data-ttu-id="fbbc7-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="fbbc7-112">Symbolic Name</span></span>|<span data-ttu-id="fbbc7-113">HK_UNSUPPORTED_IDENTITY_TABLE_VAR</span><span class="sxs-lookup"><span data-stu-id="fbbc7-113">HK_UNSUPPORTED_IDENTITY_TABLE_VAR</span></span>|  
|<span data-ttu-id="fbbc7-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="fbbc7-114">Message Text</span></span>|<span data-ttu-id="fbbc7-115">在原生編譯預存程序的內容之外使用記憶體最佳化資料表類型時，不支援該類型與其任何資料行搭配使用 IDENTITY 屬性。</span><span class="sxs-lookup"><span data-stu-id="fbbc7-115">Using a memory optimized table type that uses the IDENTITY property with any of its columns is not supported when using the type outside the context of a natively compiled stored procedure.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="fbbc7-116">使用者動作</span><span class="sxs-lookup"><span data-stu-id="fbbc7-116">User Action</span></span>  
 <span data-ttu-id="fbbc7-117">請勿使用將識別屬性與其任何資料行搭配使用的記憶體最佳化資料表類型。</span><span class="sxs-lookup"><span data-stu-id="fbbc7-117">Do not use a memory-optimized table type that uses the identity property with any of its columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbbc7-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbbc7-118">See Also</span></span>  
 [<span data-ttu-id="fbbc7-119">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="fbbc7-119">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
