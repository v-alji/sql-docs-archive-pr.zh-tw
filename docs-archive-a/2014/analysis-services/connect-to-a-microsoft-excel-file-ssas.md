---
title: 連接到 Microsoft Excel 檔案 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connexcelfile.f1
ms.assetid: 126f7d6b-d270-40e7-b23e-8d114f87065b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 79bb3d57470be8acbbb990dde71cf21b62b3cb2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593022"
---
# <a name="connect-to-a-microsoft-excel-file-ssas"></a><span data-ttu-id="a0e2f-102">連接到 Microsoft Excel 檔案 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="a0e2f-102">Connect to a Microsoft Excel File (SSAS)</span></span>
  <span data-ttu-id="a0e2f-103">**[資料表匯入精靈]** 的這個頁面可讓您連接到儲存在本機電腦上的 Microsoft Excel 檔案。</span><span class="sxs-lookup"><span data-stu-id="a0e2f-103">This page of the **Table Import Wizard** enables you to connect to a Microsoft Excel file stored on the local machine.</span></span> <span data-ttu-id="a0e2f-104">若要從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]存取精靈，請按一下 **[模型]** 功能表上的 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="a0e2f-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="a0e2f-105">若要連接 Microsoft Excel 檔案，您必須先在電腦上安裝適當的 ACE 提供者。</span><span class="sxs-lookup"><span data-stu-id="a0e2f-105">To connect to a Microsoft Excel file, you must have the appropriate ACE provider installed on your computer.</span></span> <span data-ttu-id="a0e2f-106">如需詳細資訊，請參閱[支援的資料來源 &#40;SSAS 表格式&#41;](tabular-models/data-sources-supported-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="a0e2f-106">For more information, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a0e2f-107">在這個頁面中選取檔案時，會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="a0e2f-107">The credentials of the current user are used when selecting a file in this page.</span></span> <span data-ttu-id="a0e2f-108">不過，如果在 [模擬資訊] 頁面中指定的使用者未具備從所選檔案讀取的權限，則匯入將不會成功。</span><span class="sxs-lookup"><span data-stu-id="a0e2f-108">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected file.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="a0e2f-109">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="a0e2f-109">UI element list</span></span>  
 <span data-ttu-id="a0e2f-110">**易記連接名稱**</span><span class="sxs-lookup"><span data-stu-id="a0e2f-110">**Friendly connection name**</span></span>  
 <span data-ttu-id="a0e2f-111">為此資料來源連接輸入唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="a0e2f-111">Type a unique name for this data source connection.</span></span> <span data-ttu-id="a0e2f-112">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="a0e2f-112">This is a required field.</span></span>  
  
 <span data-ttu-id="a0e2f-113">**Excel 檔案路徑**</span><span class="sxs-lookup"><span data-stu-id="a0e2f-113">**Excel File Path**</span></span>  
 <span data-ttu-id="a0e2f-114">指定 Excel 檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="a0e2f-114">Specify a full path for the Excel file.</span></span>  
  
 <span data-ttu-id="a0e2f-115">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="a0e2f-115">**Browse**</span></span>  
 <span data-ttu-id="a0e2f-116">導覽至有 Excel 檔案可用的位置。</span><span class="sxs-lookup"><span data-stu-id="a0e2f-116">Navigate to a location where an Excel file is available.</span></span>  
  
 <span data-ttu-id="a0e2f-117">**進階**</span><span class="sxs-lookup"><span data-stu-id="a0e2f-117">**Advanced**</span></span>  
 <span data-ttu-id="a0e2f-118">使用 [**設定高級屬性**] 對話方塊來設定其他連接屬性。</span><span class="sxs-lookup"><span data-stu-id="a0e2f-118">Set additional connection properties by using the **Set Advanced Properties** dialog box..</span></span>  
  
 <span data-ttu-id="a0e2f-119">**使用第一個資料列做為資料行標頭**</span><span class="sxs-lookup"><span data-stu-id="a0e2f-119">**Use first row as column headers**</span></span>  
 <span data-ttu-id="a0e2f-120">指定是否要使用第一個資料列做為目的地資料表的資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="a0e2f-120">Specify whether to use the first data row as the column headers of the destination table.</span></span>  
  
 <span data-ttu-id="a0e2f-121">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="a0e2f-121">**Test Connection**</span></span>  
 <span data-ttu-id="a0e2f-122">嘗試使用目前的設定建立與資料來源之間的連接。</span><span class="sxs-lookup"><span data-stu-id="a0e2f-122">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="a0e2f-123">顯示一則訊息，指出連接是否成功。</span><span class="sxs-lookup"><span data-stu-id="a0e2f-123">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
