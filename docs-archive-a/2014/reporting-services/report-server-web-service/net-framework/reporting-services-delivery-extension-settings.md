---
title: Reporting Services 傳遞延伸模組設定 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- XML Web service [Reporting Services], delivery extension settings
- Report Server Web service, delivery extension settings
- delivery [Reporting Services]
- network share delivery [Reporting Services]
- file share delivery [Reporting Services]
- e-mail [Reporting Services]
- mailing reports [Reporting Services]
- sharing reports
- extensions [Reporting Services], delivery
- mail [Reporting Services]
- Web service [Reporting Services], delivery extension settings
ms.assetid: 68c31a85-261c-4ec4-b8df-1f9842b46f8a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d5363c99cb858ce61f7be3b039e27a69944767b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688529"
---
# <a name="reporting-services-delivery-extension-settings"></a><span data-ttu-id="47c91-102">Reporting Services 傳遞延伸模組設定</span><span class="sxs-lookup"><span data-stu-id="47c91-102">Reporting Services Delivery Extension Settings</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="47c91-103">包括電子郵件傳遞延伸模組以及檔案共用傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="47c91-103">includes an e-mail delivery extension and a file share delivery extension.</span></span> <span data-ttu-id="47c91-104">電子郵件傳遞提供一個透過電子郵件傳送報表給個別使用者或群組的方法。</span><span class="sxs-lookup"><span data-stu-id="47c91-104">E-mail delivery provides a way to send a report to individual users or groups through e-mail.</span></span> <span data-ttu-id="47c91-105">檔案共用傳遞可讓您將轉譯的報表自動傳送給網路上的共用。</span><span class="sxs-lookup"><span data-stu-id="47c91-105">File share delivery enables you to automatically send rendered reports to a share on your network.</span></span> <span data-ttu-id="47c91-106">您可以使用其中一個支援的傳遞延伸模組搭配標準訂閱或資料驅動訂閱來傳送。</span><span class="sxs-lookup"><span data-stu-id="47c91-106">You can use either one of the supported delivery extensions with standard subscriptions or data-driven subscriptions.</span></span> <span data-ttu-id="47c91-107">每當您呼叫 <xref:ReportService2010.ReportingService2010.CreateSubscription%2A>、<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>、<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A> 和 <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A> 方法時，會傳遞特屬傳遞延伸模組類型的傳遞設定。</span><span class="sxs-lookup"><span data-stu-id="47c91-107">You pass delivery settings that are specific to the type of delivery extension whenever you call the <xref:ReportService2010.ReportingService2010.CreateSubscription%2A>,<xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>,<xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A>, and <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A> methods.</span></span> <span data-ttu-id="47c91-108">若要以程式設計的方式擷取傳遞設定清單，請使用 <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="47c91-108">To retrieve a list of delivery settings programmatically, use the <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> method.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="47c91-109">傳遞延伸模組設定需要區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="47c91-109">Delivery extension settings are case-sensitive.</span></span>  
  
## <a name="e-mail-delivery-settings"></a><span data-ttu-id="47c91-110">電子郵件傳遞設定</span><span class="sxs-lookup"><span data-stu-id="47c91-110">E-Mail Delivery Settings</span></span>  
 <span data-ttu-id="47c91-111">下表針對使用報表伺服器電子郵件的訂閱列出電子郵件傳遞設定。</span><span class="sxs-lookup"><span data-stu-id="47c91-111">The following table lists the e-mail delivery settings for subscriptions that use report server e-mail.</span></span>  
  
