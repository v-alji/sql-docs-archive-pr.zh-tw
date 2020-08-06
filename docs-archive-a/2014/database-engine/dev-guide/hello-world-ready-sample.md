---
title: Hello World Ready 範例 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: 1cb94266-f702-4a57-a1ae-689a89c98757
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7cc3088af258962a4cec615214147d1f4f09c431
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709870"
---
# <a name="hello-world-ready-sample"></a><span data-ttu-id="0b23f-102">Hello World Ready 範例</span><span class="sxs-lookup"><span data-stu-id="0b23f-102">Hello World Ready Sample</span></span>
  <span data-ttu-id="0b23f-103">Hello World Ready 範例示範涉及建立、部署及測試以簡單全球化整備 Common Language Runtime (CLR) 整合為基礎之預存程序的基本作業。</span><span class="sxs-lookup"><span data-stu-id="0b23f-103">The Hello World Ready sample demonstrates the basic operations that are involved in creating, deploying, and testing a simple world ready common language runtime (CLR) integration-based stored procedure.</span></span> <span data-ttu-id="0b23f-104">全球化整備元件可以輕鬆地當地語系化成全世界不同市場的不同語言，而不變更元件的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="0b23f-104">A world-ready component can be easily localized into different languages for different markets around the world without changing the component's source code.</span></span> <span data-ttu-id="0b23f-105">此範例還示範如何透過輸出參數，以及透過由預存程序動態建構及傳回至用戶端的記錄來傳回資料。此範例與 Hello World 範例幾乎相同，但它可更容易、更安全地當地語系化此應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b23f-105">This sample also demonstrates how to return data through an output parameter and through a record, which is dynamically constructed by the stored procedure and returned to the client.This sample is almost identical to the Hello World Sample except that it is much easier and safer to localize this application.</span></span> <span data-ttu-id="0b23f-106">若要變更當地語系化文字，需要依照以下進行：</span><span class="sxs-lookup"><span data-stu-id="0b23f-106">To change localized text requires the following:</span></span>  
  
1.  <span data-ttu-id="0b23f-107">變更 XML 檔案 (。`resx`</span><span class="sxs-lookup"><span data-stu-id="0b23f-107">Changing an XML file (the .`resx`</span></span> <span data-ttu-id="0b23f-108">resources 目錄中特定文化特性的檔案) </span><span class="sxs-lookup"><span data-stu-id="0b23f-108">file) for the particular culture in the resources directory</span></span>  
  
2.  <span data-ttu-id="0b23f-109">使用 `resgen` 建立文化資源檔</span><span class="sxs-lookup"><span data-stu-id="0b23f-109">Building the culture's resources file by using `resgen`</span></span>  
  
3.  <span data-ttu-id="0b23f-110">為該文化建立已更新的附屬 DLL</span><span class="sxs-lookup"><span data-stu-id="0b23f-110">Building the updated satellite DLL for that culture</span></span>  
  
