---
title: Azure Blob 來源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobsrc.f1
- sql11.dts.designer.afpblobsrc.f1
ms.assetid: 80645c5c-88c8-4fb0-8607-de1bb7bffcbb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a14c7022437c8a23f898a0f29c211bd9ae82aa0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599627"
---
# <a name="azure-blob-source"></a><span data-ttu-id="e815b-102">Azure Blob 來源</span><span class="sxs-lookup"><span data-stu-id="e815b-102">Azure Blob Source</span></span>
 <span data-ttu-id="e815b-103">**Azure Blob 來源** 元件可讓 SSIS 封裝從 Azure Blob 讀取資料。</span><span class="sxs-lookup"><span data-stu-id="e815b-103">The **Azure Blob Source** component enables an SSIS package to read data from an Azure blob.</span></span> <span data-ttu-id="e815b-104">支援的檔案格式：CSV 與 AVRO。</span><span class="sxs-lookup"><span data-stu-id="e815b-104">The supported file formats are: CSV and AVRO.</span></span> <span data-ttu-id="e815b-105">若要查看 Azure Blob 來源的編輯器，可在資料流程設計師上拖放 **Azure Blob 來源** ，並連按兩下以開啟編輯器。</span><span class="sxs-lookup"><span data-stu-id="e815b-105">To see the editor for the Azure Blob Source, drag and drop **Azure Blob Source** on the data flow designer and double-click it to open the editor).</span></span>  
  
1.  <span data-ttu-id="e815b-106">針對 [Azure 儲存體連線管理員]\*\*\*\* 欄位，請指定現有的 Azure 儲存體連線管理員，或建立參考 Azure 儲存體帳戶的新連線管理員。</span><span class="sxs-lookup"><span data-stu-id="e815b-106">For the **Azure storage connection manager** field, specify an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account.</span></span>  
  
2.  <span data-ttu-id="e815b-107">針對 [Blob 容器名稱]\*\*\*\* 欄位，請指定包含原始程式檔的 Blob 容器名稱。</span><span class="sxs-lookup"><span data-stu-id="e815b-107">For the **Blob container name** field, specify the name of the blob container that contains source files.</span></span>  
  
3.  <span data-ttu-id="e815b-108">針對 [Blob 名稱]\*\*\*\* 欄位，請指定 Blob 的路徑。</span><span class="sxs-lookup"><span data-stu-id="e815b-108">For the **Blob name** field, specify the path for the blob.</span></span>  
  
4.  <span data-ttu-id="e815b-109">針對 [Blob 檔案格式]\*\*\*\* 欄位，請指定要使用的 Blob 格式。</span><span class="sxs-lookup"><span data-stu-id="e815b-109">For the **Blob file format** field, specify the blob format you want to use.</span></span>  
  
5.  <span data-ttu-id="e815b-110">若檔案格式為 CSV，則您必須指定 [資料行分隔符號字元]\*\*\*\* 值。</span><span class="sxs-lookup"><span data-stu-id="e815b-110">If the file format is CSV, you must specify the **Column delimiter character** value.</span></span> <span data-ttu-id="e815b-111">若檔案中第一個資料列包含資料行名稱，請選取 [第一個資料列的資料行名稱]  。</span><span class="sxs-lookup"><span data-stu-id="e815b-111">Also select **Column names in the first data row** if the first row in the file contains column names.</span></span>  
  
6.  <span data-ttu-id="e815b-112">指定連接資訊後，請切換至 [資料行]  頁面，將來源資料行對應至 SSIS 資料流程的目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="e815b-112">After specifying the connection information, switch to the **Columns** page to map source columns to destination columns for the SSIS data flow.</span></span>  
  
  
