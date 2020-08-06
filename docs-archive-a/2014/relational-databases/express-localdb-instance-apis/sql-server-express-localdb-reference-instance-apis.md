---
title: SQL Server Express LocalDB 實例 API 參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: faec46da-0536-4de3-96f3-83e607c8a8b6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5934bc5159998db22d7c560b31457524773e74eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686931"
---
# <a name="sql-server-express-localdb-instance-api-reference"></a><span data-ttu-id="9804b-102">SQL Server Express LocalDB 執行個體 API 參考</span><span class="sxs-lookup"><span data-stu-id="9804b-102">SQL Server Express LocalDB Instance API Reference</span></span>
  <span data-ttu-id="9804b-103">在傳統、服務架構的 SQL Server 環境中，安裝在單一電腦上的個別 SQL Server 執行個體實體上是分隔的；亦即，每個執行個體必須個別予以安裝及移除、具有獨立的一組二進位檔，以及在個別的服務處理序下執行。</span><span class="sxs-lookup"><span data-stu-id="9804b-103">In the traditional, service-based SQL Server world, individual SQL Server instances installed on a single computer are physically separated; that is, each instance must be installed and removed separately, has a separate set of binaries, and runs under a separate service process.</span></span> <span data-ttu-id="9804b-104">SQL Server 執行個體名稱可用來指定使用者想要連接的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9804b-104">The SQL Server instance name is used to specify which SQL Server instance the user wants to connect to.</span></span>  
  
 <span data-ttu-id="9804b-105">SQL Server Express LocalDB 實例 API 會使用簡化的「輕」實例模型。</span><span class="sxs-lookup"><span data-stu-id="9804b-105">The SQL Server Express LocalDB instance API uses a simplified, "light" instance model.</span></span> <span data-ttu-id="9804b-106">雖然個別 LocalDB 執行個體會在不同的磁碟和登錄中，但是會使用同一組共用的 LocalDB 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="9804b-106">Although individual LocalDB instances are separated on the disk and in the registry, they use the same set of shared LocalDB binaries.</span></span> <span data-ttu-id="9804b-107">此外，LocalDB 不會使用服務；LocalDB 執行個體會視需要透過 LocalDB 執行個體 API 呼叫來啟動。</span><span class="sxs-lookup"><span data-stu-id="9804b-107">Moreover, LocalDB does not use services; LocalDB instances are launched on demand through LocalDB instance API calls.</span></span> <span data-ttu-id="9804b-108">在 LocalDB 中，執行個體名稱可用來指定使用者想要使用的 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9804b-108">In LocalDB, the instance name is used to specify which of the LocalDB instances the user wants to work with.</span></span>  
  
 <span data-ttu-id="9804b-109">LocalDB 實例一律是由單一使用者所擁有，而且只有在已啟用實例共用的情況下，才可見且只能從這個使用者的內容存取。</span><span class="sxs-lookup"><span data-stu-id="9804b-109">A LocalDB instance is always owned by a single user and is visible and accessible only from this user's context, unless instance sharing is enabled.</span></span>  
  
 <span data-ttu-id="9804b-110">雖然 LocalDB 執行個體在技術上與傳統的 SQL Server 執行個體不同，但是其用途很類似。</span><span class="sxs-lookup"><span data-stu-id="9804b-110">Although technically LocalDB instances are not the same as traditional SQL Server instances, their intended use is similar.</span></span> <span data-ttu-id="9804b-111">它們稱為「*實例*」，以強調此相似性，讓 SQL Server 使用者更直覺化。</span><span class="sxs-lookup"><span data-stu-id="9804b-111">They are called *instances* to emphasize this similarity and to make them more intuitive to SQL Server users.</span></span>  
  
 <span data-ttu-id="9804b-112">LocalDB 支援兩種執行個體：自動執行個體 (AI) 和具名執行個體 (NI)。</span><span class="sxs-lookup"><span data-stu-id="9804b-112">LocalDB supports two kinds of instances: automatic instances (AI) and named instances (NI).</span></span> <span data-ttu-id="9804b-113">LocalDB 執行個體的識別碼是執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="9804b-113">The identifier for a LocalDB instance is the instance name.</span></span>  
  
