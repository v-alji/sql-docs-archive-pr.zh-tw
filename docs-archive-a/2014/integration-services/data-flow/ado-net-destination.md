---
title: ADO NET 目的地 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.f1
helpviewer_keywords:
- destinations [Integration Services], ADO.NET
- ADO.NET destination
ms.assetid: cb883990-d875-4d8b-b868-45f9f15ebeae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8289a8c91c7b78749a341cc95055562d01164866
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701500"
---
# <a name="ado-net-destination"></a><span data-ttu-id="b5271-102">ADO NET 目的地</span><span class="sxs-lookup"><span data-stu-id="b5271-102">ADO NET Destination</span></span>
  <span data-ttu-id="b5271-103">ADO NET 目的地會將資料載入使用資料庫資料表或檢視的各種 [!INCLUDE[vstecado](../../includes/vstecado-md.md)]相容資料庫中。</span><span class="sxs-lookup"><span data-stu-id="b5271-103">The ADO NET destination loads data into a variety of [!INCLUDE[vstecado](../../includes/vstecado-md.md)]-compliant databases that use a database table or view.</span></span> <span data-ttu-id="b5271-104">您可以選擇將這些資料載入現有的資料表或檢視中，也可以建立新的資料表並將資料載入新的資料表內。</span><span class="sxs-lookup"><span data-stu-id="b5271-104">You have the option of loading this data into an existing table or view, or you can create a new table and load the data into the new table.</span></span>  
  
 <span data-ttu-id="b5271-105">您可使用 ADO NET 目的地以連線到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b5271-105">You can use the ADO NET destination to connect to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="b5271-106">不過，不支援使用 OLE DB 連接到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b5271-106">Connecting to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] by using OLE DB is not supported.</span></span> <span data-ttu-id="b5271-107">如需 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 的詳細資訊，請參閱[一般指導方針與限制 (Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228)。</span><span class="sxs-lookup"><span data-stu-id="b5271-107">For more information about [!INCLUDE[ssSDS](../../includes/sssds-md.md)], see [General Guidelines and Limitations (Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228).</span></span>  
  
## <a name="troubleshooting-the-ado-net-destination"></a><span data-ttu-id="b5271-108">ADO NET 目的地疑難排解</span><span class="sxs-lookup"><span data-stu-id="b5271-108">Troubleshooting the ADO NET Destination</span></span>  
 <span data-ttu-id="b5271-109">您可以記錄 ADO NET 目的地對外部資料提供者執行的呼叫。</span><span class="sxs-lookup"><span data-stu-id="b5271-109">You can log the calls that the ADO NET destination makes to external data providers.</span></span> <span data-ttu-id="b5271-110">您可以使用這項記錄功能，針對 ADO NET 目的地所執行之將資料儲存至外部資料來源的作業進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="b5271-110">You can use this logging capability to troubleshoot the saving of data to external data sources that the ADO NET destination performs.</span></span> <span data-ttu-id="b5271-111">若要記錄 ADO NET 目的地對外部資料提供者執行的呼叫，請啟用封裝記錄，然後在封裝層級選取 [診斷]  事件。</span><span class="sxs-lookup"><span data-stu-id="b5271-111">To log the calls that the ADO NET destination makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="b5271-112">如需詳細資訊，請參閱 [封裝執行的疑難排解工具](../troubleshooting/troubleshooting-tools-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="b5271-112">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="configuring-the-ado-net-destination"></a><span data-ttu-id="b5271-113">設定 ADO NET 目的地</span><span class="sxs-lookup"><span data-stu-id="b5271-113">Configuring the ADO NET Destination</span></span>  
 <span data-ttu-id="b5271-114">此目的地使用 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連接管理員以連接到資料來源，且連接管理員會指定要使用的 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 提供者。</span><span class="sxs-lookup"><span data-stu-id="b5271-114">This destination uses an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to connect to a data source and the connection manager specifies the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] provider to use.</span></span> <span data-ttu-id="b5271-115">如需詳細資訊，請參閱 [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="b5271-115">For more information, see [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md).</span></span>  
  
 <span data-ttu-id="b5271-116">ADO NET 目的地包含輸入資料行與目的地資料來源中資料行之間的對應。</span><span class="sxs-lookup"><span data-stu-id="b5271-116">An ADO NET destination includes mappings between input columns and columns in the destination data source.</span></span> <span data-ttu-id="b5271-117">您不需要將輸入資料行對應至所有的目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="b5271-117">You do not have to map input columns to all destination columns.</span></span> <span data-ttu-id="b5271-118">但是，某些目的地資料行的屬性可能需要對應輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="b5271-118">However, the properties of some destination columns can require the mapping of input columns.</span></span> <span data-ttu-id="b5271-119">否則，可能會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b5271-119">Otherwise, errors might occur.</span></span> <span data-ttu-id="b5271-120">例如，如果目的地資料行不允許 Null 值，您必須將輸入資料行對應到該目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="b5271-120">For example, if a destination column does not allow for null values, you must map an input column to that destination column.</span></span> <span data-ttu-id="b5271-121">此外，對應之資料行的資料類型必須相容。</span><span class="sxs-lookup"><span data-stu-id="b5271-121">In addition, the data types of mapped columns must be compatible.</span></span> <span data-ttu-id="b5271-122">例如，如果 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 提供者不支援，您就無法將具有字串資料類型的輸入資料行對應至具有數值資料類型的目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="b5271-122">For example, you cannot map an input column with a string data type to a destination column with a numeric data type if the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] provider does not support this mapping.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b5271-123">不支援將文字插入資料類型設定為影像的資料行內。</span><span class="sxs-lookup"><span data-stu-id="b5271-123">does not support inserting text into columns whose data type is set to image.</span></span> <span data-ttu-id="b5271-124">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型的詳細資訊，請參閱 [資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)＞。</span><span class="sxs-lookup"><span data-stu-id="b5271-124">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5271-125">ADO NET 目的地不支援將類型設定為 DT_DBTIME 的輸入資料行對應至類型設定為日期時間的資料庫資料行。</span><span class="sxs-lookup"><span data-stu-id="b5271-125">The ADO NET destination does not support mapping an input column whose type is set to DT_DBTIME to a database column whose type is set to datetime.</span></span> <span data-ttu-id="b5271-126">如需 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料類型的詳細資訊，請參閱 [Integration Services 資料類型](integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b5271-126">For more information about [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="b5271-127">ADO NET 目的地具有一個規則輸入和一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="b5271-127">The ADO NET destination has one regular input and one error output.</span></span>  
  
 <span data-ttu-id="b5271-128">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="b5271-128">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="b5271-129">如需可以在 [ADO NET 目的地編輯器]\*\*\*\* 對話方塊中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="b5271-129">For more information about the properties that you can set in the **ADO NET Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="b5271-130">ADO NET 目的地編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="b5271-130">ADO NET Destination Editor &#40;Connection Manager Page&#41;</span></span>](../ado-net-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="b5271-131">ADO NET 目的地編輯器 &#40;對應頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="b5271-131">ADO NET Destination Editor &#40;Mappings Page&#41;</span></span>](../ado-net-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="b5271-132">ADO NET 目的地編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="b5271-132">ADO NET Destination Editor &#40;Error Output Page&#41;</span></span>](../ado-net-destination-editor-error-output-page.md)  
  
 <span data-ttu-id="b5271-133">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="b5271-133">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="b5271-134">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="b5271-134">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="b5271-135">Common Properties</span><span class="sxs-lookup"><span data-stu-id="b5271-135">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="b5271-136">ADO NET 自訂屬性</span><span class="sxs-lookup"><span data-stu-id="b5271-136">ADO NET Custom Properties</span></span>](ado-net-custom-properties.md)  
  
 <span data-ttu-id="b5271-137">如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="b5271-137">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
