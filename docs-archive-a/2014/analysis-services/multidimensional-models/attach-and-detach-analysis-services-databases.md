---
title: 附加和卸離 Analysis Services 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssms.detachdatabase.f1
- sql12.asvs.ssms.attachdatabase.f1
- sql12.asvs.ssmsimbi.AttachDatabase.f1
- sql12.asvs.ssmsimbi.DetachDatabase.f1
helpviewer_keywords:
- databases [Analysis Services], attach
- databases [Analysis Services], detach
ms.assetid: 41887413-2d47-49b8-8614-553cb799fb18
author: minewiskan
ms.author: owend
ms.openlocfilehash: cd72277970605691e06f3baacf167ea135343b3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606457"
---
# <a name="attach-and-detach-analysis-services-databases"></a><span data-ttu-id="3ae36-102">附加和卸離 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="3ae36-102">Attach and Detach Analysis Services Databases</span></span>
  <span data-ttu-id="3ae36-103">通常在很多情況下， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫管理員 (dba) 會想要讓資料庫保持離線一段時間，然後在相同或不同的伺服器執行個體上，讓該資料庫恢復連線狀態。</span><span class="sxs-lookup"><span data-stu-id="3ae36-103">There are often situations when an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database administrator (dba) wants to take a database offline for a period, and then bring that database back online on the same server instance, or on a different one.</span></span> <span data-ttu-id="3ae36-104">這些情況通常是由商務需求所驅使，例如將資料庫移至不同的磁碟以提升效能、取得讓資料庫成長的空間，或升級產品。</span><span class="sxs-lookup"><span data-stu-id="3ae36-104">These situations are often driven by business needs, such as moving the database to a different disk for better performance, gaining room for database growth, or to upgrade a product.</span></span> <span data-ttu-id="3ae36-105">對於所有這些案例和其他情況， `Attach` 和 `Detach` 命令可讓 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dba 讓資料庫離線，並輕鬆地使其恢復上線。</span><span class="sxs-lookup"><span data-stu-id="3ae36-105">For all those cases and more, the `Attach` and `Detach` commands enable the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dba to take the database offline and bring it back online with little effort.</span></span>  
  
## <a name="attach-and-detach-commands"></a><span data-ttu-id="3ae36-106">Attach 和 Detach 命令</span><span class="sxs-lookup"><span data-stu-id="3ae36-106">Attach and Detach commands</span></span>  
 <span data-ttu-id="3ae36-107"> 命令可讓您將離線的資料庫恢復連線狀態。</span><span class="sxs-lookup"><span data-stu-id="3ae36-107">The `Attach` command enables you to bring online a database that was taken offline.</span></span> <span data-ttu-id="3ae36-108">您可以將資料庫附加至原始伺服器執行個體或其他執行個體。</span><span class="sxs-lookup"><span data-stu-id="3ae36-108">You can attach the database to the original server instance, or to another instance.</span></span> <span data-ttu-id="3ae36-109">當您附加資料庫時，使用者可以指定資料庫的 **[ReadWriteMode]** 設定。</span><span class="sxs-lookup"><span data-stu-id="3ae36-109">When you attach a database the user can specify the **ReadWriteMode** setting for the database.</span></span> <span data-ttu-id="3ae36-110"> 命令可讓您中斷資料庫與伺服器的連線。</span><span class="sxs-lookup"><span data-stu-id="3ae36-110">The `Detach` command enables you to take offline a database from the server.</span></span>  
  