## <a name="automatic-localdb-instances"></a><span data-ttu-id="9804b-114">自動 LocalDB 執行個體</span><span class="sxs-lookup"><span data-stu-id="9804b-114">Automatic LocalDB Instances</span></span>  
 <span data-ttu-id="9804b-115">自動 LocalDB 實例為「公用」;系統會為使用者自動建立和管理它們，並可供任何應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="9804b-115">Automatic LocalDB instances are "public"; they are created and managed automatically for the user and can be used by any application.</span></span> <span data-ttu-id="9804b-116">在使用者電腦上安裝的每個 LocalDB 版本都有一個自動 LocalDB 實例。</span><span class="sxs-lookup"><span data-stu-id="9804b-116">One automatic LocalDB instance exists for every version of LocalDB that is installed on the user's computer.</span></span>  
  
 <span data-ttu-id="9804b-117">自動 LocalDB 執行個體提供順暢的執行個體管理。</span><span class="sxs-lookup"><span data-stu-id="9804b-117">Automatic LocalDB instances provide seamless instance management.</span></span> <span data-ttu-id="9804b-118">使用者不需要建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="9804b-118">The user does not need to create the instance.</span></span> <span data-ttu-id="9804b-119">這讓使用者可以輕鬆安裝應用程式，並移轉至不同的電腦。</span><span class="sxs-lookup"><span data-stu-id="9804b-119">This enables users to easily install applications and to migrate to different computers.</span></span> <span data-ttu-id="9804b-120">如果目標電腦已安裝指定的 LocalDB 版本，該電腦也可以使用此版本的自動 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9804b-120">If the target computer has the specified version of LocalDB installed, the automatic LocalDB instance for that version is also available on that computer.</span></span>  
  
### <a name="automatic-instance-management"></a><span data-ttu-id="9804b-121">自動執行個體管理</span><span class="sxs-lookup"><span data-stu-id="9804b-121">Automatic Instance Management</span></span>  
 <span data-ttu-id="9804b-122">使用者不需要建立自動 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9804b-122">A user does not need to create an automatic LocalDB instance.</span></span> <span data-ttu-id="9804b-123">第一次使用實例時，會延遲建立實例，前提是使用者電腦上可以使用指定的 LocalDB 版本。</span><span class="sxs-lookup"><span data-stu-id="9804b-123">The instance is lazily created the first time the instance is used, provided that the specified version of LocalDB is available on the user's computer.</span></span> <span data-ttu-id="9804b-124">從使用者的觀點來看，如果 LocalDB 二進位檔存在，自動實例一律會存在。</span><span class="sxs-lookup"><span data-stu-id="9804b-124">From the user's point of view, the automatic instance is always present if the LocalDB binaries are present.</span></span>  
  
 <span data-ttu-id="9804b-125">刪除、共用及取消共用等其他執行個體管理作業也適用於自動執行個體。</span><span class="sxs-lookup"><span data-stu-id="9804b-125">Other instance management operations, such as Delete, Share, and Unshare, also work for automatic instances.</span></span> <span data-ttu-id="9804b-126">具體而言，刪除自動執行個體會有效地重設執行個體，進而在下一個啟動作業中重新建立。</span><span class="sxs-lookup"><span data-stu-id="9804b-126">In particular, deleting an automatic instance effectively resets the instance, which will be re-created on the next Start operation.</span></span> <span data-ttu-id="9804b-127">如果系統資料庫損毀，可能需要刪除自動執行個體。</span><span class="sxs-lookup"><span data-stu-id="9804b-127">Deleting an automatic instance may be required if the system databases become corrupted.</span></span>  
  
