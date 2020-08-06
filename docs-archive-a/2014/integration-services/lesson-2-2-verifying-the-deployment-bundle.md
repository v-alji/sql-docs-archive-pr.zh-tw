---
title: 步驟 2:確認部署配套 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6c13f5c9-c75e-4e52-94dc-2d2db2c578fe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f452a87154175ac05a050761d8f12b6bfe61cd8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592117"
---
# <a name="step-2-verifying-the-deployment-bundle"></a><span data-ttu-id="bdabc-102">步驟 2:確認部署套件組合</span><span class="sxs-lookup"><span data-stu-id="bdabc-102">Step 2: Verifying the Deployment Bundle</span></span>
  <span data-ttu-id="bdabc-103">在第 1 課中，您建立了「部署教學課程」專案，並且將封裝和輔助檔案加入至專案中。在上一項工作中，您為專案建立了部署公用程式。</span><span class="sxs-lookup"><span data-stu-id="bdabc-103">In lesson 1, you created the Deployment Tutorial project and added packages and ancillary files to the project; in the previous task you built a deployment utility for the project.</span></span>  
  
 <span data-ttu-id="bdabc-104">在這項工作中，您會確認部署配套的內容。</span><span class="sxs-lookup"><span data-stu-id="bdabc-104">In this task, you will verify the contents of the deployment bundle.</span></span> <span data-ttu-id="bdabc-105">部署配套就是您將要複製到目的地電腦上並且用來安裝封裝的資料夾。</span><span class="sxs-lookup"><span data-stu-id="bdabc-105">The deployment bundle is the folder that you will copy to the destination computer and use to install packages.</span></span> <span data-ttu-id="bdabc-106">如果您使用預設值 (bin\Deployment) 作為部署公用程式的位置，則部署配套就是 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案中 [部署教學課程] 資料夾內的 Bin\Deployment 資料夾。</span><span class="sxs-lookup"><span data-stu-id="bdabc-106">If you used the default value-bin\Deployment-as the location of the deployment utility, the deployment bundle is the Bin\Deployment folder within the Deployment Tutorial folder in the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
### <a name="to-verify-the-content-of-deployment-bundle"></a><span data-ttu-id="bdabc-107">若要確認部署配套的內容</span><span class="sxs-lookup"><span data-stu-id="bdabc-107">To verify the content of deployment bundle</span></span>  
  
1.  <span data-ttu-id="bdabc-108">在電腦上找到 bin\Deployment 資料夾。</span><span class="sxs-lookup"><span data-stu-id="bdabc-108">Locate the bin\Deployment folder on your computer.</span></span>  
  
2.  <span data-ttu-id="bdabc-109">確認下列檔案存在：</span><span class="sxs-lookup"><span data-stu-id="bdabc-109">Verify that the following files are present:</span></span>  
  
    -   <span data-ttu-id="bdabc-110">DataTransfer.dtsx</span><span class="sxs-lookup"><span data-stu-id="bdabc-110">DataTransfer.dtsx</span></span>  
  
    -   <span data-ttu-id="bdabc-111">datatransferconfig.dtsconfig</span><span class="sxs-lookup"><span data-stu-id="bdabc-111">datatransferconfig.dtsconfig</span></span>  
  
    -   <span data-ttu-id="bdabc-112">Deployment Tutorial.SSISDeploymentManifest</span><span class="sxs-lookup"><span data-stu-id="bdabc-112">Deployment Tutorial.SSISDeploymentManifest</span></span>  
  
    -   <span data-ttu-id="bdabc-113">LoadXMLData.dtsx</span><span class="sxs-lookup"><span data-stu-id="bdabc-113">LoadXMLData.dtsx</span></span>  
  
    -   <span data-ttu-id="bdabc-114">loadxmldataconfig.dtsconfig</span><span class="sxs-lookup"><span data-stu-id="bdabc-114">loadxmldataconfig.dtsconfig</span></span>  
  
    -   <span data-ttu-id="bdabc-115">NewCustomers.txt</span><span class="sxs-lookup"><span data-stu-id="bdabc-115">NewCustomers.txt</span></span>  
  
    -   <span data-ttu-id="bdabc-116">orders.xml</span><span class="sxs-lookup"><span data-stu-id="bdabc-116">orders.xml</span></span>  
  
    -   <span data-ttu-id="bdabc-117">orders.xsd</span><span class="sxs-lookup"><span data-stu-id="bdabc-117">orders.xsd</span></span>  
  
    -   <span data-ttu-id="bdabc-118">Readme.txt</span><span class="sxs-lookup"><span data-stu-id="bdabc-118">Readme.txt</span></span>  
  
