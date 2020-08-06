---
title: SQLXML 4.0 SP1 的新功能&#39;Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- SQLNCLI, SQLXML
- what's new [SQLXML]
- SQLXML, what's new
- migrating SQLXML applications
- redistributing SQLXML
- SQL Server Native Client, SQLXML
- side-by-side installations [SQLXML]
ms.assetid: 48f7720b-1705-402d-93ce-097ff1737877
author: rothja
ms.author: jroth
ms.openlocfilehash: 880937520385fbe6ce64be3fdfcbbf7d11c73741
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687750"
---
# <a name="what39s-new-in-sqlxml-40-sp1"></a><span data-ttu-id="cf2c1-102">SQLXML 4.0 SP1 的新功能&#39;</span><span class="sxs-lookup"><span data-stu-id="cf2c1-102">What&#39;s New in SQLXML 4.0 SP1</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="cf2c1-103">SQLXML 4.0 SP1 包含不同的更新和增強功能。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-103">SQLXML 4.0 SP1 includes various updates and enhancements.</span></span> <span data-ttu-id="cf2c1-104">本主題摘要說明更新並提供詳細資訊的連結 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-104">This topic summarizes the updates and provides links to more detailed information, where available.</span></span> <span data-ttu-id="cf2c1-105">SQLXML 4.0 SP1 會提供其他的增強功能以支援 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 中導入的新資料類型。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-105">SQLXML 4.0 SP1 provides additional enhancements to support the new data types introduced in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="cf2c1-106">本主題包含下列主旨：</span><span class="sxs-lookup"><span data-stu-id="cf2c1-106">This topic includes the following subjects:</span></span>  
  
-   <span data-ttu-id="cf2c1-107">安裝 SQLXML 4.0 SP1</span><span class="sxs-lookup"><span data-stu-id="cf2c1-107">Installing SQLXML 4.0 SP1</span></span>  
  
-   <span data-ttu-id="cf2c1-108">並存安裝問題</span><span class="sxs-lookup"><span data-stu-id="cf2c1-108">Side-by-Side Installation Issues</span></span>  
  
-   <span data-ttu-id="cf2c1-109">SQLXML 4.0 和 MSXML</span><span class="sxs-lookup"><span data-stu-id="cf2c1-109">SQLXML 4.0 and MSXML</span></span>  
  
-   <span data-ttu-id="cf2c1-110">轉散發 SQLXML 4.0</span><span class="sxs-lookup"><span data-stu-id="cf2c1-110">Redistributing SQLXML 4.0</span></span>  
  
-   <span data-ttu-id="cf2c1-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client 的支援</span><span class="sxs-lookup"><span data-stu-id="cf2c1-111">Support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span></span>  
  
-   <span data-ttu-id="cf2c1-112">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 所導入資料類型的支援</span><span class="sxs-lookup"><span data-stu-id="cf2c1-112">Support for Data Types Introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]</span></span>  
  
-   <span data-ttu-id="cf2c1-113">SQLXML 4.0 的 XML 大量載入變更</span><span class="sxs-lookup"><span data-stu-id="cf2c1-113">XML Bulk Load Changes for SQLXML 4.0</span></span>  
  
-   <span data-ttu-id="cf2c1-114">SQLXML 4.0 的登錄機碼變更</span><span class="sxs-lookup"><span data-stu-id="cf2c1-114">Registry Key Changes for SQLXML 4.0</span></span>  
  
-   <span data-ttu-id="cf2c1-115">移轉問題</span><span class="sxs-lookup"><span data-stu-id="cf2c1-115">Migration Issues</span></span>  
  