### <a name="automatic-instance-naming-rules"></a><span data-ttu-id="9804b-128">自動執行個體命名規則</span><span class="sxs-lookup"><span data-stu-id="9804b-128">Automatic Instance Naming Rules</span></span>  
 <span data-ttu-id="9804b-129">自動 LocalDB 執行個體的執行個體名稱採用屬於保留命名空間的特殊模式。</span><span class="sxs-lookup"><span data-stu-id="9804b-129">Automatic LocalDB instances have a special pattern for the instance name that belongs to a reserved namespace.</span></span> <span data-ttu-id="9804b-130">為了避免與具名 LocalDB 執行個體發生名稱衝突，這麼做是有必要的。</span><span class="sxs-lookup"><span data-stu-id="9804b-130">This is necessary to prevent name conflicts with named LocalDB instances.</span></span>  
  
 <span data-ttu-id="9804b-131">自動實例名稱是 LocalDB 基準發行版本號碼，前面加上單一 "v" 字元。</span><span class="sxs-lookup"><span data-stu-id="9804b-131">The automatic instance name is the LocalDB baseline release version number preceded by a single "v" character.</span></span> <span data-ttu-id="9804b-132">這看起來像 "v" 加上兩個數字，其間有一個句點;例如，11.0 或 V 12.00。</span><span class="sxs-lookup"><span data-stu-id="9804b-132">This looks like "v" plus two numbers with a period between them; for example, v11.0 or V12.00.</span></span>  
  
 <span data-ttu-id="9804b-133">不合法的自動執行個體名稱範例如下：</span><span class="sxs-lookup"><span data-stu-id="9804b-133">Examples of illegal automatic instance names are:</span></span>  
  
-   <span data-ttu-id="9804b-134">11.0 (在開頭) 遺漏 "v" 字元</span><span class="sxs-lookup"><span data-stu-id="9804b-134">11.0 (missing the "v" character at the beginning)</span></span>  
  
-   <span data-ttu-id="9804b-135">v11 (遺漏句號及第二組版本號碼)</span><span class="sxs-lookup"><span data-stu-id="9804b-135">v11 (missing a period and the second number of the version)</span></span>  
  
-   <span data-ttu-id="9804b-136">v11.</span><span class="sxs-lookup"><span data-stu-id="9804b-136">v11.</span></span> <span data-ttu-id="9804b-137">(遺漏第二組版本號碼)</span><span class="sxs-lookup"><span data-stu-id="9804b-137">(missing the second number of the version)</span></span>  
  
-   <span data-ttu-id="9804b-138">v11.0.1.2 (版本號碼超過兩個部分)</span><span class="sxs-lookup"><span data-stu-id="9804b-138">v11.0.1.2 (version number has more than two parts)</span></span>  
  
## <a name="named-localdb-instances"></a><span data-ttu-id="9804b-139">具名 LocalDB 執行個體</span><span class="sxs-lookup"><span data-stu-id="9804b-139">Named LocalDB Instances</span></span>  
 <span data-ttu-id="9804b-140">命名的 LocalDB 實例為「私用」;實例是由負責建立及管理實例的單一應用程式所擁有。</span><span class="sxs-lookup"><span data-stu-id="9804b-140">Named LocalDB instances are "private"; an instance is owned by a single application that is responsible for creating and managing the instance.</span></span> <span data-ttu-id="9804b-141">具名 LocalDB 執行個體提供隔離並提升效能。</span><span class="sxs-lookup"><span data-stu-id="9804b-141">Named LocalDB instances provide isolation and improve performance.</span></span>  
  
### <a name="named-instance-creation"></a><span data-ttu-id="9804b-142">具名執行個體建立</span><span class="sxs-lookup"><span data-stu-id="9804b-142">Named Instance Creation</span></span>  
 <span data-ttu-id="9804b-143">使用者建立具名執行個體時，必須透過 LocalDB 管理 API 以明確的方式建立，或透過 Managed 應用程式的 app.config 檔案以隱含的方式建立。</span><span class="sxs-lookup"><span data-stu-id="9804b-143">The user must create named instances explicitly through the LocalDB management API, or implicitly through the app.config file for a managed application.</span></span> <span data-ttu-id="9804b-144">Managed 應用程式也可以使用 API。</span><span class="sxs-lookup"><span data-stu-id="9804b-144">A managed application may also use the API.</span></span>  
  
 <span data-ttu-id="9804b-145">每個具名執行個體具有相關聯的 LocalDB 版本；亦即指向一組指定的 LocalDB 二進位檔。</span><span class="sxs-lookup"><span data-stu-id="9804b-145">Each named instance has an associated LocalDB version; that is, it points to a specified set of LocalDB binaries.</span></span> <span data-ttu-id="9804b-146">您可以在執行個體建立程序期間設定具名執行個體的版本。</span><span class="sxs-lookup"><span data-stu-id="9804b-146">The version for the named instance is set during the instance creation process.</span></span>  
  
