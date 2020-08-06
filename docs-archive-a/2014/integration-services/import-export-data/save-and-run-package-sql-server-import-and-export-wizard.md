---
title: 儲存並執行封裝 (SQL Server 匯入和匯出嚮導) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.saveschedule.f1
ms.assetid: b582c462-3d7a-4a4c-a2a2-2c79fedab75a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a23f69bf66ca3355f1e1c62cc42d51e4aea3da5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597925"
---
# <a name="save-and-execute-package-sql-server-import-and-export-wizard"></a><span data-ttu-id="77566-102">儲存並執行封裝 (SQL Server 匯入和匯出精靈)</span><span class="sxs-lookup"><span data-stu-id="77566-102">Save and Execute Package (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="77566-103">使用 [**儲存並執行封裝**] 對話方塊，即可立即執行封裝、儲存以供稍後執行或兩者。</span><span class="sxs-lookup"><span data-stu-id="77566-103">Use the **Save and Execute Package** dialog box to run the package immediately, save it to run later, or both.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77566-104"> 如果您在執行完成之前停止封裝，則不會儲存封裝，即使您選取 **[儲存]** 核取方塊也一樣。</span><span class="sxs-lookup"><span data-stu-id="77566-104">If you stop a package before it finishes running, the package is not saved, even if you selected the **Save** check box.</span></span>  
  
 <span data-ttu-id="77566-105">若要深入瞭解此嚮導，請參閱[SQL Server 匯入和匯出嚮導](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="77566-105">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="77566-106">若要瞭解用來啟動精靈的選項，以及成功執行嚮導所需的許可權，請參閱[執行 SQL Server 匯入和匯出嚮導](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="77566-106">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="77566-107">「SQL Server 匯入和匯出精靈」的用途在於將資料從來源複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="77566-107">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="77566-108">這個精靈也可以為您建立目的地資料庫和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="77566-108">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="77566-109">不過，如果您必須複製多個資料庫或資料表，或複製其他種類的資料庫物件，則應該改用「複製資料庫精靈」。</span><span class="sxs-lookup"><span data-stu-id="77566-109">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="77566-110">如需詳細資訊，請參閱 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="77566-110">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="77566-111">選項</span><span class="sxs-lookup"><span data-stu-id="77566-111">Options</span></span>  
 <span data-ttu-id="77566-112">**立即執行**</span><span class="sxs-lookup"><span data-stu-id="77566-112">**Execute immediately**</span></span>  
 <span data-ttu-id="77566-113">選取此選項即可立即執行封裝。</span><span class="sxs-lookup"><span data-stu-id="77566-113">Select this option to run the package immediately.</span></span>  
  
 <span data-ttu-id="77566-114">**儲存 SSIS 封裝**</span><span class="sxs-lookup"><span data-stu-id="77566-114">**Save SSIS Package**</span></span>  
 <span data-ttu-id="77566-115">儲存封裝供稍後執行，具有立即執行的選項。</span><span class="sxs-lookup"><span data-stu-id="77566-115">Save the package to run later, with the option to run it immediately.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77566-116">在 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 中，無法使用儲存此精靈所建立之封裝的選項。</span><span class="sxs-lookup"><span data-stu-id="77566-116">In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], the option to save the package created by the wizard is not available.</span></span>  
  
 <span data-ttu-id="77566-117">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="77566-117">**SQL Server**</span></span>  
 <span data-ttu-id="77566-118">選取此選項可將封裝儲存至 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` 資料庫。</span><span class="sxs-lookup"><span data-stu-id="77566-118">Select this option to save the package to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77566-119">只有當您已選取 [**儲存 SSIS 封裝**] 選項時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="77566-119">This option is available only if you have selected the **Save SSIS Package** option.</span></span>  
  
 <span data-ttu-id="77566-120">**檔案系統**</span><span class="sxs-lookup"><span data-stu-id="77566-120">**File system**</span></span>  
 <span data-ttu-id="77566-121">選取此選項即可將封裝儲存為具有 .dtsx 副檔名的檔案。</span><span class="sxs-lookup"><span data-stu-id="77566-121">Select this option to save the package as a file that has the .dtsx extension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77566-122">只有當您已選取 [**儲存 SSIS 封裝**] 選項時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="77566-122">This option is available only if you have selected the **Save SSIS Package** option.</span></span>  
  
 <span data-ttu-id="77566-123">**套件保護層級**</span><span class="sxs-lookup"><span data-stu-id="77566-123">**Package protection level**</span></span>  
 <span data-ttu-id="77566-124">從清單中選取保護等級。</span><span class="sxs-lookup"><span data-stu-id="77566-124">Select a protection level from the list.</span></span>  
  
 <span data-ttu-id="77566-125">保護等級會決定保護方法、密碼或使用者金鑰，以及封裝保護的範圍。</span><span class="sxs-lookup"><span data-stu-id="77566-125">The protection level determines the protection method, the password or user key, and the scope of package protection.</span></span> <span data-ttu-id="77566-126">保護可包括所有資料或只包括機密資料。</span><span class="sxs-lookup"><span data-stu-id="77566-126">Protection can include all data or sensitive data only.</span></span> <span data-ttu-id="77566-127">若要瞭解封裝安全性的需求和選項，請參閱[封裝中的敏感性資料存取控制](../security/access-control-for-sensitive-data-in-packages.md)和[安全性總覽 &#40;Integration Services&#41;](../security/security-overview-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="77566-127">To understand the requirements and options for package security, see [Access Control for Sensitive Data in Packages](../security/access-control-for-sensitive-data-in-packages.md) and [Security Overview &#40;Integration Services&#41;](../security/security-overview-integration-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77566-128">只有當您已選取 [**儲存 SSIS 封裝**] 選項時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="77566-128">This option is available only if you have selected the **Save SSIS Package** option.</span></span>  
  
 <span data-ttu-id="77566-129">**密碼**</span><span class="sxs-lookup"><span data-stu-id="77566-129">**Password**</span></span>  
 <span data-ttu-id="77566-130">輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="77566-130">Type a password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77566-131">只有在您已將 [**封裝保護等級**] 選項設定為 [以**密碼加密機密資料**] 或 [**以密碼加密所有資料**] 時，才可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="77566-131">This option is available only if you have set the **Package protection level** option to either **Encrypt sensitive data with password** or **Encrypt all data with password**.</span></span>  
  
 <span data-ttu-id="77566-132">**再次輸入密碼**</span><span class="sxs-lookup"><span data-stu-id="77566-132">**Retype password**</span></span>  
 <span data-ttu-id="77566-133">再輸入密碼一次。</span><span class="sxs-lookup"><span data-stu-id="77566-133">Type the password again.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77566-134">只有在您已將 [**封裝保護等級**] 選項設定為 [以**密碼加密機密資料**] 或 [**以密碼加密所有資料**] 時，才可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="77566-134">This option is available only if you have set the **Package protection level** option to either **Encrypt sensitive data with password** or **Encrypt all data with password**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77566-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77566-135">See Also</span></span>  
 <span data-ttu-id="77566-136">[執行專案和套件](../packages/run-integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="77566-136">[Execution of Projects and Packages](../packages/run-integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="77566-137">儲存封裝</span><span class="sxs-lookup"><span data-stu-id="77566-137">Save Packages</span></span>](../save-packages.md)  
  
  
