---
title: Excel 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7561361c6d4ab7e22282b25367906aa4b75e5bc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595241"
---
# <a name="excel-connection-manager"></a><span data-ttu-id="2c8f5-102">Excel 連接管理員</span><span class="sxs-lookup"><span data-stu-id="2c8f5-102">Excel Connection Manager</span></span>
  <span data-ttu-id="2c8f5-103">Excel 連接管理員可讓封裝連接到現有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 活頁簿檔案。</span><span class="sxs-lookup"><span data-stu-id="2c8f5-103">An Excel connection manager enables a package to connect to an existing [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel workbook file.</span></span> <span data-ttu-id="2c8f5-104">包含的 excel 來源和 excel 目的地 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 使用 excel 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="2c8f5-104">The Excel source and the Excel destination that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include use the Excel connection manager.</span></span>  
  
 <span data-ttu-id="2c8f5-105">當您將 Excel 連接管理員加入封裝時，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會建立一個連接管理員 (該連接管理員在執行階段會被解析為 Excel 連接)、設定連接管理員屬性，並將該連接管理員加入封裝上的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="2c8f5-105">When you add an Excel connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that is resolved as an Excel connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="2c8f5-106">連接管理員的 `ConnectionManagerType` 屬性會設為 `EXCEL`。</span><span class="sxs-lookup"><span data-stu-id="2c8f5-106">The `ConnectionManagerType` property of the connection manager is set to `EXCEL`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2c8f5-107">您不能連接到受密碼保護的 Excel 檔案。</span><span class="sxs-lookup"><span data-stu-id="2c8f5-107">You cannot connect to a password-protected Excel file.</span></span>  
  
## <a name="configuration-of-the-excel-connection-manager"></a><span data-ttu-id="2c8f5-108">設定 Excel 連接管理員</span><span class="sxs-lookup"><span data-stu-id="2c8f5-108">Configuration of the Excel Connection Manager</span></span>  
 <span data-ttu-id="2c8f5-109">您可以利用下列方式設定 Excel 連接管理員：</span><span class="sxs-lookup"><span data-stu-id="2c8f5-109">You can configure the Excel connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="2c8f5-110">指定 Excel 活頁簿檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="2c8f5-110">Specify the path of the Excel workbook file.</span></span>  
  
-   <span data-ttu-id="2c8f5-111">指定用於建立檔案的 Excel 版本。</span><span class="sxs-lookup"><span data-stu-id="2c8f5-111">Specify the version of Excel that was used to create the file.</span></span>  
  
-   <span data-ttu-id="2c8f5-112">指出所選取工作表或範圍中第一個存取資料的資料列是否包含資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="2c8f5-112">Indicate whether the first row of accessed data in the selected worksheets or ranges contains column names.</span></span>  
  
 <span data-ttu-id="2c8f5-113">如果 Excel 來源使用 Excel 連接管理員，擷取的資料中便會包含資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="2c8f5-113">If the Excel connection manager is used by an Excel source, the column names are included with the extracted data.</span></span> <span data-ttu-id="2c8f5-114">如果 Excel 目的地使用 Excel 連接管理員，資料行名稱便會包含在寫入的資料中。</span><span class="sxs-lookup"><span data-stu-id="2c8f5-114">If it is used by an Excel destination, the column names are included in the written data.</span></span>  
  
 <span data-ttu-id="2c8f5-115">Excel 連接管理員會使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 及其支援的 Excel ISAM (Indexed Sequential Access Method，索引循序存取方法) 驅動程式，連接和讀寫資料至 Excel 資料來源。</span><span class="sxs-lookup"><span data-stu-id="2c8f5-115">The Excel connection manager uses the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 and its supporting Excel ISAM (Indexed Sequential Access Method) driver to connect and read and write data to Excel data sources.</span></span> <span data-ttu-id="2c8f5-116">如需此提供者和驅動程式與 Excel 來源和 Excel 目的地搭配使用時之行為的詳細資訊，請參閱[Excel 來源](../data-flow/excel-source.md)和[excel 目的地](../data-flow/excel-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="2c8f5-116">For more information about the behavior of this provider and driver when used with Excel sources and Excel destinations, see [Excel Source](../data-flow/excel-source.md) and [Excel Destination](../data-flow/excel-destination.md).</span></span>  
  
 <span data-ttu-id="2c8f5-117">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="2c8f5-117">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="2c8f5-118">如需可在 [ [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師] 中設定之屬性的詳細資訊，請參閱 [Excel 連線管理員編輯器](../excel-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="2c8f5-118">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Excel Connection Manager Editor](../excel-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="2c8f5-119">如需以程式設計方式設定連線管理員的資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以程式設計方式加入連接](../building-packages-programmatically/adding-connections-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="2c8f5-119">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
 <span data-ttu-id="2c8f5-120">如需循環使用 Excel 檔案群組的資訊，請參閱 [使用 Foreach 迴圈容器來循環使用 Excel 檔案和資料表](../control-flow/foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="2c8f5-120">For information about looping through a group of Excel files, see [Loop through Excel Files and Tables by Using a Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="2c8f5-121">相關工作</span><span class="sxs-lookup"><span data-stu-id="2c8f5-121">Related Tasks</span></span>  
  
-   [<span data-ttu-id="2c8f5-122">使用 Foreach 迴圈容器來執行 Excel 檔案和資料表迴圈</span><span class="sxs-lookup"><span data-stu-id="2c8f5-122">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](../control-flow/foreach-loop-container.md)  
  
-   [<span data-ttu-id="2c8f5-123">使用 SQL Server Integration Services (SSIS) 從 Excel 匯入資料，或將資料匯出至 Excel</span><span class="sxs-lookup"><span data-stu-id="2c8f5-123">Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)</span></span>](../load-data-to-from-excel-with-ssis.md)
  
  
