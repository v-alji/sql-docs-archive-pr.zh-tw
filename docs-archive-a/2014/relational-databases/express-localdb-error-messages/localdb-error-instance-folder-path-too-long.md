---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 32ae8ebe102008d08a6059328ed57cd118ece019
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606333"
---
# <a name="localdb_error_instance_folder_path_too_long"></a><span data-ttu-id="00622-102">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="00622-102">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>
    
## <a name="details"></a><span data-ttu-id="00622-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="00622-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="00622-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="00622-104">Product Name</span></span>|<span data-ttu-id="00622-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="00622-105">SQL Server</span></span>|  
|<span data-ttu-id="00622-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="00622-106">Event ID</span></span>|<span data-ttu-id="00622-107">260</span><span class="sxs-lookup"><span data-stu-id="00622-107">260</span></span>|  
|<span data-ttu-id="00622-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="00622-108">Event Source</span></span>|<span data-ttu-id="00622-109">SQL Server 本機資料庫執行階段 12.0</span><span class="sxs-lookup"><span data-stu-id="00622-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="00622-110">元件</span><span class="sxs-lookup"><span data-stu-id="00622-110">Component</span></span>|<span data-ttu-id="00622-111">本機資料庫執行階段 API</span><span class="sxs-lookup"><span data-stu-id="00622-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="00622-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="00622-112">Message Text</span></span>|<span data-ttu-id="00622-113">本機資料庫執行個體資料夾的完整路徑長度比 MAX_PATH 還長。</span><span class="sxs-lookup"><span data-stu-id="00622-113">The full path length of the Local Database instance folder is longer than MAX_PATH.</span></span> <span data-ttu-id="00622-114">實例必須儲存在資料夾：%% LOCALAPPDATA%% \ Microsoft\Microsoft SQL Server 本機 DB\Instances \\<實例名稱 \> 。</span><span class="sxs-lookup"><span data-stu-id="00622-114">The instance must be stored in folder: %%LOCALAPPDATA%%\Microsoft\Microsoft SQL Server Local DB\Instances\\<instance name\>.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="00622-115">說明</span><span class="sxs-lookup"><span data-stu-id="00622-115">Explanation</span></span>  
 <span data-ttu-id="00622-116">應儲存執行個體的路徑長度超過 MAX_PATH。</span><span class="sxs-lookup"><span data-stu-id="00622-116">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="00622-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="00622-117">User Action</span></span>  
 <span data-ttu-id="00622-118">請建立長度短於 MAX_PATH 的新路徑。</span><span class="sxs-lookup"><span data-stu-id="00622-118">Create a new path that is shorter than MAX_PATH.</span></span>  
  
  
