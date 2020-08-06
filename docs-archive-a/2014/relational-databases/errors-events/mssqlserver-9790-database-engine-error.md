---
title: MSSQLSERVER_9790 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d6d065d4a0e841da3b5ecb84f902df17dcfd60c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595035"
---
# <a name="mssqlserver_9790"></a><span data-ttu-id="648a5-102">MSSQLSERVER_9790</span><span class="sxs-lookup"><span data-stu-id="648a5-102">MSSQLSERVER_9790</span></span>
    
## <a name="details"></a><span data-ttu-id="648a5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="648a5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="648a5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="648a5-104">Product Name</span></span>|<span data-ttu-id="648a5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="648a5-105">SQL Server</span></span>|  
|<span data-ttu-id="648a5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="648a5-106">Event ID</span></span>|<span data-ttu-id="648a5-107">9790</span><span class="sxs-lookup"><span data-stu-id="648a5-107">9790</span></span>|  
|<span data-ttu-id="648a5-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="648a5-108">Event Source</span></span>|<span data-ttu-id="648a5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="648a5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="648a5-110">元件</span><span class="sxs-lookup"><span data-stu-id="648a5-110">Component</span></span>|<span data-ttu-id="648a5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="648a5-111">SQLEngine</span></span>|  
|<span data-ttu-id="648a5-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="648a5-112">Symbolic Name</span></span>|<span data-ttu-id="648a5-113">SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER</span><span class="sxs-lookup"><span data-stu-id="648a5-113">SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER</span></span>|  
|<span data-ttu-id="648a5-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="648a5-114">Message Text</span></span>|<span data-ttu-id="648a5-115">無法路由內送訊息。</span><span class="sxs-lookup"><span data-stu-id="648a5-115">Unable to route the incoming message.</span></span> <span data-ttu-id="648a5-116">包含路由資訊的系統資料庫 MSDB 正處於單一使用者 (SINGLE USER) 模式。</span><span class="sxs-lookup"><span data-stu-id="648a5-116">The system database MSDB containing routing information is in SINGLE USER mode.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="648a5-117">說明</span><span class="sxs-lookup"><span data-stu-id="648a5-117">Explanation</span></span>  
 <span data-ttu-id="648a5-118">嘗試分類離線接收的訊息時發生錯誤，因為 MSDB 資料庫處於單一使用者模式中。</span><span class="sxs-lookup"><span data-stu-id="648a5-118">An error occurred while trying to classify a message received off the wire because the MSDB database was in Single User mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="648a5-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="648a5-119">User Action</span></span>  
 <span data-ttu-id="648a5-120">使用 ALTER DATABASE 命令，將 MSDB 變更為 MULTI USER 模式。</span><span class="sxs-lookup"><span data-stu-id="648a5-120">Change MSDB to be in MULTI USER mode with the ALTER DATABASE command.</span></span>  
  
  
