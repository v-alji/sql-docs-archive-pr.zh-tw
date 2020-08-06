---
title: LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: 626b73d3-a257-4b45-82fb-c6299faa0001
author: stevestein
ms.author: sstein
ms.openlocfilehash: b127bedb0dc13c0b8b5a238a8ef104ca9a00bd85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598413"
---
# <a name="localdb_error_cannot_create_instance_folder"></a><span data-ttu-id="c1c29-102">LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="c1c29-102">LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER</span></span>
    
## <a name="details"></a><span data-ttu-id="c1c29-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c1c29-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c1c29-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c1c29-104">Product Name</span></span>|<span data-ttu-id="c1c29-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c1c29-105">SQL Server</span></span>|  
|<span data-ttu-id="c1c29-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c1c29-106">Event ID</span></span>|<span data-ttu-id="c1c29-107">256</span><span class="sxs-lookup"><span data-stu-id="c1c29-107">256</span></span>|  
|<span data-ttu-id="c1c29-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c1c29-108">Event Source</span></span>|<span data-ttu-id="c1c29-109">SQL Server 本機資料庫執行階段 12.0</span><span class="sxs-lookup"><span data-stu-id="c1c29-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="c1c29-110">元件</span><span class="sxs-lookup"><span data-stu-id="c1c29-110">Component</span></span>|<span data-ttu-id="c1c29-111">本機資料庫執行階段 API</span><span class="sxs-lookup"><span data-stu-id="c1c29-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="c1c29-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c1c29-112">Message Text</span></span>|<span data-ttu-id="c1c29-113">無法在下列位置建立本機資料庫實例的資料夾：%% LOCALAPPDATA%% \ Microsoft\Microsoft SQL Server 本機 DB\Instances \\<實例名稱 \> 。</span><span class="sxs-lookup"><span data-stu-id="c1c29-113">Cannot create folder for the Local Database instance at: %%LOCALAPPDATA%%\Microsoft\Microsoft SQL Server Local DB\Instances\\<instance name\>.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c1c29-114">說明</span><span class="sxs-lookup"><span data-stu-id="c1c29-114">Explanation</span></span>  
 <span data-ttu-id="c1c29-115">無法在 %userprofile% 下建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="c1c29-115">A folder cannot be created under %userprofile%.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c1c29-116">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c1c29-116">User Action</span></span>  
  