4.  <span data-ttu-id="0b23f-111">在 SQL Server 中卸除及加入該組件</span><span class="sxs-lookup"><span data-stu-id="0b23f-111">Dropping and adding that assembly in SQL Server</span></span>  
  
 <span data-ttu-id="0b23f-112">CLR 預存程序本身的原始程式碼和組件不會變更。</span><span class="sxs-lookup"><span data-stu-id="0b23f-112">The source code and assembly for the CLR stored procedure itself does not change.</span></span> <span data-ttu-id="0b23f-113">系統會提供 `build.cmd` 指令碼，其示範如何編譯及連結資源組件。雖然應用程式的原始程式碼會根據目前正在執行的組件建立資源管理員，但是您不一定要在包含預存程序的 DLL 中內嵌文化特性中性的資源。</span><span class="sxs-lookup"><span data-stu-id="0b23f-113">A `build.cmd` script is provided which demonstrates how to compile and link the resource assemblies.Although the source code for the application creates a resource manager based the currently executing assembly, you do not have to embed the culture neutral resources in the DLL that contains the stored procedure.</span></span> <span data-ttu-id="0b23f-114">`System.Resources.NeutralResourcesLanguage attribute` 允許文化特性中性的資源存在於附屬 DLL 中。</span><span class="sxs-lookup"><span data-stu-id="0b23f-114">The `System.Resources.NeutralResourcesLanguage attribute` permits the culture-neutral resources to exist in a satellite DLL.</span></span> <span data-ttu-id="0b23f-115">為此最好使用個別的 DLL，如此一來，當需要加入或變更當地語系化文字時，就無須變更包含 CLR 預存程序的主要 DLL。</span><span class="sxs-lookup"><span data-stu-id="0b23f-115">It is much better to use a separate DLL for this purpose so that when localized text needs to be added or changed, the primary DLL that contains the CLR stored procedure does not have to be changed.</span></span> <span data-ttu-id="0b23f-116">這對 CLR 使用者定義型別特別有用，這些型別可能含有資料行及其他相依性，而使得型別難以卸除及重新加入。通常，附屬 DLL 版本必須與主組件版本相同。</span><span class="sxs-lookup"><span data-stu-id="0b23f-116">This is especially useful for CLR user-defined types that might have columns and other dependencies which would make it difficult to drop and re-add the type.Ordinarily, the satellite DLL versions must be identical to the main assembly version.</span></span> <span data-ttu-id="0b23f-117">不過，您也可以使用 `SatelliteContractVersion` 屬性來允許主組件更新，而不更新附屬組件。</span><span class="sxs-lookup"><span data-stu-id="0b23f-117">However, you can use the `SatelliteContractVersion` attribute to allow the main assembly to be updated without updating the satellite assemblies too.</span></span> <span data-ttu-id="0b23f-118">如需詳細資訊，請參閱 Microsoft .NET 文件集中的 `ResourceManager` 類別。</span><span class="sxs-lookup"><span data-stu-id="0b23f-118">For more information, see the `ResourceManager` class in the Microsoft .NET documentation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0b23f-119">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="0b23f-119">Prerequisites</span></span>  
 <span data-ttu-id="0b23f-120">此範例僅適用於 SQL Server 2005 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="0b23f-120">This sample works only with SQL Server 2005 and later versions.</span></span>  
  
 <span data-ttu-id="0b23f-121">若要建立並執行這個專案，您必須安裝下列軟體：</span><span class="sxs-lookup"><span data-stu-id="0b23f-121">To create and run this project the following the following software must be installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0b23f-122">或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express。</span><span class="sxs-lookup"><span data-stu-id="0b23f-122">or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="0b23f-123">您可以從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 文件集和範例[網站](https://www.microsoft.com/sql-server/sql-server-editions-express)免費取得 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express</span><span class="sxs-lookup"><span data-stu-id="0b23f-123">You can obtain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express free of charge from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [Web site](https://www.microsoft.com/sql-server/sql-server-editions-express)</span></span>  
  
-   <span data-ttu-id="0b23f-124">您可以從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 開發人員[網站](https://go.microsoft.com/fwlink/?linkid=62796)取得 AdventureWorks 資料庫</span><span class="sxs-lookup"><span data-stu-id="0b23f-124">The AdventureWorks database that is available at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer [Web site](https://go.microsoft.com/fwlink/?linkid=62796)</span></span>  
  
-   <span data-ttu-id="0b23f-125">.NET Framework SDK 2.0 或更新版本或是 Microsoft Visual Studio 2005 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0b23f-125">.NET Framework SDK 2.0 or later or Microsoft Visual Studio 2005 or later.</span></span> <span data-ttu-id="0b23f-126">您可以免費取得 .NET Framework SDK。</span><span class="sxs-lookup"><span data-stu-id="0b23f-126">You can obtain .NET Framework SDK free of charge.</span></span>  
  
-   <span data-ttu-id="0b23f-127">此外，您也必須符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="0b23f-127">In addition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="0b23f-128">您所使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體必須啟用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="0b23f-128">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using must have CLR integration enabled.</span></span>  
  
-   <span data-ttu-id="0b23f-129">若要啟用 CLR 整合，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="0b23f-129">In order to enable CLR integration, perform the following steps:</span></span>  
  
    #### <a name="enabling-clr-integration"></a><span data-ttu-id="0b23f-130">啟用 CLR 整合</span><span class="sxs-lookup"><span data-stu-id="0b23f-130">Enabling CLR Integration</span></span>  
  
    -   <span data-ttu-id="0b23f-131">執行下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令：</span><span class="sxs-lookup"><span data-stu-id="0b23f-131">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] commands:</span></span>  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  <span data-ttu-id="0b23f-132">若要啟用 CLR 整合，您必須擁有 `ALTER SETTINGS` 伺服器層級權限，此權限是由系統管理員 (`sysadmin`) 和伺服器管理員 (`serveradmin`) 固定伺服器角色的成員以隱含方式持有。</span><span class="sxs-lookup"><span data-stu-id="0b23f-132">To enable CLR, you must have `ALTER SETTINGS` server level permission, which is implicitly held by members of the `sysadmin` and `serveradmin` fixed server roles.</span></span>  
  