## <a name="attach-and-detach-usage"></a><span data-ttu-id="3ae36-111">Attach 和 Detach 使用方式</span><span class="sxs-lookup"><span data-stu-id="3ae36-111">Attach and Detach Usage</span></span>  
 <span data-ttu-id="3ae36-112"> 命令是用來讓現有的資料庫結構恢復連線狀態。</span><span class="sxs-lookup"><span data-stu-id="3ae36-112">The `Attach` command is used to bring online an existing database structure.</span></span> <span data-ttu-id="3ae36-113">如果資料庫是以 `ReadWrite` 模式附加，它就只能附加至伺服器執行個體一次。</span><span class="sxs-lookup"><span data-stu-id="3ae36-113">If the database is attached in `ReadWrite` mode, it can be attached only one time to a server instance.</span></span> <span data-ttu-id="3ae36-114">不過，如果資料庫是以 `ReadOnly` 模式附加，它就可以附加至不同的伺服器執行個體許多次。</span><span class="sxs-lookup"><span data-stu-id="3ae36-114">However, if the database is attached in `ReadOnly` mode, it can be attached multiple times to different server instances.</span></span> <span data-ttu-id="3ae36-115">不過，相同的資料庫無法附加至相同的伺服器執行個體超過一次。</span><span class="sxs-lookup"><span data-stu-id="3ae36-115">However, the same database cannot be attached more than one time to the same server instance.</span></span> <span data-ttu-id="3ae36-116">當您嘗試附加相同的資料庫超過一次時，即使資料已經複製到個別的資料夾，還是會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="3ae36-116">An error is raised when an attempt is made to attach the same database more than one time, even if the data has been copied to separate folders.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3ae36-117">如果需要使用密碼才能卸離資料庫，則附加資料庫時也會需要使用相同的密碼。</span><span class="sxs-lookup"><span data-stu-id="3ae36-117">If a password was required to detach the database, the same password is required to attach the database.</span></span>  
  
 <span data-ttu-id="3ae36-118"> 命令是用來讓現有的資料庫結構保持離線。</span><span class="sxs-lookup"><span data-stu-id="3ae36-118">The `Detach` command is used to take offline an existing database structure.</span></span> <span data-ttu-id="3ae36-119">卸離資料庫時，您應該提供密碼來保護機密中繼資料。</span><span class="sxs-lookup"><span data-stu-id="3ae36-119">When a database is detached, you should provide a password to protect confidential metadata.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3ae36-120">為了保護資料檔案的內容，您應該針對資料夾、子資料夾和資料檔案使用存取控制清單。</span><span class="sxs-lookup"><span data-stu-id="3ae36-120">To protect the content of the data files, you should use an access control list for the folder, subfolders, and data files.</span></span>  
  
 <span data-ttu-id="3ae36-121">當您卸離資料庫時，伺服器會遵循下列步驟進行。</span><span class="sxs-lookup"><span data-stu-id="3ae36-121">When you detach a database, the server follows these steps.</span></span>  
  
