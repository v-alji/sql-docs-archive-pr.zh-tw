---
title: 第2課：加入 Web 參考 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a2c2b8b8-6b13-45ca-ab3b-1582447b6807
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 02ca614cb042211ac468246c3003efaa5f2e8fb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702217"
---
# <a name="lesson-2-adding-a-web-reference"></a><span data-ttu-id="20a33-102">第 2 課：新增 Web 參考</span><span class="sxs-lookup"><span data-stu-id="20a33-102">Lesson 2: Adding a Web Reference</span></span>
  <span data-ttu-id="20a33-103">Web 服務探索是用戶端用來尋找 Web 服務及取得服務描述的程序。</span><span class="sxs-lookup"><span data-stu-id="20a33-103">Web service discovery is the process by which a client locates a Web service and obtains its service description.</span></span> <span data-ttu-id="20a33-104">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的 Web 服務探索程序牽涉到依照預先定義的演算法來詢問網站。</span><span class="sxs-lookup"><span data-stu-id="20a33-104">The process of Web service discovery in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] involves interrogating a Web site following a predetermined algorithm.</span></span> <span data-ttu-id="20a33-105">此程序的目的是尋找服務描述，也就是使用 Web 服務描述語言 (WSDL) 的 XML 文件集。</span><span class="sxs-lookup"><span data-stu-id="20a33-105">The goal of the process is to locate the service description, which is an XML document that uses the Web Services Description Language (WSDL).</span></span>  
  
 <span data-ttu-id="20a33-106">服務描述所描述的是可用的服務以及如何與這些服務互動。</span><span class="sxs-lookup"><span data-stu-id="20a33-106">The service description describes what services are available and how to interact with those services.</span></span> <span data-ttu-id="20a33-107">若沒有服務描述，即無法與 Web 服務建立程式化的互動。</span><span class="sxs-lookup"><span data-stu-id="20a33-107">Without a service description, it is impossible to programmatically interact with a Web service.</span></span>  
  
 <span data-ttu-id="20a33-108">您的應用程式必須有與 Web 服務通訊的方式，以及在執行階段尋找 Web 服務的方式。</span><span class="sxs-lookup"><span data-stu-id="20a33-108">Your application must have a means to communicate with the Web service and to locate it at run time.</span></span> <span data-ttu-id="20a33-109">Web 服務藉由產生與 Web 服務互動，同時提供 Web 服務本機表示的 Proxy 類別，將 Web 參考加入您的專案中。</span><span class="sxs-lookup"><span data-stu-id="20a33-109">Adding a Web reference to your project for the Web service does this by generating a proxy class that interfaces with the Web service and provides a local representation of the Web service.</span></span> <span data-ttu-id="20a33-110">如需詳細資訊，請參閱 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 文件集中的＜HOW TO：產生 XML Web Service Proxy＞。</span><span class="sxs-lookup"><span data-stu-id="20a33-110">For more information, see "How to: Generate an XML Web Service Proxy" in your [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] documentation.</span></span>  
  
### <a name="to-add-a-web-reference"></a><span data-ttu-id="20a33-111">若要加入 Web 參考</span><span class="sxs-lookup"><span data-stu-id="20a33-111">To add a Web reference</span></span>  
  
1.  <span data-ttu-id="20a33-112">在 [**專案**] 功能表上，按一下 [**加入服務參考**]。</span><span class="sxs-lookup"><span data-stu-id="20a33-112">On the **Project** menu, click **Add Service Reference**.</span></span>  
  
2.  <span data-ttu-id="20a33-113">在 [**加入服務參考**] 對話方塊中，按一下 [ **Advanced**]。</span><span class="sxs-lookup"><span data-stu-id="20a33-113">In the **Add Service Reference** dialog box, click **Advanced**.</span></span>  
  
3.  <span data-ttu-id="20a33-114">在 [**服務參考設定**] 對話方塊中，按一下 [**加入 Web 參考**]。</span><span class="sxs-lookup"><span data-stu-id="20a33-114">In the **Service Reference Settings** dialog box, click **Add Web Reference**.</span></span>  
  