-   <span data-ttu-id="0b23f-133">AdventureWorks 資料庫必須安裝在您所使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上。</span><span class="sxs-lookup"><span data-stu-id="0b23f-133">The AdventureWorks database must be installed on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using.</span></span>  
  
-   <span data-ttu-id="0b23f-134">如果您不是正在使用之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的管理員，則必須讓管理員授與您 **CreateAssembly** 權限來完成安裝。</span><span class="sxs-lookup"><span data-stu-id="0b23f-134">If you are not an administrator for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using, you must have an administrator grant you **CreateAssembly**  permission to complete the installation.</span></span>  
  
## <a name="building-the-sample"></a><span data-ttu-id="0b23f-135">建立範例</span><span class="sxs-lookup"><span data-stu-id="0b23f-135">Building the Sample</span></span>  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a><span data-ttu-id="0b23f-136">使用下列指示來建立並執行範例：</span><span class="sxs-lookup"><span data-stu-id="0b23f-136">Create and run the sample by using the following instructions:</span></span>  
  
1.  <span data-ttu-id="0b23f-137">開啟 Visual Studio 或 .NET Framework 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="0b23f-137">Open a Visual Studio or .NET Framework command prompt.</span></span>  
  
2.  <span data-ttu-id="0b23f-138">必要時，請建立範例的目錄。</span><span class="sxs-lookup"><span data-stu-id="0b23f-138">If necessary, create a directory for your sample.</span></span> <span data-ttu-id="0b23f-139">在此範例中，我們將使用 C:\MySample。</span><span class="sxs-lookup"><span data-stu-id="0b23f-139">For this example, we will use C:\MySample.</span></span>  
  
