---
title: 建立主資料管理員 Web 服務 Proxy 類別 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 8bdab026-a0c0-41f3-9d36-f3919c23247f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c4f25d749f829357f6541f14073e654bade27215
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607426"
---
# <a name="create-master-data-manager-web-service-proxy-classes"></a><span data-ttu-id="4010a-102">建立主資料管理員 Web 服務 Proxy 類別</span><span class="sxs-lookup"><span data-stu-id="4010a-102">Create Master Data Manager Web Service Proxy Classes</span></span>
  <span data-ttu-id="4010a-103">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 服務可讓您以程式設計的方式，從可以存取 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 網站的任何電腦使用 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 的功能。</span><span class="sxs-lookup"><span data-stu-id="4010a-103">The [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web service lets you make programmatic use of the features of [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] from any computer that can access your [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web site.</span></span> <span data-ttu-id="4010a-104">在您可以開始撰寫程式碼以存取 Web 服務之前，必須先產生 Proxy 類別。</span><span class="sxs-lookup"><span data-stu-id="4010a-104">Before you can start writing code to access the web service, you must generate proxy classes.</span></span> <span data-ttu-id="4010a-105">您用來執行 Web 服務作業的主要 Proxy 類別為 <xref:Microsoft.MasterDataServices.ServiceClient> 類別，此類別會實作 <xref:Microsoft.MasterDataServices.IService> 介面。</span><span class="sxs-lookup"><span data-stu-id="4010a-105">The main proxy class you use to perform web service operations is the <xref:Microsoft.MasterDataServices.ServiceClient> class, which implements the <xref:Microsoft.MasterDataServices.IService> interface.</span></span>  
  
## <a name="enable-web-service-metadata-publishing"></a><span data-ttu-id="4010a-106">啟用 Web 服務中繼資料發佈</span><span class="sxs-lookup"><span data-stu-id="4010a-106">Enable Web Service Metadata Publishing</span></span>  
 <span data-ttu-id="4010a-107">在您可以產生 Proxy 類別之前，必須啟用 Web 服務中繼資料發佈。</span><span class="sxs-lookup"><span data-stu-id="4010a-107">Before you can generate proxy classes, you must enable web service metadata publishing.</span></span> <span data-ttu-id="4010a-108">請遵循下列步驟進行：</span><span class="sxs-lookup"><span data-stu-id="4010a-108">Follow these steps to do this:</span></span>  
  
1.  <span data-ttu-id="4010a-109">在文字編輯器中開啟 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="4010a-109">Open the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web.config file in a text editor.</span></span> <span data-ttu-id="4010a-110">這個檔案位於 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 安裝路徑的 WebApplication 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4010a-110">This file is in the WebApplication folder of the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] installation path.</span></span>  
  
2.  <span data-ttu-id="4010a-111">尋找底下的 `mdsWsHttpBehavior` 區段 **\<serviceBehaviors>** 。</span><span class="sxs-lookup"><span data-stu-id="4010a-111">Find the `mdsWsHttpBehavior` section under **\<serviceBehaviors>**.</span></span> <span data-ttu-id="4010a-112">若為 **\<serviceMetadata>** 元素，請將設定 `httpGetEnabled` 為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="4010a-112">For the **\<serviceMetadata>** element, set `httpGetEnabled` to `true`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4010a-113">如果您想要透過安全通訊端層 (SSL) 啟用 Web 服務，請在 web.config 檔案的 `httpsGetEnabled` 區段中，改為將 `true` 設定為 `mdsWsHttpBehavior`。</span><span class="sxs-lookup"><span data-stu-id="4010a-113">If you want to enable Web services over Secure Sockets Layer (SSL), set `httpsGetEnabled` to `true` in the `mdsWsHttpBehavior` section of the web.config file.</span></span> <span data-ttu-id="4010a-114">您也需要變更 `mdsWsHTTPBinding` 使其設定成 SSL，與此同時也請註解非 SSL 的區段。</span><span class="sxs-lookup"><span data-stu-id="4010a-114">You also need to change `mdsWsHTTPBinding` so that it is configured for SSL, as well, and comment out the non-SSL section.</span></span>  
  
3.  <span data-ttu-id="4010a-115">儲存檔案的變更。</span><span class="sxs-lookup"><span data-stu-id="4010a-115">Save changes to the file.</span></span>  
  
4.  <span data-ttu-id="4010a-116">瀏覽至服務 URL (例如：http://yourserver/MDS/service/service.svc) 來測試中繼資料發佈。</span><span class="sxs-lookup"><span data-stu-id="4010a-116">Test metadata publishing by browsing to the service URL, for example: http://yourserver/MDS/service/service.svc.</span></span> <span data-ttu-id="4010a-117">如果已啟用中繼資料發佈，則會顯示開頭為</span><span class="sxs-lookup"><span data-stu-id="4010a-117">If metadata publishing is enabled, a page is displayed that begins with</span></span>   
    <span data-ttu-id="4010a-118">「您已建立服務」的頁面。</span><span class="sxs-lookup"><span data-stu-id="4010a-118">"You have created a service."</span></span>  
  
## <a name="creating-proxy-classes-by-using-visual-studio"></a><span data-ttu-id="4010a-119">使用 Visual Studio 建立 Proxy 類別</span><span class="sxs-lookup"><span data-stu-id="4010a-119">Creating Proxy Classes by Using Visual Studio</span></span>  
 <span data-ttu-id="4010a-120">如果您已安裝 Visual Studio 2010，產生 Proxy 類別最簡單的方式，就是將 [服務參考]\*\*\*\* 新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="4010a-120">If you have Visual Studio 2010 installed, the simplest way to generate proxy classes is to add a **Service Reference** to your project.</span></span> <span data-ttu-id="4010a-121">服務參考的位址就是 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式的 URL，並附加 /service/service.svc。</span><span class="sxs-lookup"><span data-stu-id="4010a-121">The address of the service reference is the URL of the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application, appended with /service/service.svc.</span></span> <span data-ttu-id="4010a-122">例如：http://yourserver/MDS/service/service.svc。</span><span class="sxs-lookup"><span data-stu-id="4010a-122">For example: http://yourserver/MDS/service/service.svc.</span></span> <span data-ttu-id="4010a-123">如需詳細資訊，請參閱[如何：新增、更新或移除服務參考](https://go.microsoft.com/fwlink/?LinkId=221167)。</span><span class="sxs-lookup"><span data-stu-id="4010a-123">For more information, see [How to: Add, Update, or Remove a Service Reference](https://go.microsoft.com/fwlink/?LinkId=221167).</span></span>  
  
## <a name="creating-proxy-classes-by-using-svcutilexe"></a><span data-ttu-id="4010a-124">使用 Svcutil.exe 建立 Proxy 類別</span><span class="sxs-lookup"><span data-stu-id="4010a-124">Creating Proxy Classes by Using Svcutil.exe</span></span>  
 <span data-ttu-id="4010a-125">您必須 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 安裝或 Windows SDK，才能在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 電腦上 Svcutil.exe。</span><span class="sxs-lookup"><span data-stu-id="4010a-125">You must have either [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows SDK installed in order to have Svcutil.exe on your computer.</span></span> <span data-ttu-id="4010a-126">如果您使用 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，您須使用 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 命令提示字元執行此命令。</span><span class="sxs-lookup"><span data-stu-id="4010a-126">If you use [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], you must use the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] command prompt to run the command.</span></span> <span data-ttu-id="4010a-127">如需詳細資訊，請參閱 [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](https://go.microsoft.com/fwlink/?LinkId=165027) 和[從服務中繼資料產生 WCF 用戶端](https://go.microsoft.com/fwlink/?LinkId=164821)。</span><span class="sxs-lookup"><span data-stu-id="4010a-127">For more information, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://go.microsoft.com/fwlink/?LinkId=165027) and [Generating a WCF Client from Service Metadata](https://go.microsoft.com/fwlink/?LinkId=164821).</span></span>  
  
 <span data-ttu-id="4010a-128">若要使用 Svcutil.exe 建立一組 C# Proxy 類別，請使用類似以下的命令：</span><span class="sxs-lookup"><span data-stu-id="4010a-128">To create a set of C# proxy classes by using Svcutil.exe, use a command such as the following:</span></span>  
  
```  
svcutil.exe http://<server_name:port>/<virtual_path>/Service/Service.svc   
/out:<proxy_name>.cs /messageContract /tcv:Version35   
/noconfig /ct:System.Collections.ObjectModel.Collection`1   
/namespace:*,Microsoft.MasterDataServices  
```  
  
 <span data-ttu-id="4010a-129">其中：</span><span class="sxs-lookup"><span data-stu-id="4010a-129">Where:</span></span>  
  
-   <span data-ttu-id="4010a-130">*servername*:*port* 為主控 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 之電腦的電腦名稱及連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="4010a-130">*servername*:*port* are the computer name and port number of the computer that hosts [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span>  
  
-   <span data-ttu-id="4010a-131">*virtual_path* 為 Internet Information Services (IIS) 中 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 的虛擬路徑。</span><span class="sxs-lookup"><span data-stu-id="4010a-131">*virtual_path* is the virtual path of [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] in Internet Information Services (IIS).</span></span>  
  
-   <span data-ttu-id="4010a-132">*proxy_name* 為產生之 Proxy 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="4010a-132">*proxy_name* is the name for the generated proxy file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4010a-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4010a-133">See Also</span></span>  
 [<span data-ttu-id="4010a-134">分類的 Web 服務作業 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4010a-134">Categorized Web Service Operations &#40;Master Data Services&#41;</span></span>](categorized-web-service-operations-master-data-services.md)  
  
  
