---
title: 備份資料庫工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.backupdatabasetask.f1
helpviewer_keywords:
- database backups [Integration Services]
- Back Up Database task [Integration Services]
- backing up databases [Integration Services]
- transaction log backups [Integration Services]
- backing up transaction logs [Integration Services]
ms.assetid: b8839d71-13b7-41f2-a434-cb95020e79d7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b0980d89cc915121414dd7d3c89be6f4d72eb715
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593506"
---
# <a name="back-up-database-task"></a><span data-ttu-id="c2c56-102">備份資料庫工作</span><span class="sxs-lookup"><span data-stu-id="c2c56-102">Back Up Database Task</span></span>
  <span data-ttu-id="c2c56-103">「備份資料庫」工作會執行不同類型的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫備份作業。</span><span class="sxs-lookup"><span data-stu-id="c2c56-103">The Back Up Database task performs different types of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database backups.</span></span> <span data-ttu-id="c2c56-104">如需詳細資訊，請參閱 [SQL Server 資料庫的備份與還原](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="c2c56-104">For more information, see [Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
 <span data-ttu-id="c2c56-105">使用「備份資料庫」工作，封裝即可備份單一資料庫或多個資料庫。</span><span class="sxs-lookup"><span data-stu-id="c2c56-105">By using the Back Up Database task, a package can back up a single database or multiple databases.</span></span> <span data-ttu-id="c2c56-106">如果工作僅備份單一資料庫，您可以選擇備份元件：資料庫，或其檔案和檔案群組。</span><span class="sxs-lookup"><span data-stu-id="c2c56-106">If the task backs up only a single database, you can choose the backup component: the database, or its files and filegroups.</span></span>  
  
## <a name="supported-recover-models-and-backup-types"></a><span data-ttu-id="c2c56-107">支援的復原模型和備份類型</span><span class="sxs-lookup"><span data-stu-id="c2c56-107">Supported Recover Models and Backup Types</span></span>  
 <span data-ttu-id="c2c56-108">下表列出「備份資料庫」工作支援的復原模式和備份類型。</span><span class="sxs-lookup"><span data-stu-id="c2c56-108">The following table lists the recovery models and backup types that the Back Up Database task supports.</span></span>  
  
|<span data-ttu-id="c2c56-109">復原模式</span><span class="sxs-lookup"><span data-stu-id="c2c56-109">Recovery model</span></span>|<span data-ttu-id="c2c56-110">資料庫</span><span class="sxs-lookup"><span data-stu-id="c2c56-110">Database</span></span>|<span data-ttu-id="c2c56-111">資料庫差異</span><span class="sxs-lookup"><span data-stu-id="c2c56-111">Database differential</span></span>|<span data-ttu-id="c2c56-112">交易記錄</span><span class="sxs-lookup"><span data-stu-id="c2c56-112">Transaction log</span></span>|<span data-ttu-id="c2c56-113">檔案或檔案差異</span><span class="sxs-lookup"><span data-stu-id="c2c56-113">File or file differential</span></span>|  
|--------------------|--------------|---------------------------|---------------------|-------------------------------|  
|<span data-ttu-id="c2c56-114">Simple</span><span class="sxs-lookup"><span data-stu-id="c2c56-114">Simple</span></span>|<span data-ttu-id="c2c56-115">必要</span><span class="sxs-lookup"><span data-stu-id="c2c56-115">Required</span></span>|<span data-ttu-id="c2c56-116">選用</span><span class="sxs-lookup"><span data-stu-id="c2c56-116">Optional</span></span>|<span data-ttu-id="c2c56-117">不支援</span><span class="sxs-lookup"><span data-stu-id="c2c56-117">Not supported</span></span>|<span data-ttu-id="c2c56-118">不支援</span><span class="sxs-lookup"><span data-stu-id="c2c56-118">Not supported</span></span>|  
|<span data-ttu-id="c2c56-119">完整</span><span class="sxs-lookup"><span data-stu-id="c2c56-119">Full</span></span>|<span data-ttu-id="c2c56-120">必要</span><span class="sxs-lookup"><span data-stu-id="c2c56-120">Required</span></span>|<span data-ttu-id="c2c56-121">選用</span><span class="sxs-lookup"><span data-stu-id="c2c56-121">Optional</span></span>|<span data-ttu-id="c2c56-122">必要</span><span class="sxs-lookup"><span data-stu-id="c2c56-122">Required</span></span>|<span data-ttu-id="c2c56-123">選用</span><span class="sxs-lookup"><span data-stu-id="c2c56-123">Optional</span></span>|  
|<span data-ttu-id="c2c56-124">大量記錄</span><span class="sxs-lookup"><span data-stu-id="c2c56-124">Bulk-logged</span></span>|<span data-ttu-id="c2c56-125">必要</span><span class="sxs-lookup"><span data-stu-id="c2c56-125">Required</span></span>|<span data-ttu-id="c2c56-126">選用</span><span class="sxs-lookup"><span data-stu-id="c2c56-126">Optional</span></span>|<span data-ttu-id="c2c56-127">必要</span><span class="sxs-lookup"><span data-stu-id="c2c56-127">Required</span></span>|<span data-ttu-id="c2c56-128">選用</span><span class="sxs-lookup"><span data-stu-id="c2c56-128">Optional</span></span>|  
  
 <span data-ttu-id="c2c56-129">「備份資料庫」工作會封裝 Transact-SQL BACKUP 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c2c56-129">The Back Up Database task encapsulates a Transact-SQL BACKUP statement.</span></span> <span data-ttu-id="c2c56-130">如需詳細資訊，請參閱 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c2c56-130">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
## <a name="configuration-of-the-back-up-database-task"></a><span data-ttu-id="c2c56-131">備份資料庫工作的組態</span><span class="sxs-lookup"><span data-stu-id="c2c56-131">Configuration of the Back Up Database Task</span></span>  
 <span data-ttu-id="c2c56-132">您可以透過 [ [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師] 設定屬性。</span><span class="sxs-lookup"><span data-stu-id="c2c56-132">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="c2c56-133">這項工作位於「 **設計師」中** [工具箱] **的** [維護計畫工作] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 區段。</span><span class="sxs-lookup"><span data-stu-id="c2c56-133">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="c2c56-134">如需有關可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="c2c56-134">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="c2c56-135">備份資料庫工作 &#40;維護計畫&#41;</span><span class="sxs-lookup"><span data-stu-id="c2c56-135">Back Up Database Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/options-in-the-back-up-database-task-for-maintenance-plan.md)  
  
 <span data-ttu-id="c2c56-136">如需有關如何在「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="c2c56-136">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="c2c56-137">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="c2c56-137">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
  
