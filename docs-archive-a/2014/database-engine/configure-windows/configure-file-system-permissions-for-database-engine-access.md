---
title: 設定資料庫引擎存取的檔案系統權限 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- file system permissions
- service account [SQL Server], file system permissions
- permissions [SQL Server], file system
ms.assetid: 78bba43c-4edb-4216-84ac-d6246ae5546d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1d9abbd095f2d5be7415ed28a17fb710ff8ab504
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607096"
---
# <a name="configure-file-system-permissions-for-database-engine-access"></a><span data-ttu-id="46a3b-102">設定 Database Engine 對檔案系統的存取權限</span><span class="sxs-lookup"><span data-stu-id="46a3b-102">Configure File System Permissions for Database Engine Access</span></span>
  <span data-ttu-id="46a3b-103">本主題描述如何授與 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]對資料庫檔案儲存位置的檔案系統存取權。</span><span class="sxs-lookup"><span data-stu-id="46a3b-103">This topic describes how to grant the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], file system access to the location where database files are stored.</span></span> <span data-ttu-id="46a3b-104">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 服務必須具有 Windows 檔案系統權限，才能存取資料庫檔案儲存所在的檔案資料夾。</span><span class="sxs-lookup"><span data-stu-id="46a3b-104">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] service must have permission of the Windows file system to access the file folder where database files are stored.</span></span> <span data-ttu-id="46a3b-105">其對於預設位置的權限，在安裝期間即已設定妥。</span><span class="sxs-lookup"><span data-stu-id="46a3b-105">Permission to the default location is configured during setup.</span></span> <span data-ttu-id="46a3b-106">如果您將資料庫檔案放在不同的位置，可能就必須依照下列步驟授與 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 對該位置的完整控制權限。</span><span class="sxs-lookup"><span data-stu-id="46a3b-106">If you place your database files in a different location, you might need to follow these steps to grant the [!INCLUDE[ssDE](../../includes/ssde-md.md)] the full control permission to that location.</span></span>  
  
 <span data-ttu-id="46a3b-107">從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 開始，權限會指派給其每一項服務的個別服務 SID。</span><span class="sxs-lookup"><span data-stu-id="46a3b-107">Beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] permissions are assigned to the per-service SID for each of its services.</span></span> <span data-ttu-id="46a3b-108">這樣的系統有助於服務隔離並提供深層防禦。</span><span class="sxs-lookup"><span data-stu-id="46a3b-108">This system helps provide service isolation and defense in depth.</span></span> <span data-ttu-id="46a3b-109">個別服務 SID 是衍生自服務名稱，而且每一項服務各有獨特的值。</span><span class="sxs-lookup"><span data-stu-id="46a3b-109">The per-service SID is derived from the service name and is unique to each service.</span></span> <span data-ttu-id="46a3b-110">[設定 Windows 服務帳戶與權限](configure-windows-service-accounts-and-permissions.md) 主題描述了個別服務 SID，並且在 **Windows 權限和權利**一節中提供各種名稱。</span><span class="sxs-lookup"><span data-stu-id="46a3b-110">The topic [Configure Windows Service Accounts and Permissions](configure-windows-service-accounts-and-permissions.md) describes the per-service SID and provides the names in the section **Windows Privileges and Rights**.</span></span> <span data-ttu-id="46a3b-111">檔案位置的存取權限必須指派給此個別服務 SID。</span><span class="sxs-lookup"><span data-stu-id="46a3b-111">It is the per-service SID that must be assigned the access permission on the file location.</span></span>  
  
## <a name="to-grant-file-system-permission-to-the-per-service-sid"></a><span data-ttu-id="46a3b-112">若要將檔案系統權限授與個別服務 SID</span><span class="sxs-lookup"><span data-stu-id="46a3b-112">To Grant File System Permission to the Per-service SID</span></span>  
  
1.  <span data-ttu-id="46a3b-113">使用 [Windows 檔案總管]，導覽到資料庫檔案儲存所在的檔案系統位置。</span><span class="sxs-lookup"><span data-stu-id="46a3b-113">Using Windows Explorer, navigate to the file system location where the database files are stored.</span></span> <span data-ttu-id="46a3b-114">以滑鼠右鍵按一下檔案系統資料夾，然後按一下 [內容]。</span><span class="sxs-lookup"><span data-stu-id="46a3b-114">Right-click the file system folder, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="46a3b-115">在 [安全性] 索引標籤上，按一下 [編輯]，然後按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="46a3b-115">On the **Security** tab, click **Edit**, and then **Add**.</span></span>  
  
