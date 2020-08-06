---
title: 在報表伺服器上偵測到自訂延伸模組 (Upgrade Advisor) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- rendering extensions [Reporting Services], custom extensions
- security extensions [Reporting Services]
- custom extensions [Reporting Services]
- data processing extensions [Reporting Services], custom extensions
- delivery extensions [Reporting Services]
ms.assetid: fa184bd7-11d6-4ea3-9249-bc1b13db49e5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e4be596ff0f110515155f2aa14dc00aceaf85efd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593772"
---
# <a name="custom-extensions-were-detected-on-the-report-server-upgrade-advisor"></a><span data-ttu-id="ff323-102">在報表伺服器上偵測到自訂延伸模組 (Upgrade Advisor)</span><span class="sxs-lookup"><span data-stu-id="ff323-102">Custom extensions were detected on the report server (Upgrade Advisor)</span></span>
  <span data-ttu-id="ff323-103">Upgrade Advisor 偵測到組態檔中有自訂延伸模組設定，表示您的安裝包括用於資料處理、傳遞、轉譯、安全性或驗證的一個或多個自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ff323-103">Upgrade Advisor detected custom extension settings in the configuration files, indicating that your installation includes one or more custom extensions for data processing, delivery, rendering, security, or authentication.</span></span> <span data-ttu-id="ff323-104">升級作業將會一起移動延伸模組的組態設定與升級的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ff323-104">Upgrade will move the extension configuration settings with the upgraded report server.</span></span> <span data-ttu-id="ff323-105">不過，如果自訂延伸模組安裝在現有的報表伺服器安裝資料夾中，這些自訂延伸模組的組件檔將不會在升級程序期間移至新的安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="ff323-105">However, if the custom extensions are installed in the existing report server installation folder, the assembly files for those custom extensions will not be moved to the new installation folder during the upgrade process.</span></span> <span data-ttu-id="ff323-106">升級完成之後，您必須將這些組件檔移至新的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="ff323-106">After upgrade completes, you must move the assembly files to the new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation folder.</span></span>  
  
