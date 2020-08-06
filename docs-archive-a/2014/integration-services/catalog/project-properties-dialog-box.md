---
title: 專案屬性對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isprojectprop.general.f1
- sql12.ssis.ssms.isprojectprop.permissions.f1
ms.assetid: d5cf52f5-1fe2-438a-98a3-fe117360acf8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 259ad48f2b1f33356243635bbaa5426a5199eccf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700141"
---
# <a name="project-properties-dialog-box"></a><span data-ttu-id="ea9b9-102">專案屬性對話方塊</span><span class="sxs-lookup"><span data-stu-id="ea9b9-102">Project Properties Dialog Box</span></span>
  <span data-ttu-id="ea9b9-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案是部署單位。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-103">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project is a unit of deployment.</span></span> <span data-ttu-id="ea9b9-104">每個專案可以包含封裝、參數和環境參考。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-104">Each project can contain packages, parameters, and environment references.</span></span> <span data-ttu-id="ea9b9-105">專案為安全性物件，且可以定義資料庫主體的權限。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-105">A project is a securable object and can define permissions for database principals.</span></span> <span data-ttu-id="ea9b9-106">重新部署專案時，可以將舊版專案儲存到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目錄中。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-106">When a project is re-deployed, the previous version of the project can be stored in the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] catalog.</span></span>  
  
 <span data-ttu-id="ea9b9-107">專案參數和封裝參數可以用來在執行時間將值指派給封裝內的屬性。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-107">Project parameters and package parameters can be used to assign values to properties within packages at the time of execution.</span></span> <span data-ttu-id="ea9b9-108">有些參數會在封裝執行前要求值。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-108">Some parameters require values before the package can be executed.</span></span> <span data-ttu-id="ea9b9-109">參考環境變數的參數值會要求專案在執行前已具有對應的環境參考。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-109">Parameter values that reference environment variables require that the project has the corresponding environment reference prior to execution.</span></span>  
  
 <span data-ttu-id="ea9b9-110">**您想要做什麼事？**</span><span class="sxs-lookup"><span data-stu-id="ea9b9-110">**What do you want to do?**</span></span>  
  
