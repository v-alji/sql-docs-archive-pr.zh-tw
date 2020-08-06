---
title: 以表格式模式安裝 Analysis Services |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: cd6ac80d-b735-4e3e-a024-489f1409ad33
author: minewiskan
ms.author: owend
ms.openlocfilehash: a677fd7770f646067cafb8fedf6d3705ccf2de3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688326"
---
# <a name="install-analysis-services-in-tabular-mode"></a><span data-ttu-id="079d3-102">以表格模式安裝 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="079d3-102">Install Analysis Services in Tabular Mode</span></span>
  <span data-ttu-id="079d3-103">如果您安裝 Analysis Services 以使用新表格式模型功能，則必須在支援該模型類型的伺服器模式下安裝 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="079d3-103">If you are installing Analysis Services to use the new tabular modeling features, you must install Analysis Services in a server mode that supports that type of model.</span></span> <span data-ttu-id="079d3-104">此伺服器模式為表格式，並會在安裝期間設定。</span><span class="sxs-lookup"><span data-stu-id="079d3-104">The server mode is Tabular, and it is configured during installation.</span></span>  
  
 <span data-ttu-id="079d3-105">在此模式下安裝伺服器之後，即可用來裝載您在表格式模型設計師中建立的方案。</span><span class="sxs-lookup"><span data-stu-id="079d3-105">After you install the server in this mode, you can use it host solutions that you build in tabular model designer.</span></span> <span data-ttu-id="079d3-106">如果您想透過網路存取表格式模型資料，則需要表格模式伺服器。</span><span class="sxs-lookup"><span data-stu-id="079d3-106">A tabular mode server is required if you want tabular model data access over the network.</span></span>  
  
 <span data-ttu-id="079d3-107">您可以在 [安裝精靈] 或命令列安裝程式中指定表格模式。</span><span class="sxs-lookup"><span data-stu-id="079d3-107">You can specify Tabular mode in the Installation Wizard or in a command line setup.</span></span> <span data-ttu-id="079d3-108">下列各節將描述各種方法。</span><span class="sxs-lookup"><span data-stu-id="079d3-108">The following sections describe each approach.</span></span>  
  
## <a name="installation-wizard"></a><span data-ttu-id="079d3-109">安裝精靈</span><span class="sxs-lookup"><span data-stu-id="079d3-109">Installation Wizard</span></span>  
 <span data-ttu-id="079d3-110">下列清單顯示 [SQL Server 安裝精靈] 中，用來在表格模式下安裝 Analysis Services 的頁面：</span><span class="sxs-lookup"><span data-stu-id="079d3-110">The following list shows you which pages in the SQL Server Installation wizard are used to install Analysis Services in Tabular mode:</span></span>  
  
1.  <span data-ttu-id="079d3-111">從安裝程式的 [功能樹狀目錄] 中，選取 **[Analysis Services]** 。</span><span class="sxs-lookup"><span data-stu-id="079d3-111">Select **Analysis Services** from the Feature Tree in Setup.</span></span>  
  
     <span data-ttu-id="079d3-112">![顯示 Analsyis Services 的安裝功能樹狀結構](../../../sql-server/install/media/ssas-setupas.gif "顯示 Analsyis Services 的安裝功能樹狀結構")</span><span class="sxs-lookup"><span data-stu-id="079d3-112">![Setup feature tree showing Analsyis Services](../../../sql-server/install/media/ssas-setupas.gif "Setup feature tree showing Analsyis Services")</span></span>  
  
2.  <span data-ttu-id="079d3-113">在 [Analysis Services 設定] 頁面上，請務必選取 [**表格式模式]**。</span><span class="sxs-lookup"><span data-stu-id="079d3-113">On the Analysis Services Configuration page, be sure to select **Tabular Mode**.</span></span>  
  
     <span data-ttu-id="079d3-114">![Analysis Services 組態選項中的安裝頁面](../../../sql-server/install/media/ssas-setupasconfig.gif "Analysis Services 組態選項中的安裝頁面")</span><span class="sxs-lookup"><span data-stu-id="079d3-114">![Setup page with Analysis Services config options](../../../sql-server/install/media/ssas-setupasconfig.gif "Setup page with Analysis Services config options")</span></span>  
  
 <span data-ttu-id="079d3-115">表格模式使用 xVelocity 記憶體中分析引擎 (VertiPaq)，這是您部署至 Analysis Services 之表格式模型的預設儲存引擎。</span><span class="sxs-lookup"><span data-stu-id="079d3-115">Tabular mode uses the xVelocity in-memory analytics engine (VertiPaq), which is the default storage for tabular models that you deploy to Analysis Services.</span></span> <span data-ttu-id="079d3-116">將表格式模型方案部署至伺服器之後，您可以選擇設定表格式方案，以使用 DirectQuery 磁碟儲存體作為記憶體繫結之儲存引擎的替代儲存體。</span><span class="sxs-lookup"><span data-stu-id="079d3-116">After you deploy tabular model solutions to the server, you can selectively configure tabular solutions to use DirectQuery disk storage as an alternative to memory-bound storage.</span></span>  
  
## <a name="command-line-setup"></a><span data-ttu-id="079d3-117">命令列安裝程式</span><span class="sxs-lookup"><span data-stu-id="079d3-117">Command Line Setup</span></span>  
 <span data-ttu-id="079d3-118">SQL Server 安裝程式包含可指定伺服器模式的新參數 (`ASSERVERMODE`)。</span><span class="sxs-lookup"><span data-stu-id="079d3-118">SQL Server Setup includes a new parameter (`ASSERVERMODE`) that specifies the server mode.</span></span> <span data-ttu-id="079d3-119">下列範例說明在表格式伺服器模式下安裝 Analysis Services 的命令列安裝程式。</span><span class="sxs-lookup"><span data-stu-id="079d3-119">The following example illustrates a command line setup that installs Analysis Services in Tabular server mode.</span></span>  
  
