---
title: 儲存 SSIS 套件 (SQL Server 匯入和匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.savedtspackage.f1
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d4e582558a1f86b18d935fcc6235ba5839faa031
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597921"
---
# <a name="save-ssis-package-sql-server-import-and-export-wizard"></a><span data-ttu-id="f799f-102">儲存 SSIS 封裝 (SQL Server 匯入和匯出精靈)</span><span class="sxs-lookup"><span data-stu-id="f799f-102">Save SSIS Package (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="f799f-103">使用 [**儲存 SSIS 封裝**] 頁面，即可命名、描述和儲存 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) 封裝至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` 資料庫或副檔名為 .dtsx 的檔案。</span><span class="sxs-lookup"><span data-stu-id="f799f-103">Use the **Save SSIS Package** page to name, describe, and save a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) package to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` database or to a file that has the .dtsx extension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f799f-104">在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 中，無法使用儲存此精靈所建立之封裝的選項。</span><span class="sxs-lookup"><span data-stu-id="f799f-104">In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], the option to save the package created by the wizard is not available.</span></span>  
  
 <span data-ttu-id="f799f-105">若要深入瞭解此嚮導，請參閱[SQL Server 匯入和匯出嚮導](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="f799f-105">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="f799f-106">若要瞭解啟動精靈的選項，以及成功執行嚮導所需的許可權，請參閱[執行 SQL Server 匯入和匯出嚮導](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="f799f-106">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="f799f-107">「SQL Server 匯入和匯出精靈」的用途在於將資料從來源複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="f799f-107">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="f799f-108">這個精靈也可以為您建立目的地資料庫和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="f799f-108">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="f799f-109">不過，如果您必須複製多個資料庫或資料表，或複製其他種類的資料庫物件，則應該改用「複製資料庫精靈」。</span><span class="sxs-lookup"><span data-stu-id="f799f-109">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="f799f-110">如需詳細資訊，請參閱 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="f799f-110">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="f799f-111">靜態選項</span><span class="sxs-lookup"><span data-stu-id="f799f-111">Static Options</span></span>  
 <span data-ttu-id="f799f-112">**名稱**</span><span class="sxs-lookup"><span data-stu-id="f799f-112">**Name**</span></span>  
 <span data-ttu-id="f799f-113">提供封裝的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="f799f-113">Provide a unique name for the package.</span></span>  
  
 <span data-ttu-id="f799f-114">**說明**</span><span class="sxs-lookup"><span data-stu-id="f799f-114">**Description**</span></span>  
 <span data-ttu-id="f799f-115">提供封裝的描述。</span><span class="sxs-lookup"><span data-stu-id="f799f-115">Provide a description for the package.</span></span> <span data-ttu-id="f799f-116">最佳作法是以其用途描述封裝，使封裝可以自我記錄並易於維護。</span><span class="sxs-lookup"><span data-stu-id="f799f-116">As a best practice, describe the package in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="f799f-117">**Target**</span><span class="sxs-lookup"><span data-stu-id="f799f-117">**Target**</span></span>  
 <span data-ttu-id="f799f-118">檢視先前為目的地檔案指定的目標 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或檔案)。</span><span class="sxs-lookup"><span data-stu-id="f799f-118">View the target ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or file) that was previously specified for the destination file.</span></span>  
  
## <a name="target-dynamic-options"></a><span data-ttu-id="f799f-119">目標動態選項</span><span class="sxs-lookup"><span data-stu-id="f799f-119">Target Dynamic Options</span></span>  
  
### <a name="target--sql-server"></a><span data-ttu-id="f799f-120">目標 = SQL Server</span><span class="sxs-lookup"><span data-stu-id="f799f-120">Target = SQL Server</span></span>  
 <span data-ttu-id="f799f-121">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="f799f-121">**Server name**</span></span>  
 <span data-ttu-id="f799f-122">當您已經選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目的地時，請輸入或選取目的地伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="f799f-122">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, type or select the destination server name.</span></span>  
  
 <span data-ttu-id="f799f-123">**[使用 Windows 驗證]**</span><span class="sxs-lookup"><span data-stu-id="f799f-123">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="f799f-124">當您已經選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目的地時，請指定是否使用 Windows 整合式驗證連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="f799f-124">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, specify whether to connect to the server by using Windows Integrated Authentication.</span></span> <span data-ttu-id="f799f-125">這是慣用的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="f799f-125">This is the preferred authentication method.</span></span>  
  
 <span data-ttu-id="f799f-126">**[使用 SQL Server 驗證]**</span><span class="sxs-lookup"><span data-stu-id="f799f-126">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="f799f-127">當您已經選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目的地時，請指定是否使用 SQL Server 驗證連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="f799f-127">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, specify whether to connect to the server by using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="f799f-128">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="f799f-128">**User name**</span></span>  
 <span data-ttu-id="f799f-129">當您已經選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目的地，並且指定 SQL Server 驗證時，請輸入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="f799f-129">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, and have specified SQL Server Authentication, type the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user name.</span></span>  
  
 <span data-ttu-id="f799f-130">**密碼**</span><span class="sxs-lookup"><span data-stu-id="f799f-130">**Password**</span></span>  
 <span data-ttu-id="f799f-131">當您已經選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目的地，並且指定 SQL Server 驗證時，請輸入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 密碼。</span><span class="sxs-lookup"><span data-stu-id="f799f-131">When you have selected a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, and have specified SQL Server Authentication, type the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] password.</span></span>  
  
### <a name="target--file-system"></a><span data-ttu-id="f799f-132">目標 = 檔案系統</span><span class="sxs-lookup"><span data-stu-id="f799f-132">Target = File System</span></span>  
 <span data-ttu-id="f799f-133">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="f799f-133">**File name**</span></span>  
 <span data-ttu-id="f799f-134">當您選取檔案目的地時，請輸入目的地檔案的路徑，或使用 [**流覽]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f799f-134">When you have selected a file destination, type the path for the destination file, or use the **Browse** button.</span></span>  
  
 <span data-ttu-id="f799f-135">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="f799f-135">**Browse**</span></span>  
 <span data-ttu-id="f799f-136">當您選取檔案目的地時，請使用 [**儲存封裝**] 對話方塊來流覽至目的地檔案。</span><span class="sxs-lookup"><span data-stu-id="f799f-136">When you have selected a file destination, browse to the destination file by using the **Save Package** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f799f-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f799f-137">See Also</span></span>  
 [<span data-ttu-id="f799f-138">儲存封裝</span><span class="sxs-lookup"><span data-stu-id="f799f-138">Save Packages</span></span>](../save-packages.md)  
  
  
