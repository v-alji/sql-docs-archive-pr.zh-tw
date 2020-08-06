---
title: Azure Blob 目的地 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobdest.f1
- sql11.dts.designer.afpblobdest.f1
ms.assetid: 820a1e7a-7182-4c7b-ab56-5b4097a7e042
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fb406d38b17748e8284acee4b2849a9fd99e53ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706613"
---
# <a name="azure-blob-destination"></a><span data-ttu-id="f8be0-102">Azure Blob 目的地</span><span class="sxs-lookup"><span data-stu-id="f8be0-102">Azure Blob Destination</span></span>
  <span data-ttu-id="f8be0-103">[Azure Blob 目的地]  元件可讓 SSIS 封裝將資料寫入 Azure Blob。</span><span class="sxs-lookup"><span data-stu-id="f8be0-103">The **Azure Blob Destination** component enables an SSIS package to write data to an Azure blob.</span></span> <span data-ttu-id="f8be0-104">支援的檔案格式：CSV 與 AVRO。</span><span class="sxs-lookup"><span data-stu-id="f8be0-104">The supported file formats are: CSV and AVRO.</span></span> <span data-ttu-id="f8be0-105">拖-將**Azure Blob 目的地**放到資料流程設計師，然後按兩下以查看編輯器) 。</span><span class="sxs-lookup"><span data-stu-id="f8be0-105">Ddrag-drop **Azure Blob Destination** to the data flow designer and double-click it to see the editor).</span></span>  
  
1.  <span data-ttu-id="f8be0-106">針對 [Azure 儲存體連線管理員]\*\*\*\* 欄位，請指定現有的 Azure 儲存體連線管理員，或建立參考 Azure 儲存體帳戶的新連線管理員。</span><span class="sxs-lookup"><span data-stu-id="f8be0-106">For the **Azure storage connection manager** field, specify an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account.</span></span>  
  
2.  <span data-ttu-id="f8be0-107">針對 [Blob 容器名稱]\*\*\*\* 欄位，請指定包含原始程式檔的 Blob 容器名稱。</span><span class="sxs-lookup"><span data-stu-id="f8be0-107">For the **Blob container name** field, specify the name of the blob container that contains source files.</span></span>  
  
3.  <span data-ttu-id="f8be0-108">針對 [Blob 名稱]\*\*\*\* 欄位，請指定 Blob 的路徑。</span><span class="sxs-lookup"><span data-stu-id="f8be0-108">For the **Blob name** field, specify the path for the blob.</span></span>  
  
4.  <span data-ttu-id="f8be0-109">針對 [Blob 檔案格式]\*\*\*\* 欄位，請指定要使用的 Blob 格式。</span><span class="sxs-lookup"><span data-stu-id="f8be0-109">For the **Blob file format** field, specify the blob format you want to use.</span></span>  
  
5.  <span data-ttu-id="f8be0-110">若檔案格式為 CSV，則您必須指定 [資料行分隔符號字元]\*\*\*\* 值。</span><span class="sxs-lookup"><span data-stu-id="f8be0-110">If the file format is CSV, you must specify the **Column delimiter character** value.</span></span> <span data-ttu-id="f8be0-111">如果檔案中的第一個資料列包含資料行名稱，也請選取**第一個資料列中的資料行名稱**。</span><span class="sxs-lookup"><span data-stu-id="f8be0-111">Also  select **Column names in the first data row** if the first row in the file contains column names.</span></span>  
  
6.  <span data-ttu-id="f8be0-112">指定連接資訊後，請切換至 [資料行]  頁面，將來源資料行對應至 SSIS 資料流程的目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="f8be0-112">After specifying the connection information, switch to the **Columns** page to map source columns to destination columns for the SSIS data flow.</span></span>  
  
  
