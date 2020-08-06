---
title: MSSQLSERVER_7308 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7308 (Database Engine error)
- single-threaded apartment mode
ms.assetid: cca9eab9-afb9-463d-abfd-0802257e2c99
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9978f35ebe41eeda1470220772f87e83ab1ad942
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596018"
---
# <a name="mssqlserver_7308"></a><span data-ttu-id="80e36-102">MSSQLSERVER_7308</span><span class="sxs-lookup"><span data-stu-id="80e36-102">MSSQLSERVER_7308</span></span>
    
## <a name="details"></a><span data-ttu-id="80e36-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="80e36-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="80e36-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="80e36-104">Product Name</span></span>|<span data-ttu-id="80e36-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="80e36-105">SQL Server</span></span>|  
|<span data-ttu-id="80e36-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="80e36-106">Event ID</span></span>|<span data-ttu-id="80e36-107">7308</span><span class="sxs-lookup"><span data-stu-id="80e36-107">7308</span></span>|  
|<span data-ttu-id="80e36-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="80e36-108">Event Source</span></span>|<span data-ttu-id="80e36-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="80e36-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="80e36-110">元件</span><span class="sxs-lookup"><span data-stu-id="80e36-110">Component</span></span>|<span data-ttu-id="80e36-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="80e36-111">SQLEngine</span></span>|  
|<span data-ttu-id="80e36-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="80e36-112">Symbolic Name</span></span>|<span data-ttu-id="80e36-113">RMT_STA_DISABLED</span><span class="sxs-lookup"><span data-stu-id="80e36-113">RMT_STA_DISABLED</span></span>|  
|<span data-ttu-id="80e36-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="80e36-114">Message Text</span></span>|<span data-ttu-id="80e36-115">OLE DB 提供者 '%ls' 不能用來散佈查詢，因為提供者是設定成以單一執行緒 Apartment 模式執行。</span><span class="sxs-lookup"><span data-stu-id="80e36-115">OLE DB provider '%ls' cannot be used for distributed queries because the provider is configured to run in single-threaded apartment mode.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="80e36-116">說明</span><span class="sxs-lookup"><span data-stu-id="80e36-116">Explanation</span></span>  
 <span data-ttu-id="80e36-117">您已經使用設定成以單一執行緒 Apartment (STA) 模式執行的 OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="80e36-117">You have used an OLE DB provider that is configured to run in single-threaded apartment (STA) mode.</span></span> <span data-ttu-id="80e36-118">以單一執行緒 Apartment (STA) 模式執行的 OLE DB 提供者無法用於分散式查詢。</span><span class="sxs-lookup"><span data-stu-id="80e36-118">OLE DB providers that run in single-threaded apartment (STA) mode cannot be used for distributed queries.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="80e36-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="80e36-119">User Action</span></span>  
 <span data-ttu-id="80e36-120">若要解決這個錯誤，請將提供者設定成以多執行緒 Apartment (MTA) 模式執行。</span><span class="sxs-lookup"><span data-stu-id="80e36-120">To resolve this error, configure the provider to run in multithreaded apartment (MTA) mode.</span></span> <span data-ttu-id="80e36-121">如果此提供者不支援 MTA，而且此提供者無法升級為支援 MTA 的版本，請考慮將此提供者設定為跨處理序執行。</span><span class="sxs-lookup"><span data-stu-id="80e36-121">If the provider does not support MTA, and the provider cannot be upgraded to a version that supports MTA, consider configuring the provider to run out-of-process.</span></span> <span data-ttu-id="80e36-122">提供者供應商應該能夠告訴您此提供者是否支援 MTA 或跨處理序執行。</span><span class="sxs-lookup"><span data-stu-id="80e36-122">The provider vendor should be able to tell you if the provider supports MTA or running out-of-process.</span></span>  
  
  
