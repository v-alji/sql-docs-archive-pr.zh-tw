---
title: 檢視或變更已註冊的篩選與斷詞工具 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], word breakers
- full-text search [SQL Server], filters
- filters [full-text search]
- word breakers [full-text search]
ms.assetid: f88c54df-b1aa-4701-807f-dc92c32363fd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 79ad7f1f7df15fed21a132bbe253adc7185d8c06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697810"
---
# <a name="view-or-change-registered-filters-and-word-breakers"></a><span data-ttu-id="c04a3-102">檢視或變更已註冊的篩選與斷詞工具</span><span class="sxs-lookup"><span data-stu-id="c04a3-102">View or Change Registered Filters and Word Breakers</span></span>
  <span data-ttu-id="c04a3-103">在系統上安裝或解除安裝任何斷詞工具或篩選器之後，這些變更不會自動在伺服器執行個體上生效。</span><span class="sxs-lookup"><span data-stu-id="c04a3-103">After any word breakers or filters are installed or uninstalled on a system, the changes do not automatically take effect on server instances.</span></span> <span data-ttu-id="c04a3-104">此主題描述如何檢視目前已註冊的斷詞工具或篩選，以及如何在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體上註冊新安裝的斷詞工具和篩選。</span><span class="sxs-lookup"><span data-stu-id="c04a3-104">This topic describes how to view the currently registered word breaker or filters and how to register newly installed word breakers and filters on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="to-view-a-list-of-languages-whose-word-breakers-are-currently-registered"></a><span data-ttu-id="c04a3-105">若要檢視目前已註冊斷詞工具的語言清單</span><span class="sxs-lookup"><span data-stu-id="c04a3-105">To view a list of languages whose word breakers are currently registered</span></span>  
  
1.  <span data-ttu-id="c04a3-106">使用 [sys.fulltext_languages](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) 目錄檢視，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c04a3-106">Use the [sys.fulltext_languages](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) catalog view, as follows:</span></span>  
  
    ```  
    SELECT * FROM sys.fulltext_languages;   
    ```  
  
### <a name="to-view-a-list-of-the-filters-that-are-currently-registered"></a><span data-ttu-id="c04a3-107">若要檢視目前已註冊的篩選清單</span><span class="sxs-lookup"><span data-stu-id="c04a3-107">To view a list of the filters that are currently registered</span></span>  
  
1.  <span data-ttu-id="c04a3-108">使用 [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) 系統預存程序，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c04a3-108">Use the [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) system stored procedure, as follows:</span></span>  
  
    ```  
    EXEC sp_help_fulltext_system_components 'filter';    
    ```  
  
### <a name="to-register-newly-installed-word-breakers-and-filters"></a><span data-ttu-id="c04a3-109">若要註冊新安裝的斷詞工具和篩選</span><span class="sxs-lookup"><span data-stu-id="c04a3-109">To register newly installed word breakers and filters</span></span>  
  
1.  <span data-ttu-id="c04a3-110">使用 [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql) 系統預存程序來更新語言的清單，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c04a3-110">Use the [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql) system stored procedure to update the list of languages, as follows:</span></span>  
  
    ```  
    exec sp_fulltext_service 'update_languages';   
    ```  
  
### <a name="to-unregister-uninstalled-word-breakers-and-filters"></a><span data-ttu-id="c04a3-111">取消註冊已解除安裝的斷詞工具與篩選</span><span class="sxs-lookup"><span data-stu-id="c04a3-111">To unregister uninstalled word breakers and filters</span></span>  
  
1.  <span data-ttu-id="c04a3-112">使用 **sp_fulltext_service** 來更新語言的清單，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c04a3-112">Use the **sp_fulltext_service** to update the list of languages, as follows:</span></span>  
  
    ```  
    exec sp_fulltext_service 'update_languages'  
    ```  
  
2.  <span data-ttu-id="c04a3-113">使用 **sp_fulltext_service** 重新啟動篩選背景程式主機處理序 (fdhost.exe)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c04a3-113">Use the **sp_fulltext_service** to restart the filter daemon host processes (fdhost.exe), as follows:</span></span>  
  
    ```  
    exec sp_fulltext_service 'restart_all_fdhosts';  
    ```  
  
### <a name="to-replace-existing-word-breakers-or-filters-when-installing-new-ones"></a><span data-ttu-id="c04a3-114">若要在安裝新的斷詞工具或篩選時取代現有的斷詞工具或篩選</span><span class="sxs-lookup"><span data-stu-id="c04a3-114">To replace existing word breakers or filters when installing new ones</span></span>  
  
