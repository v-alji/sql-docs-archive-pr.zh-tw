---
title: 設定檔案上傳大小上限 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ac516c63-1e79-4ae8-bca6-32d3c1a09c00
author: minewiskan
ms.author: owend
ms.openlocfilehash: 34a0adb2f22915289cccfa1f21c51038263acca0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686495"
---
# <a name="configure-maximum-file-upload-size-powerpivot-for-sharepoint"></a><span data-ttu-id="45d69-102">設定檔案上傳的大小上限 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="45d69-102">Configure Maximum File Upload Size (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="45d69-103">PowerPivot 活頁簿經常包含大量的資料，這些資料產生的檔案會超出 SharePoint 上傳所允許的檔案大小上限。</span><span class="sxs-lookup"><span data-stu-id="45d69-103">PowerPivot workbooks often contain large amounts of data that result in files that exceed the maximum file size allowed for SharePoint uploads.</span></span> <span data-ttu-id="45d69-104">當您嘗試上傳的檔案超出上限時，您將會得到以下 SharePoint 錯誤：</span><span class="sxs-lookup"><span data-stu-id="45d69-104">When you try to upload a file that exceeds the upper limit, you will get the following error on SharePoint:</span></span>  
  
-   <span data-ttu-id="45d69-105">「指定的檔案超過支援的檔案大小上限。」</span><span class="sxs-lookup"><span data-stu-id="45d69-105">"The specified file is larger than the maximum supported file size."</span></span>  
  
 <span data-ttu-id="45d69-106">若要提高檔案大小，一開始請將 Excel Services 的 [最大活頁簿大小] 調整為 50 MB。</span><span class="sxs-lookup"><span data-stu-id="45d69-106">To increase the file size, start by adjusting the Maximum Workbook Size for Excel Services to 50 megabytes.</span></span> <span data-ttu-id="45d69-107">這樣會將 Excel 的檔案大小上限對齊 SharePoint Web 應用程式的檔案大小上限 (SharePoint 2010 中的預設值為 50 MB，SharePoint 2013 中的預設值為 200 MB)。</span><span class="sxs-lookup"><span data-stu-id="45d69-107">This aligns the maximum file size limits for Excel to those of SharePoint web applications (set to 50 megabytes by default in SharePoint 2010 and 200 in SharePoint 2013).</span></span> <span data-ttu-id="45d69-108">如果您的檔案大小超出 50 MB，請同時針對 Excel Services 和 Web 應用程式增加檔案大小限制。</span><span class="sxs-lookup"><span data-stu-id="45d69-108">If your files exceed 50 megabytes in size, increase the file size limits for both Excel Services and your web application.</span></span>  
  
 <span data-ttu-id="45d69-109">您必須是 SharePoint 管理員，才能變更檔案上傳大小上限。</span><span class="sxs-lookup"><span data-stu-id="45d69-109">You must be a SharePoint administrator to change the maximum file upload size.</span></span>  
  
### <a name="configure-maximum-file-size-for-excel-services"></a><span data-ttu-id="45d69-110">設定 Excel Services 的檔案大小上限</span><span class="sxs-lookup"><span data-stu-id="45d69-110">Configure maximum file size for Excel Services</span></span>  
  
1.  <span data-ttu-id="45d69-111">在 [管理中心] 的 [應用程式管理] 中，按一下 **[管理服務應用程式]** 。</span><span class="sxs-lookup"><span data-stu-id="45d69-111">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="45d69-112">按一下 Excel Services 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="45d69-112">Click the name of your Excel Services Application.</span></span>  
  
3.  <span data-ttu-id="45d69-113">按一下 [信任的檔案位置]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="45d69-113">Click **Trusted File Locations**.</span></span>  
  