## <a name="installing-sqlxml-40-sp1"></a><span data-ttu-id="cf2c1-116">安裝 SQLXML 4.0 SP1</span><span class="sxs-lookup"><span data-stu-id="cf2c1-116">Installing SQLXML 4.0 SP1</span></span>  
 <span data-ttu-id="cf2c1-117">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 之前的版本中，SQLXML 4.0 隨附於 SQL Server 而且是所有 SQL Server 版本 (SQL Server Express 除外) 之預設安裝的一部分。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-117">Before [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], SQLXML 4.0 was released with SQL Server and was part of the default installation of all SQL Server versions except for SQL Server Express.</span></span> <span data-ttu-id="cf2c1-118">不過，從 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 開始，SQL Server 已不再包含最新版的 SQLXML (SQLXML 4.0 SP1)。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-118">Starting with [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the latest version of SQLXML (SQLXML 4.0 SP1) is no longer included in SQL Server.</span></span> <span data-ttu-id="cf2c1-119">若要安裝 SQLXML 4.0 SP1，請從[sqlxml 4.0 sp1 的安裝位置](https://www.microsoft.com/download/details.aspx?id=30403)下載。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-119">To install SQLXML 4.0 SP1, download it from [Install Location for SQLXML 4.0 SP1](https://www.microsoft.com/download/details.aspx?id=30403).</span></span>  
  
 <span data-ttu-id="cf2c1-120">SQLXML 4.0 SP1 檔案也會安裝於下列位置：</span><span class="sxs-lookup"><span data-stu-id="cf2c1-120">The SQLXML 4.0 SP1 files are installed in the following location:</span></span>  
  
 `%PROGRAMFILES%\SQLXML 4.0\`  
  
> [!NOTE]  
>  <span data-ttu-id="cf2c1-121">所有適當的 SQLXML 4.0 登錄設定都會在安裝程序時進行。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-121">All appropriate registry settings for SQLXML 4.0 are made as part of the installation process.</span></span>  
  
 <span data-ttu-id="cf2c1-122">若要允許 32 位元 SQLXML 應用程式在 64 位元 Windows 作業系統上的 Windows on Windows (WOW64) 下執行，請執行 64 位元 SQLXML 4.0 SP1 封裝 (名稱為 sqlxml4.msi)，您可以在下載中心取得該封裝。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-122">To allow 32-bit SQLXML applications to run under Windows on Windows (WOW64) on 64-bit Windows operating systems, run the 64-bit SQLXML 4.0 SP1 package, named sqlxml4.msi, which can be found on the Download Center.</span></span>  
  
#### <a name="uninstalling-sqlxml-40-sp1"></a><span data-ttu-id="cf2c1-123">解除安裝 SQLXML 4.0 SP1</span><span class="sxs-lookup"><span data-stu-id="cf2c1-123">Uninstalling SQLXML 4.0 SP1</span></span>  
 <span data-ttu-id="cf2c1-124">共用登錄機碼存在於 SQLXML 3.0 SP3、SQLXML 4.0 及 SQLXML 4.0 SP1 之間。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-124">Shared registry keys exist between SQLXML 3.0 SP3, SQLXML 4.0 and SQLXML 4.0 SP1.</span></span> <span data-ttu-id="cf2c1-125">如果包含 SQLXML 3.0 SP3 的相同電腦上已解除安裝 SQLXML 更新版本，您可能需要重新安裝 SQLXML 3.0 SP3。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-125">If the later versions of SQLXML are uninstalled on the same computer which contains SQLXML 3.0 SP3, you might need to reinstall SQLXML 3.0 SP3.</span></span>  
  
## <a name="side-by-side-installation-issues"></a><span data-ttu-id="cf2c1-126">並存安裝問題</span><span class="sxs-lookup"><span data-stu-id="cf2c1-126">Side-by-Side Installation Issues</span></span>  
 <span data-ttu-id="cf2c1-127">SQLXML 4.0 的安裝程序不會移除舊版 SQLXML 所安裝的檔案。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-127">The installation process for SQLXML 4.0 does not remove the files that were installed by earlier versions of SQLXML.</span></span> <span data-ttu-id="cf2c1-128">因此，您的電腦上可能有數個不同版本之 SQLXML 安裝的 DLL。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-128">Therefore, you can have DLLs for several different version-distinctive installations of SQLXML on your computer.</span></span> <span data-ttu-id="cf2c1-129">您可以並行執行這些安裝。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-129">You can run the installations side-by-side.</span></span> <span data-ttu-id="cf2c1-130">SQLXML 4.0 會同時包含與版本無關和與版本相關的 PROGID。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-130">SQLXML 4.0 includes both version-independent and version-dependent PROGIDs.</span></span> <span data-ttu-id="cf2c1-131">所有的實際執行應用程式都應該使用與版本相關的 PROGID。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-131">All production applications should use version-dependent PROGIDs.</span></span>  
  
## <a name="sqlxml-40-sp1-and-msxml"></a><span data-ttu-id="cf2c1-132">SQLXML 4.0 SP1 和 MSXML</span><span class="sxs-lookup"><span data-stu-id="cf2c1-132">SQLXML 4.0 SP1 and MSXML</span></span>  
 <span data-ttu-id="cf2c1-133">SQLXML 4.0 不會安裝 MSXML。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-133">SQLXML 4.0 does not install MSXML.</span></span> <span data-ttu-id="cf2c1-134">SQLXML 4.0 會使用 MSXML 6.0，這會安裝為 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更新版本安裝的一部分。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-134">SQLXML 4.0 uses MSXML 6.0, which is installed as part of the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later installation.</span></span>  
  
## <a name="redistributing-sqlxml-40-sp1"></a><span data-ttu-id="cf2c1-135">轉散發 SQLXML 4.0 SP1</span><span class="sxs-lookup"><span data-stu-id="cf2c1-135">Redistributing SQLXML 4.0 SP1</span></span>  
 <span data-ttu-id="cf2c1-136">您可以使用可轉散發安裝程式套件散發 SQLXML 4.0 SP1。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-136">You can distribute SQLXML 4.0 SP1 using the redistributable installer package.</span></span> <span data-ttu-id="cf2c1-137">使用 Chainer 和 Bootstrapper 技術是安裝多個封裝 (但對使用者卻好像是單一安裝) 的一種方法。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-137">One way to install multiple packages in what seems to the user to be a single installation is to use chainer and bootstrapper technology.</span></span> <span data-ttu-id="cf2c1-138">如需詳細資訊，請參閱＜撰寫適用於 Visual Studio 2005 的自訂啟動載入器封裝＞和＜加入自訂的必要條件＞。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-138">For more information, see Authoring a Custom Bootstrapper Package for Visual Studio 2005 and Adding Custom Prerequisites.</span></span>  
  
 <span data-ttu-id="cf2c1-139">如果應用程式的目標使用平台與當初開發時的平台不同，您可以從 Microsoft 下載中心下載 x64、Itanium 和 x86 版本的 sqlncli.msi。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-139">If your application targets a platform other than the one it was developed on, you can download versions of sqlncli.msi for x64, Itanium, and x86 from the Microsoft Download Center.</span></span>  
  
 <span data-ttu-id="cf2c1-140">MSXML 6.0 (msxml6.msi) 也有個別的轉散發安裝程式。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-140">There are also separate redistribution installation programs for MSXML 6.0 (msxml6.msi).</span></span> <span data-ttu-id="cf2c1-141">您可以在下列位置的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝光碟片上找到這些程式：</span><span class="sxs-lookup"><span data-stu-id="cf2c1-141">These can be found on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation CD in the following location:</span></span>  
  
 `%CD%\Setup\`  
  
 <span data-ttu-id="cf2c1-142">這些安裝檔案可以用於直接從光碟片安裝 MSXML 6.0，</span><span class="sxs-lookup"><span data-stu-id="cf2c1-142">These installation files can be used to install MSXML 6.0 directly from the CD.</span></span> <span data-ttu-id="cf2c1-143">也可以用於搭配您自訂的應用程式隨意同時轉散發 MSXML 6.0 和 SQLXML 4.0 SP1。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-143">They can also be used to freely redistribute MSXML 6.0 along with SQLXML 4.0 SP1 with your own custom applications.</span></span>  
  
 <span data-ttu-id="cf2c1-144">如果您要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 當做應用程式的資料提供者，則也需要轉散發該程式。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-144">You will also need to redistribute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client if you are using it as the data provider with your application.</span></span> <span data-ttu-id="cf2c1-145">如需詳細資訊，請參閱 [安裝 SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-145">For more information, see [Installing SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md).</span></span>  
  
## <a name="support-for-sql-server-native-client"></a><span data-ttu-id="cf2c1-146">SQL Server Native Client 的支援</span><span class="sxs-lookup"><span data-stu-id="cf2c1-146">Support for SQL Server Native Client</span></span>  
 <span data-ttu-id="cf2c1-147">SQLXML 4.0 同時支援 SQLOLEDB 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 提供者。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-147">SQLXML 4.0 supports both the SQLOLEDB and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client providers.</span></span> <span data-ttu-id="cf2c1-148">建議您使用相同版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client 提供者， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native client 的開發目的是要支援伺服器隨附的任何新資料類型，例如 `Date, Time` 中的、 `DateTime2` 和 `dateTimeOffset` 資料類型， [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以及 Native Client 所支援的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-148">It is recommended that you use the same version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client provider and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is developed to support any new data types that ship in the server, such as the `Date, Time`, `DateTime2`, and `dateTimeOffset` data types in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and supported by [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cf2c1-149">Native Client 是 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 導入的資料存取技術。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-149">Native Client is a data access technology that was introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="cf2c1-150">此項技術將 SQLOLEDB Provider 與 SQLODBC Driver 合而為一，成為原生的動態連結程式庫 (DLL)，同時也提供了獨立而有別於 Microsoft Data Access Components (MDAC) 的新功能。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-150">It combines the SQLOLEDB Provider and the SQLODBC Driver into one native dynamic link library (DLL), while also providing new functionality that is separate and distinct from the Microsoft Data Access Components (MDAC).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cf2c1-151">Native Client 可用於建立新的應用程式，或者加強需要利用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所導入功能 (不受 MDAC 中的 SQLOLEDB 和 SQLODBC 以及 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 支援) 的現有應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-151">Native Client can be used to create new applications or enhance existing applications that need to take advantage of features introduced in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are not supported by SQLOLEDB and SQLODBC in MDAC and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.</span></span> <span data-ttu-id="cf2c1-152">例如，用戶端的 SQLXML 功能 (例如 FOR XML) 需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 才能使用 `xml` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-152">For example, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is required for client-side SQLXML features, such as FOR XML, to use the `xml` data type.</span></span> <span data-ttu-id="cf2c1-153">如需詳細資訊，請參閱[用戶端 XML 格式 &#40;SQLXML 4.0&#41;](formatting/client-side-xml-formatting-sqlxml-4-0.md)、[使用 ADO 執行 SQLXML 4.0 查詢](using-ado-to-execute-sqlxml-4-0-queries.md)，以及[SQL Server Native Client 程式設計](../native-client/sql-server-native-client-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-153">For more information, see [Client-side XML Formatting &#40;SQLXML 4.0&#41;](formatting/client-side-xml-formatting-sqlxml-4-0.md), [Using ADO to Execute SQLXML 4.0 Queries](using-ado-to-execute-sqlxml-4-0-queries.md), and [SQL Server Native Client Programming](../native-client/sql-server-native-client-programming.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cf2c1-154">SQLXML 4.0 並非完全與 SQLXML 3.0 回溯相容。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-154">SQLXML 4.0 is not completely backward compatible with SQLXML 3.0.</span></span> <span data-ttu-id="cf2c1-155">因為某些錯誤修正和其他的功能性變更 (特別是 SQLXML ISAPI 支援的移除)，您無法將 IIS 虛擬目錄用於 SQLXML 4.0。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-155">Because of some bug fixes and other functional changes, particularly the removal of SQLXML ISAPI support, you cannot use IIS virtual directories with SQLXML 4.0.</span></span> <span data-ttu-id="cf2c1-156">雖然大部分的應用程式都可以在稍加修改後執行，但在將這些應用程式放入使用 SQLXML 4.0 的生產環境之前，必須先加以測試。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-156">Although most applications will run with minor modifications, you must test them before putting them into production with SQLXML 4.0.</span></span>  
  
## <a name="support-for-data-types-introduced-in-sql-server-2005-and-sql-server-2008"></a><span data-ttu-id="cf2c1-157">支援 SQL Server 2005 及 SQL Server 2008 中導入的資料類型</span><span class="sxs-lookup"><span data-stu-id="cf2c1-157">Support for Data Types Introduced in SQL Server 2005 and SQL Server 2008</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<span data-ttu-id="cf2c1-158">引進了 `xml` 資料類型，而 SQLXML 4.0 支援 `xml` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-158">introduced the `xml` data type, and SQLXML 4.0 supports the `xml` data type.</span></span> <span data-ttu-id="cf2c1-159">如需詳細資訊，請參閱[SQLXML 4.0 中的 Xml 資料類型支援](xml-data-type-support-in-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-159">For more information, see [xml Data Type Support in SQLXML 4.0](xml-data-type-support-in-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="cf2c1-160">如需如何在對應 XML 檢視、大量載入 XML 或執行 XML Updategram 時使用 SQLXML 中的 `xml` 資料類型的範例，請參閱下列主題所提供的範例。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-160">For examples of how to use the `xml` data type in SQLXML when mapping XML views, bulk loading XML or executing XML updategrams, refer to examples provided in the following topics.</span></span>  
  
-   [<span data-ttu-id="cf2c1-161">XSD 元素和屬性對資料表和資料行的預設對應</span><span class="sxs-lookup"><span data-stu-id="cf2c1-161">Default Mapping of XSD Elements and Attributes to Tables and Columns</span></span>](../sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
-   [<span data-ttu-id="cf2c1-162">使用 XML Updategram 插入資料</span><span class="sxs-lookup"><span data-stu-id="cf2c1-162">Inserting Data by Using XML Updategrams</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)  
  
-   [<span data-ttu-id="cf2c1-163">大量載入 XML 文件的範例</span><span class="sxs-lookup"><span data-stu-id="cf2c1-163">Examples of Bulk Loading XML Documents</span></span>](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)  
  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]<span data-ttu-id="cf2c1-164">引進了 `Date, Time` 、 `DateTime2` 和**DateTimeOffset**資料類型。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-164">introduced the `Date, Time`, `DateTime2`, and **DateTimeOffset** data types.</span></span> <span data-ttu-id="cf2c1-165">搭配 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中隨附的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client OLE DB 提供者 (SQLNCLI11) 使用時，SQLXML 4.0 SP1 會將這四個新的資料類型啟用成內建的純量類型。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-165">SQLXML 4.0 SP1 will enable these four new data types as built-in scalar types when used with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client OLE DB Provider (SQLNCLI11), which ships in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="xml-bulk-load-changes-for-sqlxml-40-sp1"></a><span data-ttu-id="cf2c1-166">SQLXML 4.0 SP1 的 XML 大量載入變更</span><span class="sxs-lookup"><span data-stu-id="cf2c1-166">XML Bulk Load Changes for SQLXML 4.0 SP1</span></span>  
  
-   <span data-ttu-id="cf2c1-167">對於 SQLXML 4.0，SchemaGen 溢位欄位是使用 `xml` 資料類型建立的。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-167">For SQLXML 4.0, the SchemaGen overflow field is created using the `xml` data type.</span></span> <span data-ttu-id="cf2c1-168">如需詳細資訊，請參閱[SQL SERVER XML 大量載入物件模型](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/sql-server-xml-bulk-load-object-model-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-168">For more information, see [SQL Server XML Bulk Load Object Model](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/sql-server-xml-bulk-load-object-model-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="cf2c1-169">如果您先前已經建立了 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 應用程式而您想要使用 SQLXML 4.0，則必須使用 Xblkld4.dll 的參考來重新編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-169">If you have previously created [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic applications and you want to use SQLXML 4.0, you must recompile the application with reference to Xblkld4.dll.</span></span>  
  
-   <span data-ttu-id="cf2c1-170">對於 Visual Basic Scripting Edition 應用程式，則必須註冊您要使用的 DLL。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-170">For Visual Basic Scripting Edition applications, you must register the DLL you want to use.</span></span> <span data-ttu-id="cf2c1-171">在下列範例中，如果您指定與版本無關的 PROGID，則應用程式會相依於最後註冊的 DLL：</span><span class="sxs-lookup"><span data-stu-id="cf2c1-171">In the following example, if you specify version-independent PROGIDs, the application depends on the last registered DLL:</span></span>  
  
    ```  
    set objBulkLoad = CreateObject("SQLXMLBulkLoad.SQLXMLBulkLoad")   
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="cf2c1-172">與版本相關的 PROGID 是 SQLXMLBulkLoad.SQLXMLBulkLoad.4.0。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-172">The version-dependent PROGID is SQLXMLBulkLoad.SQLXMLBulkLoad.4.0.</span></span>  
  
## <a name="registry-key-changes-for-sqlxml-40"></a><span data-ttu-id="cf2c1-173">SQLXML 4.0 的登錄機碼變更</span><span class="sxs-lookup"><span data-stu-id="cf2c1-173">Registry Key Changes for SQLXML 4.0</span></span>  
 <span data-ttu-id="cf2c1-174">在 SQLXML 4.0 中，登錄機碼已從舊版變更為下列項目：</span><span class="sxs-lookup"><span data-stu-id="cf2c1-174">In SQLXML 4.0, the registry keys have changed from the earlier releases to the following:</span></span>  
  
 <span data-ttu-id="cf2c1-175">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize</span><span class="sxs-lookup"><span data-stu-id="cf2c1-175">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize</span></span>  
  
 <span data-ttu-id="cf2c1-176">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\SchemaCacheSize</span><span class="sxs-lookup"><span data-stu-id="cf2c1-176">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\SchemaCacheSize</span></span>  
  
 <span data-ttu-id="cf2c1-177">如果您想要這些機碼在 SQLXML 4.0 中生效，就必須變更設定。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-177">You must change the settings if you want these keys to be in effect for SQLXML 4.0.</span></span>  
  
 <span data-ttu-id="cf2c1-178">此外，SQLXML 4.0 還導入了下列的登錄機碼：</span><span class="sxs-lookup"><span data-stu-id="cf2c1-178">In addition, SQLXML 4.0 introduces the following registry keys:</span></span>  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\ReportErrorsWithSQLInfo`  
  
     <span data-ttu-id="cf2c1-179">根據預設，SQLXML 4.0 會傳回 OLE DB 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所提供的原生錯誤資訊，而不是高層級的 SQLXML 錯誤 (舊版 SQLXML 才會提供此類錯誤)。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-179">By default, SQLXML 4.0 returns native error information provided by OLE DB and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instead of a high-level SQLXML error (as was the case in earlier versions of SQLXML).</span></span> <span data-ttu-id="cf2c1-180">如果您不要這項行為，則 DWORD 類型的這個登錄機碼值必須設定為 0 (值設值為 1)。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-180">If you do not want this behavior, the value of this registry key of type DWORD must be set to 0 (default is 1).</span></span>  
  
-   <span data-ttu-id="cf2c1-181">HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\FORXML_GenerateGUIDBraces</span><span class="sxs-lookup"><span data-stu-id="cf2c1-181">HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\FORXML_GenerateGUIDBraces</span></span>  
  
     <span data-ttu-id="cf2c1-182">根據預設，SQLXML 會傳回 SQL Server GUID 值，但沒有外面的大括號。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-182">By default, SQLXML return SQL Server GUID values without the enclosing braces.</span></span> <span data-ttu-id="cf2c1-183">如果您想要以大括弧傳回 GUID 值 (例如，{*某些 guid*} ) ，此登錄機碼的值必須設定為 1 (預設值為 0) 。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-183">If you want the GUID value returned with the braces (for example, {*some GUID*}), value of this registry key must be set to 1 (default is 0).</span></span>  
  
-   <span data-ttu-id="cf2c1-184">HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\SQL2000CompatMode</span><span class="sxs-lookup"><span data-stu-id="cf2c1-184">HKEY_LOCAL_MACHINE\Software\Microsoft\MSSQLServer\Client\SQLXML4\SQL2000CompatMode</span></span>  
  
     <span data-ttu-id="cf2c1-185">根據預設，當 XML 剖析器載入資料時，空格會根據 XML 1.0 規則而正規化。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-185">By default, when the XML parser loads the data, white spaces are normalized according to the XML 1.0 rules.</span></span> <span data-ttu-id="cf2c1-186">這會導致資料中的某些空白字元遺失。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-186">This results in loss of some of the white space characters in your data.</span></span> <span data-ttu-id="cf2c1-187">因此，資料的文字表示法在剖析之後可能不會相同，雖然資料在語意上是相同的。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-187">Thus, the textual representation of your data may not be the same after parsing, although semantically the data is the same.</span></span>  
  
     <span data-ttu-id="cf2c1-188">導入這個機碼的原因，是讓您可以選擇保有資料中的空白字元。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-188">This key is introduced so that you can choose to keep the white space characters in the data.</span></span> <span data-ttu-id="cf2c1-189">如果加入這個登錄機碼並將其值設定為 0，則 XML 中的空白字元 (LF、CR 和索引標籤) 會編碼傳回 (如果使用屬性值)。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-189">If you add this registry key and set its value to 0, white space characters (LF, CR, and tab) in the XML are returned encoded in case of attribute values.</span></span> <span data-ttu-id="cf2c1-190">如果使用元素值，則只有 CR 會編碼傳回。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-190">In case of element values, only CR is returned encoded.</span></span>  
  
     <span data-ttu-id="cf2c1-191">例如：</span><span class="sxs-lookup"><span data-stu-id="cf2c1-191">For example:</span></span>  
  
    ```  
    CREATE TABLE T( Col1 int, Col2 nvarchar(100));  
    GO  
    -- Insert data with tab, line feed and carriage return).  
    INSERT INTO T VALUES (1, 'This is a tab    . This is a line feed and CR   
     more text');  
    GO  
    -- Test this query (without the registry key).  
    SELECT * FROM T   
    FOR XML AUTO;  
    -- This is the result (no encoding of special characters).  
    <?xml version="1.0" encoding="utf-8" ?>  
    <r>  
      <T Col1="1"   
         Col2="This is a tab    . This is a line feed and CR   
     more text"/>  
    </r>  
    -- Now add registry key with value 0 and execute the query again.  
    -- Note the encoding for carriage return, line-feed and tab in the attribute value.  
    <?xml version="1.0" encoding="utf-8" ?>  
    <r>  
      <T Col1="1"   
         Col2="This is a tab    . This is a line feed and CR   
     more text"/>  
    </r>  
  
    -- Update the query and specify ELEMENTS directive  
    SELECT * FROM T  
    FOR XML AUTO, ELEMENTS  
    -- Only the carriage return is returned encoded.  
    <?xml version="1.0" encoding="utf-8" ?>  
    <r>  
       <T>  
          <Col1>1</Col1>  
          <Col2>This is a tab    . This is a line feed and CR   
     more text</Col2>  
       </T>  
    </r>  
    ```  
  
## <a name="migration-issues"></a><span data-ttu-id="cf2c1-192">移轉問題</span><span class="sxs-lookup"><span data-stu-id="cf2c1-192">Migration Issues</span></span>  
 <span data-ttu-id="cf2c1-193">下列問題可能會影響舊版 SQLXML 應用程式到 SQLXML 4.0 的移轉。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-193">The following are issues that could impact migration of your legacy SQLXML applications to SQLXML 4.0.</span></span>  
  
### <a name="ado-and-sqlxml-40-queries"></a><span data-ttu-id="cf2c1-194">ADO 和 SQLXML 4.0 查詢</span><span class="sxs-lookup"><span data-stu-id="cf2c1-194">ADO and SQLXML 4.0 Queries</span></span>  
 <span data-ttu-id="cf2c1-195">在舊版的 SQLXML 中，支援使用 IIS 虛擬目錄和 SQLXML ISAPI 篩選來執行以 URL 為基礎的查詢。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-195">In earlier versions of SQLXML, support for URL-based query execution using IIS virtual directories and the SQLXML ISAPI filter was provided.</span></span> <span data-ttu-id="cf2c1-196">對於使用 SQLXML 4.0 的應用程式，已不再提供這項支援。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-196">For applications that use SQLXML 4.0, this support is no longer available.</span></span>  
  
 <span data-ttu-id="cf2c1-197">反而可以利用在 Microsoft Data Access Components (MDAC) 2.6 和更新版本中初次導入的 ActiveX Data Objects (ADO) 的 SQL XML 延伸模組來執行 SQLXML 查詢、範本和 Updategram。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-197">Instead, SQLXML queries, templates, and updategrams can be executed by using the SQLXML extensions to ActiveX Data Objects (ADO) first introduced in Microsoft Data Access Components (MDAC) 2.6 and later.</span></span>  
  
 <span data-ttu-id="cf2c1-198">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-198">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
### <a name="supportability-for-sqlxml-30-isapi-and-data-types-introduced-in-sql-server-2005"></a><span data-ttu-id="cf2c1-199">SQL Server 2005 所導入之 SQLXML 3.0 ISAPI 和資料類型的可支援性</span><span class="sxs-lookup"><span data-stu-id="cf2c1-199">Supportability for SQLXML 3.0 ISAPI and Data Types Introduced in SQL Server 2005</span></span>  
 <span data-ttu-id="cf2c1-200">因為 ISAPI 支援已從 SQLXML 4.0 中移除，所以如果您的方案需要所導入的增強型資料類型功能 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] （例如[xml 資料類型](/sql/t-sql/xml/xml-transact-sql)或[使用者自訂資料類型） (udt) ](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)和 Web 型存取，您將需要使用另一個解決方案，例如[SQLXML MANAGED 類別](../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md)或其他類型的 HTTP 處理常式（例如，適用于 SQL Server 2005 的原生 xml Web service）。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-200">Because ISAPI support has been removed from SQLXML 4.0, if your solution requires the enhanced data typing features introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] such as the [xml data type](/sql/t-sql/xml/xml-transact-sql) or [user-defined data types (UDTs)](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) and Web-based access, you will need to use another solution such as [SQLXML managed classes](../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md) or another type of HTTP handler, such as Native XML Web Services for SQL Server 2005.</span></span>  
  
 <span data-ttu-id="cf2c1-201">或者，如果您不需要這些類型延伸模組，可以繼續使用 SQLXML 3.0 來連接 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 安裝。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-201">Alternately, if you do not require these type extensions, you can continue to use SQLXML 3.0 to connect to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] installations.</span></span> <span data-ttu-id="cf2c1-202">SQLXML 3.0 ISAPI 支援可以用於這些較新的版本，但並不能支援或辨識 `xml` 中導入的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 資料類型或 UDT 類型支援。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-202">The SQLXML 3.0 ISAPI support will work against these later versions but does not support or recognize the `xml` data type or UDT type support introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
### <a name="xml-bulk-load-security-changes-for-temporary-files"></a><span data-ttu-id="cf2c1-203">暫存檔案的 XML 大量載入安全性變更</span><span class="sxs-lookup"><span data-stu-id="cf2c1-203">XML Bulk Load Security Changes for Temporary Files</span></span>  
 <span data-ttu-id="cf2c1-204">對於 SQLXML 4.0 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，XML 大量載入檔案權限會授與執行大量載入作業的使用者。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-204">For SQLXML 4.0 and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], XML Bulk Load file permissions are granted to the user executing the bulk load operation.</span></span> <span data-ttu-id="cf2c1-205">讀取和寫入權限則是繼承自檔案系統。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-205">Read and Write permissions are inherited from the file system.</span></span> <span data-ttu-id="cf2c1-206">在舊版的 SQLXML 和 SQL Server 中，在 SQLXML 下進行 XML 大量載入會建立暫存檔，這些暫存檔並未受到保護，可由任何人讀取。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-206">In previous releases of SQLXML and SQL Server, XML Bulk Load under SQLXML would create temporary files that were not secured and could be readable by anyone.</span></span>  
  
### <a name="migration-issues-for-client-side-for-xml"></a><span data-ttu-id="cf2c1-207">用戶端 FOR XML 的移轉問題</span><span class="sxs-lookup"><span data-stu-id="cf2c1-207">Migration Issues for Client-Side FOR XML</span></span>  
 <span data-ttu-id="cf2c1-208">由於執行引擎的變更，如果在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 下執行 FOR XML 查詢，可能會在基表的中繼資料中傳回不同的值 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-208">Due to changes in the execution engine, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might return different values in the metadata for a base table than would be returned if the FOR XML query was executed under [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="cf2c1-209">發生這種情況時，FOR XML 查詢結果的用戶端格式設定會依照用來執行查詢的版本而有不同的輸出。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-209">In cases where this occurs, client-side formatting of the FOR XML query results will have differing output depending on which version the query is run against.</span></span>  
  
 <span data-ttu-id="cf2c1-210">如果使用 SQLXML 3.0 在用戶端上對 `xml` 資料類型資料行執行 FOR XML 查詢，則結果中的資料會以完全實體化的字串傳回。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-210">If a FOR XML query is executed client-side using SQLXML 3.0 over an `xml` data type column, the data in the results will come back as a fully entitized string.</span></span> <span data-ttu-id="cf2c1-211">在 SQLXML 4.0 中，如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) 是指定為提供者，則資料會傳回為 XML。</span><span class="sxs-lookup"><span data-stu-id="cf2c1-211">In SQLXML 4.0, if the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) is specified as the provider, the data will be returned as XML.</span></span>  
  
  