1.  <span data-ttu-id="c04a3-115">準備安裝含有新斷詞工具或篩選的 DLL 檔案時，請確認它的檔案名稱與伺服器執行個體上安裝的任何現有 DLL 檔案不同。</span><span class="sxs-lookup"><span data-stu-id="c04a3-115">When preparing to install a DLL file that contains new word breakers or filters, verify that it has a different filename from any of the existing DLL files installed on your server instance.</span></span>  
  
2.  <span data-ttu-id="c04a3-116">將新的 DLL 檔案複製到包含伺服器執行個體之標準 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL 檔案的目錄中。</span><span class="sxs-lookup"><span data-stu-id="c04a3-116">Copy the new DLL file into the directory containing the standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL files for the server instance.</span></span> <span data-ttu-id="c04a3-117">預設位置為：</span><span class="sxs-lookup"><span data-stu-id="c04a3-117">The default location is:</span></span>  
  
     <span data-ttu-id="c04a3-118">C:\Program Files\Microsoft SQL Server\MSSQL.*執行個體名稱*\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="c04a3-118">C:\Program Files\Microsoft SQL Server\MSSQL.*instance_name*\MSSQL\Binn</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c04a3-119">我們強烈建議您只載入已簽署且經過驗證的元件。</span><span class="sxs-lookup"><span data-stu-id="c04a3-119">We highly recommend that you load only signed and verified components.</span></span> <span data-ttu-id="c04a3-120">此外，我們建議您使用最低的可能權限，執行 FDHOST 啟動器 (MSSQLFDLauncher) 服務。</span><span class="sxs-lookup"><span data-stu-id="c04a3-120">Also, we recommend that you run the FDHOST Launcher (MSSQLFDLauncher) Service with the least possible privileges.</span></span>  
  
3.  <span data-ttu-id="c04a3-121">安裝新的斷詞工具或篩選。</span><span class="sxs-lookup"><span data-stu-id="c04a3-121">Install the new word breaker or filters.</span></span>  
  
     <span data-ttu-id="c04a3-122">**安裝並載入 Microsoft Filter Pack IFilters**</span><span class="sxs-lookup"><span data-stu-id="c04a3-122">**To install and load Microsoft Filter Pack IFilters**</span></span>  
  
    -   [<span data-ttu-id="c04a3-123">How to register Microsoft Filter Pack IFilters with SQL Server (如何對 SQL Server 註冊 Microsoft Filter Pack IFilter)</span><span class="sxs-lookup"><span data-stu-id="c04a3-123">How to register Microsoft Filter Pack IFilters with SQL Server</span></span>](https://go.microsoft.com/fwlink/?LinkId=130439)  
  
4.  <span data-ttu-id="c04a3-124">使用 **sp_fulltext_service** 將新安裝的斷詞工具與篩選，載入伺服器執行個體中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c04a3-124">Use **sp_fulltext_service** to load newly installed word breakers and filters in the server instance, as follows:</span></span>  
  
    ```  
    EXEC sp_fulltext_service @action='load_os_resources', @value=1;  
    ```  
  
5.  <span data-ttu-id="c04a3-125">使用 **sp_fulltext_service** 來更新語言的清單，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c04a3-125">Use **sp_fulltext_service** to update the list of languages, as follows:</span></span>  
  
    ```  
    EXEC sp_fulltext_service 'update_languages';  
    ```  
  
6.  <span data-ttu-id="c04a3-126">使用 **sp_fulltext_service** 重新啟動篩選背景程式主機處理序 (fdhost.exe)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c04a3-126">Restart the filter daemon host processes (fdhost.exe), using **sp_fulltext_service** as follows:</span></span>  
  
    ```  
    EXEC sp_fulltext_service 'restart_all_fdhosts';   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c04a3-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c04a3-127">See Also</span></span>  
 <span data-ttu-id="c04a3-128">[設定全文檢索篩選背景程式啟動器的服務帳戶](set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span><span class="sxs-lookup"><span data-stu-id="c04a3-128">[Set the Service Account for the Full-text Filter Daemon Launcher](set-the-service-account-for-the-full-text-filter-daemon-launcher.md) </span></span>  
 <span data-ttu-id="c04a3-129">[設定及管理搜尋的篩選](configure-and-manage-filters-for-search.md) </span><span class="sxs-lookup"><span data-stu-id="c04a3-129">[Configure and Manage Filters for Search](configure-and-manage-filters-for-search.md) </span></span>  
 [<span data-ttu-id="c04a3-130">設定及管理搜尋的斷詞工具與字幹分析器</span><span class="sxs-lookup"><span data-stu-id="c04a3-130">Configure and Manage Word Breakers and Stemmers for Search</span></span>](configure-and-manage-word-breakers-and-stemmers-for-search.md)  
  
  
