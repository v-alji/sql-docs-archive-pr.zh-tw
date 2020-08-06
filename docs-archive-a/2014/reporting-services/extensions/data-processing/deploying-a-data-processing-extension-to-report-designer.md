---
title: 如何：將資料處理延伸模組部署到報表設計師 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: 3614e601-004e-4a16-8388-836ffd67e9dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 56bd56e9d8eeeeff1781f22b42cf0eb1ce706fa4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708958"
---
# <a name="how-to-deploy-a-data-processing-extension-to-report-designer"></a><span data-ttu-id="7ed98-102">如何：將資料處理延伸模組部署到報表設計師</span><span class="sxs-lookup"><span data-stu-id="7ed98-102">How to: Deploy a Data Processing Extension to Report Designer</span></span>
  <span data-ttu-id="7ed98-103">報表設計工具在您設計報表時，使用資料處理延伸模組來擷取和處理資料。</span><span class="sxs-lookup"><span data-stu-id="7ed98-103">Report Designer uses data processing extensions for retrieving and processing data while you are designing reports.</span></span> <span data-ttu-id="7ed98-104">您應該將資料處理延伸模組組件部署到報表設計師做為私用組件，</span><span class="sxs-lookup"><span data-stu-id="7ed98-104">You should deploy your data processing extension assembly to Report Designer as a private assembly.</span></span> <span data-ttu-id="7ed98-105">您也需要在報表設計師組態檔 RSReportDesigner.config 中建立項目。</span><span class="sxs-lookup"><span data-stu-id="7ed98-105">You also need to make an entry in the Report Designer configuration file, RSReportDesigner.config.</span></span>  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a><span data-ttu-id="7ed98-106">部署資料處理延伸模組組件</span><span class="sxs-lookup"><span data-stu-id="7ed98-106">To deploy a data processing extension assembly</span></span>  
  
1.  <span data-ttu-id="7ed98-107">將組件從您的執行位置複製到報表設計師目錄。</span><span class="sxs-lookup"><span data-stu-id="7ed98-107">Copy your assembly from your staging location to the Report Designer directory.</span></span> <span data-ttu-id="7ed98-108">報表設計師目錄的預設位置是 C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies。</span><span class="sxs-lookup"><span data-stu-id="7ed98-108">The default location of the Report Designer directory is C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span>  
  
