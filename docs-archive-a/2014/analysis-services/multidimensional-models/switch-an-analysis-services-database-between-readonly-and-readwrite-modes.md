---
title: 在 ReadOnly 和 ReadWrite 模式之間切換 Analysis Services 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ReadOnly property
- ReadWriteMode command
- operations [Analysis Services - multidimensional data]
ms.assetid: 4eff8181-08dd-4fad-b091-d400fc21a020
author: minewiskan
ms.author: owend
ms.openlocfilehash: 757aedd985d969f932deacf5599716078021a1af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686501"
---
# <a name="switch-an-analysis-services-database-between-readonly-and-readwrite-modes"></a><span data-ttu-id="157a4-102">在 ReadOnly 和 ReadWrite 模式之間切換 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="157a4-102">Switch an Analysis Services database between ReadOnly and ReadWrite modes</span></span>
  <span data-ttu-id="157a4-103">通常在很多情況下，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫管理員 (dba) 會想要變更表格式或多維度資料庫的讀取/寫入模式。</span><span class="sxs-lookup"><span data-stu-id="157a4-103">There are often situations when a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database administrator (dba) wants to change the read/write mode of a tabular or multidimensional database.</span></span> <span data-ttu-id="157a4-104">這些情況通常是由商務需求所驅使，例如在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器集區之間共用資料庫，以便改善使用者經驗。</span><span class="sxs-lookup"><span data-stu-id="157a4-104">These situations are often driven by business needs, such as sharing the database among a pool of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] servers for a better user experience.</span></span>  
  
 <span data-ttu-id="157a4-105">您可以使用許多方式來切換資料庫模式。</span><span class="sxs-lookup"><span data-stu-id="157a4-105">A database mode can be switched in many ways.</span></span> <span data-ttu-id="157a4-106">本文件將說明下列常見狀況：</span><span class="sxs-lookup"><span data-stu-id="157a4-106">This document explains the following common scenarios:</span></span>  
  
-   <span data-ttu-id="157a4-107">以互動方式使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="157a4-107">Interactively using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
  
-   <span data-ttu-id="157a4-108">以程式設計方式使用 AMO</span><span class="sxs-lookup"><span data-stu-id="157a4-108">Programmatically using AMO</span></span>  
  
-   <span data-ttu-id="157a4-109">依據指令碼使用 XMLA</span><span class="sxs-lookup"><span data-stu-id="157a4-109">By script using XMLA</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="157a4-110">程序</span><span class="sxs-lookup"><span data-stu-id="157a4-110">Procedures</span></span>  
  
#### <a name="to-switch-the-readwrite-mode-of-a-database-interactively-using-management-studio"></a><span data-ttu-id="157a4-111">以互動方式使用 Management Studio 來切換資料庫的讀取/寫入模式</span><span class="sxs-lookup"><span data-stu-id="157a4-111">To switch the read/write mode of a database interactively using Management Studio</span></span>  
  
1.  <span data-ttu-id="157a4-112">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 的左窗格或右窗格中，找出要切換的資料庫。</span><span class="sxs-lookup"><span data-stu-id="157a4-112">Locate the database to be switched in the left or right pane of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="157a4-113">以滑鼠右鍵按一下資料庫，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="157a4-113">Right-click the database and select **Properties**.</span></span> <span data-ttu-id="157a4-114">尋找資料庫資料夾並記下位置。</span><span class="sxs-lookup"><span data-stu-id="157a4-114">Find the database folder and note the location.</span></span> <span data-ttu-id="157a4-115">空白的資料庫儲存位置是表示該資料庫資料夾位於伺服器資料中。</span><span class="sxs-lookup"><span data-stu-id="157a4-115">An empty database storage location indicates that the database folder is located in the server data folder.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="157a4-116">一旦資料庫卸離之後，[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 便無法再協助您取得資料庫位置。</span><span class="sxs-lookup"><span data-stu-id="157a4-116">As soon as the database is detached, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] can no longer help you obtain the database location.</span></span>  
  
3.  <span data-ttu-id="157a4-117">以滑鼠右鍵按一下資料庫，然後選取 [卸**離**]。</span><span class="sxs-lookup"><span data-stu-id="157a4-117">Right-click the database and select **Detach...**</span></span>  
  
4.  <span data-ttu-id="157a4-118">將密碼指派給要卸離的資料庫，然後按一下 [確定]\*\*\*\* 執行卸離命令。</span><span class="sxs-lookup"><span data-stu-id="157a4-118">Assign a password to the database to be detached, and then click **OK** to execute the detach command.</span></span>  
  
5.  <span data-ttu-id="157a4-119">在的左窗格或右窗格中，找出 [**資料庫**] 資料夾 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="157a4-119">Locate the **Databases** folder in the left or right pane of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
6.  <span data-ttu-id="157a4-120">以滑鼠右鍵按一下 [**資料庫**] 資料夾，然後選取 [**附加**]。</span><span class="sxs-lookup"><span data-stu-id="157a4-120">Right-click the **Databases** folder and select **Attach...**</span></span>  
  
