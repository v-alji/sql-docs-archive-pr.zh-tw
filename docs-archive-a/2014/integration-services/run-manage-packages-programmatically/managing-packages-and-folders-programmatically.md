---
title: 以程式設計方式管理套件與資料夾 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], managing
- custom enumerators [Integration Services]
ms.assetid: ec59b75d-ba09-44ac-9039-9d593bb462d9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 695ff4ad020dbdfb2564b4964a55324db4248517
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707662"
---
# <a name="managing-packages-and-folders-programmatically"></a><span data-ttu-id="e0381-102">以程式設計方式管理封裝與資料夾</span><span class="sxs-lookup"><span data-stu-id="e0381-102">Managing Packages and Folders Programmatically</span></span>
  <span data-ttu-id="e0381-103">當您以程式設計方式使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝時，您可能想要判斷個別的封裝或資料夾是否存在，或是管理儲存封裝的資料夾。</span><span class="sxs-lookup"><span data-stu-id="e0381-103">As you work programmatically with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you may want to determine whether an individual package or folder exists, or to manage the folders in which packages are stored.</span></span> <span data-ttu-id="e0381-104"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 命名空間的 <xref:Microsoft.SqlServer.Dts.Runtime> 類別，提供各種方法以滿足這些需求。</span><span class="sxs-lookup"><span data-stu-id="e0381-104">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides a variety of methods to satisfy these requirements.</span></span>  
  
##  <a name="determining-whether-a-package-or-folder-exists"></a><a name="exists"></a> <span data-ttu-id="e0381-105">判斷套件或資料夾是否存在</span><span class="sxs-lookup"><span data-stu-id="e0381-105">Determining Whether a Package or Folder Exists</span></span>  
 <span data-ttu-id="e0381-106">若要以程式設計方式判斷儲存的封裝是否存在，請在嘗試載入和執行封裝之前，呼叫下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="e0381-106">To determine programmatically whether a saved package exists, call one of the following methods before attempting to load and run the package:</span></span>  
  
|<span data-ttu-id="e0381-107">儲存位置</span><span class="sxs-lookup"><span data-stu-id="e0381-107">Storage Location</span></span>|<span data-ttu-id="e0381-108">要呼叫的方法</span><span class="sxs-lookup"><span data-stu-id="e0381-108">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="e0381-109">SSIS 封裝存放區</span><span class="sxs-lookup"><span data-stu-id="e0381-109">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|  
  
 <span data-ttu-id="e0381-110">若要以程式設計方式判斷資料夾是否存在，請在嘗試列出資料夾中儲存的封裝之前，呼叫下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="e0381-110">To determine programmatically whether a folder exists, call one of the following methods before attempting to list the packages stored in the folder, :</span></span>  
  
|<span data-ttu-id="e0381-111">儲存位置</span><span class="sxs-lookup"><span data-stu-id="e0381-111">Storage Location</span></span>|<span data-ttu-id="e0381-112">要呼叫的方法</span><span class="sxs-lookup"><span data-stu-id="e0381-112">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="e0381-113">SSIS 封裝存放區</span><span class="sxs-lookup"><span data-stu-id="e0381-113">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|  
  

  
##  <a name="managing-packages-and-folders"></a><a name="managing"></a> <span data-ttu-id="e0381-114">管理套件與資料夾</span><span class="sxs-lookup"><span data-stu-id="e0381-114">Managing Packages and Folders</span></span>  
 <span data-ttu-id="e0381-115"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 命名空間的 <xref:Microsoft.SqlServer.Dts.Runtime> 類別，提供管理封裝及儲存封裝之資料夾的其他方法。</span><span class="sxs-lookup"><span data-stu-id="e0381-115">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides additional methods for managing packages and the folders in which they are stored.</span></span>  
  
