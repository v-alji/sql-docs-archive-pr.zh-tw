---
title: 多個檔案連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- Multiple Files connection manager
- connection managers [Integration Services], Multiple Files
- connections [Integration Services], files
- multiple file connections
ms.assetid: 10bdc56e-c5cd-4ddb-b2f7-375fe57fe8b2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9ebd45aa4f0794d98be6a79125bf1874913d491
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599138"
---
# <a name="multiple-files-connection-manager"></a><span data-ttu-id="5b530-102">多個檔案連接管理員</span><span class="sxs-lookup"><span data-stu-id="5b530-102">Multiple Files Connection Manager</span></span>
  <span data-ttu-id="5b530-103">「多個檔案」連接管理員會啟用封裝以參考現有的檔案和資料夾，或是在執行階段建立檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="5b530-103">A Multiple Files connection manager enables a package to reference existing files and folders, or to create files and folders at run time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b530-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的內建工作和資料流程元件不會使用「多個檔案」連接管理員。</span><span class="sxs-lookup"><span data-stu-id="5b530-104">The built-in tasks and data flow components in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] do not use the Multiple Files connection manager.</span></span> <span data-ttu-id="5b530-105">但是，您可以在指令碼工作或指令碼元件中使用這個連接管理員。</span><span class="sxs-lookup"><span data-stu-id="5b530-105">However, you can use this connection manager in the Script task or Script component.</span></span> <span data-ttu-id="5b530-106">如需有關如何在指令碼工作中使用連接管理員的資訊，請參閱＜ [連接至指令碼工作中的資料來源](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5b530-106">For information about how to use connection managers in the Script task, see [Connecting to Data Sources in the Script Task](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md).</span></span> <span data-ttu-id="5b530-107">如需如何在腳本元件中使用連線管理員的詳細資訊，請參閱 [連接到腳本元件中的資料來源] (。/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md.</span><span class="sxs-lookup"><span data-stu-id="5b530-107">For information about how to use connection managers in the Script component, see [Connecting to Data Sources in the Script Component](../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md.</span></span>  
  
## <a name="usage-types-of-the-multiple-files-connection-manager"></a><span data-ttu-id="5b530-108">多個檔案連接管理員的使用類型</span><span class="sxs-lookup"><span data-stu-id="5b530-108">Usage Types of the Multiple Files Connection Manager</span></span>  
 <span data-ttu-id="5b530-109">「多個檔案」連接管理員的 `FileUsageType` 屬性會指定如何使用連接。</span><span class="sxs-lookup"><span data-stu-id="5b530-109">The `FileUsageType` property of the Multiple Files connection manager specifies how the connection is used.</span></span> <span data-ttu-id="5b530-110">「多個檔案」連接管理員可以建立檔案、建立資料夾、使用現有的檔案，以及使用現有的資料夾。</span><span class="sxs-lookup"><span data-stu-id="5b530-110">The Multiple Files connection manager can create files, create folders, use existing files, and use existing folders.</span></span>  
  
 <span data-ttu-id="5b530-111">下表列出 `FileUsageType` 的值。</span><span class="sxs-lookup"><span data-stu-id="5b530-111">The following table lists the values of `FileUsageType`.</span></span>  
  
|<span data-ttu-id="5b530-112">值</span><span class="sxs-lookup"><span data-stu-id="5b530-112">Value</span></span>|<span data-ttu-id="5b530-113">描述</span><span class="sxs-lookup"><span data-stu-id="5b530-113">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5b530-114">**0**</span><span class="sxs-lookup"><span data-stu-id="5b530-114">**0**</span></span>|<span data-ttu-id="5b530-115">「多個檔案」連接管理員會使用現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="5b530-115">Multiple Files connection manager uses an existing file.</span></span>|  
|<span data-ttu-id="5b530-116">**1**</span><span class="sxs-lookup"><span data-stu-id="5b530-116">**1**</span></span>|<span data-ttu-id="5b530-117">「多個檔案」連接管理員會建立檔案。</span><span class="sxs-lookup"><span data-stu-id="5b530-117">Multiple Files connection manager creates a file.</span></span>|  
|<span data-ttu-id="5b530-118">**2**</span><span class="sxs-lookup"><span data-stu-id="5b530-118">**2**</span></span>|<span data-ttu-id="5b530-119">「多個檔案」連接管理員會使用現有的資料夾。</span><span class="sxs-lookup"><span data-stu-id="5b530-119">Multiple Files connection manager uses an existing folder.</span></span>|  
|<span data-ttu-id="5b530-120">**3**</span><span class="sxs-lookup"><span data-stu-id="5b530-120">**3**</span></span>|<span data-ttu-id="5b530-121">「多個檔案」連接管理員會建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="5b530-121">Multiple Files connection manager creates a folder.</span></span>|  
  
## <a name="configuration-of-the-multiple-files-connection-manager"></a><span data-ttu-id="5b530-122">設定多個檔案連接管理員</span><span class="sxs-lookup"><span data-stu-id="5b530-122">Configuration of the Multiple Files Connection Manager</span></span>  
 <span data-ttu-id="5b530-123">當您將「多個檔案」連接管理員加入封裝時，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會建立連接管理員，用來在執行階段解析為「多個檔案」連接、設定「多個檔案」連接屬性，以及將「多個檔案」連接加入封裝的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="5b530-123">When you add a Multiple Files connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a Multiple Files connection at run time, sets the Multiple Files connection properties, and adds the Multiple Files connection to the `Connections` collection of the package.</span></span>  
  
 <span data-ttu-id="5b530-124">連接管理員的 `ConnectionManagerType` 屬性會設為 `MULTIFILE`。</span><span class="sxs-lookup"><span data-stu-id="5b530-124">The `ConnectionManagerType` property of the connection manager is set to `MULTIFILE`.</span></span>  
  
 <span data-ttu-id="5b530-125">您可以利用下列方式設定「多個檔案」連接管理員：</span><span class="sxs-lookup"><span data-stu-id="5b530-125">You can configure a Multiple Files connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="5b530-126">指定檔案和資料夾的使用類型。</span><span class="sxs-lookup"><span data-stu-id="5b530-126">Specify the usage type of files and folders.</span></span>  
  
-   <span data-ttu-id="5b530-127">指定檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="5b530-127">Specify files and folders.</span></span>  
  
-   <span data-ttu-id="5b530-128">如果使用多個檔案和資料夾，請指定存取這些檔案和資料夾的順序。</span><span class="sxs-lookup"><span data-stu-id="5b530-128">If using multiple files or folders, specify the order in which the files and folders are accessed.</span></span>  
  
 <span data-ttu-id="5b530-129">如果「多個檔案」連接管理員參考多個檔案和資料夾，則檔案和資料夾的路徑會以垂直線 (|) 字元隔開。</span><span class="sxs-lookup"><span data-stu-id="5b530-129">If the Multiple Files connection manager references multiple files and folders, the paths of the files and folders are separated by the pipe (|) character.</span></span> <span data-ttu-id="5b530-130">連接管理員的 `ConnectionString` 屬性具有下列格式：</span><span class="sxs-lookup"><span data-stu-id="5b530-130">The `ConnectionString` property of the connection manager has the following format:</span></span>  
  
 \<*path*>|\<*path*>  
  
 <span data-ttu-id="5b530-131">您也可以使用萬用字元來指定多個檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="5b530-131">You can also specify multiple files or folders using wildcard characters.</span></span> <span data-ttu-id="5b530-132">例如，若要參考 C 磁片磁碟機上的所有文字檔，屬性的值 `ConnectionString` 可以設定為 c： \\ \* .txt。</span><span class="sxs-lookup"><span data-stu-id="5b530-132">For example, to reference all the text files on the C drive, the value of the `ConnectionString` property can be set to C:\\*.txt.</span></span>  
  
 <span data-ttu-id="5b530-133">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="5b530-133">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="5b530-134">如需可在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計工具中設定之屬性的詳細資訊，請參閱 [加入檔案連接管理員對話方塊 UI 參考](add-file-connection-manager-dialog-box-ui-reference.md)(加入 [檔案連線管理員] 對話方塊 UI 參考)。</span><span class="sxs-lookup"><span data-stu-id="5b530-134">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Add File Connection Manager Dialog Box UI Reference](add-file-connection-manager-dialog-box-ui-reference.md).</span></span>  
  
 <span data-ttu-id="5b530-135">如需以程式設計方式設定連線管理員的資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以程式設計方式加入連接](../building-packages-programmatically/adding-connections-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="5b530-135">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
