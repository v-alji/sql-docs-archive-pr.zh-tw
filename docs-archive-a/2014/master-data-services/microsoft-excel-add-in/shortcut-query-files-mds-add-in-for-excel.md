---
title: 捷徑查詢檔案 (適用於 Excel 的 MDS 增益集) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 1ba0219a-6c40-41fa-aff9-8c8f41ef3220
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fe1bdbdadabe0e6448ed3bdc65316104fb26ba43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698371"
---
# <a name="shortcut-query-files-mds-add-in-for-excel"></a><span data-ttu-id="f5078-102">捷徑查詢檔案 (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="f5078-102">Shortcut Query Files (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="f5078-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，使用捷徑查詢檔案來快速連接及載入常用的資料。</span><span class="sxs-lookup"><span data-stu-id="f5078-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], use shortcut query files to quickly connect and load frequently-used data.</span></span> <span data-ttu-id="f5078-104">當您想要將 MDS 資料與其他人分享時，也可以使用。</span><span class="sxs-lookup"><span data-stu-id="f5078-104">You can also use them when you want to share MDS data with others.</span></span> <span data-ttu-id="f5078-105">您應該儲存捷徑查詢檔案並以電子郵件送出，而不是儲存工作表並以電子郵件送出。</span><span class="sxs-lookup"><span data-stu-id="f5078-105">Instead of saving the worksheet and emailing it, you should save a shortcut query file and email that instead.</span></span> <span data-ttu-id="f5078-106">如此可確保您可連接到 MDS 儲存機制來取得最新的資料。</span><span class="sxs-lookup"><span data-stu-id="f5078-106">This ensures that you are both connecting to the MDS repository to get the latest data.</span></span>  
  
 <span data-ttu-id="f5078-107">捷徑查詢檔案是包含以下相關資訊的 XML 檔案：</span><span class="sxs-lookup"><span data-stu-id="f5078-107">Shortcut query files are XML files that contain information about:</span></span>  
  
-   <span data-ttu-id="f5078-108">MDS 儲存機制連接。</span><span class="sxs-lookup"><span data-stu-id="f5078-108">The MDS repository connection.</span></span>  
  
-   <span data-ttu-id="f5078-109">模型、版本和實體。</span><span class="sxs-lookup"><span data-stu-id="f5078-109">The model, version, and entity.</span></span>  
  
-   <span data-ttu-id="f5078-110">建立捷徑時已套用的任何篩選。</span><span class="sxs-lookup"><span data-stu-id="f5078-110">Any filters that were applied when the shortcut was created.</span></span>  
  
-   <span data-ttu-id="f5078-111">建立捷徑時，從左到右的資料行順序。</span><span class="sxs-lookup"><span data-stu-id="f5078-111">The left-to-right order of the columns when the shortcut was created.</span></span>  
  
 <span data-ttu-id="f5078-112">您可以將這些檔案儲存在清單中，並在您開啟增益集時從中選擇。</span><span class="sxs-lookup"><span data-stu-id="f5078-112">You can save these files in a list and choose from them when you open the Add-in.</span></span> <span data-ttu-id="f5078-113">您可以將其匯出到您的電腦或共用位置，或是傳送給其他人。</span><span class="sxs-lookup"><span data-stu-id="f5078-113">You can export them to your computer or to a shared location, or you can send them to others.</span></span>  
  
