---
title: 存取 CDC 設計工具主控台 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- accMsDes
ms.assetid: b168c64e-c1b5-42d4-a92a-84de1dd0324e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f4f6e4df0a514cb29e36bcd1270b2537dc3ba68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708561"
---
# <a name="access-the-cdc-designer-console"></a><span data-ttu-id="a4cea-102">存取 CDC 設計工具主控台</span><span class="sxs-lookup"><span data-stu-id="a4cea-102">Access the CDC Designer Console</span></span>
  <span data-ttu-id="a4cea-103">您可以從安裝 CDC 設計工具主控台的電腦來存取此主控台。</span><span class="sxs-lookup"><span data-stu-id="a4cea-103">You can access the CDC Designer Console from the computer where you installed the console.</span></span> <span data-ttu-id="a4cea-104">如需有關安裝的詳細資訊，請參閱＜安裝＞。</span><span class="sxs-lookup"><span data-stu-id="a4cea-104">For more information about installation, see Installation.</span></span>  
  
 <span data-ttu-id="a4cea-105">當您開啟 CDC 設計工具主控台時，隨即開啟 [連接到 SQL Server] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a4cea-105">When you open the CDC Designer Console, the Connect to SQL Server dialog box opens.</span></span>  
  
 <span data-ttu-id="a4cea-106">存取 [CDC 設計工具] 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入必須擁有 MSXDBCDC 資料庫的 UPDATE 權限。</span><span class="sxs-lookup"><span data-stu-id="a4cea-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login that accesses the CDC Designer must have UPDATE permissions on the MSXDBCDC database.</span></span> <span data-ttu-id="a4cea-107">此外，此登入也必須擁有 `dbcreator` 固定伺服器角色，才能建立新的 Oracle CDC 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4cea-107">In addition, the login must also have the `dbcreator` fixed-server role to create new Oracle CDC Instances.</span></span> <span data-ttu-id="a4cea-108">建議最好讓此登入也具備正在使用之 CDC 資料庫的 SELECT 權限，否則使用者將無法檢視這些資料庫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a4cea-108">It is recommended that the login also have SELECT access to the CDC databases being used or the user will not be able to view the state of those databases.</span></span>  
  
 <span data-ttu-id="a4cea-109">在 [連接到 SQL Server] 對話方塊中輸入以下資訊。</span><span class="sxs-lookup"><span data-stu-id="a4cea-109">Enter the following information in the Connect to SQL Server dialog box.</span></span>  
  
### <a name="server-name"></a><span data-ttu-id="a4cea-110">伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="a4cea-110">Server Name</span></span>  
 <span data-ttu-id="a4cea-111">輸入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所在的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="a4cea-111">Type the name of the server where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is located.</span></span>  
  
### <a name="authentication"></a><span data-ttu-id="a4cea-112">驗證</span><span class="sxs-lookup"><span data-stu-id="a4cea-112">Authentication</span></span>  
 <span data-ttu-id="a4cea-113">選取下列其中一個：</span><span class="sxs-lookup"><span data-stu-id="a4cea-113">Select one of the following:</span></span>  
  
-   <span data-ttu-id="a4cea-114">**Windows 驗證**</span><span class="sxs-lookup"><span data-stu-id="a4cea-114">**Windows Authentication**</span></span>  
  
-   <span data-ttu-id="a4cea-115">**SQL Server 驗證**：如果您選取這個選項，必須針對您所連接之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的使用者輸入**登入**和**密碼**。</span><span class="sxs-lookup"><span data-stu-id="a4cea-115">**SQL Server Authentication**: If you select this option, you must type the **Login** and **Password** for the user in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connecting to.</span></span>  
  
 <span data-ttu-id="a4cea-116">此登入擁有的資料庫角色必須允許存取 MSXCDCDB 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a4cea-116">The login must have a database role that allows access to the MSXCDCDB database.</span></span> <span data-ttu-id="a4cea-117">建議最好讓此登入也能存取正在使用的其他任何資料庫，否則使用者將無法檢視這些資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="a4cea-117">It is recommended that the login also have access to any additional databases being used or the user will not be able to view the data in those databases.</span></span>  
  