-   <span data-ttu-id="ea9b9-111">[開啟 [專案屬性] 對話方塊](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="ea9b9-111">[Open the Project Properties dialog box](#open_dialog)</span></span>  
  
-   <span data-ttu-id="ea9b9-112">[設定 [一般] 頁面上的選項](#general)</span><span class="sxs-lookup"><span data-stu-id="ea9b9-112">[Set the options on the General page](#general)</span></span>  
  
-   <span data-ttu-id="ea9b9-113">[設定 [權限] 頁面上的選項](#permissions)</span><span class="sxs-lookup"><span data-stu-id="ea9b9-113">[Set the options on the Permissions page](#permissions)</span></span>  
  
##  <a name="open-the-project-properties-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="ea9b9-114">開啟 [專案屬性] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="ea9b9-114">Open the Project Properties dialog box</span></span>  
  
1.  <span data-ttu-id="ea9b9-115">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="ea9b9-116">您正在連線到裝載 SSISDB 資料庫的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-116">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="ea9b9-117">在 [物件總管] 中，展開樹狀目錄以顯示 **[Integration Services 目錄]** 節點。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-117">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="ea9b9-118">展開 **[SSISDB]** 節點。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-118">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="ea9b9-119">展開包含您要設定其屬性之專案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-119">Expand the folder that contains the project that you want to set properties for.</span></span>  
  
5.  <span data-ttu-id="ea9b9-120">以滑鼠右鍵按一下專案，然後再按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-120">Right-click the project, and then click **Properties**.</span></span>  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> <span data-ttu-id="ea9b9-121">設定 [一般] 頁面上的選項</span><span class="sxs-lookup"><span data-stu-id="ea9b9-121">Set the options on the General page</span></span>  
 <span data-ttu-id="ea9b9-122">使用 [一般] 頁面檢視專案屬性。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-122">Use the General page to view project properties.</span></span>  
  
 <span data-ttu-id="ea9b9-123">**名稱**</span><span class="sxs-lookup"><span data-stu-id="ea9b9-123">**Name**</span></span>  
 <span data-ttu-id="ea9b9-124">列出專案名稱。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-124">Lists the project name.</span></span>  
  
 <span data-ttu-id="ea9b9-125">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="ea9b9-125">**Identifier**</span></span>  
 <span data-ttu-id="ea9b9-126">列出專案識別碼。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-126">Lists the project ID.</span></span>  
  
 <span data-ttu-id="ea9b9-127">**說明**</span><span class="sxs-lookup"><span data-stu-id="ea9b9-127">**Description**</span></span>  
 <span data-ttu-id="ea9b9-128">顯示專案的選擇性描述。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-128">Displays the optional description of the project.</span></span>  
  
 <span data-ttu-id="ea9b9-129">**專案版本**</span><span class="sxs-lookup"><span data-stu-id="ea9b9-129">**Project Version**</span></span>  
 <span data-ttu-id="ea9b9-130">列出專案版本。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-130">Lists the project version.</span></span>  
  
 <span data-ttu-id="ea9b9-131">**部署日期**</span><span class="sxs-lookup"><span data-stu-id="ea9b9-131">**Deployment Date**</span></span>  
 <span data-ttu-id="ea9b9-132">列出部署或重新部署專案的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-132">Lists the date and time the project was deployed or redeployed.</span></span>  
  
##  <a name="set-the-options-on-the-permissions-page"></a><a name="permissions"></a> <span data-ttu-id="ea9b9-133">設定 [權限] 頁面上的選項</span><span class="sxs-lookup"><span data-stu-id="ea9b9-133">Set the options on the Permissions page</span></span>  
 <span data-ttu-id="ea9b9-134">使用 **[權限]** 頁面檢視並設定專案的明確權限。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-134">Use the **Permissions** page to view and set explicit permissions for the project.</span></span>  
  
 <span data-ttu-id="ea9b9-135">瀏覽</span><span class="sxs-lookup"><span data-stu-id="ea9b9-135">Browse</span></span>  
 <span data-ttu-id="ea9b9-136">按一下 [瀏覽]  ，使用 [瀏覽所有主體]  對話方塊選取您要設定其權限的使用者和角色。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-136">Click **Browse** to select users and roles that you want to set permissions for, by using the **Browse All Principals** dialog box.</span></span>  
  
 <span data-ttu-id="ea9b9-137">**名稱**</span><span class="sxs-lookup"><span data-stu-id="ea9b9-137">**Name**</span></span>  
 <span data-ttu-id="ea9b9-138">列出使用者或角色的名稱。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-138">Lists the name of the user or role.</span></span>  
  
 <span data-ttu-id="ea9b9-139">**型別**</span><span class="sxs-lookup"><span data-stu-id="ea9b9-139">**Type**</span></span>  
 <span data-ttu-id="ea9b9-140">列出使用者或角色的類型。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-140">Lists the type of user or role.</span></span>  
  
 <span data-ttu-id="ea9b9-141">**權限**</span><span class="sxs-lookup"><span data-stu-id="ea9b9-141">**Permission**</span></span>  
 <span data-ttu-id="ea9b9-142">列出權限。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-142">Lists the permissions.</span></span>  
  
 <span data-ttu-id="ea9b9-143">**授與者**</span><span class="sxs-lookup"><span data-stu-id="ea9b9-143">**Grantor**</span></span>  
 <span data-ttu-id="ea9b9-144">列出授與權限的使用者或角色。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-144">Lists the user or role that grants the permission.</span></span>  
  
 <span data-ttu-id="ea9b9-145">**授與**</span><span class="sxs-lookup"><span data-stu-id="ea9b9-145">**Grant**</span></span>  
 <span data-ttu-id="ea9b9-146">選取 [授與]  時，會針對使用者會或角色授與權限。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-146">When **Grant** is selected, the permission is granted for the selected user or role.</span></span>  
  
 <span data-ttu-id="ea9b9-147">**拒絕**</span><span class="sxs-lookup"><span data-stu-id="ea9b9-147">**Deny**</span></span>  
 <span data-ttu-id="ea9b9-148">選取 [拒絕]  時，會針對使用者會或角色拒絕權限。</span><span class="sxs-lookup"><span data-stu-id="ea9b9-148">When **Deny** is selected, the permission is denied for the selected user or role.</span></span>  
  
  
