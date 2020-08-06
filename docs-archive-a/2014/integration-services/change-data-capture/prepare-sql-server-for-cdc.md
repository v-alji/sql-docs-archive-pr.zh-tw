---
title: 為 CDC 準備 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- prepSqlSrv
ms.assetid: 20b51dbf-a545-4234-87ae-4228268a0fb2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dafa29d9bdb0c27decb605398a6d1cfe383427e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592816"
---
# <a name="prepare-sql-server-for-cdc"></a><span data-ttu-id="fde66-102">為 CDC 準備 SQL Server</span><span class="sxs-lookup"><span data-stu-id="fde66-102">Prepare SQL Server for CDC</span></span>
  <span data-ttu-id="fde66-103">Oracle CDC 服務要求所有目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體都必須包含 MSXDBCDC 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fde66-103">The Oracle CDC service requires all target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances to contain the MSXDBCDC database.</span></span> <span data-ttu-id="fde66-104">您可在 CDC 服務組態主控台中使用「準備 SQL Server」動作來建立這個資料庫。</span><span class="sxs-lookup"><span data-stu-id="fde66-104">You create this database using the Prepare SQL Server action in the CDC Service Configuration Console.</span></span> <span data-ttu-id="fde66-105">這樣會建立特殊指令碼，可執行該指令碼來針對這個資料庫建立必要資料表、預存程序和其他必要成品。</span><span class="sxs-lookup"><span data-stu-id="fde66-105">This creates a special script that is run to create the required tables, stored procedures, and other required artifacts for this database.</span></span> <span data-ttu-id="fde66-106">這個工作只會針對每個目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體執行一次。</span><span class="sxs-lookup"><span data-stu-id="fde66-106">This task is done one time only for each target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="fde66-107">如需有關 MSXDBCDC 資料庫的詳細資訊，請參閱＜MSXDBCDC 資料庫＞。</span><span class="sxs-lookup"><span data-stu-id="fde66-107">For more information about the MSXDBCDC database, see The MSXDBCDC Database.</span></span>  
  
 <span data-ttu-id="fde66-108">在 CDC 服務組態主控台中，按一下 [Prepare SQL Server (準備 SQL Server)]  。</span><span class="sxs-lookup"><span data-stu-id="fde66-108">In the CDC Service Configuration Console, click **Prepare SQL Server**.</span></span> <span data-ttu-id="fde66-109">如果無法使用這個選項，請確定已在主控台的左窗格選取 [Local CDC Services (本機 CDC 服務)]  。</span><span class="sxs-lookup"><span data-stu-id="fde66-109">If this option is not available, make sure that **Local CDC Services** is selected in the left pane of the console.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fde66-110">選項。</span><span class="sxs-lookup"><span data-stu-id="fde66-110">Options</span></span>  
  
### <a name="server-name"></a><span data-ttu-id="fde66-111">伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="fde66-111">Server Name</span></span>  
 <span data-ttu-id="fde66-112">輸入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所在的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="fde66-112">Type the name of the server where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is located.</span></span>  
  
### <a name="authentication"></a><span data-ttu-id="fde66-113">驗證</span><span class="sxs-lookup"><span data-stu-id="fde66-113">Authentication</span></span>  
 <span data-ttu-id="fde66-114">選取下列其中一個：</span><span class="sxs-lookup"><span data-stu-id="fde66-114">Select one of the following:</span></span>  
  
-   <span data-ttu-id="fde66-115">**Windows 驗證**</span><span class="sxs-lookup"><span data-stu-id="fde66-115">**Windows Authentication**</span></span>  
  
-   <span data-ttu-id="fde66-116">**SQL Server 驗證**：如果您選取這個選項，必須針對您所連接之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的使用者輸入**使用者名稱**和**密碼**。</span><span class="sxs-lookup"><span data-stu-id="fde66-116">**SQL Server Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connecting to.</span></span>  
  
 <span data-ttu-id="fde66-117">若要針對 Oracle CDC 準備 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，登入必須擁有 MSXDBCDC 資料庫的寫入權限。</span><span class="sxs-lookup"><span data-stu-id="fde66-117">To prepare the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance for Oracle CDC, the login must have write permission to the MSXDBCDC database.</span></span> <span data-ttu-id="fde66-118">請輸入擁有 MSXDBCDC 資料庫寫入權限之登入的認證，例如 `sysasmin` 角色的成員。</span><span class="sxs-lookup"><span data-stu-id="fde66-118">Enter the credentials for a login that has write permission to the MSXDBCDC database, such as a member of the `sysasmin` role.</span></span>  
  
