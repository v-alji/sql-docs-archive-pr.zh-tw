---
title: 將參數傳遞至 Updategram (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nullvalue attribute
- passing parameters [SQLXML]
- parameters [SQLXML]
- updategrams [SQLXML], passing parameters
- null values [SQLXML]
ms.assetid: 2354e6e7-1860-471f-8711-4e374c5a4ed2
author: rothja
ms.author: jroth
ms.openlocfilehash: 4bc29de2dab3d0bc3587cb21b7005c0c23dcf7c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597742"
---
# <a name="passing-parameters-to-updategrams-sqlxml-40"></a><span data-ttu-id="2c1e2-102">將參數傳遞至 Updategrams (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="2c1e2-102">Passing Parameters to Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="2c1e2-103">Updategrams 是範本，所以您可以將參數傳遞給它們。</span><span class="sxs-lookup"><span data-stu-id="2c1e2-103">Updategrams are templates; therefore, you can pass them parameters.</span></span> <span data-ttu-id="2c1e2-104">如需將參數傳遞至範本的詳細資訊，請參閱[Updategram &#40;SQLXML 4.0&#41;的安全性考慮](../security/updategram-security-considerations-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="2c1e2-104">For more information about passing parameters to templates, see [Updategram Security Considerations &#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="2c1e2-105">Updategrams 可讓您將 NULL 當做參數值來傳遞。</span><span class="sxs-lookup"><span data-stu-id="2c1e2-105">Updategrams allow you to pass NULL as a parameter value.</span></span> <span data-ttu-id="2c1e2-106">若要傳遞 NULL 參數值，您會指定 `nullvalue` 屬性。</span><span class="sxs-lookup"><span data-stu-id="2c1e2-106">To pass the NULL parameter value, you specify the `nullvalue` attribute.</span></span> <span data-ttu-id="2c1e2-107">然後會將指派給 `nullvalue` 屬性的值當做參數值來提供。</span><span class="sxs-lookup"><span data-stu-id="2c1e2-107">The value that is assigned to the `nullvalue` attribute is then provided as the parameter value.</span></span> <span data-ttu-id="2c1e2-108">Updategrams 將此值視為 NULL。</span><span class="sxs-lookup"><span data-stu-id="2c1e2-108">Updategrams treat this value as NULL.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2c1e2-109">在 `<sql:header>` 和 `<updg:header>` 中，您應該將 `nullvalue` 指定為不合格；但是在 `<updg:sync>` 中，您應該將 `nullvalue` 指定為合格 (例如 `updg:nullvalue`)。</span><span class="sxs-lookup"><span data-stu-id="2c1e2-109">In `<sql:header>` and `<updg:header>`, you should specify the `nullvalue` as unqualified; whereas, in `<updg:sync>`, you specify the `nullvalue` as qualified (for example, `updg:nullvalue`).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2c1e2-110">範例</span><span class="sxs-lookup"><span data-stu-id="2c1e2-110">Examples</span></span>  
 <span data-ttu-id="2c1e2-111">若要使用下列範例建立工作範例，您必須符合[執行 SQLXML 範例的需求](../../sqlxml/requirements-for-running-sqlxml-examples.md)中所指定的需求。</span><span class="sxs-lookup"><span data-stu-id="2c1e2-111">To create working samples using the following examples, you must meet the requirements specified in [Requirements for Running SQLXML Examples](../../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
 <span data-ttu-id="2c1e2-112">使用 Updategram 範例之前，請注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="2c1e2-112">Before using the updategram examples, note the following:</span></span>  
  
-   <span data-ttu-id="2c1e2-113">此範例會使用預設對應 (也就是說，updategram 中不會指定任何對應結構描述)。</span><span class="sxs-lookup"><span data-stu-id="2c1e2-113">The examples use default mapping (that is, no mapping schema is specified in the updategram).</span></span> <span data-ttu-id="2c1e2-114">如需使用對應架構之 updategram 的更多範例，請參閱[在 Updategram 中指定批註式對應架構 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="2c1e2-114">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
### <a name="a-passing-parameters-to-an-updategram"></a><span data-ttu-id="2c1e2-115">A.</span><span class="sxs-lookup"><span data-stu-id="2c1e2-115">A.</span></span> <span data-ttu-id="2c1e2-116">傳遞參數給 updategram</span><span class="sxs-lookup"><span data-stu-id="2c1e2-116">Passing parameters to an updategram</span></span>  
 <span data-ttu-id="2c1e2-117">在此範例中，updategram 會變更 umanResources.Shift 資料表內員工的姓氏。</span><span class="sxs-lookup"><span data-stu-id="2c1e2-117">In this example, the updategram changes the last name of an employee in the HumanResources.Shift table.</span></span> <span data-ttu-id="2c1e2-118">有兩個參數會傳遞給 updategram：用來唯一識別移位的 ShiftID 及 Name。</span><span class="sxs-lookup"><span data-stu-id="2c1e2-118">The updategram is passed two parameters: ShiftID, which is used to uniquely identify a shift, and Name.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:header>  
  <updg:param name="ShiftID"/>  
  <updg:param name="Name" />  
</updg:header>  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="$ShiftID" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="$Name" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="2c1e2-119">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="2c1e2-119">To test the updategram</span></span>  
  
1.  <span data-ttu-id="2c1e2-120">將上述的 updategram 複製到 [記事本] 中，並將它儲存為 UpdategramWithParameters.xml 檔。</span><span class="sxs-lookup"><span data-stu-id="2c1e2-120">Copy the updategram above into Notepad and save it to file as UpdategramWithParameters.xml.</span></span>  
  
2.  <span data-ttu-id="2c1e2-121">準備 SQLXML 4.0 測試腳本 () Sqlxml4test.vbs 在中[使用 ADO 執行 sqlxml 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)以執行 updategram，方法是在之後新增下列幾行 `cmd.Properties("Output Stream").Value = outStream` ：</span><span class="sxs-lookup"><span data-stu-id="2c1e2-121">Prepare the SQLXML 4.0 test script (Sqlxml4test.vbs) in [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) to execute the updategram by adding the following lines after the `cmd.Properties("Output Stream").Value = outStream`:</span></span>  
  
    ```  
    cmd.NamedParameters = True  
    ' CreateParameter arguments: Name, Type, Direction, Size, Value  
    cmd.Parameters.Append cmd.CreateParameter("@ShiftID",  2, 1,  0, 1)  
    cmd.Parameters.Append cmd.CreateParameter("@Name",   200, 1, 50, "New Name")  
    ```  
  
### <a name="b-passing-null-as-a-parameter-value-to-an-updategram"></a><span data-ttu-id="2c1e2-122">B.</span><span class="sxs-lookup"><span data-stu-id="2c1e2-122">B.</span></span> <span data-ttu-id="2c1e2-123">將 NULL 當做 updategram 的參數值來傳遞</span><span class="sxs-lookup"><span data-stu-id="2c1e2-123">Passing NULL as a parameter value to an updategram</span></span>  
 <span data-ttu-id="2c1e2-124">在執行 updategram 時，"isnull" 值會指派給您想要設定為 NULL 的參數。</span><span class="sxs-lookup"><span data-stu-id="2c1e2-124">In executing an updategram, the "isnull" value is assigned to the parameter that you want to set to NULL.</span></span> <span data-ttu-id="2c1e2-125">Updategram 會將 "isnulll" 參數值轉換成 NULL，並適當地加以處理。</span><span class="sxs-lookup"><span data-stu-id="2c1e2-125">Updategram converts the "isnulll" parameter value to NULL and processes it accordingly.</span></span>  
  
 <span data-ttu-id="2c1e2-126">下列 updategram 會將員工職稱設定為 NULL：</span><span class="sxs-lookup"><span data-stu-id="2c1e2-126">The following updategram sets an employee title to NULL:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:header nullvalue="isnull" >  
  <updg:param name="EmployeeID"/>  
  <updg:param name="ManagerID" />  
</updg:header>  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Employee EmployeeID="$EmployeeID" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Employee ManagerID="$ManagerID" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="2c1e2-127">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="2c1e2-127">To test the updategram</span></span>  
  
1.  <span data-ttu-id="2c1e2-128">將上述的 updategram 複製到 [記事本] 中，並將它儲存為 UpdategramPassingNullvalues.xml 檔。</span><span class="sxs-lookup"><span data-stu-id="2c1e2-128">Copy the updategram above into Notepad and save it to file as UpdategramPassingNullvalues.xml.</span></span>  
  
2.  <span data-ttu-id="2c1e2-129">準備 SQLXML 4.0 測試腳本 () Sqlxml4test.vbs 在中[使用 ADO 執行 sqlxml 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)以執行 updategram，方法是在之後新增下列幾行 `cmd.Properties("Output Stream").Value = outStream` ：</span><span class="sxs-lookup"><span data-stu-id="2c1e2-129">Prepare the SQLXML 4.0 test script (Sqlxml4test.vbs) in [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) to execute the updategram by adding the following lines after the `cmd.Properties("Output Stream").Value = outStream`:</span></span>  
  
    ```  
    cmd.NamedParameters = True  
    ' CreateParameter arguments: Name, Type, Direction, Size, Value   
    cmd.Parameters.Append cmd.CreateParameter("@EmployeeID", 3, 1, 0, 1)  
    cmd.Parameters.Append cmd.CreateParameter("@ManagerID",  3, 1, 0, Null)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2c1e2-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c1e2-130">See Also</span></span>  
 [<span data-ttu-id="2c1e2-131">&#40;SQLXML 4.0&#41;的 Updategram 安全性考慮</span><span class="sxs-lookup"><span data-stu-id="2c1e2-131">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