3.  <span data-ttu-id="0b23f-140">在 c:\MySample 中，建立 `HelloWorld.vb` (適用於 Visual Basic 範例) 或 `HelloWorld.cs` (適用於 C# 範例) 並將適當的 Visual Basic 或 C# 範例程式碼 (下面) 複製到檔案中。</span><span class="sxs-lookup"><span data-stu-id="0b23f-140">In c:\MySample, create `HelloWorld.vb` (for the Visual Basic sample) or `HelloWorld.cs` (for the C# sample) and copy the appropriate Visual Basic or C# sample code (below) into the file.</span></span>  
  
4.  <span data-ttu-id="0b23f-141">在 c:\MySample 中，建立 `messages.resx` 檔案並將範例程式碼複製到此檔案中。</span><span class="sxs-lookup"><span data-stu-id="0b23f-141">In c:\MySample, create the file `messages.resx` and copy the sample code into the file.</span></span>  
  
5.  <span data-ttu-id="0b23f-142">在 c:\MySample 中，將檔案 `messages.de.resx` 儲存在 `messages.resx` `messages.de.resx` 變更行之後，以建立檔案</span><span class="sxs-lookup"><span data-stu-id="0b23f-142">In c:\MySample, create the file `messages.de.resx` by saving the file `messages.resx` as `messages.de.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="0b23f-143">若要讀取</span><span class="sxs-lookup"><span data-stu-id="0b23f-143">To read</span></span>  
  
    -   `<value xml:space="preserve">Hallo Welt!</value>`  
  
6.  <span data-ttu-id="0b23f-144">在 c:\MySample 中，將檔案 `messages.es.resx` 儲存在 `messages.resx` `messages.es.resx` 變更行之後，以建立檔案</span><span class="sxs-lookup"><span data-stu-id="0b23f-144">In c:\MySample, create the file `messages.es.resx` by saving the file `messages.resx` as `messages.es.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="0b23f-145">若要讀取</span><span class="sxs-lookup"><span data-stu-id="0b23f-145">To read</span></span>  
  
    -   `<value xml:space="preserve">Hola a todos</value>`  
  
7.  <span data-ttu-id="0b23f-146">在 c:\MySample 中，將檔案 `messages.fr.resx` 儲存在 `messages.resx` `messages.fr.resx` 變更行之後，以建立檔案</span><span class="sxs-lookup"><span data-stu-id="0b23f-146">In c:\MySample, create the file `messages.fr.resx` by saving the file `messages.resx` as `messages.fr.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="0b23f-147">若要讀取</span><span class="sxs-lookup"><span data-stu-id="0b23f-147">To read</span></span>  
  
    -   `<value xml:space="preserve">BonjourÂ !</value>`  
  
8.  <span data-ttu-id="0b23f-148">在 c:\MySample 中，將檔案 `messages.fr-FR.resx` 儲存在 `messages.resx` `messages.fr-FR.resx` 變更行之後，以建立檔案</span><span class="sxs-lookup"><span data-stu-id="0b23f-148">In c:\MySample, create the file `messages.fr-FR.resx` by saving the file `messages.resx` as `messages.fr-FR.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="0b23f-149">若要讀取</span><span class="sxs-lookup"><span data-stu-id="0b23f-149">To read</span></span>  
  
    -   `<value xml:space="preserve">Bonjour de France!</value>`  
  
9. <span data-ttu-id="0b23f-150">在 c:\MySample 中，將檔案 `messages.it.resx` 儲存在 `messages.resx` `messages.it.resx` 變更行之後，以建立檔案</span><span class="sxs-lookup"><span data-stu-id="0b23f-150">In c:\MySample, create the file `messages.it.resx` by saving the file `messages.resx` as `messages.it.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="0b23f-151">若要讀取</span><span class="sxs-lookup"><span data-stu-id="0b23f-151">To read</span></span>  
  
    -   `<value xml:space="preserve">Buongiorno</value>`  
  
10. <span data-ttu-id="0b23f-152">在 c:\MySample 中，將檔案 `messages.ja.resx` 儲存在 `messages.resx` `messages.ja.resx` 變更行之後，以建立檔案</span><span class="sxs-lookup"><span data-stu-id="0b23f-152">In c:\MySample, create the file `messages.ja.resx` by saving the file `messages.resx` as `messages.ja.resx` after changing the line</span></span>  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   <span data-ttu-id="0b23f-153">若要讀取</span><span class="sxs-lookup"><span data-stu-id="0b23f-153">To read</span></span>  
  
    -   <span data-ttu-id="0b23f-154">`<value xml:space="preserve">` `ã"ã‚"ã«ã¡ã¯</value>`</span><span class="sxs-lookup"><span data-stu-id="0b23f-154">`<value xml:space="preserve">` `ã"ã‚"ã«ã¡ã¯</value>`</span></span>  
  
11. <span data-ttu-id="0b23f-155">在 c:\MySample 中，建立 `build.com` 檔案並將範例程式碼複製到此檔案中。</span><span class="sxs-lookup"><span data-stu-id="0b23f-155">In c:\MySample, create the file `build.com` and copy the sample code into the file</span></span>  
  
12. <span data-ttu-id="0b23f-156">執行在命令提示字元中建立的檔案，藉以建立附屬組件。</span><span class="sxs-lookup"><span data-stu-id="0b23f-156">Build the satellite assembles by executing the file build at the command prompt.</span></span>  
  
13. <span data-ttu-id="0b23f-157">在命令列提示字元中執行下列其中一段程式碼，藉以編譯範例程式碼：</span><span class="sxs-lookup"><span data-stu-id="0b23f-157">Compile the sample code from the command line prompt by executing the one of the following:</span></span>  
  
    -   `Vbc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll /out:HelloWorldReady.dll /target:library HelloWorld.vb`  
  
    -   `Csc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.XML.dll /out:HelloWorldReady.dll /target:library Hello.csCopy the tsql installation code into a file and save it as Install.sql in the sample directory.`  
  
14. <span data-ttu-id="0b23f-158">如果此範例安裝在 `C:\MySample\` 以外的目錄中，請依照指示編輯 `Install.sql` 檔案，以指向該位置。</span><span class="sxs-lookup"><span data-stu-id="0b23f-158">If the sample is installed in a directory other then `C:\MySample\`, edit the file `Install.sql` as indicated to point to that location.</span></span>  
  
15. <span data-ttu-id="0b23f-159">部署組件和預存程序，方法是執行</span><span class="sxs-lookup"><span data-stu-id="0b23f-159">Deploy the assembly and stored procedure by executing</span></span>  
  
    -   `sqlcmd -E -I -i install.sql`  
  
16. <span data-ttu-id="0b23f-160">將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 測試命令腳本複製到檔案中，並將它儲存成 `test.sql` 範例目錄中的。</span><span class="sxs-lookup"><span data-stu-id="0b23f-160">Copy [!INCLUDE[tsql](../../includes/tsql-md.md)] test command script into a file and save it as `test.sql` in the sample directory.</span></span>  
  
17. <span data-ttu-id="0b23f-161">使用下列命令來執行測試指令碼</span><span class="sxs-lookup"><span data-stu-id="0b23f-161">Execute the test script with the following command</span></span>  
  
    -   `sqlcmd -E -I -i test.sql`  
  
18. <span data-ttu-id="0b23f-162">將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 清除指令碼複製到檔案中，並將它儲存成範例目錄中的 `cleanup.sql`。</span><span class="sxs-lookup"><span data-stu-id="0b23f-162">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] cleanup script into a file and save it as `cleanup.sql` in the sample directory.</span></span>  
  
19. <span data-ttu-id="0b23f-163">使用下列命令來執行指令碼</span><span class="sxs-lookup"><span data-stu-id="0b23f-163">Execute the script with the  following command</span></span>  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a><span data-ttu-id="0b23f-164">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="0b23f-164">Sample Code</span></span>  
 <span data-ttu-id="0b23f-165">下面是此範例的程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="0b23f-165">The following are the code listings for this sample.</span></span>  
  
 <span data-ttu-id="0b23f-166">C#</span><span class="sxs-lookup"><span data-stu-id="0b23f-166">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Globalization;  
using System.Threading;  
using System.Resources;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
  
[assembly: System.Resources.NeutralResourcesLanguage("", System.Resources.UltimateResourceFallbackLocation.Satellite)]  
[assembly: System.Security.Permissions.SecurityPermissionAttribute(System.Security.Permissions.SecurityAction.RequestMinimum)]  
[assembly: System.Runtime.ConstrainedExecution.ReliabilityContract(System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance, System.Runtime.ConstrainedExecution.Cer.None)]  
  
    public sealed partial class StoredProcedures  
    {  
        private StoredProcedures()  
        {  
        }  
  
        [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1021:AvoidOutParameters"), Microsoft.SqlServer.Server.SqlProcedure]  
        public static void HelloWorldReady(string culture, out string greeting)  
        {  
ResourceManager rm   
= new ResourceManager("Messages",   
Assembly.GetExecutingAssembly());  
  
string message = rm.GetString("HelloWorld", CultureInfo.GetCultureInfo(culture));  
  
            Microsoft.SqlServer.Server.SqlMetaData columnInfo  
                = new Microsoft.SqlServer.Server.SqlMetaData("Column1", SqlDbType.NVarChar, 24);  
            SqlDataRecord greetingRecord  
                = new SqlDataRecord(new Microsoft.SqlServer.Server.SqlMetaData[] { columnInfo });  
            greetingRecord.SetString(0, message);  
            SqlContext.Pipe.Send(greetingRecord);  
            greeting = message;  
        }  
    }  
  
```  
  
 <span data-ttu-id="0b23f-167">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0b23f-167">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Globalization  
Imports System.Resources  
Imports System.Reflection  
Imports System.Runtime.InteropServices  
<Assembly: AssemblyVersion("1.0.*")>   
<Assembly: System.Runtime.InteropServices.ComVisible(False)>   
<Assembly: System.CLSCompliant(True)>   
<Assembly: System.Resources.NeutralResourcesLanguage("", System.Resources.UltimateResourceFallbackLocation.Satellite)>   
<Assembly: System.Security.Permissions.SecurityPermissionAttribute(System.Security.Permissions.SecurityAction.RequestMinimum)>   
<Assembly: System.Runtime.ConstrainedExecution.ReliabilityContract(System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState, Runtime.ConstrainedExecution.Cer.None)>   
  
Partial Public NotInheritable Class StoredProcedures  
    Private Sub New()  
    End Sub  
    <Microsoft.SqlServer.Server.SqlProcedure()> _  
    Public Shared Sub HelloWorldReady(ByVal culture As String, ByRef greeting As String)  
        Dim rm As New ResourceManager("Messages", Assembly.GetExecutingAssembly())  
        Dim message As String = rm.GetString("HelloWorld", CultureInfo.GetCultureInfo(culture))  
        Dim columnInfo As New Microsoft.SqlServer.Server.SqlMetaData("Column1", _  
            SqlDbType.NVarChar, 24)  
        Dim greetingRecord As New SqlDataRecord(New  _  
            Microsoft.SqlServer.Server.SqlMetaData() {columnInfo})  
        greetingRecord.SetString(0, message)  
        SqlContext.Pipe.Send(greetingRecord)  
        greeting = message  
    End Sub  
End Class  
  
```  
  
 <span data-ttu-id="0b23f-168">這是 `build.com`，它會建立附屬組件。</span><span class="sxs-lookup"><span data-stu-id="0b23f-168">This is `build.com`, which builds the satellite assemblies.</span></span>  
  
```  
resgen Messages.resx  
resgen Messages.de.resx  
resgen Messages.es.resx  
resgen Messages.fr.resx  
resgen Messages.fr-Fr.resx  
resgen Messages.it.resx  
resgen Messages.ja.resx  
if not exist de/ mkdir de  
if not exist es/ mkdir es  
if not exist fr/ mkdir fr  
if not exist fr-FR/ mkdir fr-FR  
if not exist it/ mkdir it  
if not exist ja/ mkdir ja  
al /t:lib /culture:de /embed:Messages.de.resources /out:de\HelloWorldReady.resources.dll  
al /t:lib /culture:es /embed:Messages.es.resources /out:es\HelloWorldReady.resources.dll  
al /t:lib /culture:fr /embed:Messages.fr.resources /out:fr\HelloWorldReady.resources.dll  
al /t:lib /culture:fr-FR /embed:Messages.fr-FR.resources /out:fr-FR\HelloWorldReady.resources.dll  
al /t:lib /culture:it /embed:Messages.it.resources /out:it\HelloWorldReady.resources.dll  
al /t:lib /culture:ja /embed:Messages.ja.resources /out:ja\HelloWorldReady.resources.dll  
al /t:lib /culture:"" /embed:Messages.resources /out:HelloWorldReady.resources.dll  
```  
  
 <span data-ttu-id="0b23f-169">這是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 安裝指令碼 (`Install.sql`)，它會部署組件並在資料庫中建立預存程序。</span><span class="sxs-lookup"><span data-stu-id="0b23f-169">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`Install.sql`), which deploys the assemblies and creates the stored procedure within the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
-- Drop existing sproc and assembly if any.  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorldReady')  
DROP PROCEDURE usp_HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady')  
DROP ASSEMBLY HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.neutral')  
DROP ASSEMBLY [HelloWorldReady.resources.neutral]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.de')  
DROP ASSEMBLY [HelloWorldReady.resources.de]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.es')  
DROP ASSEMBLY [HelloWorldReady.resources.es]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr')  
DROP ASSEMBLY [HelloWorldReady.resources.fr]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr-FR')  
DROP ASSEMBLY [HelloWorldReady.resources.fr-FR]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.it')  
DROP ASSEMBLY [HelloWorldReady.resources.it]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.ja')  
DROP ASSEMBLY [HelloWorldReady.resources.ja]  
GO  
  
DECLARE @SamplesPath nvarchar(1024)  
-- You may need to modify the value of this variable if you have installed the sample someplace other than the default location.  
Set @SamplesPath = N'C:\MySample\'  
  
-- Add the assembly and CLR integration based stored procedure  
  
CREATE ASSEMBLY HelloWorldReady  
FROM @SamplesPath + 'HelloWorldReady.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.neutral]  
FROM @SamplesPath + 'HelloWorldReady.resources.dll'  
WITH permission_set = Safe;   
  
CREATE ASSEMBLY [HelloWorldReady.resources.de]  
FROM @SamplesPath + '\de\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.es]  
FROM @SamplesPath + '\es\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.fr]  
FROM @SamplesPath + '\fr\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.fr-FR]  
FROM @SamplesPath + '\fr-FR\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.it]  
FROM @SamplesPath + '\it\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.ja]  
FROM @SamplesPath + '\ja\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
GO  
  
CREATE PROCEDURE usp_HelloWorldReady  
(  
@Culture NVarchar(12),  
@Greeting NVarchar(24) OUTPUT  
)  
AS EXTERNAL NAME HelloWorldReady.StoredProcedures.HelloWorldReady;  
GO  
  
USE master;  
GO  
```  
  
 <span data-ttu-id="0b23f-170">這是 `test.sql`，它會在每個地區設定上執行函數，藉以測試範例。</span><span class="sxs-lookup"><span data-stu-id="0b23f-170">This is `test.sql`, which tests the sample by executing the functions on each locale.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
DECLARE @GreetingDe nvarchar(24);  
DECLARE @GreetingDe_CH nvarchar(24);  
DECLARE @GreetingEn nvarchar(24);  
DECLARE @GreetingEs nvarchar(24);  
DECLARE @GreetingFr nvarchar(24);  
DECLARE @GreetingFr_FR nvarchar(24);  
DECLARE @GreetingIt nvarchar(24);  
DECLARE @GreetingJa nvarchar(24);  
  
--German as spoken anywhere in the world (the neutral German culture)  
EXEC usp_HelloWorldReady 'de', @GreetingDe OUTPUT;  
--German as spoken in Switzerland.  Because we don't have a specific assembly  
--for this case, the .NET Framework will automatically fall back to the neutral German culture DLL.  
EXEC usp_HelloWorldReady 'de-CH', @GreetingDe_CH OUTPUT;  
EXEC usp_HelloWorldReady 'en', @GreetingEn OUTPUT;  
EXEC usp_HelloWorldReady 'es', @GreetingEs OUTPUT;  
--French as spoken anywhere in the world (the neutral French culture)  
EXEC usp_HelloWorldReady 'fr', @GreetingFr OUTPUT  
--French as spoken in France.  Since we do have a specific assembly for this case, a specific   
--greeting is provided from that DLL.  The neutral French culture DLL is not used in this case.  
EXEC usp_HelloWorldReady 'fr-FR', @GreetingFr_FR OUTPUT  
EXEC usp_HelloWorldReady 'it', @GreetingIt OUTPUT;  
EXEC usp_HelloWorldReady 'ja', @GreetingJa OUTPUT;  
  
SELECT @GreetingDe AS OUTPUT_PARAMETER_DE;  
SELECT @GreetingDe_CH AS OUTPUT_PARAMETER_De_CH;  
SELECT @GreetingEn AS OUTPUT_PARAMETER_EN;  
SELECT @GreetingEs AS OUTPUT_PARAMETER_ES;  
SELECT @GreetingFr AS OUTPUT_PARAMETER_FR;  
SELECT @GreetingFr_FR AS OUTPUT_PARAMETER_Fr_FR;  
SELECT @GreetingIt AS OUTPUT_PARAMETER_IT;  
SELECT @GreetingJa AS OUTPUT_PARAMETER_JA;  
  
GO  
```  
  
 <span data-ttu-id="0b23f-171">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 會從資料庫中移除組件和預存程序。</span><span class="sxs-lookup"><span data-stu-id="0b23f-171">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the assemblies and stored procedure from the database.</span></span>  
  
```  
USE AdventureWorks;  
GO  
  
-- Drop existing sproc and assembly if any.  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorldReady')  
DROP PROCEDURE usp_HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady')  
DROP ASSEMBLY HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.neutral')  
DROP ASSEMBLY [HelloWorldReady.resources.neutral]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.de')  
DROP ASSEMBLY [HelloWorldReady.resources.de]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.es')  
DROP ASSEMBLY [HelloWorldReady.resources.es]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr')  
DROP ASSEMBLY [HelloWorldReady.resources.fr]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr-FR')  
DROP ASSEMBLY [HelloWorldReady.resources.fr-FR]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.it')  
DROP ASSEMBLY [HelloWorldReady.resources.it]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.ja')  
DROP ASSEMBLY [HelloWorldReady.resources.ja]  
GO  
  
USE master;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b23f-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b23f-172">See Also</span></span>  
 [<span data-ttu-id="0b23f-173">通用語言執行平台 &#40;CLR&#41; 整合的使用案例和範例</span><span class="sxs-lookup"><span data-stu-id="0b23f-173">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
