---
title: GenerateDatabaseRightsScript 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseRightsScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseRightsScript method
ms.assetid: f2e6dcc9-978f-4c2c-bafe-36c330247fd0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 768e73d13d3b06f7913c3c816fded1b28c56199f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706086"
---
# <a name="generatedatabaserightsscript-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="3fc93-102">GenerateDatabaseRightsScript 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="3fc93-102">GenerateDatabaseRightsScript Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="3fc93-103">產生可用來將報表伺服器資料庫和其他資料庫 (執行報表伺服器所需) 之權限授與使用者的 SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="3fc93-103">Generates a SQL Script that can be used to grant a user rights to the report server database and other databases required for a report server to run.</span></span> <span data-ttu-id="3fc93-104">呼叫者預期要連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫伺服器並執行此指令碼。</span><span class="sxs-lookup"><span data-stu-id="3fc93-104">The caller is expected to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database server and execute the script.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fc93-105">語法</span><span class="sxs-lookup"><span data-stu-id="3fc93-105">Syntax</span></span>  
  
```vb  
Public Sub GenerateDatabaseRightsScript(ByVal UserName As String, _  
    ByVal DatabaseName As String, ByVal IsRemote As Boolean, _  
    ByVal IsWindowsUser As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseRightsScript(string UserName, string DatabaseName, bool IsRemote, bool IsWindowsUser, out string Script,   
out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fc93-106">參數</span><span class="sxs-lookup"><span data-stu-id="3fc93-106">Parameters</span></span>  
 <span data-ttu-id="3fc93-107">*UserName*</span><span class="sxs-lookup"><span data-stu-id="3fc93-107">*UserName*</span></span>  
 <span data-ttu-id="3fc93-108">此指令碼將授與權限之目標使用者的使用者名稱或 Windows 安全性識別碼 (SID)。</span><span class="sxs-lookup"><span data-stu-id="3fc93-108">The user name or Windows security identifier (SID) of the user to which the script will grant rights.</span></span>  
  
 <span data-ttu-id="3fc93-109">*DatabaseName*</span><span class="sxs-lookup"><span data-stu-id="3fc93-109">*DatabaseName*</span></span>  
 <span data-ttu-id="3fc93-110">此指令碼將授與使用者存取權的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="3fc93-110">The database name to which the script will grant access to the user.</span></span>  
  
 <span data-ttu-id="3fc93-111">*IsRemote*</span><span class="sxs-lookup"><span data-stu-id="3fc93-111">*IsRemote*</span></span>  
 <span data-ttu-id="3fc93-112">指出資料庫是否位於報表伺服器遠端的布林值。</span><span class="sxs-lookup"><span data-stu-id="3fc93-112">A Boolean value to indicating whether the database is remote from the report server.</span></span>  
  
 <span data-ttu-id="3fc93-113">*IsWindowsUser*</span><span class="sxs-lookup"><span data-stu-id="3fc93-113">*IsWindowsUser*</span></span>  
 <span data-ttu-id="3fc93-114">指出指定之使用者名稱是 Windows 使用者或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者的布林值。</span><span class="sxs-lookup"><span data-stu-id="3fc93-114">A Boolean value indicating whether the specified user name is a Windows user or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user.</span></span>  
  
 <span data-ttu-id="3fc93-115">*指令碼*</span><span class="sxs-lookup"><span data-stu-id="3fc93-115">*Script*</span></span>  
 <span data-ttu-id="3fc93-116">[out] 包含所產生之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指令碼的字串。</span><span class="sxs-lookup"><span data-stu-id="3fc93-116">[out] A string containing the generated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] script.</span></span>  
  
 <span data-ttu-id="3fc93-117">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="3fc93-117">*HRESULT*</span></span>  
 <span data-ttu-id="3fc93-118">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="3fc93-118">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fc93-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="3fc93-119">Return Value</span></span>  
 <span data-ttu-id="3fc93-120">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="3fc93-120">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="3fc93-121">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="3fc93-121">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="3fc93-122">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="3fc93-122">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fc93-123">備註</span><span class="sxs-lookup"><span data-stu-id="3fc93-123">Remarks</span></span>  
 <span data-ttu-id="3fc93-124">如果 *DatabaseName* 是空的，即忽略 *IsRemote* ，而且報表伺服器組態檔值會用於資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="3fc93-124">If *DatabaseName* is empty then *IsRemote* is ignored and the report server configuration file value is used for the database name.</span></span>  
  
 <span data-ttu-id="3fc93-125">如果*IsWindowsUser*設定為 `true` ， *username*的格式應為 \<domain> \\<username \> 。</span><span class="sxs-lookup"><span data-stu-id="3fc93-125">If *IsWindowsUser* is set to `true`, *UserName* should be in the format \<domain>\\<username\>.</span></span>  
  
 <span data-ttu-id="3fc93-126">當*IsWindowsUser*設定為時 `true` ，產生的腳本會將登入許可權授與的使用者 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，並將報表伺服器資料庫設定為預設資料庫，並授與報表伺服器資料庫、報表伺服器暫存資料庫、master 資料庫和 MSDB 系統資料庫的**RSExec**角色。</span><span class="sxs-lookup"><span data-stu-id="3fc93-126">When *IsWindowsUser* is set to `true`, the generated script grants login rights to the user for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], setting the report server database as the default database, and grants the **RSExec** role on the report server database, the report server temporary database, the master database and the MSDB system database.</span></span>  
  
 <span data-ttu-id="3fc93-127">當*IsWindowsUser*設定為時 `true` ，此方法會接受標準 Windows sid 做為輸入。</span><span class="sxs-lookup"><span data-stu-id="3fc93-127">When *IsWindowsUser* is set to `true`, the method accepts standard Windows SIDs as input.</span></span> <span data-ttu-id="3fc93-128">提供了標準 Windows SID 或服務帳戶名稱時，它就會轉譯成使用者名稱字串。</span><span class="sxs-lookup"><span data-stu-id="3fc93-128">When a standard Windows SID or service account name is supplied, it is translated to a user name string.</span></span> <span data-ttu-id="3fc93-129">如果資料庫位於本機，此帳戶就會轉譯成帳戶的正確當地語系化表示。</span><span class="sxs-lookup"><span data-stu-id="3fc93-129">If the database is local, the account is translated to the correct localized representation of the account.</span></span> <span data-ttu-id="3fc93-130">如果資料庫位於遠端，此帳戶就會表示成電腦的帳戶。</span><span class="sxs-lookup"><span data-stu-id="3fc93-130">If the database is remote, the account is represented as the computer's account.</span></span>  
  
 <span data-ttu-id="3fc93-131">下表將顯示已轉譯的帳戶及其遠端表示。</span><span class="sxs-lookup"><span data-stu-id="3fc93-131">The following table shows accounts that are translated and their remote representation.</span></span>  
  
|<span data-ttu-id="3fc93-132">已轉譯的帳戶 / SID</span><span class="sxs-lookup"><span data-stu-id="3fc93-132">Account / SID that is translated</span></span>|<span data-ttu-id="3fc93-133">一般名稱</span><span class="sxs-lookup"><span data-stu-id="3fc93-133">Common Name</span></span>|<span data-ttu-id="3fc93-134">遠端名稱</span><span class="sxs-lookup"><span data-stu-id="3fc93-134">Remote Name</span></span>|  
|---------------------------------------|-----------------|-----------------|  
|<span data-ttu-id="3fc93-135">(S-1-5-18)</span><span class="sxs-lookup"><span data-stu-id="3fc93-135">(S-1-5-18)</span></span>|<span data-ttu-id="3fc93-136">[本機系統]</span><span class="sxs-lookup"><span data-stu-id="3fc93-136">Local System</span></span>|<span data-ttu-id="3fc93-137">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="3fc93-137">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="3fc93-138">.\LocalSystem</span><span class="sxs-lookup"><span data-stu-id="3fc93-138">.\LocalSystem</span></span>|<span data-ttu-id="3fc93-139">[本機系統]</span><span class="sxs-lookup"><span data-stu-id="3fc93-139">Local System</span></span>|<span data-ttu-id="3fc93-140">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="3fc93-140">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="3fc93-141">ComputerName\LocalSystem</span><span class="sxs-lookup"><span data-stu-id="3fc93-141">ComputerName\LocalSystem</span></span>|<span data-ttu-id="3fc93-142">[本機系統]</span><span class="sxs-lookup"><span data-stu-id="3fc93-142">Local System</span></span>|<span data-ttu-id="3fc93-143">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="3fc93-143">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="3fc93-144">LocalSystem</span><span class="sxs-lookup"><span data-stu-id="3fc93-144">LocalSystem</span></span>|<span data-ttu-id="3fc93-145">[本機系統]</span><span class="sxs-lookup"><span data-stu-id="3fc93-145">Local System</span></span>|<span data-ttu-id="3fc93-146">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="3fc93-146">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="3fc93-147">(S-1-5-20)</span><span class="sxs-lookup"><span data-stu-id="3fc93-147">(S-1-5-20)</span></span>|<span data-ttu-id="3fc93-148">網路服務</span><span class="sxs-lookup"><span data-stu-id="3fc93-148">Network Service</span></span>|<span data-ttu-id="3fc93-149">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="3fc93-149">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="3fc93-150">NT AUTHORITY\NetworkService</span><span class="sxs-lookup"><span data-stu-id="3fc93-150">NT AUTHORITY\NetworkService</span></span>|<span data-ttu-id="3fc93-151">網路服務</span><span class="sxs-lookup"><span data-stu-id="3fc93-151">Network Service</span></span>|<span data-ttu-id="3fc93-152">\<Domain>\\<ComputerName\>$</span><span class="sxs-lookup"><span data-stu-id="3fc93-152">\<Domain>\\<ComputerName\>$</span></span>|  
|<span data-ttu-id="3fc93-153">(S-1-5-19)</span><span class="sxs-lookup"><span data-stu-id="3fc93-153">(S-1-5-19)</span></span>|<span data-ttu-id="3fc93-154">本機服務</span><span class="sxs-lookup"><span data-stu-id="3fc93-154">Local Service</span></span>|<span data-ttu-id="3fc93-155">錯誤 - 請參閱下列內容。</span><span class="sxs-lookup"><span data-stu-id="3fc93-155">Error - see below.</span></span>|  
|<span data-ttu-id="3fc93-156">NT AUTHORITY\LocalService</span><span class="sxs-lookup"><span data-stu-id="3fc93-156">NT AUTHORITY\LocalService</span></span>|<span data-ttu-id="3fc93-157">本機服務</span><span class="sxs-lookup"><span data-stu-id="3fc93-157">Local Service</span></span>|<span data-ttu-id="3fc93-158">錯誤 - 請參閱下列內容。</span><span class="sxs-lookup"><span data-stu-id="3fc93-158">Error - see below.</span></span>|  
  
 <span data-ttu-id="3fc93-159">在 [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)]上，如果您正在使用內建帳戶，而且報表伺服器資料庫位於遠端，就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="3fc93-159">On [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)], if you are using a built-in account and the report server database is remote, an error is returned.</span></span>  
  
 <span data-ttu-id="3fc93-160">如果指定了 `LocalService` 內建帳戶，而且報表伺服器資料庫位於遠端，就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="3fc93-160">If the `LocalService` built-in account is specified and the report server database is remote, an error is returned.</span></span>  
  
 <span data-ttu-id="3fc93-161">當 *IsWindowsUser* 為 true，且必須轉譯 *UserName* 提供的值時，WMI 提供者就會判斷報表伺服器資料庫位於同一部電腦或遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="3fc93-161">When *IsWindowsUser* is true and the value supplied in *UserName* needs to be translated, the WMI provider determines whether the report server database is located on the same computer or on a remote computer.</span></span> <span data-ttu-id="3fc93-162">為了判斷安裝是否位於本機，WMI 提供者會根據下列值清單評估 DatabaseServerName 屬性。</span><span class="sxs-lookup"><span data-stu-id="3fc93-162">To determine if the installation is local, the WMI provider evaluates the DatabaseServerName property against the following list of values.</span></span> <span data-ttu-id="3fc93-163">如果找到相符項目，表示資料庫位於本機。</span><span class="sxs-lookup"><span data-stu-id="3fc93-163">If a match is found, the database is local.</span></span> <span data-ttu-id="3fc93-164">否則，就表示資料庫位於遠端。</span><span class="sxs-lookup"><span data-stu-id="3fc93-164">Otherwise, it is remote.</span></span> <span data-ttu-id="3fc93-165">此比較不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3fc93-165">The comparison is case-insensitive.</span></span>  
  
|<span data-ttu-id="3fc93-166">DatabaseServerName 的值</span><span class="sxs-lookup"><span data-stu-id="3fc93-166">Value of DatabaseServerName</span></span>|<span data-ttu-id="3fc93-167">範例</span><span class="sxs-lookup"><span data-stu-id="3fc93-167">Example</span></span>|  
|---------------------------------|-------------|  
|<span data-ttu-id="3fc93-168">"."</span><span class="sxs-lookup"><span data-stu-id="3fc93-168">"."</span></span>||  
|<span data-ttu-id="3fc93-169">"(local)"</span><span class="sxs-lookup"><span data-stu-id="3fc93-169">"(local)"</span></span>||  
|<span data-ttu-id="3fc93-170">"LOCAL"</span><span class="sxs-lookup"><span data-stu-id="3fc93-170">"LOCAL"</span></span>||  
|<span data-ttu-id="3fc93-171">localhost</span><span class="sxs-lookup"><span data-stu-id="3fc93-171">localhost</span></span>||  
|\<Machinename>|<span data-ttu-id="3fc93-172">testlab14</span><span class="sxs-lookup"><span data-stu-id="3fc93-172">testlab14</span></span>|  
|\<MachineFQDN>|<span data-ttu-id="3fc93-173">example.redmond.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="3fc93-173">example.redmond.microsoft.com</span></span>|  
|\<IPAddress>|<span data-ttu-id="3fc93-174">180.012.345,678</span><span class="sxs-lookup"><span data-stu-id="3fc93-174">180.012.345,678</span></span>|  
  
 <span data-ttu-id="3fc93-175">當*IsWindowsUser*設定為時 `true` ，WMI 提供者會呼叫 LookupAccountName 來取得帳戶的 SID，然後呼叫 LookupAccountSID 以取得要放入腳本的名稱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3fc93-175">When *IsWindowsUser* is set to `true`, the WMI provider calls LookupAccountName to get the SID for the account and then calls LookupAccountSID to get the name to put in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] script.</span></span> <span data-ttu-id="3fc93-176">這樣可確保所使用的帳戶名稱會通過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證。</span><span class="sxs-lookup"><span data-stu-id="3fc93-176">This ensures that the account name used will pass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] validation.</span></span>  
  
 <span data-ttu-id="3fc93-177">當*IsWindowsUser*設定為時 `false` ，產生的腳本會授與報表伺服器資料庫、報表伺服器暫存資料庫和 MSDB 資料庫上的**RSExec**角色。</span><span class="sxs-lookup"><span data-stu-id="3fc93-177">When *IsWindowsUser* is set to `false`, the generated script grants the **RSExec** role on the report server database, the report server temporary database, and the MSDB database.</span></span>  
  
 <span data-ttu-id="3fc93-178">當*IsWindowsUser*設定為時 `false` ，SQL Server 使用者必須已經存在於中， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 腳本才能順利執行。</span><span class="sxs-lookup"><span data-stu-id="3fc93-178">When *IsWindowsUser* is set to `false`, the SQL Server user must already exist on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the script to run successfully.</span></span>  
  
 <span data-ttu-id="3fc93-179">如果報表伺服器尚未指定報表伺服器資料庫，呼叫 GrantRightsToDatabaseUser 就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="3fc93-179">If the report server does not have a report server database specified, calling GrantRightsToDatabaseUser returns an error.</span></span>  
  
 <span data-ttu-id="3fc93-180">產生的指令碼支援 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 和 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3fc93-180">The generated script supports [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005, and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fc93-181">需求</span><span class="sxs-lookup"><span data-stu-id="3fc93-181">Requirements</span></span>  
 <span data-ttu-id="3fc93-182">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fc93-182">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fc93-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fc93-183">See Also</span></span>  
 [<span data-ttu-id="3fc93-184">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="3fc93-184">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