3.  <span data-ttu-id="46a3b-116">在 [選取使用者、電腦、服務帳戶或群組] 對話方塊中，按一下 [位置]，並從位置清單頂端選取您的電腦名稱，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="46a3b-116">In the **Select Users, Computer, Service Account, or Groups** dialog box, click **Locations**, at the top of the location list, select your computer name, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="46a3b-117">在 [**輸入要選取的物件名稱**] 方塊中，輸入《線上叢書》主題**設定 Windows 服務帳戶和許可權**中所列的個別服務 SID 名稱。</span><span class="sxs-lookup"><span data-stu-id="46a3b-117">In the **Enter the object names to select** box, type the name of the per-service SID listed in the Books Online topic **Configure Windows Service Accounts and Permissions**.</span></span> <span data-ttu-id="46a3b-118">針對 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 每個服務 SID (，針對預設實例使用**nt SERVICE\MSSQLSERVER** ，或針對已命名的實例使用**nt SERVICE\MSSQL $ InstanceName** 。 ) </span><span class="sxs-lookup"><span data-stu-id="46a3b-118">(For the [!INCLUDE[ssDE](../../includes/ssde-md.md)] per service SID, use **NT SERVICE\MSSQLSERVER** for a default instance, or **NT SERVICE\MSSQL$InstanceName** for a named instance.)</span></span>  
  
5.  <span data-ttu-id="46a3b-119">按一下 [檢查名稱]，驗證輸入項</span><span class="sxs-lookup"><span data-stu-id="46a3b-119">Click **Check Names** to validate the entry.</span></span> <span data-ttu-id="46a3b-120">驗證通常會失敗，而且可能是找不到名稱的緣故。</span><span class="sxs-lookup"><span data-stu-id="46a3b-120">The validation often fails, and might advise you that the name was not found.</span></span> <span data-ttu-id="46a3b-121">當您按一下[確定] 時，[找到多個相符名稱] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="46a3b-121">When you click **OK**, a **Multiple Names Found** dialog box appears.</span></span>  
  
6.  <span data-ttu-id="46a3b-122">現在，選取個別服務 SID （ **MSSQLSERVER**或**NT SERVICE\MSSQL $ InstanceName**），然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="46a3b-122">Now select the per-service SID, either **MSSQLSERVER** or **NT SERVICE\MSSQL$InstanceName**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="46a3b-123">再次按一下 **[確定**] 以返回 [**許可權**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="46a3b-123">Click **OK** again to return to the **Permissions** dialog box.</span></span>  
  
8.  <span data-ttu-id="46a3b-124">在 [**群組或使用者**名稱] 方塊中，選取個別服務 SID，然後在 [**許可權**] 方塊中 \<name> ，選取 [**完全控制**] 的 [**允許**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="46a3b-124">In the **Group or user** names box, select the per-service SID, and then in the **Permissions for** \<name> box, select the **Allow** check box for **Full control**.</span></span>  
  
9. <span data-ttu-id="46a3b-125">按一下 [套用]，再按兩次 [確定] 退出。</span><span class="sxs-lookup"><span data-stu-id="46a3b-125">Click **Apply**, and then click **OK** twice to exit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46a3b-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46a3b-126">See Also</span></span>  
 <span data-ttu-id="46a3b-127">[管理 Database Engine Services](manage-the-database-engine-services.md) </span><span class="sxs-lookup"><span data-stu-id="46a3b-127">[Manage the Database Engine Services](manage-the-database-engine-services.md) </span></span>  
 <span data-ttu-id="46a3b-128">[移動系統資料庫](../../relational-databases/databases/system-databases.md) </span><span class="sxs-lookup"><span data-stu-id="46a3b-128">[Move System Databases](../../relational-databases/databases/system-databases.md) </span></span>  
 [<span data-ttu-id="46a3b-129">移動使用者資料庫</span><span class="sxs-lookup"><span data-stu-id="46a3b-129">Move User Databases</span></span>](../../relational-databases/databases/move-user-databases.md)  
  
  
