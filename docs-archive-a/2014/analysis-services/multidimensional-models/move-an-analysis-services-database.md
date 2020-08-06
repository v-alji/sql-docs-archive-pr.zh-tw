---
title: 移動 Analysis Services 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- moving databases [Anlysis Services]
- moving databases
- operations [Analysis Services - multidimensional data]
ms.assetid: fa644e5d-e276-445e-98d9-673afcfb83fe
author: minewiskan
ms.author: owend
ms.openlocfilehash: bd9b099ad6765d9caccb9b0af6622eb4aa77d38c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707942"
---
# <a name="move-an-analysis-services-database"></a><span data-ttu-id="ecf43-102">移動 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="ecf43-102">Move an Analysis Services Database</span></span>
  <span data-ttu-id="ecf43-103">通常在很多情況下， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫管理員 (dba) 會想要將多維度或表格式模型資料庫移至不同的位置。</span><span class="sxs-lookup"><span data-stu-id="ecf43-103">There are often situations when an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database administrator (dba) wants to move a multidimensional or tabular model database to a different location.</span></span> <span data-ttu-id="ecf43-104">這些情況通常是由商務需求所驅使，例如將資料庫移至不同的磁碟以提升效能、取得讓資料庫成長的空間，或升級產品。</span><span class="sxs-lookup"><span data-stu-id="ecf43-104">These situations are often driven by business needs, such as moving the database to a different disk for better performance, gaining room for database growth, or to upgrade a product.</span></span>  
  
 <span data-ttu-id="ecf43-105">您可以使用許多方式來移動資料庫。</span><span class="sxs-lookup"><span data-stu-id="ecf43-105">A database can be moved in many ways.</span></span> <span data-ttu-id="ecf43-106">本文件將說明下列常見狀況：</span><span class="sxs-lookup"><span data-stu-id="ecf43-106">This document explains the following common scenarios:</span></span>  
  
-   <span data-ttu-id="ecf43-107">以互動方式使用 SSMS</span><span class="sxs-lookup"><span data-stu-id="ecf43-107">Interactively using SSMS</span></span>  
  
-   <span data-ttu-id="ecf43-108">以程式設計方式使用 AMO</span><span class="sxs-lookup"><span data-stu-id="ecf43-108">Programmatically using AMO</span></span>  
  
-   <span data-ttu-id="ecf43-109">依據指令碼使用 XMLA</span><span class="sxs-lookup"><span data-stu-id="ecf43-109">By script using XMLA</span></span>  
  
 <span data-ttu-id="ecf43-110">所有狀況都會要求使用者存取資料庫資料夾，以及使用某種方法，將檔案移至所需的最終目的地。</span><span class="sxs-lookup"><span data-stu-id="ecf43-110">All scenarios require the user to access the database folder and to use a method for moving the files to the desired final destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ecf43-111">如果您卸離資料庫但沒有指派密碼給它，就會讓資料庫處於不安全的狀態。</span><span class="sxs-lookup"><span data-stu-id="ecf43-111">Detaching a database without assigning a password to it leaves the database in an unsecured state.</span></span> <span data-ttu-id="ecf43-112">我們建議您指派密碼給資料庫，以便保護機密資訊。</span><span class="sxs-lookup"><span data-stu-id="ecf43-112">We recommend assigning a password to the database to protect confidential information.</span></span> <span data-ttu-id="ecf43-113">此外，您應該將對應的存取安全性套用至資料庫資料夾、子資料夾和檔案，防止未經授權的人員存取這些項目。</span><span class="sxs-lookup"><span data-stu-id="ecf43-113">Also, the corresponding access security should be applied to the database folder, sub-folders, and files to prevent unauthorized access to them.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="ecf43-114">程序</span><span class="sxs-lookup"><span data-stu-id="ecf43-114">Procedures</span></span>  
  
#### <a name="moving-a-database-interactively-using-ssms"></a><span data-ttu-id="ecf43-115">以互動方式使用 SSMS 來移動資料庫</span><span class="sxs-lookup"><span data-stu-id="ecf43-115">Moving a database interactively using SSMS</span></span>  
  
1.  <span data-ttu-id="ecf43-116">在 SSMS 的左窗格或右窗格中，找出要移動的資料庫。</span><span class="sxs-lookup"><span data-stu-id="ecf43-116">Locate the database to be moved in the left or right pane of SSMS.</span></span>  
  
2.  <span data-ttu-id="ecf43-117">以滑鼠右鍵按一下資料庫，然後選取 [卸**離**]。</span><span class="sxs-lookup"><span data-stu-id="ecf43-117">Right-click on the database and select **Detach...**</span></span>  
  
