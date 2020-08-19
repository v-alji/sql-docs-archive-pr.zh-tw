---
title: SAP NetWeaver BI 連線類型 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f985856b-31d5-4e56-844b-8a8ee38da67e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 42806e370e20257f5de9e49d4f59dd3bb7793f20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710213"
---
# <a name="sap-netweaver-bi-connection-type-ssrs"></a><span data-ttu-id="b2b31-102">SAP NetWeaver BI 連接類型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="b2b31-102">SAP NetWeaver BI Connection Type (SSRS)</span></span>
  <span data-ttu-id="b2b31-103">若要在報表中加入來自 SAP NetWeaver® Business Intelligence 外部資料來源的資料，您必須具有以 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)]類型之報表資料來源為基礎的資料集。</span><span class="sxs-lookup"><span data-stu-id="b2b31-103">To include data from a SAP NetWeaver® Business Intelligence external data source in your report, you must have a dataset that is based on a report data source of type [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)].</span></span> <span data-ttu-id="b2b31-104">這個內建的資料來源類型的建構基礎為 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework Data Provider 1.0 for [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)]的資料延伸模組。</span><span class="sxs-lookup"><span data-stu-id="b2b31-104">This built-in data source type is based on the data extension for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework Data Provider 1.0 for [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)].</span></span>  
  
 <span data-ttu-id="b2b31-105">這個資料延伸模組可以讓您從 InfoCubes、MultiProviders (虛擬 InfoCubes) 與 Web 查詢擷取多維度的資料，而這些資料來源已定義於 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] 外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="b2b31-105">This data extension enables you to retrieve multidimensional data from InfoCubes, MultiProviders (virtual InfoCubes), and Web-enabled queries that are defined on a [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] external data source.</span></span>  
  
 <span data-ttu-id="b2b31-106">您可以使用本主題中的資訊來建置資料來源。</span><span class="sxs-lookup"><span data-stu-id="b2b31-106">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="b2b31-107">如需逐步指示，請參閱 [加入及驗證資料連線或資料來源 &#40;Report Builder 和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="b2b31-107">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="supported-versions"></a><a name="support"></a> <span data-ttu-id="b2b31-108">支援的版本</span><span class="sxs-lookup"><span data-stu-id="b2b31-108">Supported Versions</span></span>  
 <span data-ttu-id="b2b31-109">資料提供者是針對 SAP BW 3.5 和 7.0 所開發並測試。</span><span class="sxs-lookup"><span data-stu-id="b2b31-109">The data provider has been developed for and tested against SAP BW 3.5 and 7.0.</span></span>  
  
-   <span data-ttu-id="b2b31-110">針對 SAP BW 3.5 和 7.0 支援 Package 20</span><span class="sxs-lookup"><span data-stu-id="b2b31-110">Support Package 20 for SAP BW 3.5 and 7.0</span></span>  
  
 <span data-ttu-id="b2b31-111">對於 Windows 整合式驗證，提供者是針對下列系統所開發並測試。</span><span class="sxs-lookup"><span data-stu-id="b2b31-111">For Windows Integrated Authentication the provider was developed for and tested against the following systems.</span></span>  
  
-   <span data-ttu-id="b2b31-112">SAP Portals 6.40 支援 Package 20</span><span class="sxs-lookup"><span data-stu-id="b2b31-112">SAP Portals 6.40 Support Package 20</span></span>  
  
-   <span data-ttu-id="b2b31-113">SAP 入口網站7.0 支援套件11</span><span class="sxs-lookup"><span data-stu-id="b2b31-113">SAP Portals 7.0 Support Package 11</span></span>  
  
-   <span data-ttu-id="b2b31-114">SAP Duet 1.0</span><span class="sxs-lookup"><span data-stu-id="b2b31-114">SAP Duet 1.0</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="b2b31-115">連接字串</span><span class="sxs-lookup"><span data-stu-id="b2b31-115">Connection String</span></span>  
 <span data-ttu-id="b2b31-116">請洽詢資料庫管理員，以取得用來連接資料來源的連接資訊和認證。</span><span class="sxs-lookup"><span data-stu-id="b2b31-116">Contact the database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="b2b31-117">下列連接字串範例會指定伺服器上的 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] 資料來源使用通訊埠 8000，並指定網際網路上的 XML for Analysis Services (XMLA) 使用 SOAP：</span><span class="sxs-lookup"><span data-stu-id="b2b31-117">The following connection string example specifies an [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] data source on a server using port 8000 and XML for Analysis Services (XMLA) over the Internet using SOAP:</span></span>  
  
