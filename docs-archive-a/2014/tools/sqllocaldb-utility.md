---
title: SqlLocalDB 公用程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- SqlLocalDB utility [SQL Server]
- local database runtime utility
- LocalDB, SqlLocalDB Utility
ms.assetid: d785cdb7-1ea0-4871-bde9-1ae7881190f5
author: stevestein
ms.author: sstein
ms.openlocfilehash: bfb95cea4365d56c296d14fcc09046cd7eddc0c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686584"
---
# <a name="sqllocaldb-utility"></a><span data-ttu-id="76be0-102">SqlLocalDB 公用程式</span><span class="sxs-lookup"><span data-stu-id="76be0-102">SqlLocalDB Utility</span></span>
  <span data-ttu-id="76be0-103">使用 `SqlLocalDB` 公用程式來建立 LocalDB 的實例 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssExpCurrent](../includes/ssexpcurrent-md.md)] \*\* \*\*。</span><span class="sxs-lookup"><span data-stu-id="76be0-103">Use the `SqlLocalDB` utility to create an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssExpCurrent](../includes/ssexpcurrent-md.md)]**LocalDB**.</span></span> <span data-ttu-id="76be0-104">`SqlLocalDB`公用程式 ( # A0) 是簡單的命令列工具，可讓使用者和開發人員建立及管理 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] **LocalDB**的實例。</span><span class="sxs-lookup"><span data-stu-id="76be0-104">The `SqlLocalDB` utility (SqlLocalDB.exe) is a simple command line tool to enable users and developers to create and manage an instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span> <span data-ttu-id="76be0-105">如需如何使用**LocalDB**的詳細資訊，請參閱[SQL Server 2014 Express LocalDB](../database-engine/configure-windows/sql-server-2016-express-localdb.md)。</span><span class="sxs-lookup"><span data-stu-id="76be0-105">For information about how to use **LocalDB**, see [SQL Server 2014 Express LocalDB](../database-engine/configure-windows/sql-server-2016-express-localdb.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76be0-106">語法</span><span class="sxs-lookup"><span data-stu-id="76be0-106">Syntax</span></span>  
  
```  
SqlLocalDB.exe   
{  
      [ create   | c ] <instance-name><instance-version> [-s ]  
    | [ delete   | d ] <instance-name>  
    | [ start    | s ] <instance-name>  
    | [ stop     | p ] <instance-name>  [ -i ] [ -k ]  
    | [ share    | h ] ["<user_SID>" | "<user_account>" ] "<private-name>""<shared-name>"  
    | [ unshare  | u ] "<shared-name>"  
    | [ info     | i ] <instance-name>  
    | [ versions | v ]  
    | [ trace    | t ] [ on | off ]  
    | [ help     | -? ]  
}  
```  
  
## <a name="arguments"></a><span data-ttu-id="76be0-107">引數</span><span class="sxs-lookup"><span data-stu-id="76be0-107">Arguments</span></span>  
 <span data-ttu-id="76be0-108">[ **create** | **c** ] *\<instance-name>* *\<instance-version>* [ **-s** ]</span><span class="sxs-lookup"><span data-stu-id="76be0-108">[ **create** | **c** ] *\<instance-name>* *\<instance-version>* [**-s** ]</span></span>  
 <span data-ttu-id="76be0-109">建立 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** 的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="76be0-109">Creates a new of instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span> <span data-ttu-id="76be0-110">`SqlLocalDB`使用引數所指定之二進位檔的版本 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] *\<instance-version>* 。</span><span class="sxs-lookup"><span data-stu-id="76be0-110">`SqlLocalDB` uses the version of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] binaries specified by *\<instance-version>* argument.</span></span> <span data-ttu-id="76be0-111">使用至少一個十進位數的數字格式指定版本號碼。</span><span class="sxs-lookup"><span data-stu-id="76be0-111">The version number is specified in numeric format with at least one decimal.</span></span> <span data-ttu-id="76be0-112">次要版本號碼 (Service Pack) 為選擇性。</span><span class="sxs-lookup"><span data-stu-id="76be0-112">The minor version numbers (service packs) are optional.</span></span> <span data-ttu-id="76be0-113">例如，下列兩個版本號碼都可接受：11.0 或 11.0.1186。</span><span class="sxs-lookup"><span data-stu-id="76be0-113">For example the following two version numbers are both acceptable: 11.0, or 11.0.1186.</span></span> <span data-ttu-id="76be0-114">電腦上必須安裝指定的版本。</span><span class="sxs-lookup"><span data-stu-id="76be0-114">The specified version must be installed on the computer.</span></span> <span data-ttu-id="76be0-115">如果未指定，版本號碼會預設為公用程式的版本 `SqlLocalDB` 。</span><span class="sxs-lookup"><span data-stu-id="76be0-115">If not specified, the version number defaults to the version of the `SqlLocalDB` utility.</span></span> <span data-ttu-id="76be0-116">加入 **-s** 會啟動新的 **LocalDB** 執行個體。</span><span class="sxs-lookup"><span data-stu-id="76be0-116">Adding **-s** starts the new instance of **LocalDB**.</span></span>  
  
 <span data-ttu-id="76be0-117">[ **share** | **h** ]</span><span class="sxs-lookup"><span data-stu-id="76be0-117">[ **share** | **h** ]</span></span>  
 <span data-ttu-id="76be0-118">使用指定的共用名稱來共用指定的 **LocalDB** 私用執行個體。</span><span class="sxs-lookup"><span data-stu-id="76be0-118">Shares the specified private instance of **LocalDB** using the specified shared name.</span></span> <span data-ttu-id="76be0-119">如果省略使用者 SID 或帳戶名稱，會預設為目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="76be0-119">If the user SID or account name is omitted, it defaults to the current user.</span></span>  
  
 <span data-ttu-id="76be0-120">[ **unshared** | **u** ]</span><span class="sxs-lookup"><span data-stu-id="76be0-120">[ **unshared** | **u** ]</span></span>  
 <span data-ttu-id="76be0-121">停止共用指定的 **LocalDB**共用執行個體。</span><span class="sxs-lookup"><span data-stu-id="76be0-121">Stops the sharing of the specified shared instance of **LocalDB**.</span></span>  
  
 <span data-ttu-id="76be0-122">[ **delete** | **d** ] *\<instance-name>*</span><span class="sxs-lookup"><span data-stu-id="76be0-122">[ **delete** | **d** ] *\<instance-name>*</span></span>  
 <span data-ttu-id="76be0-123">刪除指定的 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** 執行個體。</span><span class="sxs-lookup"><span data-stu-id="76be0-123">Deletes the specified instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span>  
  
 <span data-ttu-id="76be0-124">[ **start** | **s** ] " *\<instance-name>* "</span><span class="sxs-lookup"><span data-stu-id="76be0-124">[ **start** | **s** ] "*\<instance-name>*"</span></span>  
 <span data-ttu-id="76be0-125">啟動指定的 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** 執行個體。</span><span class="sxs-lookup"><span data-stu-id="76be0-125">Starts the specified instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span> <span data-ttu-id="76be0-126">當成功的陳述式傳回 **LocalDB**的具名管道位址時。</span><span class="sxs-lookup"><span data-stu-id="76be0-126">When successful the statement returns the named pipe address of the **LocalDB**.</span></span>  
  
 <span data-ttu-id="76be0-127">[ **stop** | **p** ] *\<instance-name>* [ **-i** ] [ **-k** ]</span><span class="sxs-lookup"><span data-stu-id="76be0-127">[ **stop** | **p** ] *\<instance-name>* [**-i** ] [**-k** ]</span></span>  
 <span data-ttu-id="76be0-128">停止指定的 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** 執行個體。</span><span class="sxs-lookup"><span data-stu-id="76be0-128">Stops the specified instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**.</span></span> <span data-ttu-id="76be0-129">新增 **-i**會使用選項來要求關閉實例 `NOWAIT` 。</span><span class="sxs-lookup"><span data-stu-id="76be0-129">Adding **-i** requests the instance shutdown with the `NOWAIT` option.</span></span> <span data-ttu-id="76be0-130">加入 **-k** 會在未經連絡的情況下終止執行個體處理序。</span><span class="sxs-lookup"><span data-stu-id="76be0-130">Adding **-k** kills the instance process without contacting it.</span></span>  
  
 <span data-ttu-id="76be0-131">[ **info** | **i** ] [ *\<instance-name>* ]</span><span class="sxs-lookup"><span data-stu-id="76be0-131">[ **info** | **i** ] [ *\<instance-name>* ]</span></span>  
 <span data-ttu-id="76be0-132">列出目前使用者擁有的所有 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** 執行個體。</span><span class="sxs-lookup"><span data-stu-id="76be0-132">Lists all instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** owned by the current user.</span></span>  
  
 <span data-ttu-id="76be0-133">*\<instance-name>* 會傳回指定之 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** 執行個體的名稱、版本、狀態 (執行中或已停止)、上次啟動時間，以及 **LocalDB** 的本機管道名稱。</span><span class="sxs-lookup"><span data-stu-id="76be0-133">*\<instance-name>* returns the name, version, state (Running or Stopped), last start time for the specified instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB**, and the local pipe name of the **LocalDB**.</span></span>  
  
 <span data-ttu-id="76be0-134">[ **trace** | **t** ] **on** | **off**</span><span class="sxs-lookup"><span data-stu-id="76be0-134">[ **trace** | **t** ] **on** | **off**</span></span>  
 <span data-ttu-id="76be0-135">**追蹤 on**會針對 `SqlLocalDB` 目前使用者啟用 API 呼叫的追蹤。</span><span class="sxs-lookup"><span data-stu-id="76be0-135">**trace on** enables tracing for the `SqlLocalDB` API calls for the current user.</span></span> <span data-ttu-id="76be0-136">**trace off** 停用追蹤。</span><span class="sxs-lookup"><span data-stu-id="76be0-136">**trace off** disables tracing.</span></span>  
  
 <span data-ttu-id="76be0-137">**-?**</span><span class="sxs-lookup"><span data-stu-id="76be0-137">**-?**</span></span>  
 <span data-ttu-id="76be0-138">傳回每個選項的簡短描述 `SqlLocalDB` 。</span><span class="sxs-lookup"><span data-stu-id="76be0-138">Returns brief descriptions of each `SqlLocalDB` option.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76be0-139">備註</span><span class="sxs-lookup"><span data-stu-id="76be0-139">Remarks</span></span>  
 <span data-ttu-id="76be0-140"><執行個體名稱> 引數必須遵循 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 識別碼的規則，或者必須以雙引號括住。</span><span class="sxs-lookup"><span data-stu-id="76be0-140">The *instance name* argument must follow the rules for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifiers or it must be enclosed in double quotes.</span></span>  
  
 <span data-ttu-id="76be0-141">不使用任何引數執行 SqlLocalDB 會傳回說明文字。</span><span class="sxs-lookup"><span data-stu-id="76be0-141">Executing SqlLocalDB without arguments returns the help text.</span></span>  
  
 <span data-ttu-id="76be0-142">啟動以外的作業只能在屬於目前登入之使用者的執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="76be0-142">Operations other than start can only be performed on an instance belonging to currently logged in user.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="76be0-143">範例</span><span class="sxs-lookup"><span data-stu-id="76be0-143">Examples</span></span>  
  
