---
title: MSSQLSERVER_8966 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8966 (Database Engine error)
ms.assetid: 6b1150fd-9dfd-4df9-8f08-8eca237667db
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8d3a12d5d0732ba8694db3d4c7dcae1eac59d28b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607405"
---
# <a name="mssqlserver_8966"></a><span data-ttu-id="30813-102">MSSQLSERVER_8966</span><span class="sxs-lookup"><span data-stu-id="30813-102">MSSQLSERVER_8966</span></span>
    
## <a name="details"></a><span data-ttu-id="30813-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="30813-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="30813-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="30813-104">Product Name</span></span>|<span data-ttu-id="30813-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="30813-105">SQL Server</span></span>|  
|<span data-ttu-id="30813-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="30813-106">Event ID</span></span>|<span data-ttu-id="30813-107">8966</span><span class="sxs-lookup"><span data-stu-id="30813-107">8966</span></span>|  
|<span data-ttu-id="30813-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="30813-108">Event Source</span></span>|<span data-ttu-id="30813-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="30813-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="30813-110">元件</span><span class="sxs-lookup"><span data-stu-id="30813-110">Component</span></span>|<span data-ttu-id="30813-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="30813-111">SQLEngine</span></span>|  
|<span data-ttu-id="30813-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="30813-112">Symbolic Name</span></span>|<span data-ttu-id="30813-113">DBCC3_FAILED_TO_READ_AND_LATCH_PAGE</span><span class="sxs-lookup"><span data-stu-id="30813-113">DBCC3_FAILED_TO_READ_AND_LATCH_PAGE</span></span>|  
|<span data-ttu-id="30813-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="30813-114">Message Text</span></span>|<span data-ttu-id="30813-115">無法使用閂鎖類型 TYPE 來讀取和閂鎖頁面 P_ID。</span><span class="sxs-lookup"><span data-stu-id="30813-115">Unable to read and latch page P_ID with latch type TYPE.</span></span> <span data-ttu-id="30813-116">作業失敗。</span><span class="sxs-lookup"><span data-stu-id="30813-116">OPERATION failed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="30813-117">說明</span><span class="sxs-lookup"><span data-stu-id="30813-117">Explanation</span></span>  
 <span data-ttu-id="30813-118">頁面讀取失敗或無法針對 PFS 或 GAM 頁面採用閂鎖。</span><span class="sxs-lookup"><span data-stu-id="30813-118">The page read failed or a latch could not be taken on a PFS or GAM page.</span></span> <span data-ttu-id="30813-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔中可能有閂鎖逾時或其他隨附的訊息。</span><span class="sxs-lookup"><span data-stu-id="30813-119">There may be latch time-out or other accompanying messages in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="30813-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="30813-120">User Action</span></span>  
 <span data-ttu-id="30813-121">請檢閱 SQL 錯誤記錄檔，以便找出隨附的訊息並解決這些錯誤。</span><span class="sxs-lookup"><span data-stu-id="30813-121">Review the SQL error log for accompanying messages and resolve these errors.</span></span>  
  
  
