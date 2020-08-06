---
title: MSSQLSERVER_21898 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21898 (Database Engine error)
ms.assetid: 02405b21-3d4e-4c2d-b4b3-d7b1ec05edb4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 78ce7eacf7f026bf9977af2c367b954a3639b357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699655"
---
# <a name="mssqlserver_21898"></a><span data-ttu-id="ead64-102">MSSQLSERVER_21898</span><span class="sxs-lookup"><span data-stu-id="ead64-102">MSSQLSERVER_21898</span></span>
    
## <a name="details"></a><span data-ttu-id="ead64-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ead64-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ead64-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ead64-104">Product Name</span></span>|<span data-ttu-id="ead64-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ead64-105">SQL Server</span></span>|  
|<span data-ttu-id="ead64-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ead64-106">Event ID</span></span>|<span data-ttu-id="ead64-107">21898</span><span class="sxs-lookup"><span data-stu-id="ead64-107">21898</span></span>|  
|<span data-ttu-id="ead64-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="ead64-108">Event Source</span></span>|<span data-ttu-id="ead64-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ead64-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ead64-110">元件</span><span class="sxs-lookup"><span data-stu-id="ead64-110">Component</span></span>|<span data-ttu-id="ead64-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ead64-111">SQLEngine</span></span>|  
|<span data-ttu-id="ead64-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ead64-112">Symbolic Name</span></span>|<span data-ttu-id="ead64-113">SQLErrorNum21898</span><span class="sxs-lookup"><span data-stu-id="ead64-113">SQLErrorNum21898</span></span>|  
|<span data-ttu-id="ead64-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ead64-114">Message Text</span></span>|<span data-ttu-id="ead64-115">發行者 '%s' 使用散發資料庫 '%s' 而不是 '%s'，但若要主控發行資料庫 '%s' 必須使用後者。</span><span class="sxs-lookup"><span data-stu-id="ead64-115">The publisher '%s' uses distribution database '%s' and not '%s' which is required in order to host the publishing database '%s'.</span></span> <span data-ttu-id="ead64-116">請在散發者 '%s' 上執行 `sp_changedistpublisher` 以便將發行者所使用的散發資料庫變更為 '%s'。</span><span class="sxs-lookup"><span data-stu-id="ead64-116">Run `sp_changedistpublisher` at distributor '%s' to change the distribution database used by the publisher to '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ead64-117">說明</span><span class="sxs-lookup"><span data-stu-id="ead64-117">Explanation</span></span>  
 <span data-ttu-id="ead64-118">`sp_validate_redirected_publisher` 會查詢位於本機散發者的 msdb.dbo.MSdistpublishers，以便確認新發行者所使用的散發資料庫是否與原始發行者所使用的散發資料庫相同。</span><span class="sxs-lookup"><span data-stu-id="ead64-118">`sp_validate_redirected_publisher` queries msdb.dbo.MSdistpublishers at the local distributor to verify that the distribution database used by the new publisher is the same as the distribution database used by the original publisher.</span></span> <span data-ttu-id="ead64-119">當這些資料庫不同時，就會傳回此錯誤，讓發行者不適合當做發行者資料庫的主機。</span><span class="sxs-lookup"><span data-stu-id="ead64-119">This error is returned when these databases are different, making the publisher an unsuitable host for the publisher database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ead64-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ead64-120">User Action</span></span>  
 <span data-ttu-id="ead64-121">請執行 `sp_changedistpublisher` 預存程序，將新發行者的散發資料庫變更為原始發行者所使用的散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="ead64-121">Execute stored procedure `sp_changedistpublisher` to change the distribution database for the new publisher to that used by the original publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ead64-122">如果在發行者的散發者端執行 `sp_changedistpublisher` 時輸入了錯誤的散發資料庫，執行 `sp_adddistpublisher` 便可解決問題。</span><span class="sxs-lookup"><span data-stu-id="ead64-122">Running `sp_changedistpublisher` will address the problem if the wrong distribution database was entered when `sp_adddistpublisher` was run at the distributor for the publisher.</span></span> <span data-ttu-id="ead64-123">不過，如果遠端發行者的現有發行集來自使用已識別散發資料庫的另一個發行資料庫，這項變更則不適用。</span><span class="sxs-lookup"><span data-stu-id="ead64-123">However, if the remote publisher has existing publications from another publishing database that make use of the identified distribution database, this change is not appropriate.</span></span> <span data-ttu-id="ead64-124">您必須有系統地移除使用具名散發資料庫的複寫，然後使用原始發行者的散發資料庫來重新建立複寫，才能讓新的發行者當作適合的主機。</span><span class="sxs-lookup"><span data-stu-id="ead64-124">Replication using the named distribution database needs to be systematically removed and then reestablished using the original publisher's distribution database in order for the new publisher to function as a suitable host.</span></span>  
  
  
