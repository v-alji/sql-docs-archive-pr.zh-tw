---
title: 連線到 SQL Server 進行刪除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 030b10c2-6b88-4c2c-bf67-22994be25a60
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f5f069f7686e8b6fa9176f92c9e2f47be5f2c71a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592818"
---
# <a name="connection-to-sql-server-for-delete"></a><span data-ttu-id="62e82-102">連接到 SQL Server 進行刪除</span><span class="sxs-lookup"><span data-stu-id="62e82-102">Connection to SQL Server for Delete</span></span>
  <span data-ttu-id="62e82-103">如果登入沒有包含 MSXDBCDC 資料庫之寫入權限的資料庫角色 (例如 **db_owner** 角色)，則當此登入嘗試刪除 Oracle CDC 執行個體時，便會顯示 [連接到 SQL Server] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="62e82-103">When a login without a database role that includes write permission (for example the **db_owner** role) to the MSXDBCDC database attempts to delete an Oracle CDC instance, the Connect to SQL Server dialog box is displayed.</span></span>  
  
 <span data-ttu-id="62e82-104">在此對話方塊中，您必須輸入擁有 MSXDBCDC 資料庫寫入權限之登入的認證 (例如 **db_owner** 資料庫角色)，才能刪除 Oracle CDC 執行個體。</span><span class="sxs-lookup"><span data-stu-id="62e82-104">In this dialog box you must enter the credentials for a login that has write permission to the MSXDBCDC database, such the **db_owner** database role to delete the Oracle CDC instance.</span></span>  
  
 <span data-ttu-id="62e82-105">在 [連接到 SQL Server] 對話方塊中輸入以下資訊。</span><span class="sxs-lookup"><span data-stu-id="62e82-105">Enter the following information in the Connect to SQL Server dialog box.</span></span>  
  
 <span data-ttu-id="62e82-106">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="62e82-106">**Server Name**</span></span>  
 <span data-ttu-id="62e82-107">輸入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所在的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="62e82-107">Type the name of the server where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is located.</span></span>  
  
 <span data-ttu-id="62e82-108">**驗證**</span><span class="sxs-lookup"><span data-stu-id="62e82-108">**Authentication**</span></span>  
 <span data-ttu-id="62e82-109">選取下列其中一個：</span><span class="sxs-lookup"><span data-stu-id="62e82-109">Select one of the following:</span></span>  
  
-   <span data-ttu-id="62e82-110">**Windows 驗證**</span><span class="sxs-lookup"><span data-stu-id="62e82-110">**Windows Authentication**</span></span>  
  
-   <span data-ttu-id="62e82-111">**SQL Server 驗證**：如果您選取這個選項，您必須針對您所連接之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的使用者輸入 [登入] 和 [密碼]。</span><span class="sxs-lookup"><span data-stu-id="62e82-111">**SQL Server Authentication**: If you select this option, you must type the **Login** and **Password** for the user in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connecting to.</span></span>  
  
 <span data-ttu-id="62e82-112">**選項**</span><span class="sxs-lookup"><span data-stu-id="62e82-112">**Options**</span></span>  
 <span data-ttu-id="62e82-113">按一下箭頭即可檢視要設定的可用選項。</span><span class="sxs-lookup"><span data-stu-id="62e82-113">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="62e82-114">您可以選擇保留這些選項的預設值。</span><span class="sxs-lookup"><span data-stu-id="62e82-114">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="62e82-115">可用的選項如下：</span><span class="sxs-lookup"><span data-stu-id="62e82-115">The available options are:</span></span>  
  
-   <span data-ttu-id="62e82-116">**連接逾時**：輸入此程式在產生逾時錯誤之前，等候連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的時間 (以秒數為單位)。</span><span class="sxs-lookup"><span data-stu-id="62e82-116">**Connection Timeout**: Type the time (in seconds) the program waits for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection to be established before producing a timeout error.</span></span> <span data-ttu-id="62e82-117">預設值為 **15**。</span><span class="sxs-lookup"><span data-stu-id="62e82-117">The default value is **15**.</span></span>  
  
-   <span data-ttu-id="62e82-118">**執行逾時**：輸入此程式在產生逾時錯誤之前，等候執行 SQL 命令的時間 (以秒數為單位)。</span><span class="sxs-lookup"><span data-stu-id="62e82-118">**Execution Timeout**: Type the time (in seconds) that the program waits for SQL command execution to finish before producing a timeout error.</span></span> <span data-ttu-id="62e82-119">預設值是 **30**。</span><span class="sxs-lookup"><span data-stu-id="62e82-119">The default value is **30**.</span></span>  
  
-   <span data-ttu-id="62e82-120">**加密連接**：選取 [加密連接]  ，以確保正在建立的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連接已加密來保障隱私權。</span><span class="sxs-lookup"><span data-stu-id="62e82-120">**Encrypt Connection**: Select **Encrypt Connection** to ensure that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection that being established is encrypted to guarantee privacy.</span></span>  
  
-   <span data-ttu-id="62e82-121">**進階**：按一下 [進階]  ，並在必要時，於 [進階連接屬性] 對話方塊中輸入其他任何連接屬性。</span><span class="sxs-lookup"><span data-stu-id="62e82-121">**Advanced**: Click **Advanced** and type any additional connection properties into the Advanced Connection Properties dialog box, if necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e82-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62e82-122">See Also</span></span>  
 [<span data-ttu-id="62e82-123">SQL Server 連接所需的 CDC 服務權限</span><span class="sxs-lookup"><span data-stu-id="62e82-123">SQL Server Connection Required Permissions for the CDC Service</span></span>](sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