###  <a name="removing-a-package"></a><a name="managing_rempkg"></a> <span data-ttu-id="e0381-116">移除套件</span><span class="sxs-lookup"><span data-stu-id="e0381-116">Removing a Package</span></span>  
 <span data-ttu-id="e0381-117">若要以程式設計方式移除儲存的封裝，請呼叫下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="e0381-117">To remove a saved package programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="e0381-118">儲存位置</span><span class="sxs-lookup"><span data-stu-id="e0381-118">Storage Location</span></span>|<span data-ttu-id="e0381-119">要呼叫的方法</span><span class="sxs-lookup"><span data-stu-id="e0381-119">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="e0381-120">SSIS 封裝存放區</span><span class="sxs-lookup"><span data-stu-id="e0381-120">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromSqlServer%2A>|  
  

  
###  <a name="creating-a-folder"></a><a name="managing_create"></a> <span data-ttu-id="e0381-121">建立資料夾</span><span class="sxs-lookup"><span data-stu-id="e0381-121">Creating a Folder</span></span>  
 <span data-ttu-id="e0381-122">若要以程式設計方式建立儲存資料夾，請呼叫下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="e0381-122">To create a storage folder programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="e0381-123">儲存位置</span><span class="sxs-lookup"><span data-stu-id="e0381-123">Storage Location</span></span>|<span data-ttu-id="e0381-124">要呼叫的方法</span><span class="sxs-lookup"><span data-stu-id="e0381-124">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="e0381-125">SSIS 封裝存放區</span><span class="sxs-lookup"><span data-stu-id="e0381-125">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnSqlServer%2A>|  
  

  
###  <a name="removing-a-folder"></a><a name="managing_remfldr"></a> <span data-ttu-id="e0381-126">移除資料夾</span><span class="sxs-lookup"><span data-stu-id="e0381-126">Removing a Folder</span></span>  
 <span data-ttu-id="e0381-127">若要以程式設計方式移除儲存資料夾，請呼叫下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="e0381-127">To remove a storage folder programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="e0381-128">儲存位置</span><span class="sxs-lookup"><span data-stu-id="e0381-128">Storage Location</span></span>|<span data-ttu-id="e0381-129">要呼叫的方法</span><span class="sxs-lookup"><span data-stu-id="e0381-129">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="e0381-130">SSIS 封裝存放區</span><span class="sxs-lookup"><span data-stu-id="e0381-130">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromSqlServer%2A>|  
  
  
  
###  <a name="renaming-a-folder"></a><a name="managing_rename"></a> <span data-ttu-id="e0381-131">重新命名資料夾</span><span class="sxs-lookup"><span data-stu-id="e0381-131">Renaming a Folder</span></span>  
 <span data-ttu-id="e0381-132">若要以程式設計方式重新命名儲存資料夾，請呼叫下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="e0381-132">To rename a storage folder programmatically, call one of the following methods:</span></span>  
  
|<span data-ttu-id="e0381-133">儲存位置</span><span class="sxs-lookup"><span data-stu-id="e0381-133">Storage Location</span></span>|<span data-ttu-id="e0381-134">要呼叫的方法</span><span class="sxs-lookup"><span data-stu-id="e0381-134">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="e0381-135">SSIS 封裝存放區</span><span class="sxs-lookup"><span data-stu-id="e0381-135">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnSqlServer%2A>|  
  

  
<span data-ttu-id="e0381-136">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="e0381-136">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e0381-137">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="e0381-137">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e0381-138">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="e0381-138">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e0381-139">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="e0381-139">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0381-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0381-140">See Also</span></span>  
 <span data-ttu-id="e0381-141">[套件管理 &#40;SSIS 服務&#41;](../service/package-management-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="e0381-141">[Package Management &#40;SSIS Service&#41;](../service/package-management-ssis-service.md) </span></span>  
 [<span data-ttu-id="e0381-142">以程式設計方式列舉可用的套件</span><span class="sxs-lookup"><span data-stu-id="e0381-142">Enumerating Available Packages Programmatically</span></span>](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  