### <a name="options"></a><span data-ttu-id="a4cea-118">選項。</span><span class="sxs-lookup"><span data-stu-id="a4cea-118">Options</span></span>  
 <span data-ttu-id="a4cea-119">按一下箭頭即可檢視要設定的可用選項。</span><span class="sxs-lookup"><span data-stu-id="a4cea-119">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="a4cea-120">您可以選擇保留這些選項的預設值。</span><span class="sxs-lookup"><span data-stu-id="a4cea-120">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="a4cea-121">可用的選項如下：</span><span class="sxs-lookup"><span data-stu-id="a4cea-121">The available options are:</span></span>  
  
 <span data-ttu-id="a4cea-122">**連接逾時**</span><span class="sxs-lookup"><span data-stu-id="a4cea-122">**Connection Timeout**</span></span>  
 <span data-ttu-id="a4cea-123">輸入 Oracle CDC 服務在逾時之前等候連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的時間 (以秒數為單位)。預設值為 **15**。</span><span class="sxs-lookup"><span data-stu-id="a4cea-123">Type the time (in seconds) that the CDC Service for Oracle waits for a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before timing out. The default value is **15**.</span></span>  
  
 <span data-ttu-id="a4cea-124">**執行逾時**</span><span class="sxs-lookup"><span data-stu-id="a4cea-124">**Execution Timeout**</span></span>  
 <span data-ttu-id="a4cea-125">輸入 Oracle CDC Windows 服務在逾時之前，等候執行命令的時間 (以秒數為單位)。預設值是 **30**。</span><span class="sxs-lookup"><span data-stu-id="a4cea-125">Type the time (in seconds) that the Oracle CDC Windows Service waits for a command to execute before timing out. The default value is **30**.</span></span>  
  
 <span data-ttu-id="a4cea-126">**加密連接**</span><span class="sxs-lookup"><span data-stu-id="a4cea-126">**Encrypt Connection**</span></span>  
 <span data-ttu-id="a4cea-127">針對 Oracle CDC 服務與使用加密連線之目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之間的通訊選取 [加密連線]  。**進階**：按一下 [進階]  ，並在必要時，於 [進階連接屬性] 對話方塊中輸入其他任何連接屬性。</span><span class="sxs-lookup"><span data-stu-id="a4cea-127">Select **Encrypt Connection** for communication between the Oracle CDC Service and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using an encrypted connection.**Advanced**: Click **Advanced** and type any additional connection properties into the Advanced Connection Properties dialog box, if necessary.</span></span>  
  
 <span data-ttu-id="a4cea-128">**進階**</span><span class="sxs-lookup"><span data-stu-id="a4cea-128">**Advanced**</span></span>  
 <span data-ttu-id="a4cea-129">按一下 [進階]  ，並在必要時，於 [進階連接屬性] 對話方塊中輸入其他任何連接屬性。</span><span class="sxs-lookup"><span data-stu-id="a4cea-129">Click **Advanced** and type any additional connection properties into the Advanced Connection Properties dialog box, if necessary.</span></span>  
  
 <span data-ttu-id="a4cea-130">如需 [進階連接屬性] 對話方塊的資訊，請參閱 [進階連接屬性](advanced-connection-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="a4cea-130">For information about the Advanced Connection Properties dialog box, see [Advanced Connection Properties](advanced-connection-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4cea-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4cea-131">See Also</span></span>  
 [<span data-ttu-id="a4cea-132">SQL Server 連接所需的 CDC 設計工具權限</span><span class="sxs-lookup"><span data-stu-id="a4cea-132">SQL Server Connection Required Permissions for the CDC Designer</span></span>](sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