2.  <span data-ttu-id="7ed98-109">在複製組件檔之後，開啟 RSReportDesigner.config 檔。</span><span class="sxs-lookup"><span data-stu-id="7ed98-109">After the assembly file is copied, open the RSReportDesigner.config file.</span></span> <span data-ttu-id="7ed98-110">RSReportDesigner.config 檔案也位於 Report Designer 目錄中。</span><span class="sxs-lookup"><span data-stu-id="7ed98-110">The RSReportDesigner.config file is also located in the Report Designer directory.</span></span> <span data-ttu-id="7ed98-111">您需要在資料處理延伸模組組件檔案的組態檔中建立項目。</span><span class="sxs-lookup"><span data-stu-id="7ed98-111">You need to make an entry in the configuration file for your data processing extension assembly file.</span></span> <span data-ttu-id="7ed98-112">您可以利用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或簡單的文字編輯器 (例如 [記事本]) 開啟設定檔。</span><span class="sxs-lookup"><span data-stu-id="7ed98-112">You can open the configuration file with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or with a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="7ed98-113">在 RSReportDesigner.config 檔中，找出 **Data** 元素。</span><span class="sxs-lookup"><span data-stu-id="7ed98-113">Locate the **Data** element in the RSReportDesigner.config file.</span></span> <span data-ttu-id="7ed98-114">應該針對您新建立的資料處理延伸模組，在下列位置建立項目：</span><span class="sxs-lookup"><span data-stu-id="7ed98-114">An entry for your newly created data processing extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="7ed98-115">加入資料處理延伸模組的專案，其中包括具有**Extension** `Name` 、 `Type` 和屬性值的 extension 元素 `Visible` 。</span><span class="sxs-lookup"><span data-stu-id="7ed98-115">Add an entry for your data processing extension which includes an **Extension** element with values for the `Name`, `Type`, and `Visible` attributes.</span></span> <span data-ttu-id="7ed98-116">您的輸入可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="7ed98-116">Your entry might look like the following:</span></span>  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, AssemblyName" />  
    ```  
  
     <span data-ttu-id="7ed98-117">`Name` 的值是資料處理延伸模組的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="7ed98-117">The value for `Name` is the unique name of the data processing extension.</span></span> <span data-ttu-id="7ed98-118">`Type` 的值是以逗號分隔的清單，包括實作 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 和 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> 介面之類別的完整命名空間項目，後面接著組件的名稱 (不包含 .dll 副檔名)。</span><span class="sxs-lookup"><span data-stu-id="7ed98-118">The value for `Type` is a comma-separated list that includes an entry for the fully qualified namespace of your class that implements the <xref:Microsoft.ReportingServices.Interfaces.IExtension> and <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> interfaces, followed by the name of your assembly (not including the .dll file extension).</span></span> <span data-ttu-id="7ed98-119">依預設值，資料處理延伸模組是可見的。</span><span class="sxs-lookup"><span data-stu-id="7ed98-119">By default, data processing extensions are visible.</span></span> <span data-ttu-id="7ed98-120">若要隱藏使用者介面的擴充功能（例如報表設計師），請將 `Visible` 屬性新增至**extension**元素，並將它設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="7ed98-120">To hide an extension from user interfaces, such as Report Designer, add a `Visible` attribute to the **Extension** element, and set it to `false`.</span></span>  
  
5.  <span data-ttu-id="7ed98-121">最後，針對為延伸模組授與 **FullTrust** 權限的自訂組件，新增程式碼群組。</span><span class="sxs-lookup"><span data-stu-id="7ed98-121">Finally, add a code group for your custom assembly that grants **FullTrust** permission for your extension.</span></span> <span data-ttu-id="7ed98-122">完成此動作的方法是，將程式碼群組加入預設位於 C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies 中的 rspreviewpolicy.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="7ed98-122">You do this by adding the code group to the rspreviewpolicy.config file located by default in C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span> <span data-ttu-id="7ed98-123">您的程式碼群組可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="7ed98-123">Your code group might look like the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 <span data-ttu-id="7ed98-124">URL 成員資格僅是您可以針對資料處理延伸模組所選擇的許多成員資格條件的其中一個。</span><span class="sxs-lookup"><span data-stu-id="7ed98-124">URL membership is only one of many membership conditions you might choose for your data processing extension.</span></span> <span data-ttu-id="7ed98-125">如需 [!INCLUDE[ssRSversion2005](../../../includes/ssrsversion2005-md.md)] 程式碼存取安全性的詳細資訊，請參閱[安全開發 &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="7ed98-125">For more information about code access security in [!INCLUDE[ssRSversion2005](../../../includes/ssrsversion2005-md.md)], see [Secure Development &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)</span></span>  
  
## <a name="generic-query-designer"></a><span data-ttu-id="7ed98-126">一般查詢設計工具</span><span class="sxs-lookup"><span data-stu-id="7ed98-126">Generic Query Designer</span></span>  
 <span data-ttu-id="7ed98-127">報表設計師提供可和自訂資料處理延伸模組搭配使用的一般查詢設計師。</span><span class="sxs-lookup"><span data-stu-id="7ed98-127">Report Designer provides a generic query designer that you can use with custom data processing extensions.</span></span> <span data-ttu-id="7ed98-128">這個設計工具包含兩個窗格：查詢窗格和結果窗格。</span><span class="sxs-lookup"><span data-stu-id="7ed98-128">This designer consists of two panes: a query pane and a results pane.</span></span> <span data-ttu-id="7ed98-129">您可以使用一般設計師來撰寫圖形化介面支援的查詢。</span><span class="sxs-lookup"><span data-stu-id="7ed98-129">You can use the generic designer to write queries that are not supported by the graphical interface.</span></span> <span data-ttu-id="7ed98-130">和圖形化查詢設計工具不同的是，一般查詢設計工具不會檢查查詢語法或重新設定查詢的結構。</span><span class="sxs-lookup"><span data-stu-id="7ed98-130">Unlike the graphical query designer, the generic query designer does not check query syntax or restructure the query.</span></span>  
  
#### <a name="to-enable-the-generic-query-designer-for-a-custom-extension"></a><span data-ttu-id="7ed98-131">啟用自訂延伸模組的一般查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="7ed98-131">To enable the generic query designer for a custom extension</span></span>  
  
-   <span data-ttu-id="7ed98-132">將下列專案新增至**設計**工具元素底下的 RSReportDesigner.config 檔案，並以 `Name` 您在先前專案中提供的名稱取代屬性。</span><span class="sxs-lookup"><span data-stu-id="7ed98-132">Add the following entry to the RSReportDesigner.config file under the **Designer** element, replacing the `Name` attribute with the name that you provided in previous entries.</span></span>  
  
    ```  
    <Extension Name="ExtensionName" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
## <a name="verifying-the-deployment"></a><span data-ttu-id="7ed98-133">確認部署</span><span class="sxs-lookup"><span data-stu-id="7ed98-133">Verifying the Deployment</span></span>  
 <span data-ttu-id="7ed98-134">在您可以確認部署之前，必須在本機電腦上，關閉 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="7ed98-134">Before you can verify deployment, you must close all instances of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] on your local computer.</span></span> <span data-ttu-id="7ed98-135">在您已經結束所有目前的工作階段後，您可以確認是否已將您的資料處理延伸模組成功部署至報表設計師，方法是在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中建立新的報表專案。</span><span class="sxs-lookup"><span data-stu-id="7ed98-135">After you have ended all current sessions, you can verify whether your data processing extension was deployed successfully to Report Designer by creating a new report project in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="7ed98-136">當您為報表建立新的資料集時，延伸模組應該會包含在可用資料來源類型的清單中。</span><span class="sxs-lookup"><span data-stu-id="7ed98-136">Your extension should be included in the list of available data source types when you create a new data set for your report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ed98-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ed98-137">See Also</span></span>  
 <span data-ttu-id="7ed98-138">[部署資料處理延伸模組](deploying-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="7ed98-138">[Deploying a Data Processing Extension](deploying-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="7ed98-139">[Reporting Services 延伸模組](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="7ed98-139">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="7ed98-140">[實作資料處理延伸模組](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="7ed98-140">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="7ed98-141">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="7ed98-141">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
