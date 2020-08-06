---
title: 將檔上傳至 sharepoint 文件庫 (Reporting Services SharePoint 模式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- SharePoint integration [Reporting Services], content management
- uploading reports [Reporting Services]
ms.assetid: 93bd1b19-061b-409f-8dc2-ec416b2f4b39
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 74b39f90cd90dc8a92a5f10168d98f165c211c51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706098"
---
# <a name="upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode"></a><span data-ttu-id="8d91b-102">將文件上傳到 SharePoint 文件庫 (SharePoint 模式的 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="8d91b-102">Upload Documents to a SharePoint Library (Reporting Services in SharePoint Mode)</span></span>
  <span data-ttu-id="8d91b-103">您可以將報表定義和報表模型上傳到 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="8d91b-103">You can upload report definitions and report models to a SharePoint library.</span></span> <span data-ttu-id="8d91b-104">上傳報表伺服器項目時，您必須選取文件庫或文件庫內的資料夾；</span><span class="sxs-lookup"><span data-stu-id="8d91b-104">When uploading a report server item, you must select a library or a folder within a library.</span></span> <span data-ttu-id="8d91b-105">不能將報表伺服器項目上傳到清單或頁面中。</span><span class="sxs-lookup"><span data-stu-id="8d91b-105">You cannot upload a report server item to a list or page.</span></span>  
  
 <span data-ttu-id="8d91b-106">您無法上傳資料來源 (.rds) 檔案。</span><span class="sxs-lookup"><span data-stu-id="8d91b-106">You cannot upload a data source (.rds) file.</span></span> <span data-ttu-id="8d91b-107">不過，您可以從設計工具 (例如，報表設計師) 將 .rds 檔案發行到 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="8d91b-107">However, you can publish .rds files from a design tool, such as Report Designer, to a SharePoint library.</span></span> <span data-ttu-id="8d91b-108">在發行過程中，方案會從原始的 .rsds 檔案建立新的 .rds 檔案。</span><span class="sxs-lookup"><span data-stu-id="8d91b-108">During publication, a new .rsds file is created from the original .rds file in the solution.</span></span> <span data-ttu-id="8d91b-109">您也可以在 SharePoint 文件庫中建立新的 .rsds 檔案，然後再設定已上傳的報表和模型中的資料來源連接屬性，以使用新的連接。</span><span class="sxs-lookup"><span data-stu-id="8d91b-109">You can also create a new .rsds file in a SharePoint library and then set data source connection properties in the uploaded reports and models to use the new connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8d91b-110">您必須針對 SharePoint 模式設定報表伺服器，同時 SharePoint 產品的執行個體必須具有 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 增益集，以便提供從 SharePoint 網站儲存及存取報表伺服器項目的程式檔案。</span><span class="sxs-lookup"><span data-stu-id="8d91b-110">The report server must be configured for SharePoint mode, and the instance of the SharePoint product must have the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in that provides program files for storing and accessing report server items from a SharePoint site.</span></span>  
  
 <span data-ttu-id="8d91b-111">若要將文件上傳至文件庫，您必須擁有網站層級的「加入項目」權限。</span><span class="sxs-lookup"><span data-stu-id="8d91b-111">To upload a document to a library, you must have the "Add Items" permission at the site level.</span></span> <span data-ttu-id="8d91b-112">如果使用預設安全性設定，擁有完整控制權限等級的**擁有者**群組和擁有「參與」(Contribute) 權限等級的**成員**群組都會取得這個權限。</span><span class="sxs-lookup"><span data-stu-id="8d91b-112">If you are using default security settings, this permission is granted to members of the **Owners** group who have the Full Control level of permission and to the **Members** group who have the Contribute level of permission.</span></span>  
  
### <a name="to-add-a-report-definition-or-report-model-to-a-library"></a><span data-ttu-id="8d91b-113">將報表定義或報表模型加入至文件庫</span><span class="sxs-lookup"><span data-stu-id="8d91b-113">To add a report definition or report model to a library</span></span>  
  
1.  <span data-ttu-id="8d91b-114">開啟文件庫或文件庫內的資料夾。</span><span class="sxs-lookup"><span data-stu-id="8d91b-114">Open the library or a folder within a library.</span></span> <span data-ttu-id="8d91b-115">如果尚未開啟文件庫，請按一下 [快速啟動] 上的文件庫名稱。</span><span class="sxs-lookup"><span data-stu-id="8d91b-115">If the library is not already open, click its name on the Quick Launch.</span></span> <span data-ttu-id="8d91b-116">如果找不到您的文件庫名稱，請先按一下 **[檢視所有網站內容]**，然後再按一下文件庫名稱。</span><span class="sxs-lookup"><span data-stu-id="8d91b-116">If the name of your library does not appear, click **View All Site Content**, and then click the name of your library.</span></span>  
  
2.  <span data-ttu-id="8d91b-117">在 [上傳]\*\*\*\* 功能表上，按一下 [上傳文件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8d91b-117">On the **Upload** menu, click **Upload document**.</span></span>  
  
3.  <span data-ttu-id="8d91b-118">若要上傳單一報表或報表模型檔案，請選取報表定義 (.rdl) 或報表模型 (.smdl) 檔案，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8d91b-118">To upload a single report or report model file, select a report definition (.rdl) or report model (.smdl) file and then click **OK**.</span></span>  
  
     <span data-ttu-id="8d91b-119">如果報表定義使用共用資料來源 (.rsds) 檔案，將連接資訊儲存在外部資料來源中，您可以同時上傳 .rdl 和 .rsds 檔案。</span><span class="sxs-lookup"><span data-stu-id="8d91b-119">If the report definition uses a shared data source (.rsds) file to store connection information to an external data source, you can upload the .rdl and the .rsds file at the same time.</span></span> <span data-ttu-id="8d91b-120">若要這樣做，請按一下 [上傳多份文件]\*\*\*\*，指定要上傳的兩個檔案，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8d91b-120">To do this, click **Upload Multiple Documents**, specify both files, and then click **OK**.</span></span>  
  
 <span data-ttu-id="8d91b-121">如果您上傳的報表包含共用資料來源、報表模型或子報表的參考，上傳檔案時，報表中的參考將會中斷。</span><span class="sxs-lookup"><span data-stu-id="8d91b-121">If you upload a report that contains references to shared data sources, report models, or subreports, the references will be broken in the report when the files are uploaded.</span></span> <span data-ttu-id="8d91b-122">如需如何重設參考的詳細資訊，請參閱[建立和管理共用資料來源 &#40;SharePoint 整合模式的 Reporting Services&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="8d91b-122">For more information about how to reset the references, see [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).</span></span>  
  
 <span data-ttu-id="8d91b-123">上傳報表後，報表會在您開啟時視需要執行，以擷取資料來源中的即時資料。</span><span class="sxs-lookup"><span data-stu-id="8d91b-123">When you upload a report, it runs on demand when you open it, retrieving live data from the data source.</span></span> <span data-ttu-id="8d91b-124">您可以設定讓報表依排程擷取資料或使用快取資料。</span><span class="sxs-lookup"><span data-stu-id="8d91b-124">You can configure the report to retrieve data on a schedule or use cached data.</span></span> <span data-ttu-id="8d91b-125">如需詳細資訊，請參閱[設定處理選項 &#40;SharePoint 整合模式的 Reporting Services&#41;](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="8d91b-125">For more information, see [Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md).</span></span>  
  
 <span data-ttu-id="8d91b-126">報表可以包含參數，以便讓使用者篩選資料。</span><span class="sxs-lookup"><span data-stu-id="8d91b-126">A report can contain parameters so that users can filter data.</span></span> <span data-ttu-id="8d91b-127">您可將參數設定成使用特定值，或變更使用者看到的參數外觀。</span><span class="sxs-lookup"><span data-stu-id="8d91b-127">You can configure the parameters to use specific values or change how they appear to the user.</span></span> <span data-ttu-id="8d91b-128">如需詳細資訊，請參閱[在已發行的報表上設定參數 &#40;SharePoint 整合模式的 Reporting Services&#41;](report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="8d91b-128">For more information, see [Set Parameters on a Published Report &#40;Reporting Services in SharePoint Integrated Mode&#41;](report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d91b-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d91b-129">See Also</span></span>  
 <span data-ttu-id="8d91b-130">[將報表發行至 SharePoint 文件庫](reports/publish-a-report-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="8d91b-130">[Publish a Report to a SharePoint Library](reports/publish-a-report-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="8d91b-131">[將共用資料來源發行至 SharePoint 文件庫](reports/publish-a-shared-data-source-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="8d91b-131">[Publish a Shared Data Source to a SharePoint Library](reports/publish-a-shared-data-source-to-a-sharepoint-library.md) </span></span>  
 [<span data-ttu-id="8d91b-132">授與 SharePoint 網站上報表伺服器項目的權限</span><span class="sxs-lookup"><span data-stu-id="8d91b-132">Granting Permissions on Report Server Items on a SharePoint Site</span></span>](security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
  
  
