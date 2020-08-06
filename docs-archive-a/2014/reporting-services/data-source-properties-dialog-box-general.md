---
title: 資料來源屬性對話方塊、一般 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasourceproperties.general.f1
- "10120"
ms.assetid: 44b5edd3-5c11-4d3d-91b8-5871aa0572ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c79ad70cdd4dcb10e1abce1102fa39eef4c67461
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585147"
---
# <a name="data-source-properties-dialog-box-general"></a><span data-ttu-id="612f9-102">資料來源屬性對話方塊、一般</span><span class="sxs-lookup"><span data-stu-id="612f9-102">Data Source Properties Dialog Box, General</span></span>
  <span data-ttu-id="612f9-103">選取 **[資料來源屬性]** 對話方塊上的 **[一般]** ，即可在報表中顯示和修改資料來源的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="612f9-103">Select **General** on the **Data Source Properties** dialog box to display and modify connection information for a data source in the report.</span></span>  
  
## <a name="options"></a><span data-ttu-id="612f9-104">選項。</span><span class="sxs-lookup"><span data-stu-id="612f9-104">Options</span></span>  
 <span data-ttu-id="612f9-105">**名稱**</span><span class="sxs-lookup"><span data-stu-id="612f9-105">**Name**</span></span>  
 <span data-ttu-id="612f9-106">輸入資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="612f9-106">Type the name of the data source.</span></span> <span data-ttu-id="612f9-107">資料來源名稱在報表內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="612f9-107">The data source name must be unique within the report.</span></span> <span data-ttu-id="612f9-108">根據預設，系統會將一般名稱 (例如，DataSource1 或 DataSource2) 指派給資料來源。</span><span class="sxs-lookup"><span data-stu-id="612f9-108">By default, a general name, such as DataSource1 or DataSource2, is assigned to the data source.</span></span>  
  
 <span data-ttu-id="612f9-109">**內嵌連接**</span><span class="sxs-lookup"><span data-stu-id="612f9-109">**Embedded connection**</span></span>  
 <span data-ttu-id="612f9-110">當您不想要使用共用資料來源時，選取此選項。</span><span class="sxs-lookup"><span data-stu-id="612f9-110">Select this option when you do not want to use a shared data source.</span></span>  
  
 <span data-ttu-id="612f9-111">**型別**</span><span class="sxs-lookup"><span data-stu-id="612f9-111">**Type**</span></span>  
 <span data-ttu-id="612f9-112">選取資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="612f9-112">Select a data processing extension.</span></span> <span data-ttu-id="612f9-113">此清單會顯示所有已註冊的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="612f9-113">The list displays all registered extensions.</span></span>  
  
 <span data-ttu-id="612f9-114">**連接字串**</span><span class="sxs-lookup"><span data-stu-id="612f9-114">**Connection string**</span></span>  
 <span data-ttu-id="612f9-115">輸入資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="612f9-115">Enter a connection string for the data source.</span></span> <span data-ttu-id="612f9-116">按一下 **[編輯]** ，即可使用 **[連接屬性]** 對話方塊來建立連接字串。</span><span class="sxs-lookup"><span data-stu-id="612f9-116">Click **Edit** to build the connection string using the **Connection Properties** dialog box.</span></span> <span data-ttu-id="612f9-117">請按一下 [運算式]\*\*\*\* (*fx*) 按鈕來編輯運算式。</span><span class="sxs-lookup"><span data-stu-id="612f9-117">Click the **Expressions** (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="612f9-118">**使用共用資料來源參考**</span><span class="sxs-lookup"><span data-stu-id="612f9-118">**Use shared data source reference**</span></span>  
 <span data-ttu-id="612f9-119">選取此選項即可連結至共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="612f9-119">Select this option to link to a shared data source.</span></span> <span data-ttu-id="612f9-120">從下拉式清單選取共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="612f9-120">Select a shared data source from the drop-down list.</span></span> <span data-ttu-id="612f9-121">若要編輯選取的資料來源，請按一下 **[編輯]**。</span><span class="sxs-lookup"><span data-stu-id="612f9-121">To edit the selected data source, click **Edit**.</span></span> <span data-ttu-id="612f9-122">如果選取 **[使用共用資料來源參考]** ，就會停用 **[類型]** 和 **[連接字串]** 。</span><span class="sxs-lookup"><span data-stu-id="612f9-122">If **Use shared data source reference** is selected, **Type** and **Connection string** are disabled.</span></span>  
  
 <span data-ttu-id="612f9-123">**處理查詢時使用單一交易**</span><span class="sxs-lookup"><span data-stu-id="612f9-123">**Use a single transaction when processing the queries**</span></span>  
 <span data-ttu-id="612f9-124">選取此選項，指出使用此資料來源的資料集會在單一交易中針對資料庫執行。</span><span class="sxs-lookup"><span data-stu-id="612f9-124">Select this option to indicate that datasets that use this data source are run in a single transaction against the database.</span></span> <span data-ttu-id="612f9-125">若要包含使用相同資料來源之子報表的交易，請在 **[屬性]** 窗格之子報表的 **[其他屬性]** 區段中，將 **MergeTransactions** 設定為 **True** 。</span><span class="sxs-lookup"><span data-stu-id="612f9-125">To include transactions for subreports that use the same data source, set **MergeTransactions** to **True** in the subreport's **Other** properties section of the **Properties** pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="612f9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="612f9-126">See Also</span></span>  
 <span data-ttu-id="612f9-127">[將資料加入報表 &#40;報表產生器和 SSRS&#41;](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="612f9-127">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="612f9-128">[建立 &#40;SSRS&#41;的內嵌或共用資料來源](../../2014/reporting-services/create-an-embedded-or-shared-data-source-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="612f9-128">[Create an Embedded or Shared Data Source &#40;SSRS&#41;](../../2014/reporting-services/create-an-embedded-or-shared-data-source-ssrs.md) </span></span>  
 <span data-ttu-id="612f9-129">[Reporting Services 中的資料連線、資料來源及連接字串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="612f9-129">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="612f9-130">資料來源屬性對話方塊、認證</span><span class="sxs-lookup"><span data-stu-id="612f9-130">Data Source Properties Dialog Box, Credentials</span></span>](../../2014/reporting-services/data-source-properties-dialog-box-credentials.md)  
  
  
