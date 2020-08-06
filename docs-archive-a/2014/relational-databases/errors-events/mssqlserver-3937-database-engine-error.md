---
title: MSSQLSERVER_3937 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3937 (Database Engine error)
ms.assetid: 312d5bbe-c8de-42db-af4b-4ccb448ce6ef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cac466e6eb50ad4b7a8848a1159963cb0fd35e22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699628"
---
# <a name="mssqlserver_3937"></a><span data-ttu-id="1b330-102">MSSQLSERVER_3937</span><span class="sxs-lookup"><span data-stu-id="1b330-102">MSSQLSERVER_3937</span></span>
    
## <a name="details"></a><span data-ttu-id="1b330-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1b330-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1b330-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1b330-104">Product Name</span></span>|<span data-ttu-id="1b330-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1b330-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1b330-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1b330-106">Event ID</span></span>|<span data-ttu-id="1b330-107">3937</span><span class="sxs-lookup"><span data-stu-id="1b330-107">3937</span></span>|  
|<span data-ttu-id="1b330-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="1b330-108">Event Source</span></span>|<span data-ttu-id="1b330-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1b330-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1b330-110">元件</span><span class="sxs-lookup"><span data-stu-id="1b330-110">Component</span></span>|<span data-ttu-id="1b330-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1b330-111">SQLEngine</span></span>|  
|<span data-ttu-id="1b330-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1b330-112">Symbolic Name</span></span>|<span data-ttu-id="1b330-113">XACT_FILESTREAM_ROLLBACK_ERROR</span><span class="sxs-lookup"><span data-stu-id="1b330-113">XACT_FILESTREAM_ROLLBACK_ERROR</span></span>|  
|<span data-ttu-id="1b330-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1b330-114">Message Text</span></span>|<span data-ttu-id="1b330-115">嘗試通知檔案資料流篩選驅動程式已回復交易時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1b330-115">An error occurred while trying to notify the FILESTREAM filter driver that a transaction was rolled back.</span></span> <span data-ttu-id="1b330-116">錯誤碼：0x%0x。</span><span class="sxs-lookup"><span data-stu-id="1b330-116">Error code: 0x%0x.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1b330-117">說明</span><span class="sxs-lookup"><span data-stu-id="1b330-117">Explanation</span></span>  
 <span data-ttu-id="1b330-118">當發出交易的回復通知時，RsFx 驅動程式傳回了錯誤。</span><span class="sxs-lookup"><span data-stu-id="1b330-118">An error was returned by the RsFx driver when issuing a rollback notification for a transaction.</span></span> <span data-ttu-id="1b330-119">這可能是因為資源短缺所造成。</span><span class="sxs-lookup"><span data-stu-id="1b330-119">This is probably caused by a resource shortage.</span></span> <span data-ttu-id="1b330-120">這會造成 RsFx 篩選驅動程式內的小型記憶體遺漏，但是當建立交易的 sqlservr.exe 處理序結束時，將會釋出這些記憶體。</span><span class="sxs-lookup"><span data-stu-id="1b330-120">This can cause a small memory leak in the RsFx filter driver, but this will be freed when the sqlservr.exe process that created the transaction exits.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1b330-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1b330-121">User Action</span></span>  
  