```  
  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /FEATURES=AS /ASSERVERMODE=TABULAR /INSTANCENAME=ASTabular /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 <span data-ttu-id="079d3-120">`INSTANCENAME` 必須少於 17 個字元。</span><span class="sxs-lookup"><span data-stu-id="079d3-120">`INSTANCENAME` must be less than 17 characters.</span></span>  
  
 <span data-ttu-id="079d3-121">所有預留位置帳戶值都必須取代成有效的帳戶和密碼。</span><span class="sxs-lookup"><span data-stu-id="079d3-121">All placeholder account values must be replaced with valid accounts and password.</span></span>  
  
 <span data-ttu-id="079d3-122">使用所提供的範例命令列語法時，不會安裝 SQL Server Management Studio 或 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 之類的工具。</span><span class="sxs-lookup"><span data-stu-id="079d3-122">Tools such as SQL Server Management Studio or [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] are not installed using the example command line syntax that is provided.</span></span> <span data-ttu-id="079d3-123">如需新增功能的詳細資訊，請參閱[從命令提示字元安裝 SQL Server 2014](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="079d3-123">For more information about adding features, see [Install SQL Server 2014 from the Command Prompt](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
 <span data-ttu-id="079d3-124">`ASSERVERMODE` 會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="079d3-124">`ASSERVERMODE` is case-sensitive.</span></span>  <span data-ttu-id="079d3-125">所有值都必須以大寫形式表示。</span><span class="sxs-lookup"><span data-stu-id="079d3-125">All values must be expressed in upper case.</span></span> <span data-ttu-id="079d3-126">下表描述 `ASSERVERMODE` 的有效值。</span><span class="sxs-lookup"><span data-stu-id="079d3-126">The following table describes the valid values for `ASSERVERMODE`.</span></span>  
  
|<span data-ttu-id="079d3-127">值</span><span class="sxs-lookup"><span data-stu-id="079d3-127">Value</span></span>|<span data-ttu-id="079d3-128">描述</span><span class="sxs-lookup"><span data-stu-id="079d3-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="079d3-129">MULTIDIMENSIONAL</span><span class="sxs-lookup"><span data-stu-id="079d3-129">MULTIDIMENSIONAL</span></span>|<span data-ttu-id="079d3-130">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="079d3-130">This is the default value.</span></span> <span data-ttu-id="079d3-131">如果您未設定 `ASSERVERMODE`，伺服器會以多維度伺服器模式安裝。</span><span class="sxs-lookup"><span data-stu-id="079d3-131">If you do not set `ASSERVERMODE`, the server is installed in Multidimensional server mode.</span></span>|  
|<span data-ttu-id="079d3-132">POWERPIVOT</span><span class="sxs-lookup"><span data-stu-id="079d3-132">POWERPIVOT</span></span>|<span data-ttu-id="079d3-133">此為選用值。</span><span class="sxs-lookup"><span data-stu-id="079d3-133">This value is optional.</span></span> <span data-ttu-id="079d3-134">實際上，如果您設定 `ROLE` 參數，即會自動將伺服器模式設為 1，使得 `ASSERVERMODE` 成為 PowerPivot for SharePoint 安裝的選用參數。</span><span class="sxs-lookup"><span data-stu-id="079d3-134">In practice, if you set the `ROLE` parameter, the server mode is automatically set to 1, making `ASSERVERMODE` optional for a PowerPivot for SharePoint installation.</span></span> <span data-ttu-id="079d3-135">如需詳細資訊，請參閱[從命令提示字元安裝 PowerPivot](../../../sql-server/install/install-powerpivot-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="079d3-135">For more information, see [Install PowerPivot from the Command Prompt](../../../sql-server/install/install-powerpivot-from-the-command-prompt.md).</span></span>|  
|<span data-ttu-id="079d3-136">TABULAR</span><span class="sxs-lookup"><span data-stu-id="079d3-136">TABULAR</span></span>|<span data-ttu-id="079d3-137">如果您使用命令列安裝程式，在表格模式下安裝 Analysis Services，則需要此值。</span><span class="sxs-lookup"><span data-stu-id="079d3-137">This value is required if you are installing Analysis Services in Tabular mode using command line setup.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="079d3-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="079d3-138">See Also</span></span>  
 <span data-ttu-id="079d3-139">[判斷 Analysis Services 實例的伺服器模式](../determine-the-server-mode-of-an-analysis-services-instance.md) </span><span class="sxs-lookup"><span data-stu-id="079d3-139">[Determine the Server Mode of an Analysis Services Instance](../determine-the-server-mode-of-an-analysis-services-instance.md) </span></span>  
 <span data-ttu-id="079d3-140">[設定表格式模型資料庫的記憶體內部或 DirectQuery 存取](../../tabular-models/enable-directquery-mode-in-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="079d3-140">[Configure In-Memory or DirectQuery Access for a Tabular Model Database](../../tabular-models/enable-directquery-mode-in-ssms.md) </span></span>  
 [<span data-ttu-id="079d3-141">&#40;SSAS 表格式&#41;的表格式模型</span><span class="sxs-lookup"><span data-stu-id="079d3-141">Tabular Modeling &#40;SSAS Tabular&#41;</span></span>](../../tabular-models/tabular-models-ssas.md)  
  
  