|<span data-ttu-id="47c91-112">設定</span><span class="sxs-lookup"><span data-stu-id="47c91-112">Setting</span></span>|<span data-ttu-id="47c91-113">值</span><span class="sxs-lookup"><span data-stu-id="47c91-113">Value</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="47c91-114">**自**</span><span class="sxs-lookup"><span data-stu-id="47c91-114">**TO**</span></span>|<span data-ttu-id="47c91-115">出現在電子郵件訊息的 `To` 之電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="47c91-115">The e-mail address that appears on the `To` line of the e-mail message.</span></span> <span data-ttu-id="47c91-116">分號會分隔多個電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="47c91-116">Multiple e-mail addresses are separated by semicolons.</span></span> <span data-ttu-id="47c91-117">必要。</span><span class="sxs-lookup"><span data-stu-id="47c91-117">Required.</span></span>|  
|<span data-ttu-id="47c91-118">**修**</span><span class="sxs-lookup"><span data-stu-id="47c91-118">**CC**</span></span>|<span data-ttu-id="47c91-119">出現在電子郵件訊息的 `Cc` 之電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="47c91-119">The e-mail address that appears on the `Cc` line of the e-mail message.</span></span> <span data-ttu-id="47c91-120">分號會分隔多個電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="47c91-120">Multiple e-mail addresses are separated by semicolons.</span></span> <span data-ttu-id="47c91-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="47c91-121">Optional.</span></span>|  
|<span data-ttu-id="47c91-122">**密件副本**</span><span class="sxs-lookup"><span data-stu-id="47c91-122">**BCC**</span></span>|<span data-ttu-id="47c91-123">出現在電子郵件訊息的 `Bcc` 之電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="47c91-123">The e-mail address that appears on the `Bcc` line of the e-mail message.</span></span> <span data-ttu-id="47c91-124">分號會分隔多個電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="47c91-124">Multiple e-mail addresses are separated by semicolons.</span></span> <span data-ttu-id="47c91-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="47c91-125">Optional.</span></span>|  
|<span data-ttu-id="47c91-126">**ReplyTo**</span><span class="sxs-lookup"><span data-stu-id="47c91-126">**ReplyTo**</span></span>|<span data-ttu-id="47c91-127">出現在電子郵件訊息的 `Reply-To` 標頭之電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="47c91-127">The e-mail address that appears in the `Reply-To` header of the e-mail message.</span></span> <span data-ttu-id="47c91-128">值必須是單一電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="47c91-128">The value must be a single e-mail address.</span></span> <span data-ttu-id="47c91-129">選擇性。</span><span class="sxs-lookup"><span data-stu-id="47c91-129">Optional.</span></span>|  
|`IncludeReport`|<span data-ttu-id="47c91-130">指出在電子郵件傳遞中是否包括報表的值。</span><span class="sxs-lookup"><span data-stu-id="47c91-130">A value that indicates whether to include the report in the e-mail delivery.</span></span> <span data-ttu-id="47c91-131">`true` 的值指出在電子郵件訊息的本文中所傳遞的報表。</span><span class="sxs-lookup"><span data-stu-id="47c91-131">A value of `true` indicates that the report is delivered in the body of the e-mail message.</span></span>|  
|<span data-ttu-id="47c91-132">**RenderFormat**</span><span class="sxs-lookup"><span data-stu-id="47c91-132">**RenderFormat**</span></span>|<span data-ttu-id="47c91-133">要用以產生轉譯報表的轉譯延伸模組名稱。</span><span class="sxs-lookup"><span data-stu-id="47c91-133">The name of the rendering extension to use to generate the rendered report.</span></span> <span data-ttu-id="47c91-134">名稱必須對應至報表伺服器上安裝的其中一個可見的轉譯延伸模組。</span><span class="sxs-lookup"><span data-stu-id="47c91-134">The name must correspond to one of the visible rendering extensions installed on the report server.</span></span> <span data-ttu-id="47c91-135">如果將 `IncludeReport` 設定為 `true` 的值，則這個值是必要的。</span><span class="sxs-lookup"><span data-stu-id="47c91-135">This value is required if the `IncludeReport` setting is set to a value of `true`.</span></span>|  
|<span data-ttu-id="47c91-136">**優先順序**</span><span class="sxs-lookup"><span data-stu-id="47c91-136">**Priority**</span></span>|<span data-ttu-id="47c91-137">傳送電子郵件訊息的優先權。</span><span class="sxs-lookup"><span data-stu-id="47c91-137">The priority with which the e-mail message is sent.</span></span> <span data-ttu-id="47c91-138">有效值是 `LOW`、`NORMAL` 和 `HIGH`。</span><span class="sxs-lookup"><span data-stu-id="47c91-138">Valid values are `LOW`, `NORMAL`, and `HIGH`.</span></span> <span data-ttu-id="47c91-139">預設值是 `NORMAL`。</span><span class="sxs-lookup"><span data-stu-id="47c91-139">The default value is `NORMAL`.</span></span>|  
|<span data-ttu-id="47c91-140">**主旨**</span><span class="sxs-lookup"><span data-stu-id="47c91-140">**Subject**</span></span>|<span data-ttu-id="47c91-141">電子郵件訊息主旨中的文字。</span><span class="sxs-lookup"><span data-stu-id="47c91-141">The text in the subject line of the e-mail message.</span></span>|  
|<span data-ttu-id="47c91-142">**註解**</span><span class="sxs-lookup"><span data-stu-id="47c91-142">**Comment**</span></span>|<span data-ttu-id="47c91-143">文字包括在電子郵件訊息的本文中。</span><span class="sxs-lookup"><span data-stu-id="47c91-143">The text included in the body of the e-mail message.</span></span>|  
|<span data-ttu-id="47c91-144">**IncludeLink**</span><span class="sxs-lookup"><span data-stu-id="47c91-144">**IncludeLink**</span></span>|<span data-ttu-id="47c91-145">指出在電子郵件本文中是否包括報表連結的值。</span><span class="sxs-lookup"><span data-stu-id="47c91-145">A value that indicates whether to include a link to the report in the body of the e-mail.</span></span>|  
  