## <a name="queryopener-application"></a><span data-ttu-id="f5078-114">QueryOpener 應用程式</span><span class="sxs-lookup"><span data-stu-id="f5078-114">QueryOpener Application</span></span>  
 <span data-ttu-id="f5078-115">所有安裝 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 的使用者都已安裝稱為 QueryOpener 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f5078-115">All users who install the [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] have an application called QueryOpener installed.</span></span> <span data-ttu-id="f5078-116">此應用程式是用來在 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中開啟捷徑查詢檔案。</span><span class="sxs-lookup"><span data-stu-id="f5078-116">This application is used to open shortcut query files in the [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)].</span></span> <span data-ttu-id="f5078-117">如果您按兩下捷徑查詢檔案，便會自動使用此應用程式在增益集中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="f5078-117">If you double-click a shortcut query file, this application is automatically used to open the file in the Add-in.</span></span>  
  
 <span data-ttu-id="f5078-118">當您使用這個應用程式開啟捷徑查詢檔案時，系統會提示您讓連線成為「安全」連線，這表示您信任這個位置的內容。</span><span class="sxs-lookup"><span data-stu-id="f5078-118">When you open a shortcut query file with this application, you are prompted to make the connection a "safe" connection, which means you trust content from this location.</span></span> <span data-ttu-id="f5078-119">每當您將連接標示為安全時，它就會加入至清單中。</span><span class="sxs-lookup"><span data-stu-id="f5078-119">Each time you mark a connection as safe, it is added to a list.</span></span> <span data-ttu-id="f5078-120">如果您想要清除此清單，請開啟 **[設定]** 對話方塊，並按一下 **[加入至安全清單的伺服器]** 區段中的 **[全部清除]**。</span><span class="sxs-lookup"><span data-stu-id="f5078-120">If you want to clear this list, open the **Settings** dialog box and in the **Servers Added to Safe List** section, click **Clear All**.</span></span>  
  
 <span data-ttu-id="f5078-121">應用程式的預設位置為*磁片磁碟機*： \PROGRAM Files\Microsoft SQL Server\120\Master Data Services\Excel Add-In\Microsoft.MasterDataServices.QueryOpener.exe。</span><span class="sxs-lookup"><span data-stu-id="f5078-121">The default location for the application is *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\Excel Add-In\Microsoft.MasterDataServices.QueryOpener.exe.</span></span>  
  
 <span data-ttu-id="f5078-122">有兩個方式可開啟捷徑查詢檔案：您可以匯入檔案，或是按兩下檔案並自動開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="f5078-122">There are two ways to open shortcut query files: you can import them or you can double-click them and they are opened automatically.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="f5078-123">相關工作</span><span class="sxs-lookup"><span data-stu-id="f5078-123">Related Tasks</span></span>  
  
|<span data-ttu-id="f5078-124">工作描述</span><span class="sxs-lookup"><span data-stu-id="f5078-124">Task Description</span></span>|<span data-ttu-id="f5078-125">主題</span><span class="sxs-lookup"><span data-stu-id="f5078-125">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="f5078-126">將使用中工作表的內容儲存為捷徑查詢檔案。</span><span class="sxs-lookup"><span data-stu-id="f5078-126">Save the contents of the active worksheet as a shortcut query file.</span></span>|[<span data-ttu-id="f5078-127">儲存捷徑查詢檔案 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="f5078-127">Save a Shortcut Query File &#40;MDS Add-in for Excel&#41;</span></span>](save-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|<span data-ttu-id="f5078-128">將代表使用中工作表內容的捷徑查詢檔案以電子郵件送出。</span><span class="sxs-lookup"><span data-stu-id="f5078-128">Email a shortcut query file that represents the contents of the active worksheet.</span></span>|[<span data-ttu-id="f5078-129">以電子郵件傳送捷徑查詢檔案 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="f5078-129">Email a Shortcut Query File &#40;MDS Add-in for Excel&#41;</span></span>](email-a-shortcut-query-file-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="f5078-130">相關內容</span><span class="sxs-lookup"><span data-stu-id="f5078-130">Related Content</span></span>  
  
-   [<span data-ttu-id="f5078-131">連接 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="f5078-131">Connections &#40;MDS Add-in for Excel&#41;</span></span>](connections-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="f5078-132">適用於 Microsoft Excel 的 Master Data Services 增益集</span><span class="sxs-lookup"><span data-stu-id="f5078-132">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [<span data-ttu-id="f5078-133">安全性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f5078-133">Security &#40;Master Data Services&#41;</span></span>](../security-master-data-services.md)  
  
  