4.  <span data-ttu-id="45d69-114">按一下此位置來編輯屬性。</span><span class="sxs-lookup"><span data-stu-id="45d69-114">Click the location to edit the properties.</span></span> <span data-ttu-id="45d69-115">根據預設，Excel Services 會將預設 Web 應用程式視為信任的網站。</span><span class="sxs-lookup"><span data-stu-id="45d69-115">By default, Excel Services considers the default web application a trusted site.</span></span> <span data-ttu-id="45d69-116">如果您要使用預設 Web 應用程式，請按一下 [http://]\*\*\*\* 開啟這個位置的組態頁面。</span><span class="sxs-lookup"><span data-stu-id="45d69-116">If you are using the default web application, click **http://** to open the configuration page for this location.</span></span>  
  
5.  <span data-ttu-id="45d69-117">捲動到 [活頁簿內容]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="45d69-117">Scroll to **Workbook Properties**.</span></span>  
  
6.  <span data-ttu-id="45d69-118">在 [最大活頁簿大小] 中，將檔案大小從 10 (預設值) 增加到 50 或是可容納您所使用之檔案的較大的大小。</span><span class="sxs-lookup"><span data-stu-id="45d69-118">In Maximum Workbook Size, increase the file size from 10 (the default value) to 50 or a larger size that accommodates the files you are working with.</span></span>  
  
     <span data-ttu-id="45d69-119">根據預設，50 MB 是 SharePoint Web 應用程式的檔案上傳大小上限。</span><span class="sxs-lookup"><span data-stu-id="45d69-119">By default, 50 megabytes is the maximum file upload size for SharePoint web applications.</span></span> <span data-ttu-id="45d69-120">如果您將 [最大活頁簿大小] 設定為大於 50 MB 的數字，請遵循下一個程序的步驟，將 SharePoint Web 應用程式的 [最大上傳大小] 增加為相同的值。</span><span class="sxs-lookup"><span data-stu-id="45d69-120">If you set Maximum Workbook Size to a number larger than 50 megabytes, follow the steps in the next procedure to increase the Maximum Upload Size for your SharePoint web application to the same value.</span></span>  
  
     <span data-ttu-id="45d69-121">您可以指定的最大值是 2 GB (或是管理中心內指定的 2047 MB)。</span><span class="sxs-lookup"><span data-stu-id="45d69-121">The maximum value that you can specify is 2 gigabytes (or 2047 megabytes as specified in Central Administration).</span></span>  
  
7.  <span data-ttu-id="45d69-122">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="45d69-122">Click **OK**.</span></span>  
  
### <a name="configure-maximum-file-size-for-a-sharepoint-web-application"></a><span data-ttu-id="45d69-123">設定 SharePoint Web 應用程式的檔案大小上限</span><span class="sxs-lookup"><span data-stu-id="45d69-123">Configure maximum file size for a SharePoint web application</span></span>  
  
1.  <span data-ttu-id="45d69-124">在 [管理中心] 的 [應用程式管理] 中，按一下 [**管理 web 應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="45d69-124">In Central Administration, in Application Management, click **Manage web applications**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="45d69-125">只有當您在 Excel Services 中增加 [最大活頁簿大小] 時，才執行以下步驟。</span><span class="sxs-lookup"><span data-stu-id="45d69-125">Perform the following steps only if you increased the Maximum Workbook Size in Excel Services.</span></span>  
  
2.  <span data-ttu-id="45d69-126">選取應用程式 (例如 **SharePoint - 80**)。</span><span class="sxs-lookup"><span data-stu-id="45d69-126">Select the application (for example, **SharePoint - 80**).</span></span>  
  
3.  <span data-ttu-id="45d69-127">在 Web 應用程式功能區中，按一下 [一般設定] 按鈕上的向下箭頭。</span><span class="sxs-lookup"><span data-stu-id="45d69-127">On the Web Applications ribbon, click the down arrow on the General Settings button.</span></span>  
  
4.  <span data-ttu-id="45d69-128">按一下 **[一般設定**]。</span><span class="sxs-lookup"><span data-stu-id="45d69-128">Click **General Settings**.</span></span>  
  
5.  <span data-ttu-id="45d69-129">捲動到 [最大上傳大小]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="45d69-129">Scroll to **Maximum Upload Size**.</span></span>  
  
6.  <span data-ttu-id="45d69-130">將此屬性設定為與 Excel Services 中 [最大活頁簿大小] 相同或更大的數字。</span><span class="sxs-lookup"><span data-stu-id="45d69-130">Set the property to the same number, or larger as the Maximum Workbook Size in Excel Services.</span></span>  
  
7.  <span data-ttu-id="45d69-131">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="45d69-131">Click **OK**.</span></span>  
  
  