### <a name="a-creating-an-instance-of-localdb"></a><span data-ttu-id="76be0-144">A.</span><span class="sxs-lookup"><span data-stu-id="76be0-144">A.</span></span> <span data-ttu-id="76be0-145">建立 LocalDB 的執行個體</span><span class="sxs-lookup"><span data-stu-id="76be0-145">Creating an Instance of LocalDB</span></span>  
 <span data-ttu-id="76be0-146">下列範例會使用 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**二進位檔建立名為** 的 `DEPARTMENT` LocalDB [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 執行個體，並啟動此執行個體。</span><span class="sxs-lookup"><span data-stu-id="76be0-146">The following example creates an instance of [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]**LocalDB** named `DEPARTMENT` using the [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] binaries and starts the instance.</span></span>  
  
```  
SqlLocalDB.exe create "DEPARTMENT" 12.0 -s  
```  
  
### <a name="b-working-with-a-shared-instance-of-localdb"></a><span data-ttu-id="76be0-147">B.</span><span class="sxs-lookup"><span data-stu-id="76be0-147">B.</span></span> <span data-ttu-id="76be0-148">使用 LocalDB 的共用執行個體</span><span class="sxs-lookup"><span data-stu-id="76be0-148">Working with a Shared Instance of LocalDB</span></span>  
 <span data-ttu-id="76be0-149">使用管理員權限開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="76be0-149">Open a command prompt using Administrator privileges.</span></span>  
  
```  
SqlLocalDB.exe create "DeptLocalDB"  
SqlLocalDB.exe share "DeptLocalDB" "DeptSharedLocalDB"  
SqlLocalDB.exe start "DeptLocalDB"  
SqlLocalDB.exe info "DeptLocalDB"  
REM The previous statement outputs the Instance pipe name for the next step  
sqlcmd -S np:\\.\pipe\LOCALDB#<use your pipe name>\tsql\query  
CREATE LOGIN NewLogin WITH PASSWORD = 'Passw0rd!!@52';   
GO  
CREATE USER NewLogin;  
GO  
EXIT  
```  
  
 <span data-ttu-id="76be0-150">使用 **登入執行以下程式碼以連接到** LocalDB `NewLogin` 的共用執行個體。</span><span class="sxs-lookup"><span data-stu-id="76be0-150">Execute the following code to connect to the shared instance of **LocalDB** using the `NewLogin` login.</span></span>  
  
```  
sqlcmd -S (localdb)\.\DeptSharedLocalDB -U NewLogin -P Passw0rd!!@52  
```  
  
## <a name="see-also"></a><span data-ttu-id="76be0-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76be0-151">See Also</span></span>  
 [<span data-ttu-id="76be0-152">SQL Server 2014 Express LocalDB</span><span class="sxs-lookup"><span data-stu-id="76be0-152">SQL Server 2014 Express LocalDB</span></span>](../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
  