3.  <span data-ttu-id="bdabc-119">以滑鼠右鍵按一下 Deployment Tutorial.SSISDeploymentManifest，並指向 [開啟方式]  ，然後按一下 [Internet Explorer]  。</span><span class="sxs-lookup"><span data-stu-id="bdabc-119">Right-click Deployment Tutorial.SSISDeploymentManifest, point **to Open With**, and then click **Internet Explorer**.</span></span> <span data-ttu-id="bdabc-120">您也可以在「記事本」之類的文字編輯器中開啟此檔案。</span><span class="sxs-lookup"><span data-stu-id="bdabc-120">You can also open the file in a text editor such as Notepad.</span></span> <span data-ttu-id="bdabc-121">此檔案的 XML 程式碼應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="bdabc-121">The XML code of the file should be the following:</span></span>  
  
     `<?xml version="1.0"?><DTSDeploymentManifest GeneratedBy="Domain\UserName" GeneratedFromProjectName="Deployment Tutorial" GeneratedDate="2006-02-24T13:29:02.6537669-08:00" AllowConfigurationChanges="true"><Package>DataTransfer.dtsx</Package><Package>LoadXMLData.dtsx</Package><ConfigurationFile>datatransferconfig.dtsconfig</ConfigurationFile><ConfigurationFile>loadxmldataconfig.dtsconfig</ConfigurationFile><MiscellaneousFile>Readme.txt</MiscellaneousFile><MiscellaneousFile>orders.xml</MiscellaneousFile><MiscellaneousFile>NewCustomers.txt</MiscellaneousFile><MiscellaneousFile>orders.xsd</MiscellaneousFile></DTSDeploymentManifest>`  
  
4.  <span data-ttu-id="bdabc-122">請確認屬性的值 `AllowConfigurationChanges` 為**true** ，而且 XML 包含兩個封裝的元素，分別是四個非封裝檔案的專案， `Package` `MiscellaneousFile` 以及兩個 `ConfigurationFile` XML 設定檔中每一個的元素。</span><span class="sxs-lookup"><span data-stu-id="bdabc-122">Verify that the value of the `AllowConfigurationChanges` attribute is **true** and the XML includes a `Package` element for each of the two packages, a `MiscellaneousFile` element for each of the four non-package files, and a `ConfigurationFile` element for each of the two XML configuration files.</span></span>  
  
5.  <span data-ttu-id="bdabc-123">結束 Internet Explorer 或文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="bdabc-123">Exit Internet Explorer or the text editor.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="bdabc-124">下一課</span><span class="sxs-lookup"><span data-stu-id="bdabc-124">Next Lesson</span></span>  
 [<span data-ttu-id="bdabc-125">第 3 課：安裝套件</span><span class="sxs-lookup"><span data-stu-id="bdabc-125">Lesson 3: Installing Packages</span></span>](../integration-services/lesson-3-install-ssis-package.md)  
  
<span data-ttu-id="bdabc-126">![Integration Services 圖示 (小型) ](media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="bdabc-126">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="bdabc-127">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="bdabc-127">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="bdabc-128">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="bdabc-128">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="bdabc-129">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="bdabc-129">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