4.  <span data-ttu-id="20a33-115">在 [**加入 Web 參考**] 對話方塊的 [ **url** ] 方塊中，輸入 Url 以取得報表伺服器 Web 服務的服務描述，例如 http://localhost/reportserver/reportservice2010.asmx 。</span><span class="sxs-lookup"><span data-stu-id="20a33-115">In the **URL** box of the **Add Web Reference** dialog box, type the URL to obtain the service description of the Report Server Web service, such as http://localhost/reportserver/reportservice2010.asmx.</span></span> <span data-ttu-id="20a33-116">然後**按一下 [執行] 按鈕，以**取得有關 Web 服務的資訊。</span><span class="sxs-lookup"><span data-stu-id="20a33-116">Then click the **Go** button to retrieve information about the Web service.</span></span>  
  
     <span data-ttu-id="20a33-117">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="20a33-117">\- or -</span></span>  
  
     <span data-ttu-id="20a33-118">如果報表伺服器 Web 服務存在於本機電腦上，請按一下 [瀏覽器] 窗格中的 [**本機電腦上的 Web 服務**] 連結。</span><span class="sxs-lookup"><span data-stu-id="20a33-118">If the Report Server Web service exists on the local machine, click the **Web services on the local machine** link in the browser pane.</span></span> <span data-ttu-id="20a33-119">然後按一下所提供清單中的 ReportService2010 Web 服務連結。</span><span class="sxs-lookup"><span data-stu-id="20a33-119">Then click the link for the ReportService2010 Web service from the list provided.</span></span>  
  
5.  <span data-ttu-id="20a33-120">在 [ **web 參考名稱**] 方塊中，將 web 參考重新命名為 ReportService2010，這是您將用於此 web 參考的命名空間。</span><span class="sxs-lookup"><span data-stu-id="20a33-120">In the **Web reference name** box, rename the Web reference to ReportService2010, which is the namespace you will use for this Web reference.</span></span>  
  
6.  <span data-ttu-id="20a33-121">按一下 [**加入參考**]，為目標 Web 服務新增 Web 參考。</span><span class="sxs-lookup"><span data-stu-id="20a33-121">Click **Add Reference** to add a Web reference for the target Web service.</span></span>  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <span data-ttu-id="20a33-122">會下載服務描述，並產生聯繫應用程式和報表伺服器 Web 服務的 Proxy 類別。</span><span class="sxs-lookup"><span data-stu-id="20a33-122">downloads the service description and generates a proxy class to interface between your application and the Report Server Web service.</span></span> <span data-ttu-id="20a33-123">您也必須加入 <xref:System.Web.Services> 命名空間的參考，才能讓 Web 參考運作。</span><span class="sxs-lookup"><span data-stu-id="20a33-123">You will also need to add a reference to the <xref:System.Web.Services> namespace for your Web reference to work.</span></span>  
  
7.  <span data-ttu-id="20a33-124">在 [專案] 功能表上，按一下 [加入參考]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="20a33-124">On the Project menu, click **Add Reference**.</span></span>  
  
8.  <span data-ttu-id="20a33-125">在 [**加入參考**] 對話方塊的 [ **.net** ] 索引標籤中，選取 [ **System.web**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="20a33-125">In the **Add Reference** dialog box, in the **.NET** tab, select **System.Web.Services**, then click **OK**.</span></span>  
  
 <span data-ttu-id="20a33-126">如需詳細資訊，請參閱[存取 SOAP API](../reporting-services/report-server-web-service/accessing-the-soap-api.md)。</span><span class="sxs-lookup"><span data-stu-id="20a33-126">For more information, see [Accessing the SOAP API](../reporting-services/report-server-web-service/accessing-the-soap-api.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20a33-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20a33-127">See Also</span></span>  
 <span data-ttu-id="20a33-128">[報表伺服器 Web 服務](../reporting-services/report-server-web-service/report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="20a33-128">[Report Server Web Service](../reporting-services/report-server-web-service/report-server-web-service.md) </span></span>  
 <span data-ttu-id="20a33-129">[第3課：存取 Web 服務](../../2014/tutorials/lesson-3-accessing-the-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="20a33-129">[Lesson 3: Accessing the Web Service](../../2014/tutorials/lesson-3-accessing-the-web-service.md) </span></span>  
 [<span data-ttu-id="20a33-130">使用 Visual Basic 或 Visual C&#35; &#40;SSRS 教學課程來存取報表伺服器 Web 服務&#41;</span><span class="sxs-lookup"><span data-stu-id="20a33-130">Accessing the Report Server Web Service Using Visual Basic or Visual C&#35; &#40;SSRS Tutorial&#41;</span></span>](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
