---
title: Reporting Services 中的電子郵件傳遞 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], e-mail
- e-mail [Reporting Services]
- mail [Reporting Services]
ms.assetid: fda2f130-97b9-4258-9dbb-e93a70f4d08a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9780a47b8e11f831f3a390829acdbd8ae935cf2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596467"
---
# <a name="e-mail-delivery-in-reporting-services"></a><span data-ttu-id="37f0d-102">Reporting Services 中的電子郵件傳遞</span><span class="sxs-lookup"><span data-stu-id="37f0d-102">E-Mail Delivery in Reporting Services</span></span>
  <span data-ttu-id="37f0d-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 包含了電子郵件傳遞延伸模組，可讓您透過電子郵件傳送報表給個別使用者或群組。</span><span class="sxs-lookup"><span data-stu-id="37f0d-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] includes an e-mail delivery extension that provides a way to e-mail a report to individual users or groups.</span></span> <span data-ttu-id="37f0d-104">您可以透過 Reporting Services 組態管理員並藉由編輯 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態檔，設定電子郵件傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="37f0d-104">The e-mail delivery extension is configured through the Reporting Services Configuration Manager and by editing the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuration files.</span></span>  
  
 <span data-ttu-id="37f0d-105">若要透過電子郵件散發或接收報表，您可以定義標準訂閱或資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="37f0d-105">To distribute or receive a report by e-mail, you define either a standard subscription or a data-driven subscription.</span></span> <span data-ttu-id="37f0d-106">您一次只能訂閱或散發一個報表。</span><span class="sxs-lookup"><span data-stu-id="37f0d-106">You can subscribe to or distribute only one report at a time.</span></span> <span data-ttu-id="37f0d-107">您無法建立在單一電子郵件訊息中傳遞多個報表的訂閱。</span><span class="sxs-lookup"><span data-stu-id="37f0d-107">You cannot create a subscription that delivers multiple reports in a single e-mail message.</span></span> <span data-ttu-id="37f0d-108">如需有關訂閱的詳細資訊，請參閱[在原生模式中建立、修改和刪除標準訂閱 &#40;Reporting Services&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="37f0d-108">For more information about subscriptions, see [Create, Modify, and Delete Standard Subscriptions &#40;Reporting Services in Native Mode&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md).</span></span>  
  
||  
|-|  
|<span data-ttu-id="37f0d-109">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Sharepoint 模式 &#124; sharepoint 2010 和 SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="37f0d-109">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode &#124; SharePoint 2010 and SharePoint 2013</span></span><br /><br /> <span data-ttu-id="37f0d-110">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式</span><span class="sxs-lookup"><span data-stu-id="37f0d-110">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
## <a name="e-mail-delivery-options"></a><span data-ttu-id="37f0d-111">電子郵件傳遞選項</span><span class="sxs-lookup"><span data-stu-id="37f0d-111">E-Mail Delivery Options</span></span>  
 <span data-ttu-id="37f0d-112">報表伺服器電子郵件傳遞可以利用下列方式傳遞報表：</span><span class="sxs-lookup"><span data-stu-id="37f0d-112">Report server e-mail delivery can deliver reports in the following ways:</span></span>  
  
-   <span data-ttu-id="37f0d-113">傳送通知和超連結到產生的報表。</span><span class="sxs-lookup"><span data-stu-id="37f0d-113">Send a notification and a hyperlink to the generated report.</span></span>  
  
-   <span data-ttu-id="37f0d-114">在電子郵件訊息的 [主旨:] 傳送通知。</span><span class="sxs-lookup"><span data-stu-id="37f0d-114">Send a notification in the Subject: line of an e-mail message.</span></span> <span data-ttu-id="37f0d-115">依預設，訂閱定義中的 [主旨:] 包含下列變數，處理訂閱時，會以報表特定資訊取代這些變數：</span><span class="sxs-lookup"><span data-stu-id="37f0d-115">By default, the Subject: line in the subscription definition includes the following variables that are replaced by report-specific information when the subscription is processed:</span></span>  
  
     <span data-ttu-id="37f0d-116">**@ReportName**指定報表的名稱。</span><span class="sxs-lookup"><span data-stu-id="37f0d-116">**@ReportName** specifies the name of the report.</span></span>  
  
     <span data-ttu-id="37f0d-117">**@ExecutionTime**指定報表的執行時間。</span><span class="sxs-lookup"><span data-stu-id="37f0d-117">**@ExecutionTime** specifies when the report was executed.</span></span>  
  
     <span data-ttu-id="37f0d-118">您可以將這些變數與靜態文字結合，或者修改每個訂閱 [主旨:] 中的文字。</span><span class="sxs-lookup"><span data-stu-id="37f0d-118">You can combine these variables with static text or modify the text in the Subject: line for each subscription.</span></span>  
  
-   <span data-ttu-id="37f0d-119">傳送內嵌的或附加的報表。</span><span class="sxs-lookup"><span data-stu-id="37f0d-119">Send an embedded or attached report.</span></span> <span data-ttu-id="37f0d-120">轉譯格式和瀏覽器會決定是否要內嵌或附加報表。</span><span class="sxs-lookup"><span data-stu-id="37f0d-120">The rendering format and browser determine whether the report is embedded or attached.</span></span>  
  
     <span data-ttu-id="37f0d-121">如果您的瀏覽器支援 HTML 4.0 與 MHTML，而且您選擇網頁封存轉譯格式，則報表會內嵌為訊息的一部分。</span><span class="sxs-lookup"><span data-stu-id="37f0d-121">If your browser supports HTML 4.0 and MHTML, and you choose the Web archive rendering format, the report is embedded as part of the message.</span></span> <span data-ttu-id="37f0d-122">所有其他轉譯格式 (CSV、PDF 等等) 均以附加檔案傳遞報表。</span><span class="sxs-lookup"><span data-stu-id="37f0d-122">All other rendering formats (CSV, PDF, and so on) deliver reports as attachments.</span></span> <span data-ttu-id="37f0d-123">您可以在 RSReportServer 組態檔中停用此功能。</span><span class="sxs-lookup"><span data-stu-id="37f0d-123">You can disable this functionality in the RSReportServer configuration file.</span></span>  
  
     [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="37f0d-124">在傳送報表之前，不會檢查附加檔案或訊息的大小。</span><span class="sxs-lookup"><span data-stu-id="37f0d-124">does not check the size of the attachment or message before sending the report.</span></span> <span data-ttu-id="37f0d-125">如果附加檔案或訊息超過郵件伺服器所允許的上限，將不會傳遞報表。</span><span class="sxs-lookup"><span data-stu-id="37f0d-125">If the attachment or message exceeds the maximum limit allowed by your mail server, the report is not delivered.</span></span> <span data-ttu-id="37f0d-126">如果是大型報表，請選擇其他傳遞選項之一 (例如 URL 或通知)。</span><span class="sxs-lookup"><span data-stu-id="37f0d-126">Choose one of the other delivery options (such as URL or notification) if for large reports.</span></span>  
  
 <span data-ttu-id="37f0d-127">您可以設定傳遞選項，來決定建立訂閱時如何傳遞報表。</span><span class="sxs-lookup"><span data-stu-id="37f0d-127">You set delivery options that determine how a report is delivered when you create the subscription.</span></span> <span data-ttu-id="37f0d-128">例如，您若是在訂閱中選取 [包含連結]  ，則電子郵件訊息包含連結到報表的超連結。</span><span class="sxs-lookup"><span data-stu-id="37f0d-128">For example, if you select **Include Link** in the subscription, the e-mail message includes a hyperlink to the report.</span></span>  
  
## <a name="role-based-e-mail-settings"></a><span data-ttu-id="37f0d-129">以角色為基礎的電子郵件設定</span><span class="sxs-lookup"><span data-stu-id="37f0d-129">Role-based E-Mail Settings</span></span>  
 <span data-ttu-id="37f0d-130">您訂閱報表時所使用的電子郵件傳遞設定，會依您的角色包含的是「管理個別訂閱」工作或「管理所有訂閱」工作而異。</span><span class="sxs-lookup"><span data-stu-id="37f0d-130">When you subscribe to a report, the e-mail delivery settings you work with vary depending on whether your role includes the "Manage individual subscriptions" task or the "Manage all subscriptions" task.</span></span>  
  
|<span data-ttu-id="37f0d-131">Task</span><span class="sxs-lookup"><span data-stu-id="37f0d-131">Task</span></span>|<span data-ttu-id="37f0d-132">可用的設定</span><span class="sxs-lookup"><span data-stu-id="37f0d-132">Available settings</span></span>|  
|----------|------------------------|  
|<span data-ttu-id="37f0d-133">管理個別訂閱</span><span class="sxs-lookup"><span data-stu-id="37f0d-133">Manage individual subscriptions</span></span>|<span data-ttu-id="37f0d-134">顯示讓使用者可自動化並傳遞報表給自己的欄位。</span><span class="sxs-lookup"><span data-stu-id="37f0d-134">Shows fields that enable a user to automate and deliver a report to himself or herself.</span></span> <span data-ttu-id="37f0d-135">在此模式下，接受電子郵件別名的欄位無法使用。</span><span class="sxs-lookup"><span data-stu-id="37f0d-135">In this mode, fields that accept e-mail aliases are not available.</span></span>|  
|<span data-ttu-id="37f0d-136">管理所有訂閱</span><span class="sxs-lookup"><span data-stu-id="37f0d-136">Manage all subscriptions</span></span>|<span data-ttu-id="37f0d-137">顯示支援全域散發的欄位，包括 [收件者:]、[副本:]、[密件副本:] 和 [回覆至:] 欄位，提供更多方式傳送報表給更多訂閱者。</span><span class="sxs-lookup"><span data-stu-id="37f0d-137">Shows fields that support wider distribution, including To:, Cc:, Bcc:, and Reply-To: fields, providing more ways to route a report to more subscribers.</span></span> <span data-ttu-id="37f0d-138">電子郵件別名欄位的可用性是透過 RSReportServer 組態檔設定定義。</span><span class="sxs-lookup"><span data-stu-id="37f0d-138">The availability of e-mail alias fields is defined through the RSReportServer configuration file settings.</span></span>|  
  
## <a name="specifying-e-mail-addresses-in-a-subscription"></a><span data-ttu-id="37f0d-139">在訂閱中指定電子郵件位址</span><span class="sxs-lookup"><span data-stu-id="37f0d-139">Specifying E-Mail Addresses in a Subscription</span></span>  
 <span data-ttu-id="37f0d-140">如果您是在內部網路散發報表，而且使用的是通往 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange 伺服器的 SMTP 閘道，請輸入電子郵件別名 (就像您傳送電子郵件給同事一樣)。</span><span class="sxs-lookup"><span data-stu-id="37f0d-140">If you are distributing reports within an intranet and you are using an SMTP gateway to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange server, type the e-mail alias (as if you were sending e-mail to a coworker).</span></span> <span data-ttu-id="37f0d-141">若要傳遞到外部電子郵件帳戶，請輸入完整電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="37f0d-141">If delivery is to an external e-mail account, type the full e-mail address.</span></span> <span data-ttu-id="37f0d-142">如果指定更多電子郵件地址以加入其他人到訂閱中，訂閱者會取得此訂閱所產生的報表完整副本。</span><span class="sxs-lookup"><span data-stu-id="37f0d-142">If you specify more e-mail addresses to add others to your subscription, subscribers get an exact copy of the report that is produced from this subscription.</span></span>  
  
 <span data-ttu-id="37f0d-143">報表伺服器不會驗證電子郵件地址，或從電子郵件伺服器取得電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="37f0d-143">The report server does not validate e-mail addresses or obtain e-mail addresses from an e-mail server.</span></span> <span data-ttu-id="37f0d-144">您必須事先知道要使用的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="37f0d-144">You must know in advance which e-mail addresses you want to use.</span></span> <span data-ttu-id="37f0d-145">依預設，您可以利用電子郵件傳送報表給組織內外任何有效的電子郵件帳戶。</span><span class="sxs-lookup"><span data-stu-id="37f0d-145">By default, you can e-mail reports to any valid e-mail account within or outside of your organization.</span></span> <span data-ttu-id="37f0d-146">但是，可以使用組態設定，將電子郵件傳遞至限制在您依名稱識別的郵件伺服器主機。</span><span class="sxs-lookup"><span data-stu-id="37f0d-146">Configuration settings can be used, however, to restrict e-mail delivery to mail server hosts that you identify by name.</span></span> <span data-ttu-id="37f0d-147">如果您想要支援電子郵件傳遞給非組織成員的人，則可以指定其他主機。</span><span class="sxs-lookup"><span data-stu-id="37f0d-147">You can specify additional hosts if you want to support e-mail delivery to people that are not members of your organization.</span></span>  
  
 <span data-ttu-id="37f0d-148">用來傳遞報表的電子郵件訊息，必須從電子郵件伺服器上所定義的電子郵件帳戶傳送。</span><span class="sxs-lookup"><span data-stu-id="37f0d-148">The e-mail message used to deliver the report must be sent from an e-mail account that is defined on the e-mail server.</span></span> <span data-ttu-id="37f0d-149">組態設定會指定電子郵件帳戶。</span><span class="sxs-lookup"><span data-stu-id="37f0d-149">A configuration setting specifies the e-mail account.</span></span> <span data-ttu-id="37f0d-150">電子郵件帳戶是供所有藉由電子郵件傳遞延伸模組傳遞之報表所使用的；您無法指定多個帳戶或對個別報表指定不同帳戶。</span><span class="sxs-lookup"><span data-stu-id="37f0d-150">The e-mail account is used for all reports delivered by the e-mail delivery extension; you cannot specify multiple accounts or vary the account for individual reports.</span></span>  
  
## <a name="e-mail-server-configuration"></a><span data-ttu-id="37f0d-151">電子郵件伺服器組態</span><span class="sxs-lookup"><span data-stu-id="37f0d-151">E-Mail Server Configuration</span></span>  
 <span data-ttu-id="37f0d-152">報表伺服器會透過標準連線來與電子郵件伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="37f0d-152">The report server connects with an e-mail server through a standard connection.</span></span> <span data-ttu-id="37f0d-153">並未使用以安全通訊端層 (SSL) 加密的通訊。</span><span class="sxs-lookup"><span data-stu-id="37f0d-153">It does not use communication that has been encrypted using Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="37f0d-154">電子郵件伺服器必須是與報表伺服器在相同網路中的遠端或本機 Simple Mail Transport Protocol (SMTP) 伺服器。</span><span class="sxs-lookup"><span data-stu-id="37f0d-154">The e-mail server must be a remote or local Simple Mail Transport Protocol (SMTP) server on the same network as the report server.</span></span>  
  
 <span data-ttu-id="37f0d-155">如需如何設定原生模式報表伺服器的詳細資訊，請參閱下列內容：</span><span class="sxs-lookup"><span data-stu-id="37f0d-155">For information on how to configure a native mode report server, see the following:</span></span>  
  
-   [<span data-ttu-id="37f0d-156">針對 &#40;SSRS Configuration Manager 的電子郵件傳遞設定報表伺服器&#41;</span><span class="sxs-lookup"><span data-stu-id="37f0d-156">Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
  
-   [<span data-ttu-id="37f0d-157">電子郵件設定-Configuration Manager &#40;SSRS 原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="37f0d-157">E-mail Settings - Configuration Manager &#40;SSRS Native Mode&#41;</span></span>](../install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md)  
  
 <span data-ttu-id="37f0d-158">如需如何設定 SharePoint 模式報表伺服器的詳細資訊，請參閱下列內容：</span><span class="sxs-lookup"><span data-stu-id="37f0d-158">For information on how to configure a SharePoint mode report server, see the following:</span></span>  
  
-   [<span data-ttu-id="37f0d-159">設定 Reporting Services 服務應用程式的電子郵件 &#40;SharePoint 2010 和 SharePoint 2013&#41;</span><span class="sxs-lookup"><span data-stu-id="37f0d-159">Configure E-mail for a Reporting Services Service Application &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](../install-windows/configure-e-mail-for-a-reporting-services-service-application.md)  
  
## <a name="see-also"></a><span data-ttu-id="37f0d-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37f0d-160">See Also</span></span>  
 <span data-ttu-id="37f0d-161">[工作和權限](../security/tasks-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="37f0d-161">[Tasks and Permissions](../security/tasks-and-permissions.md) </span></span>  
 <span data-ttu-id="37f0d-162">[訂閱與傳遞 &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="37f0d-162">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="37f0d-163">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="37f0d-163">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span></span>  
 [<span data-ttu-id="37f0d-164">角色指派</span><span class="sxs-lookup"><span data-stu-id="37f0d-164">Role Assignments</span></span>](../security/role-assignments.md)  
  
  