||  
|-|  
|<span data-ttu-id="ff323-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式 &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="ff323-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="ff323-108">元件</span><span class="sxs-lookup"><span data-stu-id="ff323-108">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="ff323-109">描述</span><span class="sxs-lookup"><span data-stu-id="ff323-109">Description</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="ff323-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]提供可擴充的架構，可讓開發人員建立資料處理、傳遞、轉譯、安全性和驗證的自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ff323-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] provides an extensible architecture that allows developers to create custom extensions for data processing, delivery, rendering, security, and authentication.</span></span>  
  
 <span data-ttu-id="ff323-111">如果自訂延伸模組或組件使用於 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝中，雖然您可以使用安裝程式來執行升級，但是可能必須在升級完成之後將延伸模組移至新的安裝位置，或者可能必須在升級之前執行一些步驟。</span><span class="sxs-lookup"><span data-stu-id="ff323-111">If custom extensions or assemblies are used in your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation, you can use Setup to perform an upgrade, but you may need to move extensions to the new installation location after upgrade completes, or you may need to perform steps prior to upgrade.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ff323-112">Upgrade Advisor 不會偵測出自訂程式碼組件是否設定成在報表中用於計算項目值、樣式和格式。</span><span class="sxs-lookup"><span data-stu-id="ff323-112">Upgrade Advisor does not detect whether custom code assemblies are configured for use in reports to calculate item values, styles, and formatting.</span></span> <span data-ttu-id="ff323-113">如需詳細資訊，請參閱[其他 Reporting Services 升級問題](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="ff323-113">For more information, see [Other Reporting Services Upgrade Issues](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md).</span></span>  
  
 <span data-ttu-id="ff323-114">如果您從軟體廠商購買了自訂延伸模組，請詢問廠商是否有關於升級自訂功能的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="ff323-114">If you purchased custom extensions from a software vendor, check with the vendor for additional information about upgrading your custom functionality.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="ff323-115">更正動作</span><span class="sxs-lookup"><span data-stu-id="ff323-115">Corrective Action</span></span>  
 <span data-ttu-id="ff323-116">您可以使用下列各節來判斷執行 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的升級之外或之前要執行的步驟：</span><span class="sxs-lookup"><span data-stu-id="ff323-116">Use the following sections to determine steps to perform in addition to or prior to performing an upgrade of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]:</span></span>  
  
 [<span data-ttu-id="ff323-117">自訂資料處理或傳遞延伸模組</span><span class="sxs-lookup"><span data-stu-id="ff323-117">Custom data processing or delivery extensions</span></span>](#dataprocdeliver)  
  
 [<span data-ttu-id="ff323-118">自訂轉譯延伸模組</span><span class="sxs-lookup"><span data-stu-id="ff323-118">Custom rendering extensions</span></span>](#render)  
  
 [<span data-ttu-id="ff323-119">SQL Server 2000 報表伺服器上的自訂安全性或驗證延伸模組</span><span class="sxs-lookup"><span data-stu-id="ff323-119">Custom security or authentication extensions on a SQL Server 2000 report server</span></span>](#secauth2000)  
  
 [<span data-ttu-id="ff323-120">SQL Server 2005 報表伺服器上的自訂安全性或驗證延伸模組</span><span class="sxs-lookup"><span data-stu-id="ff323-120">Custom security or authentication extensions on a SQL Server 2005 report server</span></span>](#secauth2005)  
  
 <span data-ttu-id="ff323-121">升級完成之後，請將這些延伸模組組件移至新的安裝資料夾，然後確認自訂延伸模組是否如預期方式運作。</span><span class="sxs-lookup"><span data-stu-id="ff323-121">After upgrade completes, move the extension assemblies to the new installation folder and then verify that the custom extensions work as expected.</span></span> <span data-ttu-id="ff323-122">如果您的延伸模組無法運作，可能必須重新編譯它。</span><span class="sxs-lookup"><span data-stu-id="ff323-122">If your extension does not work, you might have to recompile it.</span></span>  
  
#### <a name="to-recompile-an-extension"></a><span data-ttu-id="ff323-123">重新編譯延伸模組</span><span class="sxs-lookup"><span data-stu-id="ff323-123">To recompile an extension</span></span>  
  
1.  <span data-ttu-id="ff323-124">將 Microsoft.ReportingServices.Interfaces.dll 檔複製到包含原始程式碼的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ff323-124">Copy the Microsoft.ReportingServices.Interfaces.dll file to the folder that contains your source code.</span></span>  
  
2.  <span data-ttu-id="ff323-125">開啟包含來源檔案的專案，然後加入 Microsoft.ReportingServices.Interfaces.dll 檔的參考。</span><span class="sxs-lookup"><span data-stu-id="ff323-125">Open the project that contains your source files and add a reference to the Microsoft.ReportingServices.Interfaces.dll file.</span></span>  
  
3.  <span data-ttu-id="ff323-126">重建方案，以便繫結此延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ff323-126">Rebuild the solution to bind the extension.</span></span>  
  
 <span data-ttu-id="ff323-127">如果您決定不要繼續進行升級，可能會決定改為移轉 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ff323-127">If you decide not to continue with upgrade, you might decide to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead.</span></span> <span data-ttu-id="ff323-128">如需遷移自訂擴充功能的步驟，請參閱本主題中的[遷移自訂擴充](#migrcustext)功能。</span><span class="sxs-lookup"><span data-stu-id="ff323-128">For steps on migrating custom extensions, see [Migrating custom extensions](#migrcustext) in this topic.</span></span>  
  
###  <a name="custom-data-processing-or-delivery-extensions"></a><a name="dataprocdeliver"></a><span data-ttu-id="ff323-129">自訂資料處理或傳遞延伸模組</span><span class="sxs-lookup"><span data-stu-id="ff323-129">Custom data processing or delivery extensions</span></span>  
 <span data-ttu-id="ff323-130">如果 Upgrade Advisor 偵測到自訂資料處理或傳遞延伸模組，系統並不會封鎖升級程序。</span><span class="sxs-lookup"><span data-stu-id="ff323-130">If Upgrade Advisor detects custom data processing or delivery extensions, the upgrade process is not blocked.</span></span> <span data-ttu-id="ff323-131">不過，升級完成之後，您可能必須先執行其他步驟，然後這些延伸模組所提供的自訂功能才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="ff323-131">However, after upgrade completes, you might need to perform additional steps before the custom functionality provided by these extensions will work.</span></span> <span data-ttu-id="ff323-132">例如，如果自訂延伸模組檔案安裝在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝資料夾中，您就必須執行其他步驟。</span><span class="sxs-lookup"><span data-stu-id="ff323-132">For example, you must perform additional steps when the custom extension files are installed in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation folder.</span></span>  
  
##### <a name="post-upgrade-steps-for-custom-data-processing-or-delivery-extensions"></a><span data-ttu-id="ff323-133">自訂資料處理或傳遞延伸模組的升級後步驟</span><span class="sxs-lookup"><span data-stu-id="ff323-133">Post-upgrade steps for custom data processing or delivery extensions</span></span>  
  
1.  <span data-ttu-id="ff323-134">將延伸模組檔案移至報表伺服器的新程式資料夾。</span><span class="sxs-lookup"><span data-stu-id="ff323-134">Move the extension file or files to the new program folder for the report server.</span></span> <span data-ttu-id="ff323-135">根據預設，報表伺服器程式資料夾位於 \Program Files\Microsoft SQL Server \ MSRS10_50。 \<*instance_name*>\report sample 伺服器。</span><span class="sxs-lookup"><span data-stu-id="ff323-135">By default, the report server program folder is in \Program Files\Microsoft SQL Server\MSRS10_50.\<*instance_name*>\report server.</span></span>  
  
 <span data-ttu-id="ff323-136">如需詳細資訊，請參閱《SQL Server 線上叢書》中的＜部署資料處理延伸模組＞和＜實作傳遞延伸模組＞。</span><span class="sxs-lookup"><span data-stu-id="ff323-136">For more information, see "Deploying a Data Processing Extension" and "Implementing a Delivery Extension" in SQL Server Books Online.</span></span>  
  
###  <a name="custom-rendering-extensions"></a><a name="render"></a><span data-ttu-id="ff323-137">自訂轉譯延伸模組</span><span class="sxs-lookup"><span data-stu-id="ff323-137">Custom rendering extensions</span></span>  
 <span data-ttu-id="ff323-138">如果 Upgrade Advisor 偵測到自訂轉譯延伸模組，系統就會封鎖升級程序。</span><span class="sxs-lookup"><span data-stu-id="ff323-138">If Upgrade Advisor detects custom rendering extensions, the upgrade process is blocked.</span></span> <span data-ttu-id="ff323-139">您可以從組態檔中移除自訂延伸模組的組態項目，藉以繼續進行升級程序。</span><span class="sxs-lookup"><span data-stu-id="ff323-139">You can continue with the upgrade process by removing the custom extension configuration entries from the configuration file.</span></span> <span data-ttu-id="ff323-140">不過，這樣做將會導致升級完成之後，使用者無法使用自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ff323-140">However, this will cause the custom extensions to be unavailable to users after upgrade completes.</span></span> <span data-ttu-id="ff323-141">如果您在升級之後需要自訂轉譯延伸模組，就必須建立更新的轉譯延伸模組，或是向自訂延伸模組供應商取得更新的轉譯延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ff323-141">If you need custom rendering extensions after upgrade, you must build updated rendering extensions or obtain updated rendering extensions from a custom extension vendor.</span></span>  
  
 <span data-ttu-id="ff323-142">您必須執行一些步驟來啟用升級，或者您可能會選擇改為移轉 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ff323-142">You must perform steps to enable an upgrade or you may chose to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ff323-143">在您已經測試並確認更新的轉譯延伸模組如預期方式運作之前，請勿升級或移轉報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ff323-143">Do not upgrade or migrate your report server until you have tested and verified that the updated rendering extension works as expected.</span></span>  
  
##### <a name="to-upgrade-custom-rendering-extensions"></a><span data-ttu-id="ff323-144">升級自訂轉譯延伸模組</span><span class="sxs-lookup"><span data-stu-id="ff323-144">To upgrade custom rendering extensions</span></span>  
  
1.  <span data-ttu-id="ff323-145">取得含有最新介面的轉譯延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ff323-145">Obtain rendering extensions with the latest interfaces.</span></span>  
  
2.  <span data-ttu-id="ff323-146">從 RSReportServer.config 中移除舊的自訂轉譯延伸模組項目。</span><span class="sxs-lookup"><span data-stu-id="ff323-146">Remove the old custom rendering extension entry or entries from RSReportServer.config.</span></span>  
  
3.  <span data-ttu-id="ff323-147">升級報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ff323-147">Upgrade the report server.</span></span>  
  
4.  <span data-ttu-id="ff323-148">升級完成之後，請在報表伺服器上安裝更新的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ff323-148">After upgrade completes, install the updated extensions on the report server.</span></span>  
  
 <span data-ttu-id="ff323-149">如需詳細資訊，請參閱《SQL Server 線上叢書》中的＜實作轉譯延伸模組＞。</span><span class="sxs-lookup"><span data-stu-id="ff323-149">For more information, see "Implementing a Rendering Extension" in SQL Server Books Online.</span></span>  
  
###  <a name="custom-security-or-authentication-extensions-on-a-sql-server-2000-report-server"></a><a name="secauth2000"></a><span data-ttu-id="ff323-150">SQL Server 2000 報表伺服器上的自訂安全性或驗證延伸模組</span><span class="sxs-lookup"><span data-stu-id="ff323-150">Custom security or authentication extensions on a SQL Server 2000 report server</span></span>  
 <span data-ttu-id="ff323-151">如果 Upgrade Advisor 在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 報表伺服器上偵測到自訂安全性或驗證延伸模組，系統就會封鎖升級程序。</span><span class="sxs-lookup"><span data-stu-id="ff323-151">If Upgrade Advisor detects custom security or authentication extensions on a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] report server, the upgrade process is blocked.</span></span> <span data-ttu-id="ff323-152">您必須執行一些步驟來啟用升級，或者您可能會選擇改為移轉 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ff323-152">You must perform steps to enable an upgrade or you may chose to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead.</span></span> <span data-ttu-id="ff323-153">不論是哪一種情況，您都必須使用 Microsoft.ReportingServices.Interfaces.dll 中的最新介面來更新和重新編譯延伸模組，因為這些介面已經在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 與 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 之間變更。</span><span class="sxs-lookup"><span data-stu-id="ff323-153">In either case, you must update and recompile the extensions with the latest interfaces in Microsoft.ReportingServices.Interfaces.dll, because the interfaces have changed between [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ff323-154">在您已經測試並確認更新的安全性或驗證延伸模組如預期方式運作之前，請勿升級或移轉報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ff323-154">Do not upgrade or migrate your report server until you have tested and verified that the updated security or authentication extension works as expected.</span></span>  
  
 <span data-ttu-id="ff323-155">如果您要使用針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 所建立的自訂驗證延伸模組，就必須修改原始程式碼，以便支援針對模型驅動報表所導入的新類別和成員。</span><span class="sxs-lookup"><span data-stu-id="ff323-155">If you are using a custom authentication extension that you created for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must modify the source code to support new classes and members introduced for model-driven reporting.</span></span>  
  
##### <a name="to-upgrade-custom-security-or-authentication-extensions-from-a-sql-server-2000-report-server"></a><span data-ttu-id="ff323-156">若要從 SQL Server 2000 報表伺服器升級自訂安全性或驗證延伸模組</span><span class="sxs-lookup"><span data-stu-id="ff323-156">To upgrade custom security or authentication extensions from a SQL Server 2000 report server</span></span>  
  
1.  <span data-ttu-id="ff323-157">使用最新的介面來更新並重新編譯任何安全性或驗證延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ff323-157">Update and recompile any security or authentication extensions with the latest interfaces.</span></span>  
  
2.  <span data-ttu-id="ff323-158">從 RSReportServer.config 中移除安全性或驗證延伸模組項目。</span><span class="sxs-lookup"><span data-stu-id="ff323-158">Remove the security or authentication extension entry or entries from RSReportServer.config.</span></span>  
  
3.  <span data-ttu-id="ff323-159">升級報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ff323-159">Upgrade the report server.</span></span>  
  
4.  <span data-ttu-id="ff323-160">升級完成之後，請在報表伺服器上安裝更新的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ff323-160">After upgrade completes, install the updated extensions on the report server.</span></span>  
  
 <span data-ttu-id="ff323-161">如需詳細資訊，請參閱《SQL Server 線上叢書》中的＜實作安全性延伸模組＞。</span><span class="sxs-lookup"><span data-stu-id="ff323-161">For more information, see "Implementing a Security Extension" in SQL Server Books Online.</span></span>  
  
###  <a name="custom-security-or-authentication-extensions-on-a-sql-server-2005-report-server"></a><a name="secauth2005"></a><span data-ttu-id="ff323-162">SQL Server 2005 報表伺服器上的自訂安全性或驗證延伸模組</span><span class="sxs-lookup"><span data-stu-id="ff323-162">Custom security or authentication extensions on a SQL Server 2005 report server</span></span>  
 <span data-ttu-id="ff323-163">如果 Upgrade Advisor 在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 報表伺服器上偵測到自訂安全性或驗證延伸模組，系統就會封鎖升級程序。</span><span class="sxs-lookup"><span data-stu-id="ff323-163">If Upgrade Advisor detects custom security or authentication extensions on a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] report server, the upgrade process is blocked.</span></span> <span data-ttu-id="ff323-164">您必須執行一些步驟來啟用升級，或者您可能會選擇改為移轉 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ff323-164">You must perform steps to enable an upgrade or you may chose to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead.</span></span>  
  
##### <a name="to-upgrade-custom-security-or-authentication-extensions-from-a-sql-server-2005-report-server"></a><span data-ttu-id="ff323-165">升級來自 SQL Server 2005 報表伺服器的自訂安全性或驗證延伸模組</span><span class="sxs-lookup"><span data-stu-id="ff323-165">To upgrade custom security or authentication extensions from a SQL Server 2005 report server</span></span>  
  
1.  <span data-ttu-id="ff323-166">從 RSReportServer.config 中移除安全性或驗證延伸模組的組態項目。</span><span class="sxs-lookup"><span data-stu-id="ff323-166">Remove the security or authentication extension configuration entries from RSReportServer.config.</span></span>  
  
2.  <span data-ttu-id="ff323-167">升級報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ff323-167">Upgrade the report server.</span></span>  
  
3.  <span data-ttu-id="ff323-168">升級完成之後，請將這些組態項目重新加入 RSReportServer.config 中。</span><span class="sxs-lookup"><span data-stu-id="ff323-168">After upgrade completes, add the configuration entries back in RSReportServer.config.</span></span>  
  
4.  <span data-ttu-id="ff323-169">如果延伸模組組件安裝在舊的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝資料夾中，請將它們移至新的安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="ff323-169">If the extension assemblies were installed in the old [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation folder, move then to the new installation folder.</span></span>  
  
 <span data-ttu-id="ff323-170">如需詳細資訊，請參閱《SQL Server 線上叢書》中的＜實作安全性延伸模組＞。</span><span class="sxs-lookup"><span data-stu-id="ff323-170">For more information, see "Implementing a Security Extension" in SQL Server Books Online.</span></span>  
  
###  <a name="migrating-custom-extensions"></a><a name="migrcustext"></a><span data-ttu-id="ff323-171">遷移自訂擴充功能</span><span class="sxs-lookup"><span data-stu-id="ff323-171">Migrating custom extensions</span></span>  
 <span data-ttu-id="ff323-172">如果您決定要移轉 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 而非執行升級，請使用下列步驟，將自訂延伸模組移轉至新的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ff323-172">If you decide to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead performing an upgrade, use the steps to migrate custom extensions to the new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance.</span></span>  
  
##### <a name="to-migrate-custom-extensions-to-a-new-reporting-services-instance"></a><span data-ttu-id="ff323-173">將自訂延伸模組移轉至新的 Reporting Services 執行個體</span><span class="sxs-lookup"><span data-stu-id="ff323-173">To migrate custom extensions to a new Reporting Services instance</span></span>  
  
1.  <span data-ttu-id="ff323-174">建立或取得含有最新 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 介面的更新延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ff323-174">Build or obtain updated extensions with the latest [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] interfaces.</span></span>  
  
2.  <span data-ttu-id="ff323-175">將報表伺服器移轉至新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ff323-175">Migrate the report server to a new instance.</span></span>  
  
3.  <span data-ttu-id="ff323-176">在新的執行個體上設定延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ff323-176">Configure the extensions on the new instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff323-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff323-177">See Also</span></span>  
 [<span data-ttu-id="ff323-178">&#40;Upgrade Advisor Reporting Services 升級問題&#41;</span><span class="sxs-lookup"><span data-stu-id="ff323-178">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
