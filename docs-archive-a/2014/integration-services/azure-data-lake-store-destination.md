---
title: Azure Data Lake Store 目的地 | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSDEST.F1
- SQL11.DTS.DESIGNER.AFPADLSDEST.F1
ms.assetid: d0e86032-2a6b-48b2-898f-e94328474fde
author: yualan
ms.author: chugu
ms.openlocfilehash: 14248d14b6a944250c33a19c8cf83ab0e0330587
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707729"
---
# <a name="azure-data-lake-store-destination"></a><span data-ttu-id="089f9-102">Azure Data Lake Store 目的地</span><span class="sxs-lookup"><span data-stu-id="089f9-102">Azure Data Lake Store Destination</span></span>
  <span data-ttu-id="089f9-103">**Azure Data Lake Store 目的地** 元件可讓 SSIS 套件將資料寫入 Azure Data Lake Store。</span><span class="sxs-lookup"><span data-stu-id="089f9-103">The **Azure Data Lake Store Destination** component enables an SSIS package to write data to an Azure Data Lake Store.</span></span> <span data-ttu-id="089f9-104">支援的檔案格式為文字、Avro 和 ORC。</span><span class="sxs-lookup"><span data-stu-id="089f9-104">The supported file formats are: Text, Avro and ORC.</span></span> 
  
## <a name="configure-the-azure-data-lake-store-destination"></a><span data-ttu-id="089f9-105">設定 Azure Data Lake Store 目的地</span><span class="sxs-lookup"><span data-stu-id="089f9-105">Configure the Azure Data Lake Store Destination</span></span> 

1. <span data-ttu-id="089f9-106">將 **Azure Data Lake Store 目的地** 拖放到資料流程設計師，然後在上面按兩下以查看編輯器。</span><span class="sxs-lookup"><span data-stu-id="089f9-106">Drag-drop **Azure Data Lake Store Destination** to the data flow designer and double-click it to see the editor.</span></span>  

2.  <span data-ttu-id="089f9-107">在 [Azure Data Lake Store 連線管理員]  欄位指定現有的 Azure Data Lake Store 連線管理員，或建立參考 Azure Data Lake Store 服務的新連線管理員。</span><span class="sxs-lookup"><span data-stu-id="089f9-107">For the **Azure Data Lake Store connection manager** field, specify an existing Azure Data Lake Store Connection Manager or create a new one that refers to an Azure Data Lake Store service.</span></span>  
  
    1.  <span data-ttu-id="089f9-108">在 [檔案路徑] \*\*\*\* 欄位指定想要寫入資料的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="089f9-108">For the **File Path** field, specify the file name you want to write data to.</span></span> <span data-ttu-id="089f9-109">如果此檔案已經存在，即會覆寫其內容。</span><span class="sxs-lookup"><span data-stu-id="089f9-109">If this file already exist, its content will be overwritten.</span></span>  
  
    2.  <span data-ttu-id="089f9-110">在 [檔案格式] \*\*\*\* 欄位指定想要使用的檔案格式。</span><span class="sxs-lookup"><span data-stu-id="089f9-110">For the **File format** field, specify the file format you want to use.</span></span>  
  
        <span data-ttu-id="089f9-111">檔案格式若為文字，則您必須指定 [資料行分隔符號字元]  值。</span><span class="sxs-lookup"><span data-stu-id="089f9-111">If the file format is Text, you must specify the **Column delimiter character** value.</span></span> <span data-ttu-id="089f9-112">如果檔案中的第一個資料列包含資料行名稱，也請選取**第一個資料列中的資料行名稱**。</span><span class="sxs-lookup"><span data-stu-id="089f9-112">Also  select **Column names in the first data row** if the first row in the file contains column names.</span></span>  

        <span data-ttu-id="089f9-113">如果使用 ORC 檔案格式，您需要安裝對應平台的 JRE。</span><span class="sxs-lookup"><span data-stu-id="089f9-113">If the file format is ORC, you need to install JRE of corresponding platform.</span></span> 
  
3.  <span data-ttu-id="089f9-114">指定連接資訊後，請切換至 [資料行]  頁面，將來源資料行對應至 SSIS 資料流程的目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="089f9-114">After specifying the connection information, switch to the **Columns** page to map source columns to destination columns for the SSIS data flow.</span></span>  
