---
title: Azure Data Lake Store 來源 | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSSRC.F1
- SQL11.DTS.DESIGNER.AFPADLSSRC.F1
ms.assetid: 7d9e8457-62aa-4aea-98ee-7d1121dfae4f
author: yualan
ms.author: chugu
ms.openlocfilehash: e5bce25e303b055d734da6a00c73851f4eb0d7ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597294"
---
# <a name="azure-data-lake-store-source"></a><span data-ttu-id="abd3b-102">Azure Data Lake Store 來源</span><span class="sxs-lookup"><span data-stu-id="abd3b-102">Azure Data Lake Store Source</span></span>
  <span data-ttu-id="abd3b-103">**Azure Data Lake Store 來源** 元件可讓 SSIS 套件從 Azure Data Lake Store 讀取資料。</span><span class="sxs-lookup"><span data-stu-id="abd3b-103">The **Azure Data Lake Store Source** component enables an SSIS package to read data from an Azure Data Lake Store.</span></span> <span data-ttu-id="abd3b-104">支援的檔案格式：文字和 Avro。</span><span class="sxs-lookup"><span data-stu-id="abd3b-104">The supported file formats are: Text and Avro.</span></span>
  
## <a name="configure-the-azure-data-lake-store-source"></a><span data-ttu-id="abd3b-105">設定 Azure Data Lake Store 來源</span><span class="sxs-lookup"><span data-stu-id="abd3b-105">Configure the Azure Data Lake Store Source</span></span> 
  
1.  <span data-ttu-id="abd3b-106">若要查看 Azure Data Lake Store 來源的編輯器，可在資料流程設計師上拖放 **Azure Data Lake Store 來源** ，並連按兩下以開啟編輯器。</span><span class="sxs-lookup"><span data-stu-id="abd3b-106">To see the editor for the Azure Data Lake Store Source, drag and drop **Azure Data Lake Store Source** on the data flow designer and double-click it to open the editor).</span></span>  
  
2.  <span data-ttu-id="abd3b-107">在 [Azure Data Lake Store 連線管理員]  欄位指定現有的 Azure Data Lake Store 連線管理員，或建立參考 Azure Data Lake Store 服務的新連線管理員。</span><span class="sxs-lookup"><span data-stu-id="abd3b-107">For the **Azure Data Lake Store connection manager** field, specify an existing Azure Data Lake Store Connection Manager or create a new one that refers to an Azure Data Lake Store service.</span></span>  
  
    1.  <span data-ttu-id="abd3b-108">在 [檔案路徑]  欄位指定 Azure Data Lake Store 來源檔案的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="abd3b-108">For the **File Path** field, specify the file path of the source file in Azure Data Lake Store.</span></span>   
  
    2.  <span data-ttu-id="abd3b-109">在 [檔案格式]  欄位指定來源檔案的檔案格式。</span><span class="sxs-lookup"><span data-stu-id="abd3b-109">For the **File format** field, specify the file format of the source file.</span></span>  
  
        <span data-ttu-id="abd3b-110">檔案格式若為文字，則您必須指定 [資料行分隔符號字元]  值。</span><span class="sxs-lookup"><span data-stu-id="abd3b-110">If the file format is Text, you must specify the **Column delimiter character** value.</span></span> <span data-ttu-id="abd3b-111">若檔案中第一個資料列包含資料行名稱，請選取 [第一個資料列的資料行名稱]  。</span><span class="sxs-lookup"><span data-stu-id="abd3b-111">Also select **Column names in the first data row** if the first row in the file contains column names.</span></span>  
  
3.  <span data-ttu-id="abd3b-112">指定連接資訊後，請切換至 [資料行]  頁面，將來源資料行對應至 SSIS 資料流程的目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="abd3b-112">After specifying the connection information, switch to the **Columns** page to map source columns to destination columns for the SSIS data flow.</span></span>  