```  
DataSource=http://mySAPNetWeaverBIServer:8000/sap/bw/xml/soap/xmla  
```  
  
 <span data-ttu-id="b2b31-118">如需更多連接字串範例，請參閱 [報表產生器中的資料連接、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="b2b31-118">For more connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="b2b31-119">認證</span><span class="sxs-lookup"><span data-stu-id="b2b31-119">Credentials</span></span>  
 <span data-ttu-id="b2b31-120">需要有認證才能夠執行報表、於本機預覽報表並且從報表伺服器預覽報表。</span><span class="sxs-lookup"><span data-stu-id="b2b31-120">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="b2b31-121">發行報表之後，您可能需要變更資料來源的認證，如此當報表在報表伺服器上執行時，擷取資料的權限就會是有效的。</span><span class="sxs-lookup"><span data-stu-id="b2b31-121">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="b2b31-122">如需詳細資訊，請參閱 [Reporting Services 中的資料連線、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) ，或 [在 Report Builder 中指定認證](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="b2b31-122">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
  
  
##  <a name="queries"></a><a name="Query"></a> <span data-ttu-id="b2b31-123">查詢</span><span class="sxs-lookup"><span data-stu-id="b2b31-123">Queries</span></span>  
 <span data-ttu-id="b2b31-124">您可以在設計模式或查詢模式中使用圖形化查詢設計工具，透過瀏覽資料來源中的基礎資料結構，建立多維度運算式 (MDX) 查詢。</span><span class="sxs-lookup"><span data-stu-id="b2b31-124">You can use the graphical query designer in Design or Query mode to build a Multidimensional Expression (MDX) query by browsing the underlying data structures on the data source.</span></span> <span data-ttu-id="b2b31-125">在設計階段，您可以從查詢設計工具以互動方式執行查詢，來查看其結果。</span><span class="sxs-lookup"><span data-stu-id="b2b31-125">At design time, you can interactively run a query from the query designer to see the results.</span></span> <span data-ttu-id="b2b31-126">您建立的查詢會定義資料集的欄位。</span><span class="sxs-lookup"><span data-stu-id="b2b31-126">The query you build defines fields in the dataset.</span></span> <span data-ttu-id="b2b31-127">在執行階段，會從資料來源傳回實際的資料。</span><span class="sxs-lookup"><span data-stu-id="b2b31-127">At run time, the actual data is returned from the data source.</span></span> <span data-ttu-id="b2b31-128">請使用圖形化查詢設計工具來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b2b31-128">Use the graphical query designer to perform the following actions:</span></span>  
  
-   <span data-ttu-id="b2b31-129">在設計模式中，將資料來源的維度、成員、成員屬性以及關鍵數值拖曳到 [資料] 窗格，以建立多維度運算式 (MDX) 查詢。</span><span class="sxs-lookup"><span data-stu-id="b2b31-129">In Design mode, drag dimensions, members, member properties, and key figures from the data source onto a Data pane to build a Multidimensional Expression (MDX) query.</span></span> <span data-ttu-id="b2b31-130">請從 [導出成員] 窗格中將導出成員拖曳到 [資料] 窗格，以定義其他資料集欄位。</span><span class="sxs-lookup"><span data-stu-id="b2b31-130">Drag calculated members from the Calculated Members pane to the Data pane to define additional dataset fields.</span></span>  
  
-   <span data-ttu-id="b2b31-131">在設計模式中，將維度、成員、成員屬性以及關鍵數值拖曳到 [查詢] 窗格，或者直接在 [查詢] 窗格中輸入 MDX 文字。</span><span class="sxs-lookup"><span data-stu-id="b2b31-131">In Query mode, drag dimensions, members, member properties, and key figures onto the Query pane or type MDX text directly into the Query pane.</span></span> <span data-ttu-id="b2b31-132">請從 [導出成員] 窗格中將導出成員拖曳到 [資料] 窗格，以定義其他資料集欄位。</span><span class="sxs-lookup"><span data-stu-id="b2b31-132">Drag calculated members from the Calculated Members pane to the Data pane to define additional dataset fields.</span></span>  
  
 <span data-ttu-id="b2b31-133">當您建立查詢時，查詢設計工具會自動將預設屬性加入 MDX 查詢中。</span><span class="sxs-lookup"><span data-stu-id="b2b31-133">As you build queries, the query designer automatically adds default properties to the MDX query.</span></span> <span data-ttu-id="b2b31-134">若要包含預設屬性以外的屬性，您必須手動修改 MDX 查詢。</span><span class="sxs-lookup"><span data-stu-id="b2b31-134">To include properties other than default properties, you must manually modify the MDX query.</span></span>  
  
 <span data-ttu-id="b2b31-135">如需使用這個查詢設計工具的詳細資訊，請參閱 [SAP NetWeaver BI 查詢設計工具使用者介面 &#40;報表產生器&#41;](../sap-netweaver-bi-query-designer-user-interface-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="b2b31-135">For more information about working with this query designer, see [SAP NetWeaver BI Query Designer User Interface &#40;Report Builder&#41;](../sap-netweaver-bi-query-designer-user-interface-report-builder.md).</span></span>  
  
  
  
##  <a name="extended-field-properties"></a><a name="Extended"></a> <span data-ttu-id="b2b31-136">擴充欄位屬性</span><span class="sxs-lookup"><span data-stu-id="b2b31-136">Extended Field Properties</span></span>  
 <span data-ttu-id="b2b31-137">[!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] 資料來源支援擴充欄位屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b31-137">The [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] data source supports extended field properties.</span></span> <span data-ttu-id="b2b31-138">擴充欄位屬性是資料集欄位 `Value` 和 `IsMissing` 以外的屬性，由資料處理延伸模組所定義。</span><span class="sxs-lookup"><span data-stu-id="b2b31-138">Extended field properties are properties in addition to `Value` and `IsMissing` that are defined for a dataset field by the data processing extension.</span></span> <span data-ttu-id="b2b31-139">擴充屬性包括預先定義的屬性和自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b31-139">Extended properties include predefined properties and custom properties.</span></span> <span data-ttu-id="b2b31-140">預先定義的屬性是多個資料來源常用的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b31-140">Predefined properties are properties common to multiple data sources.</span></span> <span data-ttu-id="b2b31-141">自訂屬性對於每個資料來源都是唯一的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b31-141">Custom properties are unique to each data source.</span></span>  
  
### <a name="working-with-field-properties"></a><span data-ttu-id="b2b31-142">使用欄位屬性</span><span class="sxs-lookup"><span data-stu-id="b2b31-142">Working with Field Properties</span></span>  
 <span data-ttu-id="b2b31-143">在 [報表資料] 窗格中，並不會顯示擴充欄位屬性，因為您無法將項目拖曳至報表配置上。</span><span class="sxs-lookup"><span data-stu-id="b2b31-143">Extended field properties do not appear in the Report Data pane as items that you can drag onto your report layout.</span></span> <span data-ttu-id="b2b31-144">相反地，將該屬性的父欄位拖曳至報表，然後將預設屬性從 `Value` 變更為想要使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b31-144">Instead, you drag the parent field of the property onto the report and then change the default property from `Value` to the property you want to use.</span></span> <span data-ttu-id="b2b31-145">例如，如果 MDX 查詢設計工具中的 [Calendar Year/Month Level 01]\*\*\*\* 欄位名稱，是藉著從 [中繼資料] 窗格中將層級拖曳至 [查詢] 窗格所建立，則可以使用下列語法參照運算式中的 **Long Name** 自訂擴充屬性：</span><span class="sxs-lookup"><span data-stu-id="b2b31-145">For example, if the field name **Calendar Year/Month Level 01** is created in an MDX query designer by dropping a level from the Metadata pane onto the Query pane, you would refer to the custom extended property **Long Name** in an expression using the following syntax:</span></span>  
  
 `=Fields!Calendar_Year_Month_Level_01("Long Name")`  
  
 <span data-ttu-id="b2b31-146">當您將滑鼠指標停留在 [中繼資料] 窗格時，擴充欄位屬性的名稱會在「工具提示」中出現。</span><span class="sxs-lookup"><span data-stu-id="b2b31-146">The name for an extended field property appears in the ToolTip when you hover over a field in the Metadata pane.</span></span> <span data-ttu-id="b2b31-147">如需有關可用來瀏覽基礎資料之查詢設計工具的詳細資訊，請參閱＜ [SAP NetWeaver BI Query Designer User Interface](sap-netweaver-bi-query-designer-user-interface.md)＞。</span><span class="sxs-lookup"><span data-stu-id="b2b31-147">For more information about the query designers you can use to explore the underlying data, see [SAP NetWeaver BI Query Designer User Interface](sap-netweaver-bi-query-designer-user-interface.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b2b31-148">只有當報表執行以及從其資料集擷取資料時，由資料來源提供擴充欄位屬性的值，這些值才會存在。</span><span class="sxs-lookup"><span data-stu-id="b2b31-148">Values exist for extended field properties only if the data source provides these values when your report runs and retrieves the data for its datasets.</span></span> <span data-ttu-id="b2b31-149">這樣，您就可以利用以下描述的語法，從任何運算式參考那些 `Field` 屬性值。</span><span class="sxs-lookup"><span data-stu-id="b2b31-149">You can then refer to those `Field` property values from any expression using the syntax described below.</span></span> <span data-ttu-id="b2b31-150">然而，由於這些欄位是此資料提供者的特定欄位，而且不屬於報表定義語言的一部分，因此您對這些值所進行的變更並不會和報表定義儲存在一起。</span><span class="sxs-lookup"><span data-stu-id="b2b31-150">However, because these fields are specific to this data provider and not part of the report definition language, changes that you make to these values are not saved with the report definition.</span></span>  
  
 <span data-ttu-id="b2b31-151">請使用下列其中一個語法來參考運算式中預先定義的擴充屬性：</span><span class="sxs-lookup"><span data-stu-id="b2b31-151">Use either of the following syntaxes to refer to predefined extended properties in an expression:</span></span>  
  
-   <span data-ttu-id="b2b31-152">*Fields!FieldName.PropertyName*</span><span class="sxs-lookup"><span data-stu-id="b2b31-152">*Fields!FieldName.PropertyName*</span></span>  
  
-   <span data-ttu-id="b2b31-153">*Fields!FieldName("PropertyName")*</span><span class="sxs-lookup"><span data-stu-id="b2b31-153">*Fields!FieldName("PropertyName")*</span></span>  
  
 <span data-ttu-id="b2b31-154">請使用下列語法來參考運算式中自訂的擴充屬性：</span><span class="sxs-lookup"><span data-stu-id="b2b31-154">Use the following syntax to refer to custom extended properties in an expression:</span></span>  
  
-   <span data-ttu-id="b2b31-155">*Fields!FieldName("PropertyName")*</span><span class="sxs-lookup"><span data-stu-id="b2b31-155">*Fields!FieldName("PropertyName")*</span></span>  
  
  
  
### <a name="predefined-field-properties"></a><span data-ttu-id="b2b31-156">預先定義的欄位屬性</span><span class="sxs-lookup"><span data-stu-id="b2b31-156">Predefined Field Properties</span></span>  
 <span data-ttu-id="b2b31-157">下表提供可用在 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] 資料來源之預先定義的欄位屬性清單。</span><span class="sxs-lookup"><span data-stu-id="b2b31-157">The following table provides a list of predefined field properties that you can use for an [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] data source.</span></span>  
  
|<span data-ttu-id="b2b31-158">**屬性**</span><span class="sxs-lookup"><span data-stu-id="b2b31-158">**Property**</span></span>|<span data-ttu-id="b2b31-159">**型別**</span><span class="sxs-lookup"><span data-stu-id="b2b31-159">**Type**</span></span>|<span data-ttu-id="b2b31-160">**描述或預期的值**</span><span class="sxs-lookup"><span data-stu-id="b2b31-160">**Description or expected value**</span></span>|  
|------------------|--------------|---------------------------------------|  
|`Value`|`Object`|<span data-ttu-id="b2b31-161">指定欄位的資料值。</span><span class="sxs-lookup"><span data-stu-id="b2b31-161">Specifies the data value of the field.</span></span>|  
|`IsMissing`|`Boolean`|<span data-ttu-id="b2b31-162">指出在產生的資料集裡是否有找到欄位。</span><span class="sxs-lookup"><span data-stu-id="b2b31-162">Indicates whether the field was found in the resulting data set.</span></span>|  
|`FormattedValue`|`String`|<span data-ttu-id="b2b31-163">傳回關鍵數值的格式化值。</span><span class="sxs-lookup"><span data-stu-id="b2b31-163">Returns a formatted value for a key figure.</span></span>|  
|`BackgroundColor`|`String`|<span data-ttu-id="b2b31-164">傳回資料庫中為欄位定義的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="b2b31-164">Returns the background color defined in the database for the field.</span></span>|  
|`Color`|`String`|<span data-ttu-id="b2b31-165">傳回資料庫中為項目定義的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="b2b31-165">Returns the foreground color defined in the database for the item.</span></span>|  
|`Key`|`Object`|<span data-ttu-id="b2b31-166">傳回層級的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b2b31-166">Returns the key for a level.</span></span>|  
|`LevelNumber`|`Integer`|<span data-ttu-id="b2b31-167">如果是父子式階層，則會傳回層級或維度編號。</span><span class="sxs-lookup"><span data-stu-id="b2b31-167">For parent-child hierarchies, returns the level or dimension number.</span></span>|  
|`ParentUniqueName`|`String`|<span data-ttu-id="b2b31-168">如果是父子式階層，會傳回父層級的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="b2b31-168">For parent-child hierarchies, returns a fully qualified name of the parent level.</span></span>|  
|`UniqueName`|`String`|<span data-ttu-id="b2b31-169">傳回層級的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="b2b31-169">Returns the fully qualified name of a level.</span></span> <span data-ttu-id="b2b31-170">例如，員工的 `UniqueName` 值可能是 *[0D_Company]。 [10D_Department]。[11]*。</span><span class="sxs-lookup"><span data-stu-id="b2b31-170">For example, the `UniqueName` value for an employee might be *[0D_Company].[10D_Department].[11]*.</span></span>|  
  
 <span data-ttu-id="b2b31-171">如需在運算式中使用欄位及欄位屬性的詳細資訊，請參閱[運算式中的內建集合 &#40;報表產生器及 SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="b2b31-171">For more information about using fields and field properties in an expression, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="b2b31-172">備註</span><span class="sxs-lookup"><span data-stu-id="b2b31-172">Remarks</span></span>  
 <span data-ttu-id="b2b31-173">這個資料提供者並沒有支援所有的報表傳遞模式。</span><span class="sxs-lookup"><span data-stu-id="b2b31-173">Not all report delivery modes are supported by this data provider.</span></span> <span data-ttu-id="b2b31-174">這個資料處理延伸模組不支援透過資料驅動訂閱所傳遞的報表。</span><span class="sxs-lookup"><span data-stu-id="b2b31-174">Delivering reports through data-driven subscriptions is not supported for this data processing extension.</span></span> <span data-ttu-id="b2b31-175">如需詳細資訊，請參閱[使用外部資料來源以取得訂閱者資料 &#40;資料驅動訂閱&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="b2b31-175">For more information, see [Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md).</span></span>  
  
 <span data-ttu-id="b2b31-176">如需詳細資訊，請參閱 [搭配 SAP NetWeaver Business Intelligence 使用 SQL Server 2008 Reporting Services](https://go.microsoft.com/fwlink/?LinkId=167352)。</span><span class="sxs-lookup"><span data-stu-id="b2b31-176">For more information, see [Using SQL Server 2008 Reporting Services with SAP NetWeaver Business Intelligence](https://go.microsoft.com/fwlink/?LinkId=167352).</span></span>  
  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a> <span data-ttu-id="b2b31-177">如何主題</span><span class="sxs-lookup"><span data-stu-id="b2b31-177">How-To Topics</span></span>  
 <span data-ttu-id="b2b31-178">本節包含使用資料連接、資料來源與資料集的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="b2b31-178">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="b2b31-179">新增及驗證資料連線或資料來源 &#40;Report Builder 和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b2b31-179">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="b2b31-180">建立共用資料集或內嵌資料集 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b2b31-180">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="b2b31-181">將篩選加入資料集中 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b2b31-181">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="b2b31-182">相關章節</span><span class="sxs-lookup"><span data-stu-id="b2b31-182">Related Sections</span></span>  
 <span data-ttu-id="b2b31-183">本文件集的這些章節會提供報表資料的深入概念性資訊，以及如何定義、自訂和使用與報表資料相關組件的程序資訊。</span><span class="sxs-lookup"><span data-stu-id="b2b31-183">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="b2b31-184">將資料加入至報表 &#40;Report Builder 和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b2b31-184">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="b2b31-185">提供存取報表資料的概觀。</span><span class="sxs-lookup"><span data-stu-id="b2b31-185">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="b2b31-186">報表產生器中的資料連接、資料來源及連接字串</span><span class="sxs-lookup"><span data-stu-id="b2b31-186">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="b2b31-187">提供資料連接與資料來源的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b2b31-187">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="b2b31-188">報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b2b31-188">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="b2b31-189">提供內嵌與共用資料集的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b2b31-189">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="b2b31-190">資料集欄位集合 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b2b31-190">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="b2b31-191">提供查詢所產生之資料集欄位集合的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b2b31-191">Provides information about the dataset field collection generated by the query.</span></span>  
  
 [<span data-ttu-id="b2b31-192">Reporting Services 支援的資料來源 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b2b31-192">Data Sources Supported by Reporting Services &#40;SSRS&#41;</span></span>](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
 <span data-ttu-id="b2b31-193">提供支援每一個資料延伸模組之平台與版本的深入資訊。</span><span class="sxs-lookup"><span data-stu-id="b2b31-193">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="b2b31-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2b31-194">See Also</span></span>  
 <span data-ttu-id="b2b31-195">[報表參數 &#40;報表產生器和報表設計師&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="b2b31-195">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="b2b31-196">[篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b2b31-196">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b2b31-197">運算式 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b2b31-197">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
