---
title: Reporting Services SharePoint 模式和原生模式的命令提示字元安裝 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 048169b3-512c-41e4-895a-0416eff41268
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b2101c40c5136e89d4e30d9551187a2b63672da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686838"
---
# <a name="command-prompt-installation-of-reporting-services-sharepoint-mode-and-native-mode"></a><span data-ttu-id="3bcb1-102">Reporting Services SharePoint 模式和原生模式的命令提示字元安裝</span><span class="sxs-lookup"><span data-stu-id="3bcb1-102">Command Prompt Installation of Reporting Services SharePoint Mode and Native Mode</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="3bcb1-103">支援從 SQL Server 安裝程式進行命令列安裝。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-103">supports a command-line installation from the SQL Server setup program.</span></span> <span data-ttu-id="3bcb1-104">本主題包含數個 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]特有的命令列安裝範例。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-104">This topic contains several examples of command-line installations that are specific to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="3bcb1-105">如需所有 SQL Server 元件可用之命令列選項的完整描述，請參閱[從命令提示字元安裝 SQL Server 2014](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-105">For a complete description of the command-line options available for all SQL Server components, see [Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span> <span data-ttu-id="3bcb1-106">本主題不會就 SharePoint 產品之 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集的命令列選項進行說明。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-106">This topic does not describe command-line options for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span> <span data-ttu-id="3bcb1-107">如需增益集的命令安裝相關資訊，請參閱 [使用安裝檔 rsSharePoint.msi 安裝增益集](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md#bkmk_install_rssharepoint)。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-107">For information on command installation of the add-in, see [Install the add-in using the installation file rsSharePoint.msi](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md#bkmk_install_rssharepoint).</span></span>  
  
 <span data-ttu-id="3bcb1-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 模式 |[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式</span><span class="sxs-lookup"><span data-stu-id="3bcb1-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode</span></span>  
  
