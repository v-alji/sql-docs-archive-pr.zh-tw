---
title: 保護主資料管理員 Web 應用程式的安全 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: e360ba3a-e96b-4f85-b588-ed1f767fa973
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8f2ee807c2cd474542f701226d08427ade8279e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706574"
---
# <a name="secure-a-master-data-manager-web-application"></a><span data-ttu-id="0d4ae-102">保護主資料管理員 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="0d4ae-102">Secure a Master Data Manager Web Application</span></span>
  <span data-ttu-id="0d4ae-103">您可以使用 HTTPS 保護 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-103">You can secure the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application with HTTPS.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d4ae-104">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式可以使用 HTTP 或 HTTPS，但不能同時使用兩者。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-104">The [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application can use either HTTP or HTTPS, but not both.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0d4ae-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="0d4ae-105">Prerequisites</span></span>  
 <span data-ttu-id="0d4ae-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="0d4ae-106">To perform the procedure:</span></span>  
  
-   <span data-ttu-id="0d4ae-107">您必須是 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 安裝所在之 Web 伺服器的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-107">You must be an administrator on the web server where [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] is installed.</span></span>  
  
-   <span data-ttu-id="0d4ae-108">MDS 必須安裝在 Web 伺服器，而且 Web 應用程式必須存在。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-108">MDS must be installed on the web server, and a web application must exist.</span></span> <span data-ttu-id="0d4ae-109">如需詳細資訊，請參閱 [安裝 Master Data Services](install-master-data-services.md) 和 [建立主資料管理員 Web 應用程式 &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-109">For more information, see [Install Master Data Services](install-master-data-services.md) and [Create a Master Data Manager Web Application &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md).</span></span>  
  
### <a name="to-secure-the-master-data-manager-web-application-with-https"></a><span data-ttu-id="0d4ae-110">若要使用 HTTPS 保護主資料管理員 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="0d4ae-110">To secure the Master Data Manager web application with HTTPS</span></span>  
  
1.  <span data-ttu-id="0d4ae-111">在確認 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式已經使用 HTTP 正確設定之後，在 IIS 中建立憑證。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-111">After you have confirmed that the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application is configured correctly with HTTP, create a certificate in IIS.</span></span> <span data-ttu-id="0d4ae-112">如需詳細資訊，請參閱 [在 IIS 7 中設定伺服器憑證](https://technet.microsoft.com/library/cc732230\(WS.10\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-112">For more information, see [Configuring Server Certificates in IIS 7](https://technet.microsoft.com/library/cc732230\(WS.10\).aspx).</span></span>  
  
2.  <span data-ttu-id="0d4ae-113">在 [連接]\*\*\*\* 窗格中，按一下 [網站]\*\*\*\* 底下主控 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式的網站。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-113">In the **Connections** pane, under **Sites**, click the site that hosts the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
3.  <span data-ttu-id="0d4ae-114">在 [動作]\*\*\*\* 窗格中，按一下 [繫結]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-114">In the **Actions** pane, click **Bindings**.</span></span>  
  
4.  <span data-ttu-id="0d4ae-115">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-115">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="0d4ae-116">從清單中選取 [https]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-116">From the list, select **https**.</span></span>  
  
6.  <span data-ttu-id="0d4ae-117">選取 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-117">Select the SSL certificate.</span></span>  
  
7.  <span data-ttu-id="0d4ae-118">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-118">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="0d4ae-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-119">Optional.</span></span> <span data-ttu-id="0d4ae-120">若要移除 HTTP，讓使用者只能使用 HTTPS 存取網站，請從清單中按一下含有 **http**的資料列。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-120">To remove HTTP so that users can access the site with HTTPS only, from the list, click the row with **http**.</span></span> <span data-ttu-id="0d4ae-121">按一下 [移除]\*\*\*\*，然後在確認對話方塊中按一下 [是]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-121">Click **Remove** and on the confirmation dialog box, click **Yes**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="0d4ae-122">在移除 HTTP 之後，您必須變更 basicHttp 和 wsHttpBinding 組態。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-122">You must change basicHttp and wsHttpBinding configurations after removing HTTP.</span></span>  
  
9. <span data-ttu-id="0d4ae-123">若要關閉 [網站繫結]\*\*\*\* 對話方塊，請按一下 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-123">To close the **Site Bindings** dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="0d4ae-124">現在開啟*磁片磁碟機*： \PROGRAM Files\Microsoft SQL Server\120\Master Data services\webapplication。中的 web.config 檔案</span><span class="sxs-lookup"><span data-stu-id="0d4ae-124">Now open the web.config file from *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\WebApplication.</span></span>  
  
11. <span data-ttu-id="0d4ae-125">尋找字串 `<security mode="Message">` ，並將其變更為 `<security mode="Transport">`。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-125">Find the string `<security mode="Message">` and change it to `<security mode="Transport">`.</span></span>  
  
12. <span data-ttu-id="0d4ae-126">儲存並關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-126">Save and close the file.</span></span> <span data-ttu-id="0d4ae-127">如果出現錯誤，這可能是因為您已啟用 UAC。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-127">If you get an error, it could be because you have UAC enabled.</span></span> <span data-ttu-id="0d4ae-128">如需詳細資訊，請參閱 [關閉使用者帳戶控制](https://technet.microsoft.com/library/cc709691\(WS.10\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-128">For more information, see [Turn off User Account Control](https://technet.microsoft.com/library/cc709691\(WS.10\).aspx).</span></span> <span data-ttu-id="0d4ae-129">使用者現在應該能夠使用 HTTPS 存取網站。</span><span class="sxs-lookup"><span data-stu-id="0d4ae-129">Users should now be able to use HTTPS to access the site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d4ae-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d4ae-130">See Also</span></span>  
 [<span data-ttu-id="0d4ae-131">建立主資料管理員 Web 應用程式 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="0d4ae-131">Create a Master Data Manager Web Application &#40;Master Data Services&#41;</span></span>](create-a-master-data-manager-web-application-master-data-services.md)  
  
  
