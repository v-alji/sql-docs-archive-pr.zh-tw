---
title: 建立 SQL Server 變更資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraIns
ms.assetid: 4f79c24a-e99a-4a06-8637-51eeec406259
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0eaeb26d5bea4c9e50db29aaa45297ba763dbbfa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707721"
---
# <a name="create-the-sql-server-change-database"></a><span data-ttu-id="0a108-102">建立 SQL Server 變更資料庫</span><span class="sxs-lookup"><span data-stu-id="0a108-102">Create the SQL Server Change Database</span></span>
  <span data-ttu-id="0a108-103">當您啟動新增執行個體精靈時，隨即開啟 [建立 CDC 資料庫] 頁面。</span><span class="sxs-lookup"><span data-stu-id="0a108-103">When you start the New Instance wizard, the Create CDC Database page opens.</span></span> <span data-ttu-id="0a108-104">使用 [建立 CDC 資料庫] 頁面可提供有關新的 CDC 執行個體及建立新的變更資料庫的資訊。</span><span class="sxs-lookup"><span data-stu-id="0a108-104">Use the Create CDC Database page to provide information about the new CDC instance and create a new Change database.</span></span>  
  
 <span data-ttu-id="0a108-105">當您建立新的 CDC 資料庫時，它會啟用 SQL Server CDC，而這樣的啟用需要屬於 `sysadmin` 固定伺服器角色成員的登入。</span><span class="sxs-lookup"><span data-stu-id="0a108-105">When you create a new CDC database it is enabled for SQL Server CDC and this enablement requires a login that is a member of the `sysadmin` fixed-server role.</span></span>  
  
 <span data-ttu-id="0a108-106">如果啟動「建立 Oracle CDC 執行個體」精靈的使用者不是 `sysadmin` 固定伺服器角色的成員，便會開啟 [連接到 SQL Server] 對話方塊，並要求系統管理員 (sysadmin) 角色成員的認證，才能執行「為 SQL Server CDC 啟用資料庫」工作。</span><span class="sxs-lookup"><span data-stu-id="0a108-106">When a user that starts the Create an Oracle CDC Instance wizard is not a member of the `sysadmin` fixed-server role, the Connect to SQL Server dialog box opens and requests the credentials for a member of the sysadmin role to carry out the Enable the database for SQL Server CDC task.</span></span> <span data-ttu-id="0a108-107">當建立 CDC 資料庫時，將會捨棄 `sysadmin` 登入，而且會使用之前進入 Oracle 設計工具主控台時所使用的原始 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入繼續工作。</span><span class="sxs-lookup"><span data-stu-id="0a108-107">When the CDC database is created, the `sysadmin` login is discarded and work resumes with the original [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used when the Oracle Designer Console was entered.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0a108-108">如果是「為 SQL Server CDC 啟用資料庫」以外的工作，用於執行 [新增執行個體精靈] 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入必須擁有 `dbcreator` 固定伺服器角色及 MSXDBCDC 資料庫的 UPDATE 權限。</span><span class="sxs-lookup"><span data-stu-id="0a108-108">For tasks other than Enable the database for SQL Server CDC of, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used for running the New Instance Wizard must have the `dbcreator` fixed-server role and UPDATE permissions on the MSXDBCDC database.</span></span>  
  
 <span data-ttu-id="0a108-109">如需有關在 [連接到 SQL Server] 對話方塊中輸入資料的詳細資訊，請參閱＜ [SQL Server Connection for Instance Creation](sql-server-connection-for-instance-creation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="0a108-109">For information on entering the data in the Connect to SQL Server dialog box, see [SQL Server Connection for Instance Creation](sql-server-connection-for-instance-creation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0a108-110">選項。</span><span class="sxs-lookup"><span data-stu-id="0a108-110">Options</span></span>  
 <span data-ttu-id="0a108-111">**Oracle CDC 執行個體**</span><span class="sxs-lookup"><span data-stu-id="0a108-111">**Oracle CDC Instance**</span></span>  
 <span data-ttu-id="0a108-112">輸入以下有關您建立之 CDC 執行個體的資訊。</span><span class="sxs-lookup"><span data-stu-id="0a108-112">Type the following information about the CDC instance you are creating.</span></span>  
  
-   <span data-ttu-id="0a108-113">**名稱**：輸入新服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a108-113">**Name**: Type a name for the new service.</span></span> <span data-ttu-id="0a108-114">這也會是新的變更資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a108-114">This will also be the name of the new Change database.</span></span>  
  
-   <span data-ttu-id="0a108-115">**描述**：輸入新執行個體的描述，幫助您識別該執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a108-115">**Description**: Type a description for the new instance to help you identify it.</span></span> <span data-ttu-id="0a108-116">這是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="0a108-116">This is optional.</span></span>  
  
 <span data-ttu-id="0a108-117">**SQL Server 變更資料庫**</span><span class="sxs-lookup"><span data-stu-id="0a108-117">**SQL Server Change Database**</span></span>  
 <span data-ttu-id="0a108-118">此區段是用來建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="0a108-118">This section is used to create the database.</span></span>  
  
1.  <span data-ttu-id="0a108-119">**變更資料庫**：新的變更資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a108-119">**Change Database**: The name of the new Change database.</span></span> <span data-ttu-id="0a108-120">此資料庫的名稱與您提供給執行個體的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="0a108-120">The name of the database is the same as the name that you gave to the instance.</span></span> <span data-ttu-id="0a108-121">這個唯讀欄位會顯示資料庫的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="0a108-121">This read-only field displays the full path to the database.</span></span>  
  
2.  <span data-ttu-id="0a108-122">**建立資料庫**：按一下 **[建立資料庫]** ，即可建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="0a108-122">**Create Database**: Click **Create Database** to create the database.</span></span>  
  
     <span data-ttu-id="0a108-123">若要建立資料庫，登入必須擁有 `sysasmin` 伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="0a108-123">To create the database, the login must have the `sysasmin` server role.</span></span> <span data-ttu-id="0a108-124">如需詳細資訊，請參閱上述的安全性注意事項。</span><span class="sxs-lookup"><span data-stu-id="0a108-124">See the security note above for more information.</span></span>  
  
     <span data-ttu-id="0a108-125">在您建立資料庫之後，可以按 **[下一步]** [Connect to an Oracle Source Database](connect-to-an-oracle-source-database.md)。</span><span class="sxs-lookup"><span data-stu-id="0a108-125">After you create the database, you can click **Next** to [Connect to an Oracle Source Database](connect-to-an-oracle-source-database.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a108-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a108-126">See Also</span></span>  
 <span data-ttu-id="0a108-127">[如何建立 SQL Server 變更資料庫執行個體](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="0a108-127">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="0a108-128">Oracle CDC 服務</span><span class="sxs-lookup"><span data-stu-id="0a108-128">The Oracle CDC Service</span></span>](the-oracle-cdc-service.md)  
  
  