3.  <span data-ttu-id="ecf43-118">將密碼指派給要卸離的資料庫，然後按一下 [確定]\*\*\*\* 執行卸離命令。</span><span class="sxs-lookup"><span data-stu-id="ecf43-118">Assign a password to the database to be detached, then click **OK** to execute the detach command.</span></span>  
  
4.  <span data-ttu-id="ecf43-119">您可以使用任何作業系統機制或移動檔案的標準方法，將資料庫資料夾移至新的位置。</span><span class="sxs-lookup"><span data-stu-id="ecf43-119">Use any operating system mechanism or your standard method for moving files to move the database folder to the new location.</span></span>  
  
5.  <span data-ttu-id="ecf43-120">在 SSMS 的左窗格或右窗格中，找出 [資料庫]\*\*\*\* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ecf43-120">Locate the **Databases** folder in the left or right pane of SSMS.</span></span>  
  
6.  <span data-ttu-id="ecf43-121">以滑鼠右鍵按一下 [**資料庫**] 資料夾，然後選取 [**附加**]。</span><span class="sxs-lookup"><span data-stu-id="ecf43-121">Right-click on the **Databases** folder and select **Attach...**</span></span>  
  
7.  <span data-ttu-id="ecf43-122">在 [資料夾]\*\*\*\* 文字方塊中，輸入資料庫資料夾的新位置。</span><span class="sxs-lookup"><span data-stu-id="ecf43-122">In the **folder** text box, type the new location of the database folder.</span></span> <span data-ttu-id="ecf43-123">或者，您可以使用 [流覽] 按鈕 (**...** ]) 尋找資料庫檔案夾。</span><span class="sxs-lookup"><span data-stu-id="ecf43-123">Alternatively, you can use the browse button (**...**) to locate the database folder.</span></span>  
  
8.  <span data-ttu-id="ecf43-124">選取 `ReadWrite` 資料庫的模式。</span><span class="sxs-lookup"><span data-stu-id="ecf43-124">Select the `ReadWrite` mode for the database.</span></span>  
  
9. <span data-ttu-id="ecf43-125">輸入在步驟 3 中使用的密碼，然後按一下 [確定]\*\*\*\* 執行附加命令。</span><span class="sxs-lookup"><span data-stu-id="ecf43-125">Type the password used in step 3 and click **OK** to execute the attach command.</span></span>  
  
#### <a name="moving-a-database-programmatically-using-amo"></a><span data-ttu-id="ecf43-126">以程式設計方式使用 AMO 來移動資料庫</span><span class="sxs-lookup"><span data-stu-id="ecf43-126">Moving a database programmatically using AMO</span></span>  
  
1.  <span data-ttu-id="ecf43-127">在您的 C# 應用程式中，改寫下列範例程式碼並完成指定的工作。</span><span class="sxs-lookup"><span data-stu-id="ecf43-127">In your C# application, adapt the following sample code and complete the indicated tasks.</span></span>  
  
 `private void MoveDb(Server server, string dbName,`  
  
 `string dbInitialLocation, string dbFinalLocation,`  
  
 `string dbPassword, ReadWriteMode dbReadWriteMode)`  
  
 `{`  
  
 `//Verify dbInitialLocation exists before continuing`  
  
 `if (server.Databases.ContainsName(dbName))`  
  
 `{`  
  
 `Database db;`  
  
 `//Save current cursor and change cursor to Cursors.WaitCursor`  
  
 `db = server.Databases[dbName];`  
  
 `db.Detach(dbPassword);`  
  
 `//Add your own code to copy the database files to the destination where you intend to attach the database`  
  
 `//Verify dbFinalLocation exists before continuing`  
  
 `server.Attach(dbFinalLocation, dbReadWriteMode, dbPassword);`  
  
 `//Restore cursor to its original`  
  
 `}`  
  
 `}`  
  
1.  <span data-ttu-id="ecf43-128">在您的 C# 應用程式中，使用必要的參數來叫用 `MoveDb()` 。</span><span class="sxs-lookup"><span data-stu-id="ecf43-128">In your C# application, invoke `MoveDb()` with the necessary parameters.</span></span>  
  
2.  <span data-ttu-id="ecf43-129">編譯並執行程式碼，以便移動資料庫。</span><span class="sxs-lookup"><span data-stu-id="ecf43-129">Compile and execute your code to move the database.</span></span>  
  
#### <a name="moving-a-database-by-script-using-xmla"></a><span data-ttu-id="ecf43-130">依據指令碼使用 XMLA 來移動資料庫</span><span class="sxs-lookup"><span data-stu-id="ecf43-130">Moving a database by script using XMLA</span></span>  
  
1.  <span data-ttu-id="ecf43-131">在 SSMS 中開啟新的 XMLA 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ecf43-131">Open a new XMLA tab in SSMS.</span></span>  
  
