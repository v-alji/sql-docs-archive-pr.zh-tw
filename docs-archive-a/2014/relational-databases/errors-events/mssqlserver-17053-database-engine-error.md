---
title: MSSQLSERVER_17053 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17053 (Database Engine error)
ms.assetid: e0a01f3d-d0aa-4c38-8bcc-82e59de50512
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 11137ba334b66f20c7d9a6caaaf7d1ef42c15dec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584549"
---
# <a name="mssqlserver_17053"></a><span data-ttu-id="be9a3-102">MSSQLSERVER_17053</span><span class="sxs-lookup"><span data-stu-id="be9a3-102">MSSQLSERVER_17053</span></span>
    
## <a name="details"></a><span data-ttu-id="be9a3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="be9a3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="be9a3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="be9a3-104">Product Name</span></span>|<span data-ttu-id="be9a3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="be9a3-105">SQL Server</span></span>|  
|<span data-ttu-id="be9a3-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="be9a3-106">Event ID</span></span>|<span data-ttu-id="be9a3-107">17053</span><span class="sxs-lookup"><span data-stu-id="be9a3-107">17053</span></span>|  
|<span data-ttu-id="be9a3-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="be9a3-108">Event Source</span></span>|<span data-ttu-id="be9a3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="be9a3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="be9a3-110">元件</span><span class="sxs-lookup"><span data-stu-id="be9a3-110">Component</span></span>|<span data-ttu-id="be9a3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="be9a3-111">SQLEngine</span></span>|  
|<span data-ttu-id="be9a3-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="be9a3-112">Symbolic Name</span></span>|<span data-ttu-id="be9a3-113">OS_ERROR</span><span class="sxs-lookup"><span data-stu-id="be9a3-113">OS_ERROR</span></span>|  
|<span data-ttu-id="be9a3-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="be9a3-114">Message Text</span></span>|<span data-ttu-id="be9a3-115">%ls:發現作業系統錯誤 %ls。</span><span class="sxs-lookup"><span data-stu-id="be9a3-115">%ls: Operating system error %ls encountered.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="be9a3-116">說明</span><span class="sxs-lookup"><span data-stu-id="be9a3-116">Explanation</span></span>  
 <span data-ttu-id="be9a3-117">發生一般作業系統錯誤。</span><span class="sxs-lookup"><span data-stu-id="be9a3-117">Generic operating system error occurred.</span></span>  <span data-ttu-id="be9a3-118">不確定產生的狀態為何。</span><span class="sxs-lookup"><span data-stu-id="be9a3-118">Not clear what the resulting state is.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="be9a3-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="be9a3-119">User Action</span></span>  
 <span data-ttu-id="be9a3-120">通常這項錯誤會與某些其他錯誤一起出現，而且應該可用來協助診斷該項失敗。</span><span class="sxs-lookup"><span data-stu-id="be9a3-120">Usually this is in conjunction with some other error and should be used to help diagnose that failure.</span></span> <span data-ttu-id="be9a3-121">範例包括讀取或寫入失敗的資料或記錄檔、登錄讀取/寫入作業，或其他無法預期的 Win32API 失敗。</span><span class="sxs-lookup"><span data-stu-id="be9a3-121">Examples would include reads or writes to data or log files that fail, registry read/write operations, or other unexpected Win32API failures.</span></span>  
  
  
