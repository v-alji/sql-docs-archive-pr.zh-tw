---
title: MSSQLSERVER_21899 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21899 (Database Engine error)
ms.assetid: 32b87a7c-5380-4638-b147-dd78618f6625
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cb1af04b56685d0e1b5a703b812d08d88909b693
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699649"
---
# <a name="mssqlserver_21899"></a><span data-ttu-id="107fd-102">MSSQLSERVER_21899</span><span class="sxs-lookup"><span data-stu-id="107fd-102">MSSQLSERVER_21899</span></span>
    
## <a name="details"></a><span data-ttu-id="107fd-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="107fd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="107fd-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="107fd-104">Product Name</span></span>|<span data-ttu-id="107fd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="107fd-105">SQL Server</span></span>|  
|<span data-ttu-id="107fd-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="107fd-106">Event ID</span></span>|<span data-ttu-id="107fd-107">21899</span><span class="sxs-lookup"><span data-stu-id="107fd-107">21899</span></span>|  
|<span data-ttu-id="107fd-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="107fd-108">Event Source</span></span>|<span data-ttu-id="107fd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="107fd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="107fd-110">元件</span><span class="sxs-lookup"><span data-stu-id="107fd-110">Component</span></span>|<span data-ttu-id="107fd-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="107fd-111">SQLEngine</span></span>|  
|<span data-ttu-id="107fd-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="107fd-112">Symbolic Name</span></span>|<span data-ttu-id="107fd-113">SQLErrorNum21899</span><span class="sxs-lookup"><span data-stu-id="107fd-113">SQLErrorNum21899</span></span>|  
|<span data-ttu-id="107fd-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="107fd-114">Message Text</span></span>|<span data-ttu-id="107fd-115">在重新導向發行者 '%s' 上進行的查詢，可判斷原始發行者 '%s' 的訂閱者是否有 sysserver 項目失敗，發生錯誤 '%d'，錯誤訊息 '%s'。</span><span class="sxs-lookup"><span data-stu-id="107fd-115">The query at the redirected publisher '%s' to determine whether there were sysserver entries for the subscribers of the original publisher '%s' failed with error '%d', error message '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="107fd-116">說明</span><span class="sxs-lookup"><span data-stu-id="107fd-116">Explanation</span></span>  
 <span data-ttu-id="107fd-117">`sp_validate_redirected_publisher` 會查詢位於遠端伺服器之發行者資料庫的訂閱中繼資料資料表，以便判斷其相關聯的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="107fd-117">`sp_validate_redirected_publisher` queries the subscription metadata tables of the publisher database at the remote server to determine its associated subscribers.</span></span> <span data-ttu-id="107fd-118">如果此查詢失敗，就會傳回錯誤 21899。</span><span class="sxs-lookup"><span data-stu-id="107fd-118">Error 21899 is returned if this query fails.</span></span> <span data-ttu-id="107fd-119">驗證查詢需要存取位於重新導向發行者的已發行資料庫。</span><span class="sxs-lookup"><span data-stu-id="107fd-119">The validation query requires access to the published database at the redirected publisher.</span></span> <span data-ttu-id="107fd-120">如果針對原始發行者呼叫 `sp_adddistpublisher` 時指定的登入未經授權，無法存取位於重新導向發行者的已發行資料庫，就會傳回錯誤 21899。</span><span class="sxs-lookup"><span data-stu-id="107fd-120">If the login specified when `sp_adddistpublisher` is called for the original publisher is not authorized to access the published database at the redirected publisher, error 21899 is returned.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="107fd-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="107fd-121">User Action</span></span>  
 <span data-ttu-id="107fd-122">請檢閱引用的錯誤訊息，以便判斷失敗的原因並且採取適當的更正動作。</span><span class="sxs-lookup"><span data-stu-id="107fd-122">Review the cited error message to determine the cause of the failure and take appropriate corrective action</span></span>  
  
  
