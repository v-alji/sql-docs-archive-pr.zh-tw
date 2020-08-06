---
title: ADO NET 來源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.f1
helpviewer_keywords:
- ADO.NET source
- sources [Integration Services], ADO.NET
- sources [Integration Services], DataReader
- .NET Framework [Integration Services]
- DataReader source
ms.assetid: 2a2f1750-2cda-4dda-9dca-623a96a6b3c0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eb50a6171ed29fc5328663d8ce9992e0462e02f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706618"
---
# <a name="ado-net-source"></a><span data-ttu-id="0386b-102">ADO NET 來源</span><span class="sxs-lookup"><span data-stu-id="0386b-102">ADO NET Source</span></span>
  <span data-ttu-id="0386b-103">ADO NET 來源會從 .NET 提供者取用資料，並使該資料可供資料流程使用。</span><span class="sxs-lookup"><span data-stu-id="0386b-103">The ADO NET source consumes data from a .NET provider and makes the data available to the data flow.</span></span>  
  
 <span data-ttu-id="0386b-104">您可以使用 ADO NET 來源以連線到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0386b-104">You can use the ADO NET source to connect to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="0386b-105">不過，不支援使用 OLE DB 連接到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0386b-105">Connecting to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] by using OLE DB is not supported.</span></span> <span data-ttu-id="0386b-106">如需 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 的詳細資訊，請參閱[一般指導方針與限制 (Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228)。</span><span class="sxs-lookup"><span data-stu-id="0386b-106">For more information about [!INCLUDE[ssSDS](../../includes/sssds-md.md)], see [General Guidelines and Limitations (Azure SQL Database)](https://go.microsoft.com/fwlink/?LinkId=248228).</span></span>  
  
## <a name="data-type-support"></a><span data-ttu-id="0386b-107">資料類型支援</span><span class="sxs-lookup"><span data-stu-id="0386b-107">Data Type Support</span></span>  
 <span data-ttu-id="0386b-108">此來源會將未對應到特定 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料類型的所有資料類型轉換成 DT_NTEXT [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="0386b-108">The source converts any data type that does not map to a specific [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type to the DT_NTEXT [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type.</span></span> <span data-ttu-id="0386b-109">即使資料類型為 `System.Object`，還是會發生轉換。</span><span class="sxs-lookup"><span data-stu-id="0386b-109">This conversion occurs even if the data type is `System.Object`.</span></span>  
  
 <span data-ttu-id="0386b-110">您可以將 DT_NTEXT 資料類型變更為 DT_WSTR 資料類型，或是將 DT_WSTR 資料類型變更為 DT_NTEXT 資料類型。</span><span class="sxs-lookup"><span data-stu-id="0386b-110">You can change the DT_NTEXT data type to the DT_WSTR data type, or the change DT_WSTR to DT_NTEXT.</span></span> <span data-ttu-id="0386b-111">您可以在 ADO NET 來源的 **[進階編輯器]** 對話方塊中設定 **[DataType]** 屬性，以變更資料類型。</span><span class="sxs-lookup"><span data-stu-id="0386b-111">You change data types by setting the **DataType** property in the **Advanced Editor** dialog box of the ADO NET source.</span></span> <span data-ttu-id="0386b-112">如需詳細資訊，請參閱 [Common Properties](../common-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="0386b-112">For more information, see [Common Properties](../common-properties.md).</span></span>  
  
 <span data-ttu-id="0386b-113">您可以在 ADO NET 來源之後使用資料轉換，將 DT_NTEXT 資料類型轉換成 DT_BYTES 或 DT_STR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="0386b-113">The DT_NTEXT data type can also be converted to the DT_BYTES or DT_STR data type by using a Data Conversion transformation after the ADO NET source.</span></span> <span data-ttu-id="0386b-114">如需詳細資訊，請參閱 [Data Conversion Transformation](transformations/data-conversion-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="0386b-114">For more information, see [Data Conversion Transformation](transformations/data-conversion-transformation.md).</span></span>  
  
 <span data-ttu-id="0386b-115">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]中，資料類型 DT_DBDATE、DT_DBTIME2、DT_DBTIMESTAMP2 和 DT_DBTIMESTAMPOFFSET 會對應到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的某些日期資料類型。</span><span class="sxs-lookup"><span data-stu-id="0386b-115">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the date data types, DT_DBDATE, DT_DBTIME2, DT_DBTIMESTAMP2, and DT_DBTIMESTAMPOFFSET, map to certain date data types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0386b-116">您可以設定 ADO NET 來源，從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用的日期資料類型轉換成 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 使用的資料類型。</span><span class="sxs-lookup"><span data-stu-id="0386b-116">You can configure the ADO NET source to convert the date data types from those that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses to those that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] uses.</span></span> <span data-ttu-id="0386b-117">如果要設定 ADO NET 來源，以轉換這些日期資料類型，請將 **連接管理員的** [Type System Version] [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 屬性設定為 **[Latest]** 。</span><span class="sxs-lookup"><span data-stu-id="0386b-117">To configure the ADO NET source to convert these date data types, set the **Type System Version** property of the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to **Latest**.</span></span> <span data-ttu-id="0386b-118">(**Type System Version** 屬性位於 [連線管理員]  對話方塊的 [全部]  頁面上。</span><span class="sxs-lookup"><span data-stu-id="0386b-118">(The **Type System Version** property is on the **All** page of the **Connection Manager** dialog box.</span></span> <span data-ttu-id="0386b-119">若要開啟 [連線管理員]  對話方塊，請以滑鼠右鍵按一下 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員，然後按一下 [編輯]  。)</span><span class="sxs-lookup"><span data-stu-id="0386b-119">To open the **Connection Manager** dialog box, right-click the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager, and then click **Edit**.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0386b-120">如果 **連線管理員的** Type System Version [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 屬性設定為 **SQL Server 2005**，系統會將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型轉換成 DT_WSTR。</span><span class="sxs-lookup"><span data-stu-id="0386b-120">If the **Type System Version** property for the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager is set to **SQL Server 2005**, the system converts the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date data types to DT_WSTR.</span></span>  
  
 <span data-ttu-id="0386b-121">當 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 連線管理員將提供者指定為 .NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient) 時，系統會將使用者定義資料類型 (UDT) 轉換成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 二進位大型物件 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="0386b-121">The system converts user-defined data types (UDTs) to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] binary large objects (BLOB) when the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager specifies the provider as the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient).</span></span> <span data-ttu-id="0386b-122">當系統轉換 UDT 資料類型時，會套用以下規則：</span><span class="sxs-lookup"><span data-stu-id="0386b-122">The system applies the following rules when it converts the UDT data type:</span></span>  
  
-   <span data-ttu-id="0386b-123">如果資料不是大型 UDT，系統會將資料轉換成 DT_BYTES。</span><span class="sxs-lookup"><span data-stu-id="0386b-123">If the data is a non-large UDT, the system converts the data to DT_BYTES.</span></span>  
  
-   <span data-ttu-id="0386b-124">如果資料不是大型 UDT，而且資料庫上資料行的 **Length** 屬性設定為 -1 或是大於 8,000 個位元組的值，則系統會將資料轉換成 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="0386b-124">If the data is a non-large UDT, and the **Length** property of the column on the database is set to -1 or a value greater than 8,000 bytes, the system converts the data to DT_IMAGE.</span></span>  
  
-   <span data-ttu-id="0386b-125">如果資料是大型 UDT，系統會將資料轉換成 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="0386b-125">If the data is a large UDT, the system converts the data to DT_IMAGE.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0386b-126">如果 ADO NET 來源未設定為使用錯誤輸出，系統會將資料流向 DT_IMAGE 資料行 (以 8,000 個位元組的區塊為單位)。</span><span class="sxs-lookup"><span data-stu-id="0386b-126">If the ADO NET source is not configured to use error output, the system streams the data to the DT_IMAGE column in chunks of 8,000 bytes.</span></span> <span data-ttu-id="0386b-127">如果 ADO NET 來源設定為使用錯誤輸出，系統會將整個位元組陣列傳遞給 DT_IMAGE 資料行。</span><span class="sxs-lookup"><span data-stu-id="0386b-127">If the ADO NET source is configured to use error output, the system passes the whole array of bytes to the DT_IMAGE column.</span></span> <span data-ttu-id="0386b-128">如需如何設定元件使用錯誤輸出的詳細資訊，請參閱 [處理資料中的錯誤](error-handling-in-data.md)。</span><span class="sxs-lookup"><span data-stu-id="0386b-128">For more information about how to configure components to use error output, see [Error Handling in Data](error-handling-in-data.md).</span></span>  
  
 <span data-ttu-id="0386b-129">如需 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料類型、支援的資料類型轉換及橫跨某些資料庫 (包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) 之資料類型對應的詳細資訊，請參閱 [Integration Services 資料類型](integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="0386b-129">For more information about the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, supported data type conversions, and data type mapping across certain databases including [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="0386b-130">如需將 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料類型對應至 Managed 資料類型的詳細資訊，請參閱 [使用資料流程中的資料類型](../extending-packages-custom-objects/data-flow/working-with-data-types-in-the-data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="0386b-130">For information about mapping [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types to managed data types, see [Working with Data Types in the Data Flow](../extending-packages-custom-objects/data-flow/working-with-data-types-in-the-data-flow.md).</span></span>  
  
## <a name="ado-net-source-troubleshooting"></a><span data-ttu-id="0386b-131">疑難排解 ADO NET 來源</span><span class="sxs-lookup"><span data-stu-id="0386b-131">ADO NET Source Troubleshooting</span></span>  
 <span data-ttu-id="0386b-132">您可以記錄 ADO NET 來源對外部資料提供者所執行的呼叫。</span><span class="sxs-lookup"><span data-stu-id="0386b-132">You can log the calls that the ADO NET source makes to external data providers.</span></span> <span data-ttu-id="0386b-133">您可以使用這項記錄功能，疑難排解 ADO NET 來源執行的從外部資料來源載入資料的作業。</span><span class="sxs-lookup"><span data-stu-id="0386b-133">You can use this logging capability to troubleshoot the loading of data from external data sources that the ADO NET source performs.</span></span> <span data-ttu-id="0386b-134">若要記錄 ADO NET 來源對外部資料提供者執行的呼叫，請啟用封裝記錄，然後在封裝層級上選取 **[診斷]** 事件。</span><span class="sxs-lookup"><span data-stu-id="0386b-134">To log the calls that the ADO NET source makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="0386b-135">如需詳細資訊，請參閱 [封裝執行的疑難排解工具](../troubleshooting/troubleshooting-tools-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="0386b-135">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="ado-net-source-configuration"></a><span data-ttu-id="0386b-136">ADO NET 來源組態</span><span class="sxs-lookup"><span data-stu-id="0386b-136">ADO NET Source Configuration</span></span>  
 <span data-ttu-id="0386b-137">您可藉由提供定義結果集的 SQL 陳述式，以設定 ADO NET 來源。</span><span class="sxs-lookup"><span data-stu-id="0386b-137">You configure the ADO NET source by providing the SQL statement that defines the result set.</span></span> <span data-ttu-id="0386b-138">例如，連接到 [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] 資料庫並使用 SQL 陳述式 `SELECT * FROM Production.Product` 的 ADO NET 來源會從 **Production.Product** 資料表擷取所有資料列，並提供資料集給下游元件。</span><span class="sxs-lookup"><span data-stu-id="0386b-138">For example, an ADO NET source that connects to the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] database and uses the SQL statement `SELECT * FROM Production.Product` extracts all the rows from the **Production.Product** table and provides the dataset to a downstream component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0386b-139">當您使用 SQL 陳述式呼叫從暫存資料表傳回結果的預存程序時，請使用 WITH RESULT SETS 選項定義結果集的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0386b-139">When you use an SQL statement to invoke a stored procedure that returns results from a temporary table, use the WITH RESULT SETS option to define metadata for the result set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0386b-140">如果您使用 SQL 陳述式執行預存程序，封裝就會失敗且出現下列錯誤。透過在 exec 陳述式前面加上 `SET FMTONLY OFF` 陳述式也許能夠解決這項錯誤。</span><span class="sxs-lookup"><span data-stu-id="0386b-140">If you use an SQL statement to execute a stored procedure and the package fails with the following error, you may be able to resolve the error by adding the `SET FMTONLY OFF` statement before the exec statement.</span></span>  
>   
>  <span data-ttu-id="0386b-141">**在資料來源中找不到資料行 <資料行名稱>。**</span><span class="sxs-lookup"><span data-stu-id="0386b-141">**Column <column_name> cannot be found at the datasource.**</span></span>  
  
 <span data-ttu-id="0386b-142">ADO NET 來源會使用 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連接管理員連接到資料來源，且由連接管理員指定 .NET 提供者。</span><span class="sxs-lookup"><span data-stu-id="0386b-142">The ADO NET source uses an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to connect to a data source, and the connection manager specifies the .NET provider.</span></span> <span data-ttu-id="0386b-143">如需詳細資訊，請參閱 [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="0386b-143">For more information, see [ADO.NET Connection Manager](../connection-manager/ado-net-connection-manager.md).</span></span>  
  
 <span data-ttu-id="0386b-144">ADO NET 來源有一個一般輸出和一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="0386b-144">The ADO NET source has one regular output and one error output.</span></span>  
  
 <span data-ttu-id="0386b-145">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="0386b-145">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="0386b-146">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="0386b-146">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="0386b-147">Common Properties</span><span class="sxs-lookup"><span data-stu-id="0386b-147">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="0386b-148">ADO NET 自訂屬性</span><span class="sxs-lookup"><span data-stu-id="0386b-148">ADO NET Custom Properties</span></span>](ado-net-custom-properties.md)  
  
 <span data-ttu-id="0386b-149">如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="0386b-149">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0386b-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0386b-150">See Also</span></span>  
 <span data-ttu-id="0386b-151">[DataReader 目的地](datareader-destination.md) </span><span class="sxs-lookup"><span data-stu-id="0386b-151">[DataReader Destination](datareader-destination.md) </span></span>  
 <span data-ttu-id="0386b-152">[ADO NET 目的地](ado-net-destination.md) </span><span class="sxs-lookup"><span data-stu-id="0386b-152">[ADO NET Destination](ado-net-destination.md) </span></span>  
 [<span data-ttu-id="0386b-153">資料流程</span><span class="sxs-lookup"><span data-stu-id="0386b-153">Data Flow</span></span>](data-flow.md)  
  
  
