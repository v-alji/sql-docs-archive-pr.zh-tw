---
title: Excel 連線管理員編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelconnection.f1
helpviewer_keywords:
- Excel Connection Manager Editor
ms.assetid: 7ff097e4-cafb-4885-a898-05b2a46628c1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f66de13b710e5ccb577e6f2d67c215572e34767
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596803"
---
# <a name="excel-connection-manager-editor"></a><span data-ttu-id="3d3f3-102">Excel 連接管理員編輯器</span><span class="sxs-lookup"><span data-stu-id="3d3f3-102">Excel Connection Manager Editor</span></span>
  <span data-ttu-id="3d3f3-103">使用 [Excel 連線管理員編輯器]\*\*\*\* 對話方塊，將連接加入現有或新的 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 活頁簿檔案。</span><span class="sxs-lookup"><span data-stu-id="3d3f3-103">Use the **Excel Connection Manager Editor** dialog box to add a connection to an existing or a new [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] workbook file.</span></span>  
  
 <span data-ttu-id="3d3f3-104">若要深入了解快取連線管理員，請參閱 [Excel 連線管理員](connection-manager/excel-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3f3-104">To learn more about the Excel connection manager, see [Excel Connection Manager](connection-manager/excel-connection-manager.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3d3f3-105">您不能連接到受密碼保護的 Excel 檔案。</span><span class="sxs-lookup"><span data-stu-id="3d3f3-105">You cannot connect to a password-protected Excel file.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3d3f3-106">選項</span><span class="sxs-lookup"><span data-stu-id="3d3f3-106">Options</span></span>  
 <span data-ttu-id="3d3f3-107">**Excel 檔案路徑**</span><span class="sxs-lookup"><span data-stu-id="3d3f3-107">**Excel file path**</span></span>  
 <span data-ttu-id="3d3f3-108">輸入現有或新的 Excel 活頁簿檔案 (.xls) 的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="3d3f3-108">Type the path and file name of an existing or a new Excel workbook file (.xls).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="3d3f3-109">當您選取指向新的/不存在檔案的**Excel 連接**，然後針對**Excel 工作表的 [名稱**] 按一下 [**新增**] 時，[ **Excel 目的地編輯器**] 會自動建立 excel 檔案。</span><span class="sxs-lookup"><span data-stu-id="3d3f3-109">The **Excel Destination Editor** automatically creates the Excel file when you select an **Excel Connection** that points to a new/non-existent file and then click **New** for **Name of the Excel Sheet**.</span></span>  
  
 <span data-ttu-id="3d3f3-110">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="3d3f3-110">**Browse**</span></span>  
 <span data-ttu-id="3d3f3-111">使用 [**開啟**] 對話方塊，即可流覽至 excel 檔案所在的資料夾，或您要建立新檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="3d3f3-111">Use the **Open** dialog box to navigate to the folder in which the excel file exists or where you want to create the new file.</span></span>  
  
 <span data-ttu-id="3d3f3-112">**Excel 版本**</span><span class="sxs-lookup"><span data-stu-id="3d3f3-112">**Excel version**</span></span>  
 <span data-ttu-id="3d3f3-113">指定用於建立檔案的 Microsoft Excel 版本。</span><span class="sxs-lookup"><span data-stu-id="3d3f3-113">Specify the version of Microsoft Excel that was used to create the file.</span></span>  
  
|<span data-ttu-id="3d3f3-114">選項</span><span class="sxs-lookup"><span data-stu-id="3d3f3-114">Option</span></span>|<span data-ttu-id="3d3f3-115">描述</span><span class="sxs-lookup"><span data-stu-id="3d3f3-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3d3f3-116">Excel 97-2003</span><span class="sxs-lookup"><span data-stu-id="3d3f3-116">Excel 97-2003</span></span>|<span data-ttu-id="3d3f3-117">檔案是使用 Excel 97 或更新版本建立的。</span><span class="sxs-lookup"><span data-stu-id="3d3f3-117">File was created using Excel 97 or later.</span></span>|  
|<span data-ttu-id="3d3f3-118">Excel 3。0</span><span class="sxs-lookup"><span data-stu-id="3d3f3-118">Excel 3.0</span></span>|<span data-ttu-id="3d3f3-119">檔案是使用 Excel 3.0 所建立。</span><span class="sxs-lookup"><span data-stu-id="3d3f3-119">File was created using Excel 3.0.</span></span>|  
|<span data-ttu-id="3d3f3-120">Excel 4。0</span><span class="sxs-lookup"><span data-stu-id="3d3f3-120">Excel 4.0</span></span>|<span data-ttu-id="3d3f3-121">檔案是使用 Excel 4.0 建立的。</span><span class="sxs-lookup"><span data-stu-id="3d3f3-121">File was created using Excel 4.0.</span></span>|  
|<span data-ttu-id="3d3f3-122">Excel 5。0</span><span class="sxs-lookup"><span data-stu-id="3d3f3-122">Excel 5.0</span></span>|<span data-ttu-id="3d3f3-123">檔案是使用 Excel 95 (7.0) 建立的。</span><span class="sxs-lookup"><span data-stu-id="3d3f3-123">File was created using Excel 95 (7.0).</span></span>|  
  
 <span data-ttu-id="3d3f3-124">**第一個資料列有資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="3d3f3-124">**First row has column names**</span></span>  
 <span data-ttu-id="3d3f3-125">指定選取之工作表中資料的第一個資料列是否包含資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="3d3f3-125">Specify whether the first row of data in the selected worksheet contains column names.</span></span> <span data-ttu-id="3d3f3-126">此選項的預設值是 **[True]**。</span><span class="sxs-lookup"><span data-stu-id="3d3f3-126">The default value of this option is **True**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d3f3-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d3f3-127">See Also</span></span>  
 <span data-ttu-id="3d3f3-128">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3d3f3-128">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="3d3f3-129">使用 Foreach 迴圈容器來執行 Excel 檔案和資料表迴圈</span><span class="sxs-lookup"><span data-stu-id="3d3f3-129">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
