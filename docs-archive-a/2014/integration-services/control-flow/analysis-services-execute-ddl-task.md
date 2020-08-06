---
title: Analysis Services 執行 DDL 工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asexecuteddltask.f1
helpviewer_keywords:
- Analysis Services Execute DDL task
- DDL
ms.assetid: 7f25c8c6-b601-41f2-9553-be0a2ee0751a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a75bae174c816cdabd07ce688e068cbadb016b45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596214"
---
# <a name="analysis-services-execute-ddl-task"></a><span data-ttu-id="68fa7-102">Analysis Services 執行 DDL 工作</span><span class="sxs-lookup"><span data-stu-id="68fa7-102">Analysis Services Execute DDL Task</span></span>
  <span data-ttu-id="68fa7-103">「 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行 DDL」工作會執行可建立、卸除或修改採礦模型和多維度物件 (如 Cube 和維度) 的資料定義語言 (DDL) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="68fa7-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL task runs data definition language (DDL) statements that can create, drop, or alter mining models and multidimensional objects such as cubes and dimensions.</span></span> <span data-ttu-id="68fa7-104">例如，DDL 陳述式可在 **Adventure Works** Cube 中建立資料分割，或在 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] ([!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中所含的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]範例資料庫) 中刪除維度。</span><span class="sxs-lookup"><span data-stu-id="68fa7-104">For example, a DDL statement can create a partition in the **Adventure Works** cube, or delete a dimension in [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], the sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="68fa7-105">「 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行 DDL」工作會使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 連接管理員連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的執行個體或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="68fa7-105">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL task uses an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="68fa7-106">如需相關資訊，請參閱 [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="68fa7-106">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="68fa7-107">包括多項執行商業智慧作業的工作，例如處理分析物件和執行資料採礦預測查詢。</span><span class="sxs-lookup"><span data-stu-id="68fa7-107">includes a number of tasks that perform business intelligence operations, such as processing analytic objects and running data mining prediction queries.</span></span>  
  
 <span data-ttu-id="68fa7-108">如需有關相關之商業智慧工作的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="68fa7-108">For more information about related business intelligence tasks, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="68fa7-109">Analysis Services 處理工作</span><span class="sxs-lookup"><span data-stu-id="68fa7-109">Analysis Services Processing Task</span></span>](analysis-services-processing-task.md)  
  
-   [<span data-ttu-id="68fa7-110">資料採礦查詢工作</span><span class="sxs-lookup"><span data-stu-id="68fa7-110">Data Mining Query Task</span></span>](data-mining-query-task.md)  
  
## <a name="ddl-statements"></a><span data-ttu-id="68fa7-111">DDL 陳述式</span><span class="sxs-lookup"><span data-stu-id="68fa7-111">DDL Statements</span></span>  
 <span data-ttu-id="68fa7-112">DDL 陳述式會在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 指令碼語言 (ASSL) 中以陳述式的方式呈現，在 XML for Analysis (XMLA) 命令中則會加上框架。</span><span class="sxs-lookup"><span data-stu-id="68fa7-112">The DDL statements are represented as statements in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language (ASSL), and framed in an XML for Analysis (XMLA) command.</span></span>  
  