2.  <span data-ttu-id="ecf43-132">複製下列 XMLA 指令碼範本：</span><span class="sxs-lookup"><span data-stu-id="ecf43-132">Copy the following script template for XMLA</span></span>  
  
 `<Detach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Object>`  
  
 `<DatabaseID>%dbName%</DatabaseID>`  
  
 `<Password>%password%</Password>`  
  
 `</Object>`  
  
 `</Detach>`  
  
1.  <span data-ttu-id="ecf43-133">將 `%dbName%` 取代成資料庫名稱，而將 `%password%` 取代成密碼。</span><span class="sxs-lookup"><span data-stu-id="ecf43-133">Replace `%dbName%` with the name of the database and `%password%` with the password.</span></span> <span data-ttu-id="ecf43-134">% 字元屬於範本的一部分，而且您必須移除這些字元。</span><span class="sxs-lookup"><span data-stu-id="ecf43-134">The % characters are part of the template and must be removed.</span></span>  
  
2.  <span data-ttu-id="ecf43-135">執行 XMLA 命令。</span><span class="sxs-lookup"><span data-stu-id="ecf43-135">Execute the XMLA command.</span></span>  
  
3.  <span data-ttu-id="ecf43-136">您可以使用任何作業系統機制或移動檔案的標準方法，將資料庫資料夾移至新的位置。</span><span class="sxs-lookup"><span data-stu-id="ecf43-136">Use any operating system mechanism or your standard method for moving files to move the database folder to the new location.</span></span>  
  
4.  <span data-ttu-id="ecf43-137">將下列 XMLA 指令碼範本複製到新的 XMLA 索引標籤中：</span><span class="sxs-lookup"><span data-stu-id="ecf43-137">Copy the following script template for XMLA in a new XMLA tab</span></span>  
  
 `<Attach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Folder>%dbFolder%</Folder>`  
  
 `<ReadWriteMode xmlns="https://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>`  
  
 `</Attach>`  
  
1.  <span data-ttu-id="ecf43-138">將 `%dbFolder%` 取代成資料庫資料夾的完整 UNC 路徑、將 `%ReadOnlyMode%` 取代成對應的 `ReadOnly` 或 `ReadWrite` 值，並將 `%password%` 取代成密碼。</span><span class="sxs-lookup"><span data-stu-id="ecf43-138">Replace `%dbFolder%` with the complete UNC path of the database folder, `%ReadOnlyMode%` with the corresponding value `ReadOnly` or `ReadWrite`, and `%password%` with the password.</span></span> <span data-ttu-id="ecf43-139">% 字元屬於範本的一部分，而且您必須移除這些字元。</span><span class="sxs-lookup"><span data-stu-id="ecf43-139">The % characters are part of the template and must be removed.</span></span>  
  
2.  <span data-ttu-id="ecf43-140">執行 XMLA 命令。</span><span class="sxs-lookup"><span data-stu-id="ecf43-140">Execute the XMLA command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecf43-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecf43-141">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <span data-ttu-id="ecf43-142">[Microsoft.analysisservices。卸離 \*](/dotnet/api/microsoft.analysisservices.core.database.detach) </span><span class="sxs-lookup"><span data-stu-id="ecf43-142">[Microsoft.AnalysisServices.Database.Detach\*](/dotnet/api/microsoft.analysisservices.core.database.detach) </span></span>  
 <span data-ttu-id="ecf43-143">[附加和卸離 Analysis Services 資料庫](attach-and-detach-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="ecf43-143">[Attach and Detach Analysis Services Databases](attach-and-detach-analysis-services-databases.md) </span></span>  
 <span data-ttu-id="ecf43-144">[資料庫儲存位置](database-storage-location.md) </span><span class="sxs-lookup"><span data-stu-id="ecf43-144">[Database Storage Location](database-storage-location.md) </span></span>  
 <span data-ttu-id="ecf43-145">[資料庫 Readwritemode](database-readwritemodes.md) </span><span class="sxs-lookup"><span data-stu-id="ecf43-145">[Database ReadWriteModes](database-readwritemodes.md) </span></span>  
 <span data-ttu-id="ecf43-146">[Attach 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element) </span><span class="sxs-lookup"><span data-stu-id="ecf43-146">[Attach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element) </span></span>  
 <span data-ttu-id="ecf43-147">[Detach 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span><span class="sxs-lookup"><span data-stu-id="ecf43-147">[Detach Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element) </span></span>  
 <span data-ttu-id="ecf43-148">[ReadWriteMode 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element) </span><span class="sxs-lookup"><span data-stu-id="ecf43-148">[ReadWriteMode Element](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element) </span></span>  
 [<span data-ttu-id="ecf43-149">DbStorageLocation 元素</span><span class="sxs-lookup"><span data-stu-id="ecf43-149">DbStorageLocation Element</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)  
  
  
