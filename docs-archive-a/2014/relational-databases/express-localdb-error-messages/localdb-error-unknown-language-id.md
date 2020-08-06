---
title: LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: fa082dca-bf88-46e7-b61e-7ac8835a3493
author: stevestein
ms.author: sstein
ms.openlocfilehash: e71f7b443a1999a5edbb17dc11ee4d578834faf4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597128"
---
# <a name="localdb_error_unknown_language_id"></a><span data-ttu-id="ee207-102">LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID</span><span class="sxs-lookup"><span data-stu-id="ee207-102">LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID</span></span>
    
## <a name="details"></a><span data-ttu-id="ee207-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ee207-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ee207-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ee207-104">Product Name</span></span>|<span data-ttu-id="ee207-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ee207-105">SQL Server</span></span>|  
|<span data-ttu-id="ee207-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ee207-106">Event ID</span></span>|<span data-ttu-id="ee207-107">270</span><span class="sxs-lookup"><span data-stu-id="ee207-107">270</span></span>|  
|<span data-ttu-id="ee207-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="ee207-108">Event Source</span></span>|<span data-ttu-id="ee207-109">SQL Server 本機資料庫執行階段 12.0</span><span class="sxs-lookup"><span data-stu-id="ee207-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="ee207-110">元件</span><span class="sxs-lookup"><span data-stu-id="ee207-110">Component</span></span>|<span data-ttu-id="ee207-111">本機資料庫執行階段 API</span><span class="sxs-lookup"><span data-stu-id="ee207-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="ee207-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ee207-112">Message Text</span></span>|<span data-ttu-id="ee207-113">取得當地語系化的錯誤訊息時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ee207-113">Error getting the localized error message.</span></span> <span data-ttu-id="ee207-114">'Language ID' 參數所指定的語言是未知的。</span><span class="sxs-lookup"><span data-stu-id="ee207-114">The language specified by 'Language ID' parameter is unknown.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ee207-115">說明</span><span class="sxs-lookup"><span data-stu-id="ee207-115">Explanation</span></span>  
 <span data-ttu-id="ee207-116">本機資料庫執行階段錯誤訊息的要求語言是未知的或不受支援。</span><span class="sxs-lookup"><span data-stu-id="ee207-116">The requested language for the Local Database Runtime error message is unknown or not supported.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ee207-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ee207-117">User Action</span></span>  
 <span data-ttu-id="ee207-118">請嘗試要求本機資料庫執行階段錯誤訊息的其中一種支援語言或預設語言。</span><span class="sxs-lookup"><span data-stu-id="ee207-118">Try requesting one of the supported languages for Local Database Runtime error messages, or a default language.</span></span>  
  
  
