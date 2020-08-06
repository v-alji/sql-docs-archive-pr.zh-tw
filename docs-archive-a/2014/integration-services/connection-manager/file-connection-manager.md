---
title: 檔案連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- files [Integration Services]
- connection managers [Integration Services], File
- connections [Integration Services], files
- File connection manager
ms.assetid: 019078bc-44ee-4975-9169-0f9a89e3f3be
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cebb5438003c6b14c547d14012ff1bc1175a706d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706621"
---
# <a name="file-connection-manager"></a><span data-ttu-id="045df-102">檔案連接管理員</span><span class="sxs-lookup"><span data-stu-id="045df-102">File Connection Manager</span></span>
  <span data-ttu-id="045df-103">「檔案」連接管理員會啟用封裝以參考現有的檔案或資料夾，或是在執行階段建立檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="045df-103">A File connection manager enables a package to reference an existing file or folder, or to create a file or folder at run time.</span></span> <span data-ttu-id="045df-104">例如，您可以參考 Excel 檔案。</span><span class="sxs-lookup"><span data-stu-id="045df-104">For example, you can reference an Excel file.</span></span> <span data-ttu-id="045df-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的某些元件會使用檔案中資訊來執行其工作。</span><span class="sxs-lookup"><span data-stu-id="045df-105">Certain components in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] use information in files to perform their work.</span></span> <span data-ttu-id="045df-106">例如，「執行 SQL」工作可參考包含工作執行的 SQL 陳述式之檔案。</span><span class="sxs-lookup"><span data-stu-id="045df-106">For example, an Execute SQL task can reference a file that contains the SQL statements that the task executes.</span></span> <span data-ttu-id="045df-107">有些元件則會對檔案執行作業。</span><span class="sxs-lookup"><span data-stu-id="045df-107">Other components perform operations on files.</span></span> <span data-ttu-id="045df-108">例如，檔案系統工作可參考某個檔案以將其複製到新位置。</span><span class="sxs-lookup"><span data-stu-id="045df-108">For example, the File System task can reference a file to copy it to a new location.</span></span>  
  
## <a name="usage-types-of-the-file-connection-manager"></a><span data-ttu-id="045df-109">檔案連接管理員的使用類型</span><span class="sxs-lookup"><span data-stu-id="045df-109">Usage Types of the File Connection Manager</span></span>  
 <span data-ttu-id="045df-110">「檔案」連接管理員的 `FileUsageType` 屬性，會指定如何使用檔案連接。</span><span class="sxs-lookup"><span data-stu-id="045df-110">The `FileUsageType` property of the File connection manager specifies how the file connection is used.</span></span> <span data-ttu-id="045df-111">「檔案」連接管理員可以建立檔案、建立資料夾、使用現有的檔案，或使用現有的資料夾。</span><span class="sxs-lookup"><span data-stu-id="045df-111">The File connection manager can create a file, create a folder, use an existing file, or use an existing folder.</span></span>  
  
 <span data-ttu-id="045df-112">下表列出 `FileUsageType` 的值。</span><span class="sxs-lookup"><span data-stu-id="045df-112">The following table lists the values of `FileUsageType`.</span></span>  
  
|<span data-ttu-id="045df-113">值</span><span class="sxs-lookup"><span data-stu-id="045df-113">Value</span></span>|<span data-ttu-id="045df-114">描述</span><span class="sxs-lookup"><span data-stu-id="045df-114">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="045df-115">「檔案」連接管理員會使用現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="045df-115">File connection manager uses an existing file.</span></span>|  
|`1`|<span data-ttu-id="045df-116">「檔案」連接管理員會建立檔案。</span><span class="sxs-lookup"><span data-stu-id="045df-116">File connection manager creates a file.</span></span>|  
|`2`|<span data-ttu-id="045df-117">「檔案」連接管理員會使用現有的資料夾。</span><span class="sxs-lookup"><span data-stu-id="045df-117">File connection manager uses an existing folder.</span></span>|  
|`3`|<span data-ttu-id="045df-118">「檔案」連接管理員會建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="045df-118">File connection manager creates a folder.</span></span>|  
  
## <a name="multiple-file-or-folder-connections"></a><span data-ttu-id="045df-119">多個檔案或資料夾連接</span><span class="sxs-lookup"><span data-stu-id="045df-119">Multiple File or Folder Connections</span></span>  
 <span data-ttu-id="045df-120">「檔案」連接管理員只能參考一個檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="045df-120">The File connection manager can reference only one file or folder.</span></span> <span data-ttu-id="045df-121">若要參考多個檔案或資料夾，請使用「多個檔案」連接管理員，而非「檔案」連接管理員。</span><span class="sxs-lookup"><span data-stu-id="045df-121">To reference multiple files or folders, use a Multiple Files connection manager instead of a File connection manager.</span></span> <span data-ttu-id="045df-122">如需詳細資訊，請參閱 [Multiple Files Connection Manager](multiple-files-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="045df-122">For more information, see [Multiple Files Connection Manager](multiple-files-connection-manager.md).</span></span>  
  
## <a name="configuration-of-the-file-connection-manager"></a><span data-ttu-id="045df-123">設定檔案連接管理員</span><span class="sxs-lookup"><span data-stu-id="045df-123">Configuration of the File Connection Manager</span></span>  
 <span data-ttu-id="045df-124">當您將「檔案」連接管理員加入封裝時，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會建立連接管理員，用來在執行階段解析為「檔案」連接、設定「檔案」連接屬性，以及將「檔案」連接加入封裝的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="045df-124">When you add a File connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a File connection at run time, sets the File connection properties, and adds the File connection to the `Connections` collection of the package.</span></span>  
  
 <span data-ttu-id="045df-125">連接管理員的 `ConnectionManagerType` 屬性會設為 `FILE`。</span><span class="sxs-lookup"><span data-stu-id="045df-125">The `ConnectionManagerType` property of the connection manager is set to `FILE`.</span></span>  
  
 <span data-ttu-id="045df-126">您可以利用下列方式設定「檔案」連接管理員：</span><span class="sxs-lookup"><span data-stu-id="045df-126">You can configure a File connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="045df-127">指定使用類型。</span><span class="sxs-lookup"><span data-stu-id="045df-127">Specify the usage type.</span></span>  
  
-   <span data-ttu-id="045df-128">指定檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="045df-128">Specify a file or folder.</span></span>  
  
 <span data-ttu-id="045df-129">您可以針對檔案連線管理員來設定 ConnectionString 屬性，其方式是在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的 [屬性] 視窗中指定運算式。</span><span class="sxs-lookup"><span data-stu-id="045df-129">You can set the ConnectionString property for the File connection manager by specifying an expression in the Properties window of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="045df-130">但是，若您在使用運算式來指定檔案或資料夾時想要避免驗證錯誤，請在 **檔案連線管理員編輯器**中針對 **檔案/資料夾**，加入檔案或資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="045df-130">However, to avoid a validation error when you use an expression to specify the file or folder, in the **File Connection Manager Editor**, for **File/Folder**, add a file or folder path.</span></span>  
  
 <span data-ttu-id="045df-131">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="045df-131">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="045df-132">如需可在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計工具中設定之屬性的詳細資訊，請參閱 [File Connection Manager Editor](../file-connection-manager-editor.md)(檔案連線管理員編輯器)。</span><span class="sxs-lookup"><span data-stu-id="045df-132">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [File Connection Manager Editor](../file-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="045df-133">如需以程式設計方式設定連線管理員的資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以程式設計方式加入連接](../building-packages-programmatically/adding-connections-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="045df-133">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