|<span data-ttu-id="3ae36-122">卸離讀取/寫入資料庫</span><span class="sxs-lookup"><span data-stu-id="3ae36-122">Detaching a read/write database</span></span>|<span data-ttu-id="3ae36-123">卸離唯讀資料庫</span><span class="sxs-lookup"><span data-stu-id="3ae36-123">Detaching a read-only database</span></span>|  
|--------------------------------------|-------------------------------------|  
|<span data-ttu-id="3ae36-124">1) 伺服器發出在資料庫上執行 CommitExclusive 鎖定的要求</span><span class="sxs-lookup"><span data-stu-id="3ae36-124">1) The server issues a request for a CommitExclusive Lock on the database</span></span><br /><span data-ttu-id="3ae36-125">2) 伺服器等候直到所有進行中的交易都已認可或回復為止</span><span class="sxs-lookup"><span data-stu-id="3ae36-125">2) The server waits until all ongoing transactions are either committed or rolled back</span></span><br /><span data-ttu-id="3ae36-126">3) 伺服器建立卸離資料庫所需的所有中繼資料</span><span class="sxs-lookup"><span data-stu-id="3ae36-126">3) The server builds all the metadata that it must have to detach the database</span></span><br /><span data-ttu-id="3ae36-127">4) 資料庫標示為已刪除</span><span class="sxs-lookup"><span data-stu-id="3ae36-127">4) The database is marked as deleted</span></span><br /><span data-ttu-id="3ae36-128">5) 伺服器認可交易</span><span class="sxs-lookup"><span data-stu-id="3ae36-128">5) The server commits the transaction</span></span>|<span data-ttu-id="3ae36-129">1) 資料庫標示為已刪除</span><span class="sxs-lookup"><span data-stu-id="3ae36-129">1) The database is marked as deleted</span></span><br /><span data-ttu-id="3ae36-130">2) 伺服器認可交易</span><span class="sxs-lookup"><span data-stu-id="3ae36-130">2) The server commits the transaction</span></span><br /><br /> <br /><br /> <span data-ttu-id="3ae36-131">注意：您無法針對唯讀資料庫變更卸離密碼。</span><span class="sxs-lookup"><span data-stu-id="3ae36-131">Note: The detaching password cannot be changed for a read-only database.</span></span> <span data-ttu-id="3ae36-132">如果您針對已經包含密碼的卸離資料庫提供密碼參數，就會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="3ae36-132">An error is raised if the password parameter is provided for an attached database that already contains a password.</span></span>|  
  
 <span data-ttu-id="3ae36-133"> 和  命令必須當做單一作業執行。</span><span class="sxs-lookup"><span data-stu-id="3ae36-133">The `Attach` and `Detach` commands must be executed as single operations.</span></span> <span data-ttu-id="3ae36-134">它們無法在同一個交易中與其他作業結合。</span><span class="sxs-lookup"><span data-stu-id="3ae36-134">They cannot be combined with other operations in the same transaction.</span></span> <span data-ttu-id="3ae36-135">此外， `Attach` 和 `Detach` 命令是不可部分完成的交易式命令。</span><span class="sxs-lookup"><span data-stu-id="3ae36-135">Also, the `Attach` and `Detach` commands are atomic transactional commands.</span></span> <span data-ttu-id="3ae36-136">這表示此作業不是成功，就是失敗。</span><span class="sxs-lookup"><span data-stu-id="3ae36-136">This means the operation will either succeed or fail.</span></span> <span data-ttu-id="3ae36-137">沒有任何資料庫會處於未完成的狀態。</span><span class="sxs-lookup"><span data-stu-id="3ae36-137">No database will be left in an uncompleted state.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3ae36-138">您必須擁有伺服器或資料庫管理員權限才能執行 `Detach` 命令。</span><span class="sxs-lookup"><span data-stu-id="3ae36-138">Server or database administrator privileges are required to execute the `Detach` command.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3ae36-139">您必須擁有伺服器管理員權限才能執行 `Attach` 命令。</span><span class="sxs-lookup"><span data-stu-id="3ae36-139">Server administrator privileges are required to execute the `Attach` command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae36-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ae36-140">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <span data-ttu-id="3ae36-141">[Microsoft.analysisservices。卸離 \*](/dotnet/api/microsoft.analysisservices.core.database.detach) </span><span class="sxs-lookup"><span data-stu-id="3ae36-141">[Microsoft.AnalysisServices.Database.Detach\*](/dotnet/api/microsoft.analysisservices.core.database.detach) </span></span>  
 <span data-ttu-id="3ae36-142">[移動 Analysis Services 資料庫](move-an-analysis-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="3ae36-142">[Move an Analysis Services Database](move-an-analysis-services-database.md) </span></span>  
 <span data-ttu-id="3ae36-143">[資料庫 Readwritemode](database-readwritemodes.md) </span><span class="sxs-lookup"><span data-stu-id="3ae36-143">[Database ReadWriteModes](database-readwritemodes.md) </span></span>  
 <span data-ttu-id="3ae36-144">[在 ReadOnly 和 ReadWrite 模式之間切換 Analysis Services 資料庫](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md) </span><span class="sxs-lookup"><span data-stu-id="3ae36-144">[Switch an Analysis Services database between ReadOnly and ReadWrite modes](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md) </span></span>  
 <span data-ttu-id="3ae36-145">[Detach 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span><span class="sxs-lookup"><span data-stu-id="3ae36-145">[Detach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span></span>  
 [<span data-ttu-id="3ae36-146">Attach 元素</span><span class="sxs-lookup"><span data-stu-id="3ae36-146">Attach Element</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)  
  
  