7.  <span data-ttu-id="157a4-121">在 [資料夾]\*\*\*\* 文字方塊中，輸入資料庫資料夾的原始位置。</span><span class="sxs-lookup"><span data-stu-id="157a4-121">In the **folder** text box, type the original location of the database folder.</span></span> <span data-ttu-id="157a4-122">或者，您可以使用 [流覽] 按鈕 (**...** ]) 尋找資料庫檔案夾。</span><span class="sxs-lookup"><span data-stu-id="157a4-122">Alternatively, you can use the browse button (**...**) to locate the database folder.</span></span>  
  
8.  <span data-ttu-id="157a4-123">選取資料庫的讀取/寫入模式。</span><span class="sxs-lookup"><span data-stu-id="157a4-123">Select the read/write mode for the database.</span></span>  
  
9. <span data-ttu-id="157a4-124">輸入在步驟3中使用的密碼，然後按一下 **[確定]** 以執行 [附加] 命令。</span><span class="sxs-lookup"><span data-stu-id="157a4-124">Type the password that was used in step 3 and click **OK** to execute the attach command.</span></span>  
  
#### <a name="to-switch-the-readwrite-mode-to-a-database-programmatically-using-amo"></a><span data-ttu-id="157a4-125">以程式設計方式使用 AMO 來切換資料庫的讀取/寫入模式</span><span class="sxs-lookup"><span data-stu-id="157a4-125">To switch the read/write mode to a database programmatically using AMO</span></span>  
  
1.  <span data-ttu-id="157a4-126">在您的 C# 應用程式中，改寫下列範例程式碼並完成指定的工作。</span><span class="sxs-lookup"><span data-stu-id="157a4-126">In your C# application, adapt the following sample code and complete the indicated tasks.</span></span>  
  
 `private void SwitchReadWrite(Server server, string dbName,`  
  
 `ReadWriteMode dbReadWriteMode)`  
  
 `{`  
  
 `if (server.Databases.ContainsName(dbName))`  
  
 `{`  
  
 `Database db;`  
  
 `string databaseLocation;`  
  
 `db = server.Databases[dbName];`  
  
 `databaseLocation = db.DbStorageLocation;`  
  
 `if (databaseLocation == null)`  
  
 `{`  
  
 `string dataDir = server.ServerProperties["DataDir"].Value;`  
  
 `String[] possibleFolders = Directory.GetDirectories(dataDir, string.Concat(dbName,"*"), SearchOption.TopDirectoryOnly);`  
  
 `if (possibleFolders.Length > 1)`  
  
 `{`  
  
 `List<String> sortedFolders = new List<string>(possibleFolders.Length);`  
  
 `sortedFolders.AddRange(possibleFolders);`  
  
 `sortedFolders.Sort();`  
  
 `databaseLocation = sortedFolders[sortedFolders.Count - 1];`  
  
 `}`  
  
 `else`  
  
 `{`  
  
 `databaseLocation = possibleFolders[0];`  
  
 `}`  
  
 `}`  
  
 `db.Detach();`  
  
 `server.Attach(databaseLocation, dbReadWriteMode);`  
  
 `}`  
  
 `}`  
  
1.  <span data-ttu-id="157a4-127">在您的 C# 應用程式中，使用必要的參數來叫用 `SwitchReadWrite()` 。</span><span class="sxs-lookup"><span data-stu-id="157a4-127">In your C# application, invoke `SwitchReadWrite()` with the necessary parameters.</span></span>  
  
2.  <span data-ttu-id="157a4-128">編譯並執行程式碼，以便移動資料庫。</span><span class="sxs-lookup"><span data-stu-id="157a4-128">Compile and execute your code to move the database.</span></span>  
  
#### <a name="to-switch-the-readwrite-mode-to-a-database-by-script-using-xmla"></a><span data-ttu-id="157a4-129">依據指令碼使用 XMLA 來切換資料庫的讀取/寫入模式</span><span class="sxs-lookup"><span data-stu-id="157a4-129">To switch the read/write mode to a database by script using XMLA</span></span>  
  
1.  <span data-ttu-id="157a4-130">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 的左窗格或右窗格中，找出要切換的資料庫。</span><span class="sxs-lookup"><span data-stu-id="157a4-130">Locate the database to be switched in the left or right pane of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="157a4-131">以滑鼠右鍵按一下資料庫，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="157a4-131">Right-click the database and select **Properties**.</span></span> <span data-ttu-id="157a4-132">尋找資料庫資料夾並記下位置。</span><span class="sxs-lookup"><span data-stu-id="157a4-132">Find the database folder and note the location.</span></span> <span data-ttu-id="157a4-133">空白的資料庫儲存位置是表示該資料庫資料夾位於伺服器資料中。</span><span class="sxs-lookup"><span data-stu-id="157a4-133">An empty database storage location indicates that the database folder is located in the server data folder.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="157a4-134">一旦資料庫卸離之後，[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 便無法再協助您取得資料庫位置。</span><span class="sxs-lookup"><span data-stu-id="157a4-134">As soon as the database is detached, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] can no longer help you obtain the database location.</span></span>  
  
