---
title: SetDatabaseConnection 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetDatabaseConnection (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDatabaseConnection method
ms.assetid: c040aa78-92b8-41e4-9ae2-eff9fcdddc5b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b5c62777edd1fab2b0cb3babc13ab09f7bcf32a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706069"
---
# <a name="setdatabaseconnection-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="1d5d6-102">SetDatabaseConnection 方法 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="1d5d6-102">SetDatabaseConnection Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="1d5d6-103">設定特定報表伺服器資料庫的報表伺服器資料庫連接。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-103">Sets the report server database connection to a particular report server database.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d5d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="1d5d6-104">Syntax</span></span>  
  
```vb  
Public Sub SetDatabaseConnection(Server as String, _  
    DatabaseName as string, CredentialsType as Integer, _  
    Username as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void BackupEncryptionKey(string Server,   
    string DatabaseName, Int32 CredentialsType,   
    string UserName, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d5d6-105">參數</span><span class="sxs-lookup"><span data-stu-id="1d5d6-105">Parameters</span></span>  
 <span data-ttu-id="1d5d6-106">*Server*</span><span class="sxs-lookup"><span data-stu-id="1d5d6-106">*Server*</span></span>  
 <span data-ttu-id="1d5d6-107">用來主控報表伺服器資料庫之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-107">The name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is used to host the report server database.</span></span>  
  
 <span data-ttu-id="1d5d6-108">*DatabaseName*</span><span class="sxs-lookup"><span data-stu-id="1d5d6-108">*DatabaseName*</span></span>  
 <span data-ttu-id="1d5d6-109">報表伺服器資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-109">The name of the report server database.</span></span>  
  
 <span data-ttu-id="1d5d6-110">*CredentialsType*</span><span class="sxs-lookup"><span data-stu-id="1d5d6-110">*CredentialsType*</span></span>  
 <span data-ttu-id="1d5d6-111">要用於連接的認證類型。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-111">The type of credentials to use for the connection.</span></span> <span data-ttu-id="1d5d6-112">值可以是：</span><span class="sxs-lookup"><span data-stu-id="1d5d6-112">Values can be:</span></span>  
  
-   <span data-ttu-id="1d5d6-113">0 - Windows</span><span class="sxs-lookup"><span data-stu-id="1d5d6-113">0 - Windows</span></span>  
  
-   <span data-ttu-id="1d5d6-114">1 - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d5d6-114">1 - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="1d5d6-115">2 - Windows 服務</span><span class="sxs-lookup"><span data-stu-id="1d5d6-115">2 - Windows Service</span></span>  
  
 <span data-ttu-id="1d5d6-116">*UserName*</span><span class="sxs-lookup"><span data-stu-id="1d5d6-116">*UserName*</span></span>  
 <span data-ttu-id="1d5d6-117">用來連接至報表伺服器資料庫的帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-117">The account name used to connect to the report server database.</span></span>  
  
 <span data-ttu-id="1d5d6-118">*密碼*</span><span class="sxs-lookup"><span data-stu-id="1d5d6-118">*Password*</span></span>  
 <span data-ttu-id="1d5d6-119">用來連接至報表伺服器資料庫的密碼。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-119">The password used to connect to the report server database.</span></span>  
  
 <span data-ttu-id="1d5d6-120">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="1d5d6-120">*HRESULT*</span></span>  
 <span data-ttu-id="1d5d6-121">[out] 指出呼叫成功或失敗的值。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-121">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d5d6-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="1d5d6-122">Return Value</span></span>  
 <span data-ttu-id="1d5d6-123">傳回 *HRESULT* ，指出方法呼叫成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-123">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="1d5d6-124">值為 0 表示方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-124">A value of 0 indicates that the method call was successful.</span></span> <span data-ttu-id="1d5d6-125">非零值則表示已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-125">A non-zero value indicates that an error has occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d5d6-126">備註</span><span class="sxs-lookup"><span data-stu-id="1d5d6-126">Remarks</span></span>  
 <span data-ttu-id="1d5d6-127">當 *CredentialsType* 參數設為 0 時 (Windows)，即必須設定 *UserName* 和 *Password* 參數。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-127">When the *CredentialsType* parameter is set to 0 (Windows), the *UserName* and *Password* parameters must be set.</span></span> <span data-ttu-id="1d5d6-128">*UserName* 參數必須採用「網域\使用者名稱」格式，且此值必須代表有效的 Windows 登入。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-128">The *UserName* parameter must be in the form "domain\username", and the value must represent a valid Windows logon.</span></span>  
  
 <span data-ttu-id="1d5d6-129">當 *CredentialsType* 參數設為 1 時 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])，傳入 *UserName* 參數的值必須符合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入名稱的需求。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-129">When the *CredentialsType* parameter is set to 1 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), the value passed in the *UserName* parameter must conform to the requirements of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login name.</span></span>  
  
 <span data-ttu-id="1d5d6-130">當 *CredentialsType* 參數設為 2 時 (Windows 服務)，報表伺服器就會使用整合式安全性來連接至報表伺服器資料庫，並忽略 *UserName* 和 *Password* 參數。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-130">When the *CredentialsType* parameter is set to 2 (Windows Service), the report server uses integrated security to connect to the report server database and the *UserName* and *Password* parameters are ignored.</span></span> <span data-ttu-id="1d5d6-131">報表伺服器 Web 服務將會使用 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 帳戶或應用程式集區的帳戶和 Windows 服務帳戶來存取報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-131">The Reporting Server Web service will use either the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] account or an application pool's account and the Windows service account to access the report server database.</span></span>  
  
 <span data-ttu-id="1d5d6-132">SetDatabaseConnection 方法一經呼叫，就會在指定之報表伺服器的組態檔中加密並儲存認證和資料庫資訊。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-132">When called, the SetDatabaseConnection method encrypts and stores the credentials and database information in the configuration file for the specified report server.</span></span>  
  
 <span data-ttu-id="1d5d6-133">SetDatabaseConnection 方法不會檢查報表伺服器是否能夠使用指定的資料來連接至報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-133">The SetDatabaseConnection method does not check that the report server can connect to the report server database using the data specified.</span></span>  
  
 <span data-ttu-id="1d5d6-134">第一次設定時，ConnectionPoolSize 屬性是根據下列處理器設定的：ConnectionPoolSize = #Processors \* 75。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-134">When set for the first time, the ConnectionPoolSize property is set based on the following processors: ConnectionPoolSize = #Processors \* 75.</span></span>  
  
 <span data-ttu-id="1d5d6-135">SetDatabaseConnection 方法不會將權限授與指定的帳戶。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-135">The SetDatabaseConnection method does not grant permissions to the specified account(s).</span></span> <span data-ttu-id="1d5d6-136">您必須針對需要存取報表伺服器資料庫的每個帳戶呼叫 [GenerateDatabaseRightsScript](configurationsetting-method-generatedatabaserightsscript.md) 方法，並且執行產生的指令碼。</span><span class="sxs-lookup"><span data-stu-id="1d5d6-136">You must call the [GenerateDatabaseRightsScript](configurationsetting-method-generatedatabaserightsscript.md) method for each account that requires access to the report server database and run the resulting script.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d5d6-137">需求</span><span class="sxs-lookup"><span data-stu-id="1d5d6-137">Requirements</span></span>  
 <span data-ttu-id="1d5d6-138">**命名空間：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d5d6-138">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d5d6-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d5d6-139">See Also</span></span>  
 [<span data-ttu-id="1d5d6-140">MSReportServer_ConfigurationSetting 成員</span><span class="sxs-lookup"><span data-stu-id="1d5d6-140">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
