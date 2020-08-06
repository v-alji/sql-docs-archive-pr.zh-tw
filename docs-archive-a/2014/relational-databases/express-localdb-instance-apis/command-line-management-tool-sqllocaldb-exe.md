---
title: 命令列管理工具： SqlLocalDB.exe |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_location:
- sqluserinstance.dll
ms.assetid: dd0882b1-a8a9-447a-8bdf-0f9d7f36d336
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d21a6a8879e981e52bd2e7d3bd05a37e65d8cf4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592029"
---
# <a name="command-line-management-tool-sqllocaldbexe"></a><span data-ttu-id="3a3d8-102">命令列管理工具：SqlLocalDB.exe</span><span class="sxs-lookup"><span data-stu-id="3a3d8-102">Command-Line Management Tool: SqlLocalDB.exe</span></span>
  <span data-ttu-id="3a3d8-103">SqlLocalDB.exe 是可讓使用者從命令列輕鬆管理 LocalDB 執行個體的簡單工具。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-103">SqlLocalDB.exe is a simple tool that enables the user to easily manage LocalDB instances from the command line.</span></span> <span data-ttu-id="3a3d8-104">它會實作為 LocalDB 執行個體 API 外圍的簡單包裝函式。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-104">It is implemented as a simple wrapper around the LocalDB instance API.</span></span> <span data-ttu-id="3a3d8-105">就像在許多類似的 SQL Server 工具 (例如 SQLCMD) 中一樣，參數會當做命令列引數傳遞給 SqlLocalDB，並且將輸出傳送到主控台。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-105">As in many similar SQL Server tools (for example, SQLCMD), parameters are passed to SqlLocalDB as command-line arguments and output is sent to the console.</span></span>  
  
 <span data-ttu-id="3a3d8-106">SqlLocalDB 可讓開發人員使用 LocalDB，而不需要撰寫呼叫 API 的程式碼，或依賴其他工具來完成作業。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-106">SqlLocalDB enables developers to use LocalDB without having to write code to call the API or depend on other tools to do it for them.</span></span>  
  
## <a name="sqllocaldb-options"></a><span data-ttu-id="3a3d8-107">SqlLocalDB 選項</span><span class="sxs-lookup"><span data-stu-id="3a3d8-107">SqlLocalDB Options</span></span>  
 <span data-ttu-id="3a3d8-108">SqlLocalDB 支援下列選項。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-108">SqlLocalDB supports the following options.</span></span>  
  
|<span data-ttu-id="3a3d8-109">選項</span><span class="sxs-lookup"><span data-stu-id="3a3d8-109">Option</span></span>|<span data-ttu-id="3a3d8-110">作用</span><span class="sxs-lookup"><span data-stu-id="3a3d8-110">What it does</span></span>|  
|------------|------------------|  
|`-?`|<span data-ttu-id="3a3d8-111">列印說明文字。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-111">Prints help text.</span></span>|  
|`create&#124;c "instance name" [version-number] [-s]`|<span data-ttu-id="3a3d8-112">以指定的名稱和版本建立新的 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-112">Creates a new LocalDB instance with a specified name and version.</span></span><br /><br /> <span data-ttu-id="3a3d8-113">如果省略 [version-number] 參數，預設為 SqlLocalDB 組建版本。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-113">If the [version-number] parameter is omitted, it defaults to the SqlLocalDB build version.</span></span><br /><br /> <span data-ttu-id="3a3d8-114">-s 會啟動新建立的 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-114">-s starts the new LocalDB instance after it is created.</span></span>|  
|`delete&#124;d "instance name"`|<span data-ttu-id="3a3d8-115">刪除具有指定之名稱的 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-115">Deletes the LocalDB instance with the specified name.</span></span>|  
|`start&#124;s "instance name"`|<span data-ttu-id="3a3d8-116">啟動具有指定之名稱的 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-116">Starts the LocalDB instance with the specified name.</span></span>|  
|`stop&#124;p "instance name" [-i&#124;-k]`|<span data-ttu-id="3a3d8-117">在目前查詢完成執行之後，停止具有指定之名稱的 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-117">Stops the LocalDB instance with the specified name, after current queries finish running.</span></span><br /><br /> <span data-ttu-id="3a3d8-118">-i 會使用 NOWAIT 選項要求關閉 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-118">-i requests the LocalDB instance shutdown with the NOWAIT option.</span></span><br /><br /> <span data-ttu-id="3a3d8-119">-k 會在未經連絡的情況下終止 LocalDB 執行個體處理序。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-119">-k kills the LocalDB instance process without contacting it.</span></span>|  
|`share&#124;h ["owner SID or account"] "private name" "shared name"`|<span data-ttu-id="3a3d8-120">使用指定的共用名稱來共用指定的私用執行個體。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-120">Shares the specified private instance using the specified shared name.</span></span> <span data-ttu-id="3a3d8-121">如果省略使用者 SID 或帳戶名稱，會預設為目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-121">If the user SID or account name is omitted, it defaults to the current user.</span></span>|  
|`unshare&#124;u "shared name"`|<span data-ttu-id="3a3d8-122">取消共用指定的共用 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-122">Unshares the specified shared LocalDB instance.</span></span>|  
|`info&#124;i`|<span data-ttu-id="3a3d8-123">列出目前使用者擁有之所有現有的 LocalDB 執行個體，以及所有共用的 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-123">Lists all existing LocalDB instances that are owned by the current user and all shared LocalDB instances.</span></span>|  
|`info&#124;i "instance name"`|<span data-ttu-id="3a3d8-124">列印指定之 LocalDB 執行個體的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-124">Prints the information about the specified LocalDB instance.</span></span>|  
|`versions&#124;v`|<span data-ttu-id="3a3d8-125">列出電腦上安裝的所有 LocalDB 版本。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-125">Lists all LocalDB versions installed on the computer.</span></span>|  
|||  
|`trace&#124;t on&#124;off`|<span data-ttu-id="3a3d8-126">開啟及關閉追蹤。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-126">Turns tracing on and off.</span></span>|  
  
 <span data-ttu-id="3a3d8-127">SqlLocalDB 會將空格視為分隔符號；你必須使用引號括住包含空格和特殊字元的執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="3a3d8-127">SqlLocalDB treats spaces as delimiters; you must surround the instance names that contain spaces and special characters with quotes.</span></span> <span data-ttu-id="3a3d8-128">例如：</span><span class="sxs-lookup"><span data-stu-id="3a3d8-128">For example:</span></span>  
  
 `SqlLocalDB create "My instance name with spaces"`  
  
  