-   <span data-ttu-id="68fa7-113">ASSL 是用來定義和描述 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的執行個體，及其包含的資料庫和資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="68fa7-113">ASSL is used to define and describe an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and the databases and database objects it contains.</span></span> <span data-ttu-id="68fa7-114">如需詳細資訊，請參閱[Analysis Services 指令碼語言 &#40;ASSL&#41; 參考](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)。</span><span class="sxs-lookup"><span data-stu-id="68fa7-114">For more information, see [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).</span></span>  
  
-   <span data-ttu-id="68fa7-115">XMLA 為命令語言，用來傳送動作命令 (如「建立」、「改變」或「處理」) 至 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="68fa7-115">XMLA is a command language that is used to send action commands, such as Create, Alter, or Process, to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="68fa7-116">如需詳細資訊，請參閱 [XML for Analysis &#40;XMLA&#41; 參考](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)。</span><span class="sxs-lookup"><span data-stu-id="68fa7-116">For more information, see [XML for Analysis  &#40;XMLA&#41; Reference](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference).</span></span>  
  
 <span data-ttu-id="68fa7-117">如果 DDL 程式碼存放在另一個檔案中，「 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行 DDL」工作便會使用「檔案」連線管理員指定該檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="68fa7-117">If the DDL code is stored in a separate file, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL task uses a File connection manager to specify the path of the file.</span></span> <span data-ttu-id="68fa7-118">如需相關資訊，請參閱 [File Connection Manager](../connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="68fa7-118">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="68fa7-119">由於 DDL 陳述式可能包含密碼和其他機密資訊，因此包含一或多項「[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行 DDL」工作的封裝應使用封裝保護等級 `EncryptAllWithUserKey` 或 `EncryptAllWithPassword`。</span><span class="sxs-lookup"><span data-stu-id="68fa7-119">Because DDL statements can contain passwords and other sensitive information, a package that contains one or more [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL tasks should use the package protection level `EncryptAllWithUserKey` or `EncryptAllWithPassword`.</span></span> <span data-ttu-id="68fa7-120">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 封裝](../integration-services-ssis-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="68fa7-120">For more information, see [Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md).</span></span>  
  
### <a name="ddl-examples"></a><span data-ttu-id="68fa7-121">DDL 範例</span><span class="sxs-lookup"><span data-stu-id="68fa7-121">DDL Examples</span></span>  
 <span data-ttu-id="68fa7-122">下列三種 DDL 陳述式由 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] ([!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中所含的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料庫) 中的指令碼物件所產生。</span><span class="sxs-lookup"><span data-stu-id="68fa7-122">The following three DDL statements were generated by scripting objects in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="68fa7-123">下列 DDL 陳述式會刪除 **Promotion** 維度。</span><span class="sxs-lookup"><span data-stu-id="68fa7-123">The following DDL statement deletes the **Promotion** dimension.</span></span>  
  
```  
<Delete xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 <span data-ttu-id="68fa7-124">下列 DDL 陳述式會處理 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] Cube。</span><span class="sxs-lookup"><span data-stu-id="68fa7-124">The following DDL statement processes the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] cube.</span></span>  
  
```  
<Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Parallel>  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      </Object>  
      <Type>ProcessFull</Type>  
      <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
    </Process>  
  </Parallel>  
</Batch>  
  
```  
  
 <span data-ttu-id="68fa7-125">下列 DDL 陳述式會建立 **預測** 採礦模型。</span><span class="sxs-lookup"><span data-stu-id="68fa7-125">The following DDL statement creates the **Forecasting** mining model.</span></span>  
  
```  
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <MiningStructureID>Forecasting</MiningStructureID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningModel xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Forecasting</ID>  
            <Name>Forecasting</Name>  
            <Algorithm>Microsoft_Time_Series</Algorithm>  
            <AlgorithmParameters>  
                <AlgorithmParameter>  
                    <Name>PERIODICITY_HINT</Name>  
                    <Value xsi:type="xsd:string">{12}</Value>  
                </AlgorithmParameter>  
            </AlgorithmParameters>  
            <Columns>  
                <Column>  
                    <ID>Amount</ID>  
                    <Name>Amount</Name>  
                    <SourceColumnID>Amount</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Model Region</ID>  
                    <Name>Model Region</Name>  
                    <SourceColumnID>Model Region</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
                <Column>  
                    <ID>Quantity</ID>  
                    <Name>Quantity</Name>  
                    <SourceColumnID>Quantity</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Time Index</ID>  
                    <Name>Time Index</Name>  
                    <SourceColumnID>Time Index</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
            </Columns>  
            <Collation>Latin1_General_CS_AS_KS</Collation>  
        </MiningModel>  
    </ObjectDefinition>  
</Create>  
  
```  
  
 <span data-ttu-id="68fa7-126">下列三種 DDL 陳述式由 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] ([!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中所含的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料庫) 中的指令碼物件所產生。</span><span class="sxs-lookup"><span data-stu-id="68fa7-126">The following three DDL statements were generated by scripting objects in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="68fa7-127">下列 DDL 陳述式會刪除 **Promotion** 維度。</span><span class="sxs-lookup"><span data-stu-id="68fa7-127">The following DDL statement deletes the **Promotion** dimension.</span></span>  
  
```  
<Delete xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 <span data-ttu-id="68fa7-128">下列 DDL 陳述式會處理 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] Cube。</span><span class="sxs-lookup"><span data-stu-id="68fa7-128">The following DDL statement processes the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] cube.</span></span>  
  
```  
<Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Parallel>  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      </Object>  
      <Type>ProcessFull</Type>  
      <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
    </Process>  
  </Parallel>  
</Batch>  
  
```  
  
 <span data-ttu-id="68fa7-129">下列 DDL 陳述式會建立 **預測** 採礦模型。</span><span class="sxs-lookup"><span data-stu-id="68fa7-129">The following DDL statement creates the **Forecasting** mining model.</span></span>  
  
```  
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <MiningStructureID>Forecasting</MiningStructureID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningModel xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Forecasting</ID>  
            <Name>Forecasting</Name>  
            <Algorithm>Microsoft_Time_Series</Algorithm>  
            <AlgorithmParameters>  
                <AlgorithmParameter>  
                    <Name>PERIODICITY_HINT</Name>  
                    <Value xsi:type="xsd:string">{12}</Value>  
                </AlgorithmParameter>  
            </AlgorithmParameters>  
            <Columns>  
                <Column>  
                    <ID>Amount</ID>  
                    <Name>Amount</Name>  
                    <SourceColumnID>Amount</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Model Region</ID>  
                    <Name>Model Region</Name>  
                    <SourceColumnID>Model Region</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
                <Column>  
                    <ID>Quantity</ID>  
                    <Name>Quantity</Name>  
                    <SourceColumnID>Quantity</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Time Index</ID>  
                    <Name>Time Index</Name>  
                    <SourceColumnID>Time Index</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
            </Columns>  
            <Collation>Latin1_General_CS_AS_KS</Collation>  
        </MiningModel>  
    </ObjectDefinition>  
</Create>  
  
```  
  
## <a name="configuration-of-the-analysis-services-execute-ddl-task"></a><span data-ttu-id="68fa7-130">設定 Analysis Services 執行 DDL 工作</span><span class="sxs-lookup"><span data-stu-id="68fa7-130">Configuration of the Analysis Services Execute DDL Task</span></span>  
 <span data-ttu-id="68fa7-131">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="68fa7-131">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="68fa7-132">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="68fa7-132">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="68fa7-133">Analysis Services 執行 DDL 工作編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="68fa7-133">Analysis Services Execute DDL Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="68fa7-134">Analysis Services 執行 DDL 工作編輯器 &#40;DDL 頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="68fa7-134">Analysis Services Execute DDL Task Editor &#40;DDL Page&#41;</span></span>](../analysis-services-execute-ddl-task-editor-ddl-page.md)  
  
-   [<span data-ttu-id="68fa7-135">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="68fa7-135">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="68fa7-136">如需在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="68fa7-136">For more information about setting these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="68fa7-137">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="68fa7-137">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-analysis-services-execute-ddl-task"></a><span data-ttu-id="68fa7-138">以程式設計方式設定 Analysis Services 執行 DDL 工作</span><span class="sxs-lookup"><span data-stu-id="68fa7-138">Programmatic Configuration of the Analysis Services Execute DDL Task</span></span>  
 <span data-ttu-id="68fa7-139">如需有關以程式設計方式設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="68fa7-139">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.DataTransformationServices.Tasks.DTSProcessingTask.ASExecuteDDLTask>  
  
  
