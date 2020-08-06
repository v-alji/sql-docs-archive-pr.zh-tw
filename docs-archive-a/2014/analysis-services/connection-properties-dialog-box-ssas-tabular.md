---
title: '[連接屬性] 對話方塊 (SSAS-表格式) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssmsimbi.ConnectionProperties.F1
ms.assetid: 17bae8ae-2ba0-4978-be70-61c687f59d54
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e4b0360d59f43bc932f68a846f239c4873a5aa9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592998"
---
# <a name="connection-properties-dialog-box-ssas---tabular"></a><span data-ttu-id="c78f1-102">連接屬性對話方塊 (SSAS - 表格式)</span><span class="sxs-lookup"><span data-stu-id="c78f1-102">Connection Properties Dialog Box (SSAS - Tabular)</span></span>
  <span data-ttu-id="c78f1-103">在 SQL Server Management Studio 中，使用此頁面檢視或修改表格式模型資料庫所用之資料來源的連接屬性。</span><span class="sxs-lookup"><span data-stu-id="c78f1-103">Use this page to view or modify in SQL Server Management Studio the connection properties of a data source used by a tabular model database.</span></span>  
  
 <span data-ttu-id="c78f1-104">此對話方塊提供時間戳記和其他描述性資訊，再加上決定連接特性的可自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="c78f1-104">This dialog box provides timestamps and other descriptive information, plus customizable properties that determine characteristics of the connection.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c78f1-105">選項</span><span class="sxs-lookup"><span data-stu-id="c78f1-105">Options</span></span>  
  
|<span data-ttu-id="c78f1-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="c78f1-106">Term</span></span>|<span data-ttu-id="c78f1-107">定義</span><span class="sxs-lookup"><span data-stu-id="c78f1-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="c78f1-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="c78f1-108">**Name**</span></span>|<span data-ttu-id="c78f1-109">指定資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="c78f1-109">Specifies the name of the data source.</span></span>|  
|<span data-ttu-id="c78f1-110">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="c78f1-110">**ID**</span></span>|<span data-ttu-id="c78f1-111">顯示資料來源物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c78f1-111">Displays the identifier of the data source object.</span></span>|  
|<span data-ttu-id="c78f1-112">**說明**</span><span class="sxs-lookup"><span data-stu-id="c78f1-112">**Description**</span></span>|<span data-ttu-id="c78f1-113">顯示資料來源物件的描述。</span><span class="sxs-lookup"><span data-stu-id="c78f1-113">Displays the description of the data source object.</span></span>|  
|<span data-ttu-id="c78f1-114">**建立時間戳記**</span><span class="sxs-lookup"><span data-stu-id="c78f1-114">**Create Timestamp**</span></span>|<span data-ttu-id="c78f1-115">顯示建立資料庫的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="c78f1-115">Displays the date and time the database was created.</span></span>|  
|<span data-ttu-id="c78f1-116">**上次結構描述更新**</span><span class="sxs-lookup"><span data-stu-id="c78f1-116">**Last Schema Update**</span></span>|<span data-ttu-id="c78f1-117">顯示上次更新資料庫的中繼資料的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="c78f1-117">Displays the date and time the metadata for the database was last updated.</span></span>|  
|<span data-ttu-id="c78f1-118">**連接字串**</span><span class="sxs-lookup"><span data-stu-id="c78f1-118">**Connection String**</span></span>|<span data-ttu-id="c78f1-119">顯示連接字串，這個連接字串用於連接到提供資料給模型的資料來源。</span><span class="sxs-lookup"><span data-stu-id="c78f1-119">Displays the connection string used to connect to the data source that provides data to the model.</span></span>|  
|<span data-ttu-id="c78f1-120">**最大連接數目**</span><span class="sxs-lookup"><span data-stu-id="c78f1-120">**Maximum Number of Connections**</span></span>|<span data-ttu-id="c78f1-121">指定這個資料庫的用戶端連接數目上限。</span><span class="sxs-lookup"><span data-stu-id="c78f1-121">Specifies the maximum number of client connections to this database.</span></span>|  
|<span data-ttu-id="c78f1-122">**隔離**</span><span class="sxs-lookup"><span data-stu-id="c78f1-122">**Isolation**</span></span>|<span data-ttu-id="c78f1-123">有效值是 ReadCommitted 或快照集。</span><span class="sxs-lookup"><span data-stu-id="c78f1-123">Valid values are ReadCommitted or Snapshot.</span></span> <span data-ttu-id="c78f1-124">如需詳細資訊，請參閱 [Isolation 元素 &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/isolation-element-assl)。</span><span class="sxs-lookup"><span data-stu-id="c78f1-124">For more information, see [Isolation Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/isolation-element-assl).</span></span>|  
|<span data-ttu-id="c78f1-125">**查詢逾時**</span><span class="sxs-lookup"><span data-stu-id="c78f1-125">**Query Timeout**</span></span>|<span data-ttu-id="c78f1-126">指定一段時間 (以秒為單位)，經過這段時間之後，嘗試擷取資料的行為就會逾時。</span><span class="sxs-lookup"><span data-stu-id="c78f1-126">Specifies the time, in seconds, after which an attempt to retrieve data is timed out.</span></span>|  
|<span data-ttu-id="c78f1-127">**Managed 提供者**</span><span class="sxs-lookup"><span data-stu-id="c78f1-127">**Managed Provider**</span></span>|<span data-ttu-id="c78f1-128">指定 Managed 提供者的名稱。</span><span class="sxs-lookup"><span data-stu-id="c78f1-128">Specifies the name of the managed provider.</span></span> <span data-ttu-id="c78f1-129">如果資料來源連接使用原生 OLE DB 提供者，此值為空白。</span><span class="sxs-lookup"><span data-stu-id="c78f1-129">If the data source connection uses a native OLE DB provider, this value is empty.</span></span>|  
|<span data-ttu-id="c78f1-130">**模擬資訊**</span><span class="sxs-lookup"><span data-stu-id="c78f1-130">**Impersonation Info**</span></span>|<span data-ttu-id="c78f1-131">指定用於下列項目的模擬帳戶：在處理或重新整理資料時的資料庫連接、針對關聯式資料存放區執行的查詢 (透過 DirectQuery)、非正規 (out-of-line) 繫結，遠端資料分割，以及從目標到來源的資料庫同步處理。</span><span class="sxs-lookup"><span data-stu-id="c78f1-131">Specifies the impersonation account used for database connections when processing or refreshing data, queries that run against a relational data store (via DirectQuery), out-of-line bindings, remote partitions, and database synchronization from target to source.</span></span><br /><br /> <span data-ttu-id="c78f1-132">有效值包含 Analysis Services 服務帳戶或一組特定的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="c78f1-132">Valid values include the Analysis Services service account or a specific set of Windows credentials.</span></span> <span data-ttu-id="c78f1-133">請勿指定 **[使用目前使用者的認證]** 或 **[繼承]**。</span><span class="sxs-lookup"><span data-stu-id="c78f1-133">Do not specify **Use the credentials of the current user** or **Inherit**.</span></span> <span data-ttu-id="c78f1-134">表格式模型資料庫不支援這些認證選項。</span><span class="sxs-lookup"><span data-stu-id="c78f1-134">Those credential options are not supported for a tabular model database.</span></span>|  
  
  
