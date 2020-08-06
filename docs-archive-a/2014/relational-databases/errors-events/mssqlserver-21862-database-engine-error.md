---
title: MSSQLSERVER_21862 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21862 (Database Engine error)
ms.assetid: a1d393dd-453b-4d45-9aa5-7d371213e32b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b945350d9c7a862d4274f464afbd7fc5472f732c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699670"
---
# <a name="mssqlserver_21862"></a><span data-ttu-id="c0966-102">MSSQLSERVER_21862</span><span class="sxs-lookup"><span data-stu-id="c0966-102">MSSQLSERVER_21862</span></span>
    
## <a name="details"></a><span data-ttu-id="c0966-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c0966-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c0966-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c0966-104">Product Name</span></span>|<span data-ttu-id="c0966-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c0966-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c0966-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c0966-106">Event ID</span></span>|<span data-ttu-id="c0966-107">21862</span><span class="sxs-lookup"><span data-stu-id="c0966-107">21862</span></span>|  
|<span data-ttu-id="c0966-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c0966-108">Event Source</span></span>|<span data-ttu-id="c0966-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c0966-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c0966-110">元件</span><span class="sxs-lookup"><span data-stu-id="c0966-110">Component</span></span>|<span data-ttu-id="c0966-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c0966-111">SQLEngine</span></span>|  
|<span data-ttu-id="c0966-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c0966-112">Symbolic Name</span></span>|<span data-ttu-id="c0966-113">SQLErrorNum21862</span><span class="sxs-lookup"><span data-stu-id="c0966-113">SQLErrorNum21862</span></span>|  
|<span data-ttu-id="c0966-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c0966-114">Message Text</span></span>|<span data-ttu-id="c0966-115">在使用 'database snapshot' 或 'database snapshot character' 同步處理方法的發行集內，無法發行檔案資料流資料行。</span><span class="sxs-lookup"><span data-stu-id="c0966-115">FILESTREAM columns cannot be published in a publication by using a synchronization method of either 'database snapshot' or 'database snapshot character'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c0966-116">說明</span><span class="sxs-lookup"><span data-stu-id="c0966-116">Explanation</span></span>  
 <span data-ttu-id="c0966-117">由於無法透過資料庫快照集來存取 FILESTREAM 資料，因此當針對發行集的同步處理方法指定了 *database snapshot* 或 *database_snapshot_character* 參數時，快照集代理程式將無法讀取 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="c0966-117">Because FILESTREAM data cannot be accessed through a database snapshot, the snapshot agent will be unable to read FILESTREAM data when either the *database snapshot* or *database_snapshot_character* parameter is specified for the synchronization method of the publication.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c0966-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c0966-118">User Action</span></span>  
 <span data-ttu-id="c0966-119">將發行集同步處理方法變更為 *database snapshot* 或 *database_snapshot_character* 以外的項目，或是從發行集中排除 FILESTREAM 資料行。</span><span class="sxs-lookup"><span data-stu-id="c0966-119">Change the publication synchronization method to something other than *database snapshot* or *database_snapshot_character*, or just exclude the FILESTREAM column from the publication.</span></span>  
  
  