## <a name="file-share-delivery-settings"></a><span data-ttu-id="47c91-146">檔案共用傳遞設定</span><span class="sxs-lookup"><span data-stu-id="47c91-146">File Share Delivery Settings</span></span>  
 <span data-ttu-id="47c91-147">下表列出訂閱的檔案共用傳遞設定。</span><span class="sxs-lookup"><span data-stu-id="47c91-147">The following table lists the file share delivery settings for subscriptions.</span></span>  
  
|<span data-ttu-id="47c91-148">設定</span><span class="sxs-lookup"><span data-stu-id="47c91-148">Setting</span></span>|<span data-ttu-id="47c91-149">值</span><span class="sxs-lookup"><span data-stu-id="47c91-149">Value</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="47c91-150">**名稱**</span><span class="sxs-lookup"><span data-stu-id="47c91-150">**FILENAME**</span></span>|<span data-ttu-id="47c91-151">儲存到磁碟的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="47c91-151">The name of the file that is saved to disk.</span></span>|  
|<span data-ttu-id="47c91-152">**FILEEXTN**</span><span class="sxs-lookup"><span data-stu-id="47c91-152">**FILEEXTN**</span></span>|<span data-ttu-id="47c91-153">指出轉譯報表是否包括副檔名。</span><span class="sxs-lookup"><span data-stu-id="47c91-153">Indicates whether to include a file extension for the rendered report.</span></span> <span data-ttu-id="47c91-154">值是 `true` 或是 `false`。</span><span class="sxs-lookup"><span data-stu-id="47c91-154">The value is either `true` or `false`.</span></span>|  
|<span data-ttu-id="47c91-155">**PATH**</span><span class="sxs-lookup"><span data-stu-id="47c91-155">**PATH**</span></span>|<span data-ttu-id="47c91-156">儲存報表的資料夾路徑或是 UNC 檔案共用路徑。</span><span class="sxs-lookup"><span data-stu-id="47c91-156">The folder path or UNC file share path to which to save the report.</span></span>|  
|<span data-ttu-id="47c91-157">**RENDER_FORMAT**</span><span class="sxs-lookup"><span data-stu-id="47c91-157">**RENDER_FORMAT**</span></span>|<span data-ttu-id="47c91-158">儲存到磁碟的報表格式。</span><span class="sxs-lookup"><span data-stu-id="47c91-158">The format of the report that is saved to disk.</span></span>|  
|<span data-ttu-id="47c91-159">**USERNAME**</span><span class="sxs-lookup"><span data-stu-id="47c91-159">**USERNAME**</span></span>|<span data-ttu-id="47c91-160">存取網路資源或磁碟所需的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="47c91-160">The username required to access the network resource or disk.</span></span>|  
|<span data-ttu-id="47c91-161">**許可權**</span><span class="sxs-lookup"><span data-stu-id="47c91-161">**PASSWORD**</span></span>|<span data-ttu-id="47c91-162">存取網路資源或磁碟所需的密碼。</span><span class="sxs-lookup"><span data-stu-id="47c91-162">The password required to access the network resource or disk.</span></span>|  
|<span data-ttu-id="47c91-163">**WRITEMODE**</span><span class="sxs-lookup"><span data-stu-id="47c91-163">**WRITEMODE**</span></span>|<span data-ttu-id="47c91-164">存取磁碟時使用的寫入模式。</span><span class="sxs-lookup"><span data-stu-id="47c91-164">The write mode to use when accessing the disk.</span></span> <span data-ttu-id="47c91-165">有效值是 `None`、`Overwrite` 和 `AutoIncrement`。</span><span class="sxs-lookup"><span data-stu-id="47c91-165">Valid values are `None`, `Overwrite`, and `AutoIncrement`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47c91-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47c91-166">See Also</span></span>  
 <span data-ttu-id="47c91-167">[SSRS&#41;&#40;的技術參考](../../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="47c91-167">[Technical Reference &#40;SSRS&#41;](../../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="47c91-168">使用 Web 服務和 .NET Framework 建置應用程式</span><span class="sxs-lookup"><span data-stu-id="47c91-168">Building Applications Using the Web Service and the .NET Framework</span></span>](building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