### <a name="named-instance-naming-rules"></a><span data-ttu-id="9804b-147">具名執行個體命名規則</span><span class="sxs-lookup"><span data-stu-id="9804b-147">Named Instance Naming Rules</span></span>  
 <span data-ttu-id="9804b-148">LocalDB 執行個體名稱最多可以包含共 128 個字元 (這是 `sysname` 資料類型加諸的限制)。</span><span class="sxs-lookup"><span data-stu-id="9804b-148">A LocalDB instance name can have up to a total of 128 characters (the limit is imposed by the `sysname` data type).</span></span> <span data-ttu-id="9804b-149">這與傳統的 SQL Server 執行個體名稱相較下十分不同，傳統的執行個體限制使用 16 個 ASCII 字元的 NetBIOS 名稱。</span><span class="sxs-lookup"><span data-stu-id="9804b-149">This is a significant difference compared to traditional SQL Server instance names, which are limited to NetBIOS names of 16 ASCII characters.</span></span> <span data-ttu-id="9804b-150">這項差異的原因在於 LocalDB 會將資料庫視為檔案，因此意指以檔案為基礎的語義，因此使用者可以更輕鬆地選擇實例名稱。</span><span class="sxs-lookup"><span data-stu-id="9804b-150">The reason for this difference is that LocalDB treats databases as files, and therefore implies file-based semantics, so it's intuitive for users to have more freedom in choosing instance names.</span></span>  
  
 <span data-ttu-id="9804b-151">LocalDB 執行個體名稱可以在檔案名稱元件內包含合法的任何 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="9804b-151">A LocalDB instance name can contain any Unicode characters that are legal within the filename component.</span></span> <span data-ttu-id="9804b-152">檔案名元件中不合法的字元通常包含下列字元： ASCII/Unicode 字元1到31，以及引號 ( 「) 、小於 (\<), greater than (>) 、管道 (|) 、倒退鍵 ( \b) 、tab ( \t) 、冒號 (： ) 、星號 ( \* ) 、問號 (、) 、反斜線 (\\) 和正斜線 (/) 。</span><span class="sxs-lookup"><span data-stu-id="9804b-152">Illegal characters in a filename component generally include the following characters: ASCII/Unicode characters 1 through 31, as well as quote ("), less than (\<), greater than (>), pipe (|), backspace (\b), tab (\t), colon (:), asterisk (\*), question mark (?), backslash (\\), and forward slash (/).</span></span> <span data-ttu-id="9804b-153">請注意，由於 Null 字元 (\0) 用於字串結束字元，因此允許使用；將忽略第一個 Null 字元之後的所有字元。</span><span class="sxs-lookup"><span data-stu-id="9804b-153">Note that the null character (\0) is allowed because it is used for string termination; everything after the first null character will be ignored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9804b-154">不合法的字元清單可能取決於作業系統，並且可能在未來版本中變更。</span><span class="sxs-lookup"><span data-stu-id="9804b-154">The list of illegal characters may depend on the operating system and may change in future releases.</span></span>  
  
 <span data-ttu-id="9804b-155">執行個體名稱中的開頭及尾端空白會予以忽略並修剪。</span><span class="sxs-lookup"><span data-stu-id="9804b-155">Leading and trailing white spaces in instance names are ignored and will be trimmed.</span></span>  
  
 <span data-ttu-id="9804b-156">為避免命名衝突，名為 LocalDB 實例的名稱不能遵循自動實例的命名模式，如先前的「自動實例命名規則」中所述。</span><span class="sxs-lookup"><span data-stu-id="9804b-156">To avoid naming conflicts, named LocalDB instances cannot have a name that follows the naming pattern for automatic instances, as described earlier in "Automatic Instance Naming Rules."</span></span> <span data-ttu-id="9804b-157">嘗試使用遵循自動實例命名模式的名稱來建立名為的實例，實際上會建立預設實例。</span><span class="sxs-lookup"><span data-stu-id="9804b-157">An attempt to create a named instance with a name that follows the automatic instance naming pattern effectively creates a default instance.</span></span>  
  
## <a name="sql-server-express-localdb-reference-topics"></a><span data-ttu-id="9804b-158">SQL Server Express LocalDB 參考主題</span><span class="sxs-lookup"><span data-stu-id="9804b-158">SQL Server Express LocalDB Reference Topics</span></span>  
 [<span data-ttu-id="9804b-159">SQL Server Express LocalDB 標頭和版本資訊</span><span class="sxs-lookup"><span data-stu-id="9804b-159">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
 <span data-ttu-id="9804b-160">提供標頭檔資訊和登錄機碼，以尋找 LocalDB 執行個體 API。</span><span class="sxs-lookup"><span data-stu-id="9804b-160">Provides header file information and registry keys for finding the LocalDB instance API.</span></span>  
  
 [<span data-ttu-id="9804b-161">命令列管理工具：SqlLocalDB.exe</span><span class="sxs-lookup"><span data-stu-id="9804b-161">Command-Line Management Tool: SqlLocalDB.exe</span></span>](command-line-management-tool-sqllocaldb-exe.md)  
 <span data-ttu-id="9804b-162">描述 SqlLocalDB.exe，此工具可從命令列管理 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9804b-162">Describes SqlLocalDB.exe, a tool for managing LocalDB instances from the command line.</span></span>  
  
 [<span data-ttu-id="9804b-163">LocalDBCreateInstance 函數</span><span class="sxs-lookup"><span data-stu-id="9804b-163">LocalDBCreateInstance Function</span></span>](localdbcreateinstance-function.md)  
 <span data-ttu-id="9804b-164">描述新建 LocalDB 執行個體的函數。</span><span class="sxs-lookup"><span data-stu-id="9804b-164">Describes the function to create a new LocalDB instance.</span></span>  
  
 [<span data-ttu-id="9804b-165">LocalDBDeleteInstance 函數</span><span class="sxs-lookup"><span data-stu-id="9804b-165">LocalDBDeleteInstance Function</span></span>](localdbdeleteinstance-function.md)  
 <span data-ttu-id="9804b-166">描述移除 LocalDB 執行個體的函數。</span><span class="sxs-lookup"><span data-stu-id="9804b-166">Describes the function to remove a LocalDB instance.</span></span>  
  
 [<span data-ttu-id="9804b-167">LocalDBFormatMessage 函數</span><span class="sxs-lookup"><span data-stu-id="9804b-167">LocalDBFormatMessage Function</span></span>](localdbformatmessage-function.md)  
 <span data-ttu-id="9804b-168">描述傳回 LocalDB 錯誤之當地語系化說明的函數。</span><span class="sxs-lookup"><span data-stu-id="9804b-168">Describes the function to return the localized description for a LocalDB error.</span></span>  
  
 [<span data-ttu-id="9804b-169">LocalDBGetInstanceInfo 函數</span><span class="sxs-lookup"><span data-stu-id="9804b-169">LocalDBGetInstanceInfo Function</span></span>](localdbgetinstanceinfo-function.md)  
 <span data-ttu-id="9804b-170">描述取得 LocalDB 執行個體資訊的函數；例如，執行個體是否存在、版本資訊，執行個體是否正在執行等等。</span><span class="sxs-lookup"><span data-stu-id="9804b-170">Describes the function to get information for a LocalDB instance, such as whether it exists, version information, whether it is running, and so on.</span></span>  
  
 [<span data-ttu-id="9804b-171">LocalDBGetInstances 函數</span><span class="sxs-lookup"><span data-stu-id="9804b-171">LocalDBGetInstances Function</span></span>](localdbgetinstances-function.md)  
 <span data-ttu-id="9804b-172">描述傳回指定版本之所有 LocalDB 執行個體的函數。</span><span class="sxs-lookup"><span data-stu-id="9804b-172">Describes the function to return all the LocalDB instances with a specified version.</span></span>  
  
 [<span data-ttu-id="9804b-173">LocalDBGetVersionInfo 函數</span><span class="sxs-lookup"><span data-stu-id="9804b-173">LocalDBGetVersionInfo Function</span></span>](localdbgetversioninfo-function.md)  
 <span data-ttu-id="9804b-174">描述傳回指定版本之所有 LocalDB 執行個體的函數。</span><span class="sxs-lookup"><span data-stu-id="9804b-174">Describes the function to return information for a specified LocalDB version.</span></span>  
  
 [<span data-ttu-id="9804b-175">LocalDBGetVersions 函數</span><span class="sxs-lookup"><span data-stu-id="9804b-175">LocalDBGetVersions Function</span></span>](localdbgetversions-function.md)  
 <span data-ttu-id="9804b-176">描述傳回電腦上所有可用之 LocalDB 版本的函數。</span><span class="sxs-lookup"><span data-stu-id="9804b-176">Describes the function to return all LocalDB versions available on a computer.</span></span>  
  
 [<span data-ttu-id="9804b-177">LocalDBShareInstance 函數</span><span class="sxs-lookup"><span data-stu-id="9804b-177">LocalDBShareInstance Function</span></span>](localdbshareinstance-function.md)  
 <span data-ttu-id="9804b-178">描述共用指定 LocalDB 執行個體的函數。</span><span class="sxs-lookup"><span data-stu-id="9804b-178">Describes the function to share a specified LocalDB instance.</span></span>  
  
 [<span data-ttu-id="9804b-179">LocalDBStartInstance 函數</span><span class="sxs-lookup"><span data-stu-id="9804b-179">LocalDBStartInstance Function</span></span>](localdbstartinstance-function.md)  
 <span data-ttu-id="9804b-180">描述啟動指定 LocalDB 執行個體的函數。</span><span class="sxs-lookup"><span data-stu-id="9804b-180">Describes the function to start a specified LocalDB instance.</span></span>  
  
 [<span data-ttu-id="9804b-181">LocalDBStartTracing 函數</span><span class="sxs-lookup"><span data-stu-id="9804b-181">LocalDBStartTracing Function</span></span>](localdbstarttracing-function.md)  
 <span data-ttu-id="9804b-182">描述為使用者啟用 API 追蹤的函數。</span><span class="sxs-lookup"><span data-stu-id="9804b-182">Describes the function to enable API tracing for a user.</span></span>  
  
 [<span data-ttu-id="9804b-183">LocalDBStopInstance 函數</span><span class="sxs-lookup"><span data-stu-id="9804b-183">LocalDBStopInstance Function</span></span>](localdbstopinstance-function.md)  
 <span data-ttu-id="9804b-184">描述停止執行指定 LocalDB 執行個體的函數。</span><span class="sxs-lookup"><span data-stu-id="9804b-184">Describes the function to stop a specified LocalDB instance from running.</span></span>  
  
 [<span data-ttu-id="9804b-185">LocalDBStopTracing 函數</span><span class="sxs-lookup"><span data-stu-id="9804b-185">LocalDBStopTracing Function</span></span>](localdbstoptracing-function.md)  
 <span data-ttu-id="9804b-186">描述為使用者停用 API 追蹤的函數。</span><span class="sxs-lookup"><span data-stu-id="9804b-186">Describes the function to disable API tracing for a user.</span></span>  
  
 [<span data-ttu-id="9804b-187">LocalDBUnshareInstance 函數</span><span class="sxs-lookup"><span data-stu-id="9804b-187">LocalDBUnshareInstance Function</span></span>](localdbunshareinstance-function.md)  
 <span data-ttu-id="9804b-188">描述停止共用指定 LocalDB 執行個體的函數。</span><span class="sxs-lookup"><span data-stu-id="9804b-188">Describes the function to stop sharing a specified LocalDB instance.</span></span>  
  
  
