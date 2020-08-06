---
title: Attunity 適用於 Oracle 的異動資料擷取服務的使用者角色 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: be0ec384-e03b-4483-96ca-02b289804d6a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e694da0cfd8645fe594b049b6dc2394b55d1bb55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704337"
---
# <a name="user-roles-for-change-data-capture-service-for-oracle-by-attunity"></a><span data-ttu-id="47bfe-102">Attunity Oracle Change Data Capture 服務的使用者角色</span><span class="sxs-lookup"><span data-stu-id="47bfe-102">User Roles for Change Data Capture Service for Oracle by Attunity</span></span>
  <span data-ttu-id="47bfe-103">本節描述 Attunity Oracle Change Data Capture (CDC) 服務的使用者角色。</span><span class="sxs-lookup"><span data-stu-id="47bfe-103">This section describes the user roles for the Change Data Capture Service for Oracle by Attunity.</span></span> <span data-ttu-id="47bfe-104">描述的角色包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫角色、Windows 角色或 Oracle 資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="47bfe-104">The roles described are [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database roles, Windows roles, or Oracle database roles.</span></span>  
  
## <a name="windows-user-roles"></a><span data-ttu-id="47bfe-105">Windows 使用者角色</span><span class="sxs-lookup"><span data-stu-id="47bfe-105">Windows User Roles</span></span>  
 <span data-ttu-id="47bfe-106">以下描述 Oracle CDC 服務使用的 Windows 使用者角色。</span><span class="sxs-lookup"><span data-stu-id="47bfe-106">The following describes the Windows user roles used by the Oracle CDC Service.</span></span>  
  
### <a name="computer-administrator-oracle-cdc-service"></a><span data-ttu-id="47bfe-107">電腦管理員：Oracle CDC 服務</span><span class="sxs-lookup"><span data-stu-id="47bfe-107">Computer Administrator: Oracle CDC Service</span></span>  
 <span data-ttu-id="47bfe-108">電腦管理員是負責建立和維護電腦上 CDC 服務的 Windows 使用者。</span><span class="sxs-lookup"><span data-stu-id="47bfe-108">The computer administrator is a Windows user responsible for creating and maintaining the CDC Service on the computer.</span></span> <span data-ttu-id="47bfe-109">這個使用者必須屬於本機電腦管理員的群組。</span><span class="sxs-lookup"><span data-stu-id="47bfe-109">This user must belong to the group of local machine administrators.</span></span>  
  
 <span data-ttu-id="47bfe-110">Oracle CDC 服務電腦管理員所執行的工作包括：</span><span class="sxs-lookup"><span data-stu-id="47bfe-110">The tasks performed by the Oracle CDC Service Computer Administrator include:</span></span>  
  
-   <span data-ttu-id="47bfe-111">安裝 Oracle CDC 服務軟體</span><span class="sxs-lookup"><span data-stu-id="47bfe-111">Installing the CDC Service for Oracle software</span></span>  
  
-   <span data-ttu-id="47bfe-112">建立 Oracle CDC Windows 服務</span><span class="sxs-lookup"><span data-stu-id="47bfe-112">Creating an Oracle CDC Windows service</span></span>  
  
-   <span data-ttu-id="47bfe-113">設定與目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的 CDC 服務連接 (連接字串和認證)</span><span class="sxs-lookup"><span data-stu-id="47bfe-113">Setting up the CDC Service connection to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (connection string and credentials)</span></span>  
  
-   <span data-ttu-id="47bfe-114">確定 Oracle 記錄採礦認證可透過 CDC 服務主要密碼來保障安全</span><span class="sxs-lookup"><span data-stu-id="47bfe-114">Ensuring that the CDC Service Master Password with which Oracle log mining credentials are protected</span></span>  
  
-   <span data-ttu-id="47bfe-115">刪除 CDC 服務 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="47bfe-115">Deleting a CDC Service Windows service</span></span>  
  
-   <span data-ttu-id="47bfe-116">解除安裝 Oracle CDC 服務軟體</span><span class="sxs-lookup"><span data-stu-id="47bfe-116">Uninstalling the CDC Service for Oracle software</span></span>  
  
-   <span data-ttu-id="47bfe-117">維護 Oracle CDC 服務軟體 (例如，安裝更新)</span><span class="sxs-lookup"><span data-stu-id="47bfe-117">Maintaining the CDC Service for Oracle software (for example, installing updates)</span></span>  
  
-   <span data-ttu-id="47bfe-118">啟動和停止 CDC 服務 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="47bfe-118">Starting and stopping a CDC Service Windows service</span></span>  
  
 <span data-ttu-id="47bfe-119">當使用高可用性組態 (例如 Microsoft 容錯移轉叢集) 時，電腦管理員必須具備額外的責任和權限，例如：</span><span class="sxs-lookup"><span data-stu-id="47bfe-119">When working with high-availability configurations, such as Microsoft failover clusters, the computer administrator must have additional responsibilities and permissions such as:</span></span>  
  
-   <span data-ttu-id="47bfe-120">在所有叢集節點上安裝和維護 Oracle CDC 服務軟體。</span><span class="sxs-lookup"><span data-stu-id="47bfe-120">Installation and maintenance of the CDC Service for Oracle software on all cluster nodes.</span></span>  
  
-   <span data-ttu-id="47bfe-121">在各個叢集節點上定義 CDC 服務 Windows 服務的一般叢集服務資源。</span><span class="sxs-lookup"><span data-stu-id="47bfe-121">Defining generic cluster service resources for the CDC Service' Windows service on the various cluster nodes.</span></span>  
  
-   <span data-ttu-id="47bfe-122">當做授權的電腦管理員，負責管理 Oracle CDC 服務安裝所在的電腦。</span><span class="sxs-lookup"><span data-stu-id="47bfe-122">Acting as the computer administrator authorized as an administrator on the computer where the CDC Service for Oracle is installed.</span></span> <span data-ttu-id="47bfe-123">這個人會安裝 Oracle CDC 服務，並使用 CDC 服務組態主控台在本機電腦上設定 Oracle CDC 服務。</span><span class="sxs-lookup"><span data-stu-id="47bfe-123">This person installs the CDC Service for Oracle and uses the CDC Service Configuration Console to configure a CDC Service for Oracle on a local computer.</span></span>  
  
### <a name="service-account-oracle-cdc-service"></a><span data-ttu-id="47bfe-124">服務帳戶：Oracle CDC 服務</span><span class="sxs-lookup"><span data-stu-id="47bfe-124">Service Account: Oracle CDC Service</span></span>  
 <span data-ttu-id="47bfe-125">這個 Oracle CDC 服務 Windows 服務帳戶是用於執行 Oracle CDC 服務的 Windows 帳戶 (服務帳戶)。</span><span class="sxs-lookup"><span data-stu-id="47bfe-125">This is Oracle CDC Service Windows Service Account is a Windows account used for running the Oracle CDC Service (the Service Account).</span></span>  
  
 <span data-ttu-id="47bfe-126">此服務帳戶的唯一必要權限是要能夠使用 Oracle 用戶端和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 提供者。</span><span class="sxs-lookup"><span data-stu-id="47bfe-126">The only required privilege necessary for the service account is to be able to use the Oracle client and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native client ODBC provider.</span></span> <span data-ttu-id="47bfe-127">除非特定提供者需要，否則這個帳戶不需要存取檔案 (例如，如果 Oracle 用戶端連接字串參考 **tnsnames.ora** 檔案中的 Oracle 資料庫執行個體，則該檔案必須可供服務帳戶讀取)。</span><span class="sxs-lookup"><span data-stu-id="47bfe-127">This account does not need to access files unless required by specific providers (for example, if the Oracle client connection string references Oracle database instances in a **tnsnames.ora** file, then that file must be read-accessible to the service account).</span></span>  
  
 <span data-ttu-id="47bfe-128">當您在 Windows Vista 或 Windows Server 2008 上建立 Oracle CDC 服務時，預設服務帳戶為 NETWORK SERVICE 帳戶。</span><span class="sxs-lookup"><span data-stu-id="47bfe-128">When creating an Oracle CDC Service on Windows Vista or Windows Server 2008, the default service account is the NETWORK SERVICE account.</span></span>  
  
 <span data-ttu-id="47bfe-129">在 Windows 7、Windows Server 2008 R2 及更新版本上，預設服務帳戶為 NT Service\\<服務名稱>。</span><span class="sxs-lookup"><span data-stu-id="47bfe-129">On Windows 7, Windows Server 2008 R2 and later, the default service account is NT Service\\<service-name>.</span></span>  
  
 <span data-ttu-id="47bfe-130">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在另一部電腦上執行或者為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 叢集執行個體，而且此服務需要使用 Windows 驗證連接到目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，此服務帳戶應該是網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="47bfe-130">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs on another machine or is a clustered [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance and there the service needs to connect to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Windows authentication, then the service account should be a domain account.</span></span>  
  
## <a name="sql-server-user-roles"></a><span data-ttu-id="47bfe-131">SQL Server 使用者角色</span><span class="sxs-lookup"><span data-stu-id="47bfe-131">SQL Server User Roles</span></span>  
 <span data-ttu-id="47bfe-132">以下描述 Oracle CDC 服務使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者角色。</span><span class="sxs-lookup"><span data-stu-id="47bfe-132">The following describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user roles used by the Oracle CDC Service.</span></span>  
  
### <a name="oracle-cdc-service-administrator"></a><span data-ttu-id="47bfe-133">Oracle CDC 服務管理員</span><span class="sxs-lookup"><span data-stu-id="47bfe-133">Oracle CDC Service Administrator</span></span>  
 <span data-ttu-id="47bfe-134">CDC 服務管理員是可完全控制目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上之 Oracle CDC 服務成品的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者。</span><span class="sxs-lookup"><span data-stu-id="47bfe-134">The CDC Service Administrator is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user with full control over the Oracle CDC Service artifacts in the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="47bfe-135">CDC 服務管理員會使用 Oracle CDC 設計工具主控台來設計 Oracle CDC 執行個體。</span><span class="sxs-lookup"><span data-stu-id="47bfe-135">The CDC Service Administrator uses the Oracle CDC Designer Console to design Oracle CDC Instances.</span></span>  
  
 <span data-ttu-id="47bfe-136">CDC 服務管理員應該被授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定伺服器角色 **public** 和 **dbcreator**。</span><span class="sxs-lookup"><span data-stu-id="47bfe-136">The CDC Service Administrator should be granted the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fixed server roles **public** and **dbcreator**.</span></span>  
  
 <span data-ttu-id="47bfe-137">CDC 服務管理員所執行的工作包括：</span><span class="sxs-lookup"><span data-stu-id="47bfe-137">The tasks performed by the CDC Service Administrator include:</span></span>  
  
-   <span data-ttu-id="47bfe-138">準備 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體來主控 Oracle CDC 執行個體 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫)。</span><span class="sxs-lookup"><span data-stu-id="47bfe-138">Preparing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to host Oracle CDC Instances (which are [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases).</span></span> <span data-ttu-id="47bfe-139">在此工作中，將會於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中建立稱為 MSXDBCDC 的特殊資料庫。</span><span class="sxs-lookup"><span data-stu-id="47bfe-139">In this task, a special database called MSXDBCDC is created in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="47bfe-140">建立 Oracle CDC 執行個體 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="47bfe-140">Creating an Oracle CDC Instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="47bfe-141">工作包括針對 CDC 啟用新建立的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫，這需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員 (**sysadmin**)。</span><span class="sxs-lookup"><span data-stu-id="47bfe-141">Task includes enabling the newly created [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database for CDC, which requires a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator (**sysadmin**).</span></span>  
  
-   <span data-ttu-id="47bfe-142">設計 Oracle CDC 執行個體。</span><span class="sxs-lookup"><span data-stu-id="47bfe-142">Designing an Oracle CDC Instance.</span></span> <span data-ttu-id="47bfe-143">此工作包括提供有關來源 Oracle 資料庫和擷取資料表的資訊，這需要 Oracle 資料庫管理員。</span><span class="sxs-lookup"><span data-stu-id="47bfe-143">This task includes providing information about the source Oracle database and captured tables, which requires an Oracle database administrator.</span></span>  
  
-   <span data-ttu-id="47bfe-144">維護一段時間的 Oracle CDC 執行個體，其中包括加入/移除擷取執行個體和更新組態。</span><span class="sxs-lookup"><span data-stu-id="47bfe-144">Maintaining the Oracle CDC Instance over time, which includes adding/removing capture instances and updating configuration.</span></span>  
  
-   <span data-ttu-id="47bfe-145">啟用或停用 Oracle CDC 執行個體。</span><span class="sxs-lookup"><span data-stu-id="47bfe-145">Enabling or disabling an Oracle CDC Instance.</span></span>  
  
-   <span data-ttu-id="47bfe-146">監視 Oracle CDC 執行個體的狀態。</span><span class="sxs-lookup"><span data-stu-id="47bfe-146">Monitoring the state of an Oracle CDC Instance.</span></span>  
  
-   <span data-ttu-id="47bfe-147">針對影響 Oracle CDC 執行個體的問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="47bfe-147">Troubleshooting issues that affect the Oracle CDC Instance.</span></span>  
  
 <span data-ttu-id="47bfe-148">CDC 服務管理員至少一開始會在與 Oracle CDC 執行個體相關聯之 **CDC 資料庫的** db_owner [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定資料庫角色中。</span><span class="sxs-lookup"><span data-stu-id="47bfe-148">The CDC Service Administrator is, at least initially, in the **db_owner** fixed database role for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC database associated with the Oracle CDC Instance.</span></span> <span data-ttu-id="47bfe-149">這會提供 CDC 服務管理員對於 CDC 資料庫中儲存之變更資料的存取權。</span><span class="sxs-lookup"><span data-stu-id="47bfe-149">This gives the CDC Service Administrator access to the change data stored in the CDC database.</span></span> <span data-ttu-id="47bfe-150">一旦建立，CDC 資料庫的 **db_owner** 角色就可以指派給不同的使用者，該使用者可以執行上面列出的所有工作，除了準備 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體和建立另一個 Oracle CDC 執行個體以外。</span><span class="sxs-lookup"><span data-stu-id="47bfe-150">Once created, the **db_owner** role of the CDC database can be assigned to a different user who can carry out all of the tasks listed above except for preparing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance and creating another Oracle CDC Instance).</span></span>  
  
 <span data-ttu-id="47bfe-151">CDC 服務管理員不需要知道建立 Oracle CDC Windows 服務所指定的主要密碼。</span><span class="sxs-lookup"><span data-stu-id="47bfe-151">The CDC Service Administrator does not need to know the master password specified with the creation of the Oracle CDC Windows service.</span></span>  
  
### <a name="system-administrator"></a><span data-ttu-id="47bfe-152">系統管理員</span><span class="sxs-lookup"><span data-stu-id="47bfe-152">System Administrator</span></span>  
 <span data-ttu-id="47bfe-153">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者，而且應該將與 Oracle CDC 服務相關聯之 **執行個體的** 系統管理員 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定伺服器角色授與給他。</span><span class="sxs-lookup"><span data-stu-id="47bfe-153">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user and should be granted the fixed server **sysadmin** role on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance associated with the Oracle CDC Service(s).</span></span>  
  
 <span data-ttu-id="47bfe-154">只有一個 Oracle CDC 特有的工作需要由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員執行，也就是針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC 的 Oracle CDC 執行個體啟用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="47bfe-154">There is only one Oracle CDC specific task that carried out with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] System Administrator and that is to enable the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database for an Oracle CDC Instance for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC.</span></span> <span data-ttu-id="47bfe-155">在建立新的 Oracle CDC 執行個體時，便會使用 Oracle CDC 設計工具主控台執行此工作。</span><span class="sxs-lookup"><span data-stu-id="47bfe-155">This task is performed using the Oracle CDC Designer console when creating a new Oracle CDC Instance.</span></span>  
  
### <a name="oracle-cdc-service-user"></a><span data-ttu-id="47bfe-156">Oracle CDC 服務使用者</span><span class="sxs-lookup"><span data-stu-id="47bfe-156">Oracle CDC Service User</span></span>  
 <span data-ttu-id="47bfe-157">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC 服務使用者是由 Oracle CDC 服務所使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入，可針對 MSXDBCDC 以及此服務所處理的所有 Oracle CDC 執行個體 (CDC 資料庫) 來執行其工作。</span><span class="sxs-lookup"><span data-stu-id="47bfe-157">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Service user is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login which is used by the Oracle CDC Service to perform its work against the MSXDBCDC and all of the Oracle CDC Instances (CDC databases) handled by this service.</span></span>  
  
 <span data-ttu-id="47bfe-158">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC 服務使用者應該被授與以下權限：</span><span class="sxs-lookup"><span data-stu-id="47bfe-158">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Service user should be granted the following:</span></span>  
  
-   <span data-ttu-id="47bfe-159">伺服器所處理之所有 CDC 資料庫的固定資料庫角色 **db_dlladmin**、 **db_datareader**和 **db_datawriter** 的成員。</span><span class="sxs-lookup"><span data-stu-id="47bfe-159">Member of the fixed database roles **db_dlladmin**, **db_datareader**, and **db_datawriter** for all CDC databases handled by the server.</span></span>  
  
-   <span data-ttu-id="47bfe-160">MSXDBCDC 資料庫之固定資料庫角色 **db_datareader** 和 **db_datawriter** 的成員。</span><span class="sxs-lookup"><span data-stu-id="47bfe-160">Member of the fixed database roles **db_datareader** and **db_datawriter** for the MSXDBCDC database.</span></span>  
  
 <span data-ttu-id="47bfe-161">因為 Oracle CDC 服務會使用單一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入處理所有 CDC 資料庫和 MSXDBCDC 資料庫，所以應該在所有的這些資料庫中對應這個登入。</span><span class="sxs-lookup"><span data-stu-id="47bfe-161">Because the Oracle CDC Service uses a single [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to work with all CDC databases and the MSXDBCDC database, this login should be mapped in all of these databases.</span></span>  
  
### <a name="oracle-cdc-change-consumer"></a><span data-ttu-id="47bfe-162">Oracle CDC 變更取用者</span><span class="sxs-lookup"><span data-stu-id="47bfe-162">Oracle CDC Change Consumer</span></span>  
 <span data-ttu-id="47bfe-163">Oracle CDC 變更取用者是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者，他會取用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC 執行個體資料庫中 CDC 資料表內所儲存的變更。</span><span class="sxs-lookup"><span data-stu-id="47bfe-163">The Oracle CDC Change Consumer is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user that consumes changes stored in the CDC tables in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Instance database.</span></span>  
  
 <span data-ttu-id="47bfe-164">這個使用者會決定透過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC 基礎結構所產生的 CDC 功能來存取每一個 CDC 資料表所需的使用者角色。</span><span class="sxs-lookup"><span data-stu-id="47bfe-164">This user determines the user role that is required for accessing each of the CDC tables through the CDC functions generated by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC infrastructure.</span></span> <span data-ttu-id="47bfe-165">如果在指定擷取執行個體時並未指定任何使用者角色，則變更的存取只限於 CDC 資料庫的 **db_owner** 固定資料庫角色成員。</span><span class="sxs-lookup"><span data-stu-id="47bfe-165">If no user role is specified when a capture instance is specified, access to the changes is limited to the member of the **db_owner** fixed database role of the CDC database.</span></span>  
  
## <a name="oracle-user-roles"></a><span data-ttu-id="47bfe-166">Oracle 使用者角色</span><span class="sxs-lookup"><span data-stu-id="47bfe-166">Oracle User Roles</span></span>  
 <span data-ttu-id="47bfe-167">以下描述 Oracle CDC 服務使用的 Oracle 使用者角色。</span><span class="sxs-lookup"><span data-stu-id="47bfe-167">The following describes the Oracle user roles used by the Oracle CDC Service.</span></span>  
  
### <a name="database-administrator-dba"></a><span data-ttu-id="47bfe-168">資料庫管理員 (DBA)</span><span class="sxs-lookup"><span data-stu-id="47bfe-168">Database Administrator (DBA)</span></span>  
 <span data-ttu-id="47bfe-169">Oracle 資料庫管理員 (DBA) 是 Oracle 資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="47bfe-169">The Oracle database administrator (DBA) is an Oracle database user.</span></span> <span data-ttu-id="47bfe-170">Oracle DBA 所執行的工作包括：</span><span class="sxs-lookup"><span data-stu-id="47bfe-170">The tasks performed by the Oracle DBA include:</span></span>  
  
-   <span data-ttu-id="47bfe-171">設定來源 Oracle 資料庫在 ARCHIVELOG 模式工作。</span><span class="sxs-lookup"><span data-stu-id="47bfe-171">Setting the source Oracle database to work in ARCHIVELOG mode.</span></span>  
  
-   <span data-ttu-id="47bfe-172">設定擁有必要權限的記錄採礦使用者。</span><span class="sxs-lookup"><span data-stu-id="47bfe-172">Setting up a log mining user with the required permissions.</span></span>  
  
-   <span data-ttu-id="47bfe-173">為擷取的資料表設定補充記錄。</span><span class="sxs-lookup"><span data-stu-id="47bfe-173">Setting supplemental logging for captured tables.</span></span>  
  
-   <span data-ttu-id="47bfe-174">幫助還原不再可用的封存交易記錄檔，以便進行處理。</span><span class="sxs-lookup"><span data-stu-id="47bfe-174">Helping to restore archived transaction log files no longer available so they can be processed.</span></span>  
  
 <span data-ttu-id="47bfe-175">Oracle 資料庫管理員可以取得需要執行的 Oracle SQL 指令碼，以便可以在執行之前加以評估。</span><span class="sxs-lookup"><span data-stu-id="47bfe-175">The Oracle database administrator can get Oracle SQL scripts that need to run so they can be evaluated before running them.</span></span> <span data-ttu-id="47bfe-176">Oracle 資料庫管理員還可以直接從 Oracle CDC 設計工具主控台執行 Oracle SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="47bfe-176">The Oracle database administrator can also directly run Oracle SQL scripts from the Oracle CDC Designer console.</span></span>  
  
 <span data-ttu-id="47bfe-177">如果 Oracle 資料庫管理員選擇使用 Oracle CDC 設計工具主控台，則不會保存管理員的認證，除了使用這些認證的內容 (對話) 以外。</span><span class="sxs-lookup"><span data-stu-id="47bfe-177">If the Oracle database administrator chooses to use the Oracle CDC Designer console, administrator's credentials are not kept except for the context (dialog) in which they were used.</span></span>  
  
 <span data-ttu-id="47bfe-178">Oracle 資料庫管理員會與 Oracle CDC 服務管理員一起協調 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC 執行個體組態的工作。</span><span class="sxs-lookup"><span data-stu-id="47bfe-178">The Oracle database administrator works in coordination with the Oracle CDC Service administrator on the configuration of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Instances.</span></span>  
  
### <a name="log-mining-user"></a><span data-ttu-id="47bfe-179">記錄採礦使用者</span><span class="sxs-lookup"><span data-stu-id="47bfe-179">Log Mining User</span></span>  
 <span data-ttu-id="47bfe-180">Oracle 記錄採礦器使用者是特殊的 Oracle 資料庫使用者，他會被授與存取和處理 Oracle 交易記錄的必要權限。</span><span class="sxs-lookup"><span data-stu-id="47bfe-180">The Oracle Log Miner user is a special Oracle database user that is granted the required privileges for accessing and processing the Oracle transaction logs.</span></span>  
  
 <span data-ttu-id="47bfe-181">這個使用者的認證會使用非對稱金鑰加密儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC 執行個體資料庫中。</span><span class="sxs-lookup"><span data-stu-id="47bfe-181">The credentials for this user are stored in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Instance database using asymmetric key encryption.</span></span> <span data-ttu-id="47bfe-182">這些認證僅供 Oracle CDC 服務存取，而無法供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC 執行個體資料庫擁有者存取。</span><span class="sxs-lookup"><span data-stu-id="47bfe-182">They are accessible only to the Oracle CDC Service but not to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Instance database owner.</span></span>  
  
 <span data-ttu-id="47bfe-183">下列清單描述記錄採礦使用者應該被授與的必要權限：</span><span class="sxs-lookup"><span data-stu-id="47bfe-183">The following list describes the required privileges of the log mining user should be granted:</span></span>  
  
-   <span data-ttu-id="47bfe-184">SELECT on \<any-captured-table></span><span class="sxs-lookup"><span data-stu-id="47bfe-184">SELECT on \<any-captured-table></span></span>  
  
-   <span data-ttu-id="47bfe-185">SELECT ANY TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="47bfe-185">SELECT ANY TRANSACTION</span></span>  
  
-   <span data-ttu-id="47bfe-186">EXECUTE on DBMS_LOGMNR</span><span class="sxs-lookup"><span data-stu-id="47bfe-186">EXECUTE on DBMS_LOGMNR</span></span>  
  
-   <span data-ttu-id="47bfe-187">SELECT on V$LOGMNR_CONTENTS</span><span class="sxs-lookup"><span data-stu-id="47bfe-187">SELECT on V$LOGMNR_CONTENTS</span></span>  
  
-   <span data-ttu-id="47bfe-188">SELECT on V$ARCHIVED_LOG</span><span class="sxs-lookup"><span data-stu-id="47bfe-188">SELECT on V$ARCHIVED_LOG</span></span>  
  
-   <span data-ttu-id="47bfe-189">SELECT on V$LOG</span><span class="sxs-lookup"><span data-stu-id="47bfe-189">SELECT on V$LOG</span></span>  
  
-   <span data-ttu-id="47bfe-190">SELECT on V$LOGFILE</span><span class="sxs-lookup"><span data-stu-id="47bfe-190">SELECT on V$LOGFILE</span></span>  
  
-   <span data-ttu-id="47bfe-191">SELECT on V$DATABASE</span><span class="sxs-lookup"><span data-stu-id="47bfe-191">SELECT on V$DATABASE</span></span>  
  
-   <span data-ttu-id="47bfe-192">SELECT on V$THREAD</span><span class="sxs-lookup"><span data-stu-id="47bfe-192">SELECT on V$THREAD</span></span>  
  
-   <span data-ttu-id="47bfe-193">SELECT on V$PARAMETER</span><span class="sxs-lookup"><span data-stu-id="47bfe-193">SELECT on V$PARAMETER</span></span>  
  
-   <span data-ttu-id="47bfe-194">SELECT on DBA_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="47bfe-194">SELECT on DBA_REGISTRY</span></span>  
  
-   <span data-ttu-id="47bfe-195">SELECT on ALL_INDEXES</span><span class="sxs-lookup"><span data-stu-id="47bfe-195">SELECT on ALL_INDEXES</span></span>  
  
-   <span data-ttu-id="47bfe-196">SELECT on ALL_OBJECTS</span><span class="sxs-lookup"><span data-stu-id="47bfe-196">SELECT on ALL_OBJECTS</span></span>  
  
-   <span data-ttu-id="47bfe-197">SELECT on DBA_OBJECTS</span><span class="sxs-lookup"><span data-stu-id="47bfe-197">SELECT on DBA_OBJECTS</span></span>  
  
-   <span data-ttu-id="47bfe-198">SELECT on ALL_TABLES</span><span class="sxs-lookup"><span data-stu-id="47bfe-198">SELECT on ALL_TABLES</span></span>  
  
 <span data-ttu-id="47bfe-199">如果有任何權限不能授與給 V$xxx，則應該授與給 V $xxx。</span><span class="sxs-lookup"><span data-stu-id="47bfe-199">If any of these privileges cannot be granted to a V$xxx, then they should be granted to the V $xxx.</span></span>  
  
### <a name="schema-user"></a><span data-ttu-id="47bfe-200">結構描述使用者</span><span class="sxs-lookup"><span data-stu-id="47bfe-200">Schema User</span></span>  
 <span data-ttu-id="47bfe-201">Oracle 結構描述使用者是具有要擷取之 Oracle 資料表結構描述讀取存取權的 Oracle 使用者。</span><span class="sxs-lookup"><span data-stu-id="47bfe-201">The Oracle Schema User is an Oracle user with read access to the schema of the Oracle tables to be captured.</span></span> <span data-ttu-id="47bfe-202">當使用 Oracle CDC 設計工具主控台來擷取 Oracle 結構描述、要擷取的資料表以及其資料行、索引和索引鍵的清單時，便需要這個使用者。</span><span class="sxs-lookup"><span data-stu-id="47bfe-202">This user is necessary when working with the Oracle CDC Designer console to retrieve the list of Oracle schema, tables to be captured and their columns, indexes and keys.</span></span>  
  
 <span data-ttu-id="47bfe-203">絕對不會儲存這個使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="47bfe-203">The credentials for this user are never stored.</span></span> <span data-ttu-id="47bfe-204">每當需要這些認證時，CDC 設計工具主控台便會要求這些認證，而且在其餘 UI 工作階段會保存這些認證。</span><span class="sxs-lookup"><span data-stu-id="47bfe-204">They are requested by the CDC Designer console each time they are needed and they are kept for the rest of the UI sessions.</span></span>  
  
  
