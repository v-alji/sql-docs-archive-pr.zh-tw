---
title: Integration Services (SSIS) 和 Studio 環境 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- studio environments [Integration Services]
- tools [Integration Services], Business Intelligence Development Studio
- Business Intelligence Development Studio, Integration Services in
- SQL Server Management Studio [Integration Services]
- SSIS, studio environments
- SQL Server Integration Services, studio environments
- tools [Integration Services], SQL Server Management Studio
ms.assetid: 4eb73e65-d9f3-4ac6-a408-abfa85afc537
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bfe0cf7ef482dce3870db8c730c597daf1d539e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596173"
---
# <a name="integration-services-ssis-and-studio-environments"></a><span data-ttu-id="f2c57-102">Integration Services (SSIS) 和 Studio 環境</span><span class="sxs-lookup"><span data-stu-id="f2c57-102">Integration Services (SSIS) and Studio Environments</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="f2c57-103">包含兩個可搭配 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]使用的 Studio：</span><span class="sxs-lookup"><span data-stu-id="f2c57-103">includes two studios for working with [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="f2c57-104">可用於開發商務解決方案所需的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="f2c57-104">for developing the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages that a business solution requires.</span></span> [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="f2c57-105">會提供 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案，讓您在其中建立封裝。</span><span class="sxs-lookup"><span data-stu-id="f2c57-105">provides the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in which you create packages.</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="f2c57-106">適合用來在實際執行環境中管理套件。</span><span class="sxs-lookup"><span data-stu-id="f2c57-106">for managing packages in a production environment.</span></span>  
  
## <a name="sql-server-data-tools"></a><span data-ttu-id="f2c57-107">SQL Server Data Tools</span><span class="sxs-lookup"><span data-stu-id="f2c57-107">SQL Server Data Tools</span></span>  
 <span data-ttu-id="f2c57-108">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]在  中工作時，您可以執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="f2c57-108">Working in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="f2c57-109">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行 [ 匯入和匯出精靈]，以便建立將資料從來源複製至目的地的基本封裝。</span><span class="sxs-lookup"><span data-stu-id="f2c57-109">Run the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard to create basic packages that copy data from a source to a destination.</span></span>  
  
-   <span data-ttu-id="f2c57-110">建立包含複雜控制流程、資料流程、事件驅動邏輯及記錄的封裝。</span><span class="sxs-lookup"><span data-stu-id="f2c57-110">Create packages that include complex control flow, data flow, event-driven logic, and logging.</span></span>  
  
-   <span data-ttu-id="f2c57-111">[!INCLUDE[ssIS](../includes/ssis-md.md)] 使用「 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]設計師」中的疑難排解及監視功能與  中的偵錯功能，對封裝進行測試及偵錯。</span><span class="sxs-lookup"><span data-stu-id="f2c57-111">Test and debug packages by using the troubleshooting and monitoring features in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, and the debugging features in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="f2c57-112">建立在執行階段更新封裝及封裝物件之屬性的組態。</span><span class="sxs-lookup"><span data-stu-id="f2c57-112">Create configurations that update the properties of packages and package objects at run time.</span></span>  
  
-   <span data-ttu-id="f2c57-113">建立可在其他電腦上安裝封裝及其相依性的部署公用程式。</span><span class="sxs-lookup"><span data-stu-id="f2c57-113">Create a deployment utility that can install packages and their dependencies on other computers.</span></span>  
  
-   <span data-ttu-id="f2c57-114">將封裝的複本儲存至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb 資料庫、[!INCLUDE[ssIS](../includes/ssis-md.md)] 封裝存放區及檔案系統。</span><span class="sxs-lookup"><span data-stu-id="f2c57-114">Save copies of packages to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb database, the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store, and the file system.</span></span>  
  
 <span data-ttu-id="f2c57-115">如需 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]的詳細資訊，請參閱 [SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/hh272686.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f2c57-115">For more information about [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], see [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686.aspx).</span></span>  
  
## <a name="sql-server-management-studio"></a><span data-ttu-id="f2c57-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f2c57-116">SQL Server Management Studio</span></span>  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="f2c57-117">會提供 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務，您可以使用該服務管理封裝、監視執行中封裝以及判斷 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 物件的影響及資料歷程。</span><span class="sxs-lookup"><span data-stu-id="f2c57-117">provides the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service that you use to manage packages, monitor running packages, and determine impact and data lineage for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
 <span data-ttu-id="f2c57-118">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]在  中工作時，您可以執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="f2c57-118">Working in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="f2c57-119">建立資料夾，以便使用對您的組織具有意義的方式組織封裝。</span><span class="sxs-lookup"><span data-stu-id="f2c57-119">Create folders to organize packages in a way that is meaningful to your organization.</span></span>  
  
-   <span data-ttu-id="f2c57-120">使用「執行封裝」公用程式，執行儲存在本機電腦上的封裝。</span><span class="sxs-lookup"><span data-stu-id="f2c57-120">Run packages that are stored on the local computer by using the Execute Package utility.</span></span>  
  
-   <span data-ttu-id="f2c57-121">執行「執行封裝」公用程式產生執行 **dtexec** 命令提示字元公用程式 (dtexec.exe) 時使用的命令列。</span><span class="sxs-lookup"><span data-stu-id="f2c57-121">Run the Execute Package utility to generate a command line to use when you run the **dtexec** command prompt utility (dtexec.exe).</span></span>  
  
-   <span data-ttu-id="f2c57-122">將封裝匯入和匯出 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb 資料庫、「[!INCLUDE[ssIS](../includes/ssis-md.md)] 封裝存放區」及檔案系統。</span><span class="sxs-lookup"><span data-stu-id="f2c57-122">Import and export packages to and from the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb database, the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store, and the file system.</span></span>  
  
