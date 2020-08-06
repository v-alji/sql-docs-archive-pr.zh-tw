---
title: 安裝 SQL Server Native Client |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, uninstalling
- SQLNCLI, installing
- SQLNCLI, uninstalling
- Setup [SQL Server Native Client]
- uninstalling SQL Server Native Client
- data access [SQL Server Native Client], uninstalling SQL Server Native Client
- installing SQL Server Native Client
- SQL Server Native Client, installing
- data access [SQL Server Native Client], installing SQL Server Native Client
- removing SQL Server Native Client
ms.assetid: c6abeab2-0052-49c9-be79-cfbc50bff5c1
author: rothja
ms.author: jroth
ms.openlocfilehash: 86a30924dc6dfc0b5b4f4dc176f0186d8f35b2f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597078"
---
# <a name="installing-sql-server-native-client"></a><span data-ttu-id="cda35-102">安裝 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="cda35-102">Installing SQL Server Native Client</span></span>
  <span data-ttu-id="cda35-103">Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 會在您安裝 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] 時安裝。</span><span class="sxs-lookup"><span data-stu-id="cda35-103">Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 is installed when you install [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].</span></span> <span data-ttu-id="cda35-104">沒有 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="cda35-104">There is no [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Native Client.</span></span> <span data-ttu-id="cda35-105">如需詳細資訊，請參閱[SQL Server Native Client 的新功能](../sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="cda35-105">For more information, see [What's New in SQL Server Native Client](../sql-server-native-client.md).</span></span> <span data-ttu-id="cda35-106">您也可以從 SQL Server 2012 功能套件網頁取得 sqlncli.msi。</span><span class="sxs-lookup"><span data-stu-id="cda35-106">You can also get sqlncli.msi from the SQL Server 2012 Feature Pack web page.</span></span> <span data-ttu-id="cda35-107">若要下載最新版本的 SQL Server Native Client，請移至[Microsoft？SQL Server？？2012 SP2 功能套件](https://www.microsoft.com/download/details.aspx?id=43339)。</span><span class="sxs-lookup"><span data-stu-id="cda35-107">To download the most recent version of the SQL Server Native Client, go to [Microsoft?? SQL Server?? 2012 SP2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=43339).</span></span> <span data-ttu-id="cda35-108">如果電腦上也安裝了早於 SQL Server 2012 的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client，則 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 會與舊版本並存安裝。</span><span class="sxs-lookup"><span data-stu-id="cda35-108">If a previous version of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client earlier than SQL Server 2012 is also installed on the computer, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 will be installed side-by-side with the earlier version.</span></span>  
  
 <span data-ttu-id="cda35-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 檔案 (sqlncli11.dll、sqlnclir11.rll 和 s11ch_sqlncli.chm) 會安裝到下列位置：</span><span class="sxs-lookup"><span data-stu-id="cda35-109">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client files (sqlncli11.dll, sqlnclir11.rll, and s11ch_sqlncli.chm) are installed to the following location:</span></span>  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  <span data-ttu-id="cda35-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式的所有適當的登錄設定，都會在安裝程序時進行。</span><span class="sxs-lookup"><span data-stu-id="cda35-110">All appropriate registry settings for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver are made as part of the installation process.</span></span>  
  
 <span data-ttu-id="cda35-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 標頭和程式庫檔 (sqlncli.h 和 sqlncli11.lib) 會安裝到下列位置：</span><span class="sxs-lookup"><span data-stu-id="cda35-111">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client header and library files (sqlncli.h and sqlncli11.lib) are installed in the following location:</span></span>  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 <span data-ttu-id="cda35-112">除了在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝時進行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 的安裝外，還可以利用名為 sqlncli.msi 的轉散發安裝程式，這個程式可以在下列位置的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝磁碟上找到：`%CD%\Setup\`。</span><span class="sxs-lookup"><span data-stu-id="cda35-112">In addition to installing [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client as part of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation, there is also a redistributable installation program named sqlncli.msi, which can be found on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation disk in the following location: `%CD%\Setup\`.</span></span>  
  
 <span data-ttu-id="cda35-113">您可以透過 sqlncli.msi 散佈 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="cda35-113">You can distribute [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client through sqlncli.msi.</span></span> <span data-ttu-id="cda35-114">當您部署應用程式時，可能必須安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="cda35-114">You might have to install [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client when you deploy an application.</span></span> <span data-ttu-id="cda35-115">使用 Chainer 和 Bootstrapper 技術是安裝多個封裝 (但對使用者卻好像是單一安裝) 的一種方法。</span><span class="sxs-lookup"><span data-stu-id="cda35-115">One way to install multiple packages in what seems to the user to be a single installation is to use chainer and bootstrapper technology.</span></span> <span data-ttu-id="cda35-116">如需詳細資訊，請參閱[撰寫適用於 Visual Studio 2005 的自訂啟動載入器套件](https://go.microsoft.com/fwlink/?LinkId=115667)和[新增自訂的必要條件](https://go.microsoft.com/fwlink/?LinkId=115668)。</span><span class="sxs-lookup"><span data-stu-id="cda35-116">For more information, see [Authoring a Custom Bootstrapper Package for Visual Studio 2005](https://go.microsoft.com/fwlink/?LinkId=115667) and [Adding Custom Prerequisites](https://go.microsoft.com/fwlink/?LinkId=115668).</span></span>  
  
 <span data-ttu-id="cda35-117">x64 和 Itanium 版本的 sqlncli.msi 會安裝 32 位元版本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。</span><span class="sxs-lookup"><span data-stu-id="cda35-117">The x64 and Itanium versions of sqlncli.msi also install the 32-bit version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="cda35-118">如果應用程式的目標使用平台與當初開發時的平台不同，您可以從 Microsoft 下載中心下載 x64、Itanium 和 x86 版本的 sqlncli.msi。</span><span class="sxs-lookup"><span data-stu-id="cda35-118">If your application targets a platform other than the one it was developed on, you can download versions of sqlncli.msi for x64, Itanium, and x86 from the Microsoft Download Center.</span></span>  
  
 <span data-ttu-id="cda35-119">當您叫用 sqlncli.msi 時，依預設會安裝用戶端元件。</span><span class="sxs-lookup"><span data-stu-id="cda35-119">When you invoke sqlncli.msi, only the client components are installed by default.</span></span> <span data-ttu-id="cda35-120">用戶端元件是支援執行使用 Native Client 開發之應用程式的檔案 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cda35-120">The client components are files that support running an application that was developed using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="cda35-121">如果也要安裝 SDK 元件，請在命令列上指定 `ADDLOCAL=All`。</span><span class="sxs-lookup"><span data-stu-id="cda35-121">To also install the SDK components, specify `ADDLOCAL=All` on the command line.</span></span> <span data-ttu-id="cda35-122">例如：</span><span class="sxs-lookup"><span data-stu-id="cda35-122">For example:</span></span>  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a><span data-ttu-id="cda35-123">無訊息安裝</span><span class="sxs-lookup"><span data-stu-id="cda35-123">Silent Install</span></span>  
 <span data-ttu-id="cda35-124">如果您搭配 msiexec 使用 /passive、/qn、/qb 或 /qr 選項，則也必須指定 IACCEPTSQLNCLILICENSETERMS=YES，以明確指出您接受使用者授權條款。</span><span class="sxs-lookup"><span data-stu-id="cda35-124">If you use the /passive, /qn, /qb, or /qr option with msiexec, you must also specify IACCEPTSQLNCLILICENSETERMS=YES, to explicitly indicate that you accept the terms of the end user license.</span></span> <span data-ttu-id="cda35-125">此選項必須以全部大寫的字母指定。</span><span class="sxs-lookup"><span data-stu-id="cda35-125">This option must be specified in all capital letters.</span></span>  
  
## <a name="uninstalling-sql-server-native-client"></a><span data-ttu-id="cda35-126">解除安裝 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="cda35-126">Uninstalling SQL Server Native Client</span></span>  
 <span data-ttu-id="cda35-127">因為 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 伺服器和工具之類的應用程式相依 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native client，所以在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 卸載所有相依的應用程式之前，請務必不要卸載 native client。</span><span class="sxs-lookup"><span data-stu-id="cda35-127">Because applications such as [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] server and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tools depend on [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, it is important not to uninstall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client until all dependent applications are uninstalled.</span></span> <span data-ttu-id="cda35-128">若要提供應用程式相依于 Native Client 的警告給使用者 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，請使用 MSI 中的 APPGUID 安裝選項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cda35-128">To provider users with a warning that your application depends on [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, use the APPGUID install option in your MSI, as follows:</span></span>  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 <span data-ttu-id="cda35-129">傳遞給 APPGUID 的值是您特定的產品代碼。</span><span class="sxs-lookup"><span data-stu-id="cda35-129">The value passed to APPGUID is your specific product code.</span></span> <span data-ttu-id="cda35-130">使用 Microsoft Installer 來封裝應用程式安裝程式時，必須建立產品代碼。</span><span class="sxs-lookup"><span data-stu-id="cda35-130">A product code must be created when using Microsoft Installer to bundle your application setup program.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda35-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cda35-131">See Also</span></span>  
 <span data-ttu-id="cda35-132">[使用 SQL Server Native Client 建立應用程式](installing-sql-server-native-client.md) </span><span class="sxs-lookup"><span data-stu-id="cda35-132">[Building Applications with SQL Server Native Client](installing-sql-server-native-client.md) </span></span>  
 [<span data-ttu-id="cda35-133">安裝的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="cda35-133">Installation How-to Topics</span></span>](../../../sql-server/install/installation-how-to-topics.md)  
  
  