3.  <span data-ttu-id="157a4-135">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中開啟新的 XMLA 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="157a4-135">Open a new XMLA tab in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
4.  <span data-ttu-id="157a4-136">複製下列 XMLA 指令碼範本：</span><span class="sxs-lookup"><span data-stu-id="157a4-136">Copy the following script template for XMLA:</span></span>  
  
 `<Detach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Object>`  
  
 `<DatabaseID>%dbName%</DatabaseID>`  
  
 `<Password>%password%</Password>`  
  
 `</Object>`  
  
 `</Detach>`  
  
1.  <span data-ttu-id="157a4-137">將 `%dbName%` 取代成資料庫名稱，而將 `%password%` 取代成密碼。</span><span class="sxs-lookup"><span data-stu-id="157a4-137">Replace `%dbName%` with the name of the database and `%password%` with the password.</span></span> <span data-ttu-id="157a4-138">% 字元屬於範本的一部分，而且您必須移除這些字元。</span><span class="sxs-lookup"><span data-stu-id="157a4-138">The % characters are part of the template and must be removed.</span></span>  
  
2.  <span data-ttu-id="157a4-139">執行 XMLA 命令。</span><span class="sxs-lookup"><span data-stu-id="157a4-139">Execute the XMLA command.</span></span>  
  
3.  <span data-ttu-id="157a4-140">將下列 XMLA 指令碼範本複製到新的 XMLA 索引標籤中：</span><span class="sxs-lookup"><span data-stu-id="157a4-140">Copy the following script template for XMLA in a new XMLA tab</span></span>  
  
 <span data-ttu-id="157a4-141">`<Attach xmlns="https://schemas.microsoft.com/analysisservices/2003` `/engine` `">`</span><span class="sxs-lookup"><span data-stu-id="157a4-141">`<Attach xmlns="https://schemas.microsoft.com/analysisservices/2003` `/engine` `">`</span></span>  
  
 `<Folder>%dbFolder%</Folder>`  
  
 `<ReadWriteMode xmlns="https://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>`  
  
 `</Attach>`  
  
1.  <span data-ttu-id="157a4-142">將 `%dbFolder%` 取代成資料庫資料夾的完整 UNC 路徑、將 `%ReadOnlyMode%` 取代成對應的 `ReadOnly` 或 `ReadWrite` 值，並將 `%password%` 取代成密碼。</span><span class="sxs-lookup"><span data-stu-id="157a4-142">Replace `%dbFolder%` with the complete UNC path of the database folder, `%ReadOnlyMode%` with the corresponding value `ReadOnly` or `ReadWrite`, and `%password%` with the password.</span></span> <span data-ttu-id="157a4-143">% 字元屬於範本的一部分，而且您必須移除這些字元。</span><span class="sxs-lookup"><span data-stu-id="157a4-143">The % characters are part of the template and must be removed.</span></span>  
  
2.  <span data-ttu-id="157a4-144">執行 XMLA 命令。</span><span class="sxs-lookup"><span data-stu-id="157a4-144">Execute the XMLA command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="157a4-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="157a4-145">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <span data-ttu-id="157a4-146">[Microsoft.analysisservices。卸離 \*](/dotnet/api/microsoft.analysisservices.core.database.detach) </span><span class="sxs-lookup"><span data-stu-id="157a4-146">[Microsoft.AnalysisServices.Database.Detach\*](/dotnet/api/microsoft.analysisservices.core.database.detach) </span></span>  
 <span data-ttu-id="157a4-147">[附加和卸離 Analysis Services 資料庫](attach-and-detach-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="157a4-147">[Attach and Detach Analysis Services Databases](attach-and-detach-analysis-services-databases.md) </span></span>  
 <span data-ttu-id="157a4-148">[資料庫儲存位置](database-storage-location.md) </span><span class="sxs-lookup"><span data-stu-id="157a4-148">[Database Storage Location](database-storage-location.md) </span></span>  
 <span data-ttu-id="157a4-149">[資料庫 Readwritemode](database-readwritemodes.md) </span><span class="sxs-lookup"><span data-stu-id="157a4-149">[Database ReadWriteModes](database-readwritemodes.md) </span></span>  
 <span data-ttu-id="157a4-150">[Attach 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element) </span><span class="sxs-lookup"><span data-stu-id="157a4-150">[Attach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element) </span></span>  
 <span data-ttu-id="157a4-151">[Detach 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span><span class="sxs-lookup"><span data-stu-id="157a4-151">[Detach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span></span>  
 <span data-ttu-id="157a4-152">[ReadWriteMode 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element) </span><span class="sxs-lookup"><span data-stu-id="157a4-152">[ReadWriteMode Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element) </span></span>  
 [<span data-ttu-id="157a4-153">DbStorageLocation 元素</span><span class="sxs-lookup"><span data-stu-id="157a4-153">DbStorageLocation Element</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)  
  
  
