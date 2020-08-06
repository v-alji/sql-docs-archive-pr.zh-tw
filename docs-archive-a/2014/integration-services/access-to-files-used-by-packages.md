---
title: 存取封裝所使用的檔案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, security
- packages [Integration Services], security
- configuration files [Integration Services]
- checkpoint files
- Integration Services packages, security
- logs [Integration Services], security
- files [Integration Services], security
- SQL Server Integration Services packages, security
ms.assetid: 2e3ddea9-5289-4289-a70e-11c018f34977
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8db9511c91c9f229b7002f5b16cf077910a4ccf0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592830"
---
# <a name="access-to-files-used-by-packages"></a><span data-ttu-id="00455-102">對封裝使用之檔案的存取權</span><span class="sxs-lookup"><span data-stu-id="00455-102">Access to Files Used by Packages</span></span>
  <span data-ttu-id="00455-103">封裝保護等級不會保護儲存於封裝之外的檔案。</span><span class="sxs-lookup"><span data-stu-id="00455-103">The package protection level does not protect files that are stored outside the package.</span></span> <span data-ttu-id="00455-104">這些檔案包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="00455-104">These files include the following:</span></span>  
  
-   <span data-ttu-id="00455-105">組態檔</span><span class="sxs-lookup"><span data-stu-id="00455-105">Configuration files</span></span>  
  
-   <span data-ttu-id="00455-106">檢查點檔案</span><span class="sxs-lookup"><span data-stu-id="00455-106">Checkpoint files</span></span>  
  
-   <span data-ttu-id="00455-107">記錄檔</span><span class="sxs-lookup"><span data-stu-id="00455-107">Log files</span></span>  
  
 <span data-ttu-id="00455-108">您必須分開保護這些檔案，尤其是當檔案中包含機密資訊時。</span><span class="sxs-lookup"><span data-stu-id="00455-108">These files must be protected separately, especially if they include sensitive information.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="00455-109">組態檔</span><span class="sxs-lookup"><span data-stu-id="00455-109">Configuration Files</span></span>  
 <span data-ttu-id="00455-110">如果組態中含有機密資訊，例如登入和密碼資訊，則應考慮將組態儲存至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中，或使用存取控制清單 (ACL) 來限制對儲存檔案之位置或資料夾的存取權，且只允許特定帳戶擁有其存取權。</span><span class="sxs-lookup"><span data-stu-id="00455-110">If you have sensitive information in a configuration, such as login and password information, you should consider saving the configuration to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], or use an access control list (ACL) to restrict access to the location or folder where you store the files and allow access only to certain accounts.</span></span> <span data-ttu-id="00455-111">通常，您可以將存取權授與您允許執行封裝的帳戶，以及負責管理和疑難排解封裝的帳戶，其工作可能包括檢閱組態、檢查點和記錄檔的內容。</span><span class="sxs-lookup"><span data-stu-id="00455-111">Typically, you would grant access to the accounts that you permit to run packages, and to the accounts that manage and troubleshoot packages, which may include reviewing the contents of configuration, checkpoint, and log files.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="00455-112">提供更安全的儲存體，因為它可以提供伺服器和資料庫層級的保護。</span><span class="sxs-lookup"><span data-stu-id="00455-112">provides the more secure storage because it offers protection at the server and database levels.</span></span> <span data-ttu-id="00455-113">若要將組態儲存至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，您可以使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 組態類型。</span><span class="sxs-lookup"><span data-stu-id="00455-113">To save configurations to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration type.</span></span> <span data-ttu-id="00455-114">若要儲存至檔案系統，則可以使用 XML 組態類型。</span><span class="sxs-lookup"><span data-stu-id="00455-114">To save to the file system, you use the XML configuration type.</span></span>  
  
 <span data-ttu-id="00455-115">如需詳細資訊，請參閱 [封裝組態](../../2014/integration-services/package-configurations.md)、 [建立封裝組態](../../2014/integration-services/create-package-configurations.md)和 [SQL Server 安裝的安全性考量](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)。</span><span class="sxs-lookup"><span data-stu-id="00455-115">For more information, see [Package Configurations](../../2014/integration-services/package-configurations.md), [Create Package Configurations](../../2014/integration-services/create-package-configurations.md), and [Security Considerations for a SQL Server Installation](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md).</span></span>  
  
## <a name="checkpoint-files"></a><span data-ttu-id="00455-116">檢查點檔案</span><span class="sxs-lookup"><span data-stu-id="00455-116">Checkpoint Files</span></span>  
 <span data-ttu-id="00455-117">同樣地，如果封裝使用的檢查點檔案包含機密資訊，應使用存取控制清單 (ACL) 來保護儲存檔案之位置或資料夾的安全。</span><span class="sxs-lookup"><span data-stu-id="00455-117">Similarly, if the checkpoint file that the package uses includes sensitive information, you should use an access control list (ACL) to secure the location or folder where you store the file.</span></span> <span data-ttu-id="00455-118">檢查點檔案儲存有關封裝進度和目前變數值的目前狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="00455-118">Checkpoint files save current state information on the progress of the package as well as the current values of variables.</span></span> <span data-ttu-id="00455-119">例如，封裝可能包括含有電話號碼的自訂變數。</span><span class="sxs-lookup"><span data-stu-id="00455-119">For example, the package may include a custom variable that contains a telephone number.</span></span> <span data-ttu-id="00455-120">如需詳細資訊，請參閱 [使用檢查點來重新啟動封裝](packages/restart-packages-by-using-checkpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="00455-120">For more information, see [Restart Packages by Using Checkpoints](packages/restart-packages-by-using-checkpoints.md).</span></span>  
  
## <a name="log-files"></a><span data-ttu-id="00455-121">記錄檔</span><span class="sxs-lookup"><span data-stu-id="00455-121">Log Files</span></span>  
 <span data-ttu-id="00455-122">寫入檔案系統的記錄項目也應使用存取控制清單 (ACL) 保護其安全。</span><span class="sxs-lookup"><span data-stu-id="00455-122">Log entries that are written to the file system should also be secured using an access control list (ACL).</span></span> <span data-ttu-id="00455-123">記錄項目還可以儲存於 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料表中，由 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安全性進行保護。</span><span class="sxs-lookup"><span data-stu-id="00455-123">Log entries can also be stored in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tables and protected by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] security.</span></span> <span data-ttu-id="00455-124">記錄項目可能包含機密資訊，例如，如果封裝包含建構參考電話號碼之 SQL 陳述式的「執行 SQL」工作，SQL 陳述式的記錄項目便會包含電話號碼。</span><span class="sxs-lookup"><span data-stu-id="00455-124">Log entries may include sensitive information, For example, if the package contains an Execute SQL task that constructs an SQL statement that refers to a telephone number, the log entry for the SQL statement includes the telephone number.</span></span> <span data-ttu-id="00455-125">SQL 陳述式可能還顯示有關資料庫中資料表與資料行名稱的私用資訊。</span><span class="sxs-lookup"><span data-stu-id="00455-125">The SQL statement may also reveal private information about table and column names in databases.</span></span> <span data-ttu-id="00455-126">如需詳細資訊，請參閱 [集成服務 &#40;SSIS&#41; 記錄](performance/integration-services-ssis-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="00455-126">For more information, see [Integration Services &#40;SSIS&#41; Logging](performance/integration-services-ssis-logging.md).</span></span>  
  
  
