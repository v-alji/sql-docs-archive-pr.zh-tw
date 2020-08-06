---
title: 用來建立執行個體的 SQL Server 連線 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 81d0e7e2-d8f0-4bd9-9565-218ce996f28e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cdff17b763257c2a3280981c1f5c16040cc61413
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592814"
---
# <a name="sql-server-connection-for-instance-creation"></a><span data-ttu-id="ffdf5-102">用來建立執行個體的 SQL Server 連接</span><span class="sxs-lookup"><span data-stu-id="ffdf5-102">SQL Server Connection for Instance Creation</span></span>
  <span data-ttu-id="ffdf5-103">建立 Oracle CDC 執行個體時的其中一個首要步驟就是在目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上建立 CDC 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ffdf5-103">One of the first steps when creating an Oracle CDC Instance is the creation of a CDC database on the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="ffdf5-104">這個 CDC 資料庫會啟用 SQL Server CDC，而這樣的啟用需要屬於 `sysadmin` 固定伺服器角色成員的登入。</span><span class="sxs-lookup"><span data-stu-id="ffdf5-104">This CDC database is enabled for SQL Server CDC and this enablement requires a login that is a member of the `sysadmin` fixed-server role.</span></span>  
  
 <span data-ttu-id="ffdf5-105">如果啟動 [建立 Oracle CDC 執行個體精靈]  的使用者不是 `sysadmin` 固定伺服器角色的成員，便會開啟 [連接到 SQL Server]  對話方塊，並要求 `sysadmin` 角色成員的認證，才能執行「為 SQL Server CDC 啟用資料庫」工作。</span><span class="sxs-lookup"><span data-stu-id="ffdf5-105">When a user that starts the **Create an Oracle CDC Instance** wizard is not a member of the `sysadmin` fixed-server role, the **Connect to SQL Server** dialog box opens and requests the credentials for a member of the `sysadmin` role to carry out the Enable the database for SQL Server CDC task.</span></span> <span data-ttu-id="ffdf5-106">當建立 CDC 資料庫時，將會捨棄 `sysadmin` 登入，而且會使用之前進入 Oracle 設計工具主控台時所使用的原始 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入繼續工作。</span><span class="sxs-lookup"><span data-stu-id="ffdf5-106">When the CDC database is created, the `sysadmin` login is discarded and work resumes with the original [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used when the Oracle Designer Console was entered.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="ffdf5-107">工作清單</span><span class="sxs-lookup"><span data-stu-id="ffdf5-107">Task List</span></span>  
 <span data-ttu-id="ffdf5-108">在 [連接到 SQL Server]  對話方塊中輸入以下資訊。</span><span class="sxs-lookup"><span data-stu-id="ffdf5-108">Enter the following information in the **Connect to SQL Server** dialog box.</span></span>  
  
 <span data-ttu-id="ffdf5-109">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="ffdf5-109">**Server Name**</span></span>  
 <span data-ttu-id="ffdf5-110">輸入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所在的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="ffdf5-110">Type the name of the server where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is located.</span></span>  
  
 <span data-ttu-id="ffdf5-111">**驗證**</span><span class="sxs-lookup"><span data-stu-id="ffdf5-111">**Authentication**</span></span>  
 <span data-ttu-id="ffdf5-112">選取下列其中一個：</span><span class="sxs-lookup"><span data-stu-id="ffdf5-112">Select one of the following:</span></span>  
  
-   <span data-ttu-id="ffdf5-113">**Windows 驗證**</span><span class="sxs-lookup"><span data-stu-id="ffdf5-113">**Windows Authentication**</span></span>  
  
-   <span data-ttu-id="ffdf5-114">**SQL Server 驗證**：如果您選取這個選項，必須針對您所連接之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的使用者輸入**登入**和**密碼**。</span><span class="sxs-lookup"><span data-stu-id="ffdf5-114">**SQL Server Authentication**: If you select this option, you must type the **Login** and **Password** for the user in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connecting to.</span></span>  
  
 <span data-ttu-id="ffdf5-115">此登入擁有的資料庫角色必須允許存取 MSXCDCDB 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ffdf5-115">The login must have a database role that allows access to the MSXCDCDB database.</span></span> <span data-ttu-id="ffdf5-116">建議最好讓此登入也能存取正在使用的其他任何資料庫，否則使用者將無法檢視這些資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="ffdf5-116">It is recommended that the login also have access to any additional databases being used or the user will not be able to view the data in those databases.</span></span>  
  
 <span data-ttu-id="ffdf5-117">**選項**</span><span class="sxs-lookup"><span data-stu-id="ffdf5-117">**Options**</span></span>  
 <span data-ttu-id="ffdf5-118">按一下箭頭即可檢視要設定的可用選項。</span><span class="sxs-lookup"><span data-stu-id="ffdf5-118">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="ffdf5-119">您可以選擇保留這些選項的預設值。</span><span class="sxs-lookup"><span data-stu-id="ffdf5-119">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="ffdf5-120">可用的選項如下：</span><span class="sxs-lookup"><span data-stu-id="ffdf5-120">The available options are:</span></span>  
  
-   <span data-ttu-id="ffdf5-121">**連接逾時**：輸入 Oracle CDC 服務在逾時之前等候連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的時間 (以秒數為單位)。預設值為 **15**。</span><span class="sxs-lookup"><span data-stu-id="ffdf5-121">**Connection Timeout**: Type the time (in seconds) that the CDC Service for Oracle waits for a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before timing out. The default value is **15**.</span></span>  
  
-   <span data-ttu-id="ffdf5-122">**執行逾時**：輸入 Oracle CDC Windows 服務在逾時之前，等候執行命令的時間 (以秒數為單位)。預設值是 **30**。</span><span class="sxs-lookup"><span data-stu-id="ffdf5-122">**Execution Timeout**: Type the time (in seconds) that the Oracle CDC Windows Service waits for a command to execute before timing out. The default value is **30**.</span></span>  
  
-   <span data-ttu-id="ffdf5-123">**加密連接**：針對 Oracle CDC 服務與使用加密連線之目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之間的通訊選取 [加密連線]  。</span><span class="sxs-lookup"><span data-stu-id="ffdf5-123">**Encrypt Connection**: Select **Encrypt Connection** for communication between the Oracle CDC Service and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using an encrypted connection.</span></span>  
  
-   <span data-ttu-id="ffdf5-124">**進階**：按一下 [進階]  ，並在必要時，於 [進階連接屬性] 對話方塊中輸入其他任何連接屬性。</span><span class="sxs-lookup"><span data-stu-id="ffdf5-124">**Advanced**: Click **Advanced** and type any additional connection properties into the Advanced Connection Properties dialog box, if necessary.</span></span>  
  
     <span data-ttu-id="ffdf5-125">如需 [進階連接屬性] 對話方塊的資訊，請參閱 [進階連接屬性](advanced-connection-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="ffdf5-125">For information about the Advanced Connection Properties dialog box, see [Advanced Connection Properties](advanced-connection-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffdf5-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffdf5-126">See Also</span></span>  
 <span data-ttu-id="ffdf5-127">[建立 SQL Server 變更資料庫](create-the-sql-server-change-database.md) </span><span class="sxs-lookup"><span data-stu-id="ffdf5-127">[Create the SQL Server Change Database](create-the-sql-server-change-database.md) </span></span>  
 [<span data-ttu-id="ffdf5-128">SQL Server 連接所需的 CDC 設計工具權限</span><span class="sxs-lookup"><span data-stu-id="ffdf5-128">SQL Server Connection Required Permissions for the CDC Designer</span></span>](sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