## <a name="rsinstallmode-native-mode"></a><span data-ttu-id="3bcb1-109">RSINSTALLMODE (原生模式)</span><span class="sxs-lookup"><span data-stu-id="3bcb1-109">RSINSTALLMODE (Native Mode)</span></span>  
 <span data-ttu-id="3bcb1-110">安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的主要輸入設定為 **/RSINSTALLMODE** 輸入設定。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-110">The primary input setting for installing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is the **/RSINSTALLMODE** input setting.</span></span> <span data-ttu-id="3bcb1-111">此設定包含兩個選項： **DefaultNativeMode** 和 **FilesOnlyMode**</span><span class="sxs-lookup"><span data-stu-id="3bcb1-111">The setting has two options: **DefaultNativeMode** and **FilesOnlyMode**</span></span>  
  
 <span data-ttu-id="3bcb1-112">如果安裝包含 SQL Server Database Engine，預設 RSINSTALLMODE 為 DefaultNativeMode。如果安裝不包含 SQL Server Database Engine，預設 RSINSTALLMODE 為 FilesOnlyMode。如果選擇 DefaultNativeMode 但安裝不包含 SQL Server Database Engine，安裝會自動將 RSINSTALLMODE 變更為 FilesOnlyMode。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-112">If the installation includes the SQL Server Database engine, the default RSINSTALLMODE is DefaultNativeMode.If the installation does not include the SQL Server Database engine, the default RSINSTALLMODE is FilesOnlyMode.If you choose DefaultNativeMode but the installation does not include the SQL Server Database engine, the installation automatically changes the RSINSTALLMODE to FilesOnlyMode.</span></span> <span data-ttu-id="3bcb1-113">如需輸入設定的詳細資訊，請參閱[從命令提示字元安裝 SQL Server 2014](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-113">For more information on the input settings, see [Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
## <a name="rsshpinstallmode-sharepoint-mode"></a><span data-ttu-id="3bcb1-114">RSSHPINSTALLMODE (SharePoint 模式)</span><span class="sxs-lookup"><span data-stu-id="3bcb1-114">RSSHPINSTALLMODE (SharePoint Mode)</span></span>  
 <span data-ttu-id="3bcb1-115">在 SharePoint 模式中安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的輸入設定是 **/RSSHPINSTALLMODE**。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-115">The input setting to install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode is **/RSSHPINSTALLMODE**.</span></span> <span data-ttu-id="3bcb1-116">此輸入設定包含一個選項：SharePointFilesOnlyMode。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-116">The input setting has one option: SharePointFilesOnlyMode.</span></span> <span data-ttu-id="3bcb1-117">這個選項會安裝 SharePoint 模式所需的所有檔案，但是安裝之後需要進行設定。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-117">The option installs all the files needed for SharePoint mode but, configuration is required following installation.</span></span> <span data-ttu-id="3bcb1-118">額外設定步驟是使用 SharePoint 管理中心完成。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-118">The additional configuration steps are completed using SharePoint Central Administration.</span></span> <span data-ttu-id="3bcb1-119">如需詳細資訊，請參閱 [安裝適用於 SharePoint 2010 的 Reporting Services SharePoint 模式](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-119">For more information, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).</span></span>  
  
## <a name="examples-of-sharepoint-mode-installation"></a><span data-ttu-id="3bcb1-120">SharePoint 模式安裝範例</span><span class="sxs-lookup"><span data-stu-id="3bcb1-120">Examples of SharePoint Mode Installation</span></span>  
 <span data-ttu-id="3bcb1-121">以下範例將安裝 SQL Server 資料庫引擎服務和 SharePoint 模式的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，以及適用於 SharePoint 的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集 (RS_SHPWFE)。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-121">The following example installs SQL Server the database engine service and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode as well as the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint (RS_SHPWFE).</span></span>  
  
```  
setup /q /ACTION=install /FEATURES=SQL, RS_SHP, RS_SHPWFE,TOOLS /INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /SQLSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /AGTSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE"  
```  
  
 <span data-ttu-id="3bcb1-122">以下範例只會安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-122">The following example installs only [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>  
  
```  
Setup.exe /q /ACTION="Install" /IACCEPTSQLSERVERLICENSETERMS /FEATURES="RS_SHP" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SECURITYMODE="SQL" /SAPWD="*****" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Name]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="[Account Name]" /UPDATEENABLED="False"  
  
```  
  
 <span data-ttu-id="3bcb1-123">以下範例會安裝所有 SQL Server 功能，包括 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式和 SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-123">The following example installs all of the SQL Server features, including both [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode and SharePoint mode.</span></span>  
  
```  
Setup.exe /q /ACTION="Install" /INSTANCENAME="MSSQLSERVER" /FEATURES="SQLEngine,Replication,SNAC,SNAC_SDK,Browser,Writer,AS,IS,MDS,Adv_SSMS,BC,BOL,Conn,SDK,DReplay_CTLR,DReplay_CLT, RS_SHP,RS_SHPWFE,DQC,BIDS,FullText, RS,DQ,SSMS" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SQLSVCACCOUNT="[Account Name]" /SQLSVCPASSWORD="********" /AGTSVCACCOUNT="[Account Nam]" /AGTSVCPASSWORD="********" /CTLRSVCACCOUNT="[Account Nam]" /CTLRSVCPASSWORD="********" /CLTSVCACCOUNT="[Account Nam]" /CLTSVCPASSWORD="********" /ASSVCACCOUNT="[Account Nam]" /ASSVCPASSWORD="********" /RSSVCACCOUNT="[Account Nam]" /RSSVCPASSWORD="********" /FTSVCACCOUNT="[Account Nam]" /FTSVCPASSWORD="********" /SECURITYMODE="SQL" /SAPWD="********" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Nam]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSSHPINSTALLMODE="SharePointFilesOnlyMode" /RSINSTALLMODE="DefaultNativeMode"  
```  
  
## <a name="examples-of-sharepoint-mode-upgrade"></a><span data-ttu-id="3bcb1-124">SharePoint 模式升級範例</span><span class="sxs-lookup"><span data-stu-id="3bcb1-124">Examples of SharePoint Mode Upgrade</span></span>  
 <span data-ttu-id="3bcb1-125">下列範例會升級 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-125">The following example upgrades [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="3bcb1-126">**RSUPGRADEPASSWORD** 是現有報表伺服器服務帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-126">**RSUPGRADEPASSWORD** is the password of the existing Report Server service account.</span></span> <span data-ttu-id="3bcb1-127">除非 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務帳戶是內建帳戶，否則在升級案例中，RSUPGRADEPASSWORD 是必填欄位。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-127">RSUPGRADEPASSWORD is a required field in an upgrade scenario unless the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service account is a built-in account.</span></span>  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[PID value]" /FTSVCACCOUNT="[DOMAIN\ACCOUNT]" /FTSVCPASSWORD="[ACCOUNTPASSSWORD]" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSUPGRADEPASSWORD="******"  
```  
  
 <span data-ttu-id="3bcb1-128">下列範例可用於升級使用 SharePoint 共用服務架構為基礎的 SharePoint 模式安裝。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-128">The following example can be used to upgrade a SharePoint Mode installation that is based on the SharePoint shared service architecture.</span></span> <span data-ttu-id="3bcb1-129">此範例會使用切換參數 ALLOWUPGRADEFORSSRSSHAREPOINTMODE。</span><span class="sxs-lookup"><span data-stu-id="3bcb1-129">The example uses switch ALLOWUPGRADEFORSSRSSHAREPOINTMODE.</span></span> <span data-ttu-id="3bcb1-130">若要升級不是以共用服務架構為基礎的舊版本，不需要此參數：</span><span class="sxs-lookup"><span data-stu-id="3bcb1-130">The switch is not needed for upgrading older versions that are not based on the shared service architecture:</span></span>  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[Your PID Value]" /FTSVCACCOUNT="[ACCOUNT Name]" /FTSVCPASSWORD="****" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /ALLOWUPGRADEFORSSRSSHAREPOINTMODE="True"  
```  
  
## <a name="examples-of-native-mode-installation"></a><span data-ttu-id="3bcb1-131">原生模式安裝範例</span><span class="sxs-lookup"><span data-stu-id="3bcb1-131">Examples of Native Mode Installation</span></span>  
  
```  
Setup.exe /q /ACTION="Install" /INSTANCENAME="MSSQLSERVER" /FEATURES="SQLEngine,Replication,SNAC,SNAC_SDK,Browser,Writer,AS,IS,MDS,Adv_SSMS,BC,BOL,Conn,SDK,DReplay_CTLR,DReplay_CLT,DQC,BIDS,FullText, RS,DQ,SSMS" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SQLSVCACCOUNT="[Account Name]" /SQLSVCPASSWORD="********" /AGTSVCACCOUNT="[Account Nam]" /AGTSVCPASSWORD="********" /CTLRSVCACCOUNT="[Account Nam]" /CTLRSVCPASSWORD="********" /CLTSVCACCOUNT="[Account Nam]" /CLTSVCPASSWORD="********" /ASSVCACCOUNT="[Account Nam]" /ASSVCPASSWORD="********" /RSSVCACCOUNT="[Account Nam]" /RSSVCPASSWORD="********" /FTSVCACCOUNT="[Account Nam]" /FTSVCPASSWORD="********" /SECURITYMODE="SQL" /SAPWD="********" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Nam]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSINSTALLMODE="DefaultNativeMode"  
```  
  
## <a name="see-also"></a><span data-ttu-id="3bcb1-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bcb1-132">See Also</span></span>  
 <span data-ttu-id="3bcb1-133">[從命令提示字元安裝 SQL Server 2014](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="3bcb1-133">[Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span></span>  
 <span data-ttu-id="3bcb1-134">[SysPrep 參數](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#SysPrep) </span><span class="sxs-lookup"><span data-stu-id="3bcb1-134">[SysPrep Parameters](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#SysPrep) </span></span>  
 [<span data-ttu-id="3bcb1-135">從命令提示字元安裝 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="3bcb1-135">Install PowerPivot from the Command Prompt</span></span>](../../sql-server/install/install-powerpivot-from-the-command-prompt.md)  
  
  