### <a name="options"></a><span data-ttu-id="fde66-119">選項。</span><span class="sxs-lookup"><span data-stu-id="fde66-119">Options</span></span>  
 <span data-ttu-id="fde66-120">按一下箭頭即可檢視要設定的可用選項。</span><span class="sxs-lookup"><span data-stu-id="fde66-120">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="fde66-121">您可以選擇保留這些選項的預設值。</span><span class="sxs-lookup"><span data-stu-id="fde66-121">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="fde66-122">可用的選項如下：</span><span class="sxs-lookup"><span data-stu-id="fde66-122">The available options are:</span></span>  
  
-   <span data-ttu-id="fde66-123">**連接逾時**：輸入 Oracle CDC 服務在逾時之前等候連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的時間 (以秒數為單位)。預設值為 **15**。</span><span class="sxs-lookup"><span data-stu-id="fde66-123">**Connection Timeout**: Type the time (in seconds) that the CDC Service for Oracle waits for a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before timing out. The default value is **15**.</span></span>  
  
-   <span data-ttu-id="fde66-124">**執行逾時**：輸入 Oracle CDC Windows 服務在逾時之前，等候執行命令的時間 (以秒數為單位)。預設值是 **30**。</span><span class="sxs-lookup"><span data-stu-id="fde66-124">**Execution Timeout**: Type the time (in seconds) that the Oracle CDC Windows Service waits for a command to execute before timing out. The default value is **30**.</span></span>  
  
-   <span data-ttu-id="fde66-125">**加密連接**：針對 Oracle CDC 服務與使用加密連線之目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之間的通訊選取 [加密連線]  。</span><span class="sxs-lookup"><span data-stu-id="fde66-125">**Encrypt Connection**: Select **Encrypt Connection** for communication between the Oracle CDC Service and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using an encrypted connection.</span></span>  
  
-   <span data-ttu-id="fde66-126">**進階**：必要時輸入其他任何連接屬性。</span><span class="sxs-lookup"><span data-stu-id="fde66-126">**Advanced**: Type any additional connection properties, if necessary.</span></span>  
  
### <a name="view-script"></a><span data-ttu-id="fde66-127">檢視指令碼</span><span class="sxs-lookup"><span data-stu-id="fde66-127">View Script</span></span>  
 <span data-ttu-id="fde66-128">按一下 [檢視指令碼]  ，檢視安裝指令碼的唯讀版本。</span><span class="sxs-lookup"><span data-stu-id="fde66-128">Click **View Script** to view a read-only version of the setup script.</span></span> <span data-ttu-id="fde66-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員可以將此指令碼複製到 SQL Server 管理主控台來進行編輯 (必要的話)。</span><span class="sxs-lookup"><span data-stu-id="fde66-129">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator can copy this script into the SQL Server Management Console to edit it, if necessary.</span></span> <span data-ttu-id="fde66-130">如需準備 SQL Server 指令碼的詳細資訊，請參閱 [為 Oracle CDC 檢視指令碼準備 SQL Server](prepare-sql-server-for-oracle-cdc-view-script.md)。</span><span class="sxs-lookup"><span data-stu-id="fde66-130">For more information about the Prepare SQL Server Script, see [Prepare SQL Server for Oracle CDC-View Script](prepare-sql-server-for-oracle-cdc-view-script.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde66-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fde66-131">See Also</span></span>  
 <span data-ttu-id="fde66-132">[如何使用 CDC 服務](work-with-cdc-services.md) </span><span class="sxs-lookup"><span data-stu-id="fde66-132">[How to Work with CDC Services](work-with-cdc-services.md) </span></span>  
 [<span data-ttu-id="fde66-133">如何準備 SQL Server 以使用 CDC</span><span class="sxs-lookup"><span data-stu-id="fde66-133">How to Prepare SQL Server for CDC</span></span>](prepare-sql-server-for-cdc.md)  
  
  
