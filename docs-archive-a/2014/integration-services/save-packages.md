---
title: 儲存套件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, saving
- packages [Integration Services], saving
- saving packages
- SSIS packages, saving
- SQL Server Integration Services packages, saving
ms.assetid: 17c1de2c-637f-45c2-a148-79294bae0af4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 102e2c3eab001c230722bf3485d6ea9731aa99a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706585"
---
# <a name="save-packages"></a><span data-ttu-id="f4cdc-102">儲存封裝</span><span class="sxs-lookup"><span data-stu-id="f4cdc-102">Save Packages</span></span>
  <span data-ttu-id="f4cdc-103">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，您可以使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師來建立封裝，並將封裝儲存為檔案系統中的 XML 檔案 (.dtsx 檔案)。</span><span class="sxs-lookup"><span data-stu-id="f4cdc-103">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] you build packages by using [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer and save the packages to the file system as XML files (.dtsx files).</span></span> <span data-ttu-id="f4cdc-104">您也可以將封裝 XML 檔案的複本儲存至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中的 msdb 資料庫，或儲存至封裝存放區。</span><span class="sxs-lookup"><span data-stu-id="f4cdc-104">You can also save copies of the package XML file to the msdb database in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or to the package store.</span></span> <span data-ttu-id="f4cdc-105">封裝存放區代表 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務所管理之檔案系統位置中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f4cdc-105">The package store represents the folders in the file system location that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages.</span></span>  
  
 <span data-ttu-id="f4cdc-106">如果您將封裝儲存至檔案系統，可以在稍後使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務將封裝匯入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 或匯入封裝存放區。</span><span class="sxs-lookup"><span data-stu-id="f4cdc-106">If you save a package to the file system, you can later use the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service to import the package to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or to the package store.</span></span> <span data-ttu-id="f4cdc-107">如需詳細資訊，請參閱[匯入和匯出封裝 &#40;SSIS 服務&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="f4cdc-107">For more information, see [Import and Export Packages &#40;SSIS Service&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md).</span></span>  
  
 <span data-ttu-id="f4cdc-108">您也可以使用命令提示字元公用程式 **dtutil**，在檔案系統與 msdb 之間複製封裝。</span><span class="sxs-lookup"><span data-stu-id="f4cdc-108">You can also use a command prompt utility, **dtutil**, to copy a package between the file system and msdb.</span></span> <span data-ttu-id="f4cdc-109">如需詳細資訊，請參閱 [dtutil Utility](dtutil-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="f4cdc-109">For more information, see [dtutil Utility](dtutil-utility.md).</span></span>  
  
### <a name="to-save-a-package"></a><span data-ttu-id="f4cdc-110">若要儲存封裝</span><span class="sxs-lookup"><span data-stu-id="f4cdc-110">To save a package</span></span>  
  
-   [<span data-ttu-id="f4cdc-111">將封裝儲存至檔案系統</span><span class="sxs-lookup"><span data-stu-id="f4cdc-111">Save a Package to the File System</span></span>](../../2014/integration-services/save-a-package-to-the-file-system.md)  
  
-   [<span data-ttu-id="f4cdc-112">儲存封裝的複本</span><span class="sxs-lookup"><span data-stu-id="f4cdc-112">Save a Copy of a Package</span></span>](../../2014/integration-services/save-a-copy-of-a-package.md)  
  
  
