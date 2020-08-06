---
title: SqlXmlCommand 物件 (SQLXML Managed 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void ExecuteNonQuery() method
- namespaces property
- Stream ExecuteStream() method
- CommandType property
- RootTag property
- OutputEncoding property
- XmlReader ExecuteXmlReader() method
- Managed Classes [SQLXML], SqlXmlCommand object
- SQLXML Managed Classes, SqlXmlCommand object
- Base Path property
- void ClearParameters() method
- public void ExecuteToStream(Stream outputStream) method
- SqlXmlCommand object
- CommandText property
- XslPath property
- SchemaPath property
- SqlXmlParameter CreateParameter() method
- ClientSideXML property
- CommandStream property
ms.assetid: c1f9e0bb-a89d-4d6a-a96e-289ef516a3a6
author: rothja
ms.author: jroth
ms.openlocfilehash: 78b72581f549ea007dae0cdc7044fd9a809920af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596572"
---
# <a name="sqlxmlcommand-object-sqlxml-managed-classes"></a><span data-ttu-id="601e0-102">SqlXmlCommand 物件 (SQLXML Managed 類別)</span><span class="sxs-lookup"><span data-stu-id="601e0-102">SqlXmlCommand Object (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="601e0-103">這是 SqlXmlCommand 物件的構造函式：</span><span class="sxs-lookup"><span data-stu-id="601e0-103">This is the constructor for the SqlXmlCommand object:</span></span>  
  
```  
public SqlXmlCommand(string cnString)  
```  
  
 <span data-ttu-id="601e0-104">其中 `cnString` 是用來識別伺服器、資料庫和登入資訊的 ADO 或 OLEDB 連接字串，例如 `Provider=SQLOLEDB; Server=(local); database=AdventureWorks; Integrated Security=SSPI"` 。</span><span class="sxs-lookup"><span data-stu-id="601e0-104">Where `cnString` is the ADO or OLEDB connection string that identifies the server, database, and the login information-for example, `Provider=SQLOLEDB; Server=(local); database=AdventureWorks; Integrated Security=SSPI"`.</span></span>  
  
 <span data-ttu-id="601e0-105">在連接字串中，`Provider` 必須為 SQLOLEDB 而 `Data Provider` 不應包含在連接字串中。</span><span class="sxs-lookup"><span data-stu-id="601e0-105">In the connection string, the `Provider` must be SQLOLEDB and the `Data Provider` should not be included in the provider string).</span></span>  
  
 <span data-ttu-id="601e0-106">如需實用範例，請參閱[&#40;SQLXML Managed 類別&#41;執行 SQL 查詢](sqlxml-4-0-net-framework-support-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="601e0-106">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="601e0-107">方法</span><span class="sxs-lookup"><span data-stu-id="601e0-107">Methods</span></span>  
 <span data-ttu-id="601e0-108">TheSqlXmlCommand 物件支援數種方法，包括下列執行命令的方法：</span><span class="sxs-lookup"><span data-stu-id="601e0-108">TheSqlXmlCommand object supports several methods, including the following methods for executing a command:</span></span>  
  
 <span data-ttu-id="601e0-109">void ExecuteNonQuery ( # A1</span><span class="sxs-lookup"><span data-stu-id="601e0-109">void ExecuteNonQuery()</span></span>  
 <span data-ttu-id="601e0-110">執行命令，但不會傳回任何東西。</span><span class="sxs-lookup"><span data-stu-id="601e0-110">Executes the command, but does not return anything.</span></span> <span data-ttu-id="601e0-111">如果您要執行非查詢命令 (也就是不會傳回任何東西的命令)，此方法相當實用。</span><span class="sxs-lookup"><span data-stu-id="601e0-111">This method is useful if you want to execute a nonquery command (that is, a command that does not return anything).</span></span> <span data-ttu-id="601e0-112">例如，執行更新記錄但不會傳回任何東西的 Updategram 或 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="601e0-112">An example is executing an updategram or a DiffGram that updates records but returns nothing.</span></span>  
  
 <span data-ttu-id="601e0-113">Stream ExecuteStream ( # A1</span><span class="sxs-lookup"><span data-stu-id="601e0-113">Stream ExecuteStream()</span></span>  
 <span data-ttu-id="601e0-114">傳回新的資料流程物件。</span><span class="sxs-lookup"><span data-stu-id="601e0-114">Returns a new Stream object.</span></span> <span data-ttu-id="601e0-115">當您希望讓新資料流中的查詢結果傳回給您時，此方法相當實用。</span><span class="sxs-lookup"><span data-stu-id="601e0-115">This method is useful when you want the query results returned to you in a new stream.</span></span> <span data-ttu-id="601e0-116">如需實用範例，請參閱[&#40;SQLXML Managed 類別&#41;執行 SQL 查詢](sqlxml-4-0-net-framework-support-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="601e0-116">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
 <span data-ttu-id="601e0-117">public void ExecuteToStream (Stream outputStream) </span><span class="sxs-lookup"><span data-stu-id="601e0-117">public void ExecuteToStream(Stream outputStream)</span></span>  
 <span data-ttu-id="601e0-118">將查詢結果寫入現有的資料流。</span><span class="sxs-lookup"><span data-stu-id="601e0-118">Writes the query results to an existing stream.</span></span> <span data-ttu-id="601e0-119">當您有需要 (附加結果的資料流程時，這個方法就很有用，例如，若要將查詢結果寫入 HttpResponse. OutputStream) 。</span><span class="sxs-lookup"><span data-stu-id="601e0-119">This method is useful when you have a stream to which you need the results appended (for example, to have the query results written to the System.Web.HttpResponse.OutputStream).</span></span> <span data-ttu-id="601e0-120">如需實用範例，請參閱[&#40;SQLXML Managed 類別&#41;執行 SQL 查詢](sqlxml-4-0-net-framework-support-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="601e0-120">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
 <span data-ttu-id="601e0-121">XmlReader ExecuteXmlReader ( # A1</span><span class="sxs-lookup"><span data-stu-id="601e0-121">XmlReader ExecuteXmlReader()</span></span>  
 <span data-ttu-id="601e0-122">傳回 XmlReader 物件。</span><span class="sxs-lookup"><span data-stu-id="601e0-122">Returns an XmlReader object.</span></span> <span data-ttu-id="601e0-123">您可以使用這個方法直接操作 XmlReader 物件中的資料，或插入 System.Xml 的可鏈結架構。</span><span class="sxs-lookup"><span data-stu-id="601e0-123">You can use this method to either manipulate data in the XmlReader object directly or plug in the chainable architecture of System.Xml.</span></span> <span data-ttu-id="601e0-124">如需詳細資訊，請參閱 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 文件集。</span><span class="sxs-lookup"><span data-stu-id="601e0-124">For more information, see the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework documentation.</span></span> <span data-ttu-id="601e0-125">如需實用範例，請參閱[使用 ExecuteXMLReader 方法執行 SQL 查詢](executing-sql-queries-by-using-the-executexmlreader-method.md)。</span><span class="sxs-lookup"><span data-stu-id="601e0-125">For a working sample, see [Executing SQL Queries by Using the ExecuteXMLReader Method](executing-sql-queries-by-using-the-executexmlreader-method.md).</span></span>  
  
 <span data-ttu-id="601e0-126">TheSqlXmlCommand 物件也支援下列其他方法：</span><span class="sxs-lookup"><span data-stu-id="601e0-126">TheSqlXmlCommand object also supports these additional methods:</span></span>  
  
 <span data-ttu-id="601e0-127">SqlXmlParameter CreateParameter ( # A1</span><span class="sxs-lookup"><span data-stu-id="601e0-127">SqlXmlParameter CreateParameter()</span></span>  
 <span data-ttu-id="601e0-128">建立 SqlXmlParameter 物件。</span><span class="sxs-lookup"><span data-stu-id="601e0-128">Creates an SqlXmlParameter object.</span></span> <span data-ttu-id="601e0-129">您可以設定這個物件的*Name*和*Value*參數值。</span><span class="sxs-lookup"><span data-stu-id="601e0-129">You can set values for the *Name* and *Value* parameters of this object.</span></span> <span data-ttu-id="601e0-130">如果您要將參數傳遞到命令，這個方法相當實用。</span><span class="sxs-lookup"><span data-stu-id="601e0-130">This method is useful if you want to pass parameters to a command.</span></span> <span data-ttu-id="601e0-131">如需實用範例，請參閱[&#40;SQLXML Managed 類別&#41;執行 SQL 查詢](sqlxml-4-0-net-framework-support-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="601e0-131">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
 <span data-ttu-id="601e0-132">void ClearParameters ( # A1</span><span class="sxs-lookup"><span data-stu-id="601e0-132">void ClearParameters()</span></span>  
 <span data-ttu-id="601e0-133">清除針對給定命令物件建立的參數。</span><span class="sxs-lookup"><span data-stu-id="601e0-133">Clears parameter(s) that were created for a given command object.</span></span> <span data-ttu-id="601e0-134">如果您要在相同的命令物件上執行多個查詢，這個方法相當實用。</span><span class="sxs-lookup"><span data-stu-id="601e0-134">This method is useful if you want to execute multiple queries on the same command object.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="601e0-135">屬性</span><span class="sxs-lookup"><span data-stu-id="601e0-135">Properties</span></span>  
 <span data-ttu-id="601e0-136">SqlXmlCommand 物件也支援下列屬性：</span><span class="sxs-lookup"><span data-stu-id="601e0-136">The SqlXmlCommand object also supports these properties:</span></span>  
  
 <span data-ttu-id="601e0-137">ClientSideXml</span><span class="sxs-lookup"><span data-stu-id="601e0-137">ClientSideXml</span></span>  
 <span data-ttu-id="601e0-138">設定為 True 時，指定在用戶端而不是伺服器上會將資料列集轉換成 XML。</span><span class="sxs-lookup"><span data-stu-id="601e0-138">When set to True, specifies that conversion of the rowset to XML is to occur on the client instead of on the server.</span></span> <span data-ttu-id="601e0-139">如果您想要將效能負載移到中介層，這個屬性會很實用。</span><span class="sxs-lookup"><span data-stu-id="601e0-139">This property is useful when you want to move the performance load to the middle tier.</span></span> <span data-ttu-id="601e0-140">此屬性也可讓您利用 FOR XML 包裝現有的預存程序來取得 XML 輸出。</span><span class="sxs-lookup"><span data-stu-id="601e0-140">The property also allows you to wrap the existing stored procedures with FOR XML to get XML output.</span></span>  
  
 <span data-ttu-id="601e0-141">SchemaPath</span><span class="sxs-lookup"><span data-stu-id="601e0-141">SchemaPath</span></span>  
 <span data-ttu-id="601e0-142">對應結構描述的名稱以及目錄路徑 (例如，C:\x\y\MySchema.xml)。</span><span class="sxs-lookup"><span data-stu-id="601e0-142">The name of the mapping schema along with the directory path (for example, C:\x\y\MySchema.xml).</span></span> <span data-ttu-id="601e0-143">此屬性對於指定 XPath 查詢的對應結構描述相當實用。</span><span class="sxs-lookup"><span data-stu-id="601e0-143">This property is useful for specifying a mapping schema for XPath queries.</span></span> <span data-ttu-id="601e0-144">指定的路徑可以是相對或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="601e0-144">The path that is specified can be absolute or relative.</span></span> <span data-ttu-id="601e0-145">如果路徑是相對的，則會使用 [基底路徑] 中所指定的基底路徑來解析相對路徑。</span><span class="sxs-lookup"><span data-stu-id="601e0-145">If the path is relative, the base path that is specified in Base Path is used to resolve the relative path.</span></span> <span data-ttu-id="601e0-146">如果未指定基底路徑，相對路徑會相對於目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="601e0-146">If no base path is specified, the relative path is relative to the current directory.</span></span> <span data-ttu-id="601e0-147">如需實用範例，請參閱[存取 .Net 環境中的 SQLXML 功能](accessing-sqlxml-functionality-in-the-net-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="601e0-147">For a working sample, see [Accessing SQLXML Functionality in the .NET Environment](accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
 <span data-ttu-id="601e0-148">XslPath</span><span class="sxs-lookup"><span data-stu-id="601e0-148">XslPath</span></span>  
 <span data-ttu-id="601e0-149">XSL 檔案的名稱與目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="601e0-149">The name of the XSL file along with the directory path.</span></span> <span data-ttu-id="601e0-150">指定的路徑可以是相對或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="601e0-150">The path that is specified can be absolute or relative.</span></span> <span data-ttu-id="601e0-151">如果路徑是相對的，則會使用 [基底路徑] 中所指定的基底路徑來解析相對路徑。</span><span class="sxs-lookup"><span data-stu-id="601e0-151">If the path is relative, the base path that is specified in Base Path is used to resolve the relative path.</span></span> <span data-ttu-id="601e0-152">如果未指定基底路徑，相對路徑會相對於目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="601e0-152">If no base path is specified, the relative path is relative to the current directory.</span></span> <span data-ttu-id="601e0-153">如需實用範例，請參閱[&#40;SQLXML Managed 類別套用 XSL 轉換&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="601e0-153">For a working sample, see [Applying an XSL Transformation &#40;SQLXML Managed Classes&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).</span></span>  
  
 <span data-ttu-id="601e0-154">基底路徑</span><span class="sxs-lookup"><span data-stu-id="601e0-154">Base Path</span></span>  
 <span data-ttu-id="601e0-155">基底路徑 (目錄路徑)。</span><span class="sxs-lookup"><span data-stu-id="601e0-155">The base path (a directory path).</span></span> <span data-ttu-id="601e0-156">這個屬性可用於解析指定給 XSL 檔案 (的相對路徑，方法是使用 XslPath 屬性) 、使用 SchemaPath 屬性)  (的對應架構檔案，或 (使用屬性) 指定的 XML 範本中的外部架構參考 `mapping-schema` 。</span><span class="sxs-lookup"><span data-stu-id="601e0-156">This property is useful for resolving a relative path that is specified for an XSL file (by using the XslPath property), a mapping schema file (by using the SchemaPath property), or an external schema reference in an XML template (specified by using the `mapping-schema` attribute).</span></span>  
  
 <span data-ttu-id="601e0-157">OutputEncoding</span><span class="sxs-lookup"><span data-stu-id="601e0-157">OutputEncoding</span></span>  
 <span data-ttu-id="601e0-158">指定命令執行時所傳回之資料流的編碼。</span><span class="sxs-lookup"><span data-stu-id="601e0-158">Specifies the encoding for the stream that is returned when the command executes.</span></span> <span data-ttu-id="601e0-159">此屬性對於要求所傳回之資料流的特定編碼相當實用。</span><span class="sxs-lookup"><span data-stu-id="601e0-159">This property is useful for requesting a specific encoding for the stream that is returned.</span></span> <span data-ttu-id="601e0-160">一些常用的編碼為 UTF-8、ANSI 和 Unicode。</span><span class="sxs-lookup"><span data-stu-id="601e0-160">Some commonly used encodings are UTF-8, ANSI, and Unicode.</span></span> <span data-ttu-id="601e0-161">UTF-8 是預設編碼。</span><span class="sxs-lookup"><span data-stu-id="601e0-161">UTF-8 is the default encoding.</span></span>  
  
 <span data-ttu-id="601e0-162">命名空間</span><span class="sxs-lookup"><span data-stu-id="601e0-162">Namespaces</span></span>  
 <span data-ttu-id="601e0-163">允許使用命名空間的 XPath 查詢得以執行。</span><span class="sxs-lookup"><span data-stu-id="601e0-163">Enables the execution of XPath queries that use namespaces.</span></span> <span data-ttu-id="601e0-164">如需使用命名空間之 XPath 查詢的詳細資訊，請參閱[使用命名空間執行 Xpath 查詢 &#40;SQLXML Managed 類別&#41;](executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="601e0-164">For more information about XPath queries with namespaces, see [Executing XPath Queries with Namespaces &#40;SQLXML Managed Classes&#41;](executing-xpath-queries-with-namespaces-sqlxml-managed-classes.md).</span></span> <span data-ttu-id="601e0-165">如需實用範例，請參閱[&#40;SQLXML Managed 類別&#41;執行 XPath 查詢](executing-xpath-queries-sqlxml-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="601e0-165">For a working sample, see [Executing XPath Queries &#40;SQLXML Managed Classes&#41;](executing-xpath-queries-sqlxml-managed-classes.md).</span></span>  
  
 <span data-ttu-id="601e0-166">RootTag</span><span class="sxs-lookup"><span data-stu-id="601e0-166">RootTag</span></span>  
 <span data-ttu-id="601e0-167">提供命令執行所產生之 XML 的單一根元素。</span><span class="sxs-lookup"><span data-stu-id="601e0-167">Provides the single root element for XML generated by command execution.</span></span> <span data-ttu-id="601e0-168">有效的 XML 文件需要單一根層級標籤。</span><span class="sxs-lookup"><span data-stu-id="601e0-168">A valid XML document requires a single root-level tag.</span></span> <span data-ttu-id="601e0-169">如果執行的命令產生 XML 片段 (沒有單一最上層元素)，您可以指定傳回之 XML 的根元素。</span><span class="sxs-lookup"><span data-stu-id="601e0-169">If the command executed generates an XML fragment (without a single top-level element) you can specify a root element for the returning XML.</span></span> <span data-ttu-id="601e0-170">如需實用範例，請參閱[&#40;SQLXML Managed 類別套用 XSL 轉換&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="601e0-170">For a working sample, see [Applying an XSL Transformation &#40;SQLXML Managed Classes&#41;](applying-an-xsl-transformation-sqlxml-managed-classes.md).</span></span>  
  
 <span data-ttu-id="601e0-171">CommandText</span><span class="sxs-lookup"><span data-stu-id="601e0-171">CommandText</span></span>  
 <span data-ttu-id="601e0-172">命令的文字。</span><span class="sxs-lookup"><span data-stu-id="601e0-172">The text of the command.</span></span> <span data-ttu-id="601e0-173">此屬性對於指定您要執行之命令的文字相當實用。</span><span class="sxs-lookup"><span data-stu-id="601e0-173">This property is used for specifying the text of the command you want to execute.</span></span> <span data-ttu-id="601e0-174">如需實用範例，請參閱[&#40;SQLXML Managed 類別&#41;執行 SQL 查詢](sqlxml-4-0-net-framework-support-managed-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="601e0-174">For a working sample, see [Executing SQL Queries &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md).</span></span>  
  
 <span data-ttu-id="601e0-175">CommandStream</span><span class="sxs-lookup"><span data-stu-id="601e0-175">CommandStream</span></span>  
 <span data-ttu-id="601e0-176">命令資料流。</span><span class="sxs-lookup"><span data-stu-id="601e0-176">The command stream.</span></span> <span data-ttu-id="601e0-177">如果您要從檔案 (例如，XML 範本) 執行命令，此屬性相當實用。</span><span class="sxs-lookup"><span data-stu-id="601e0-177">This property is useful if you want to execute a command from a file (for example, an XML template).</span></span> <span data-ttu-id="601e0-178">當您使用 CommandStream 時，只支援「**範本**」、「 **UpdateGram** 」和「 **DiffGram」 CommandType**值。</span><span class="sxs-lookup"><span data-stu-id="601e0-178">When you are using CommandStream, only **"Template"**, **"UpdateGram"** and **"DiffGram"CommandType** values are supported.</span></span> <span data-ttu-id="601e0-179">如需實用範例，請參閱[使用 CommandStream 屬性執行範本](executing-template-files-by-using-the-commandstream-property.md)檔案。</span><span class="sxs-lookup"><span data-stu-id="601e0-179">For a working sample, see [Executing Template Files by Using the CommandStream Property](executing-template-files-by-using-the-commandstream-property.md).</span></span>  
  
 <span data-ttu-id="601e0-180">CommandType</span><span class="sxs-lookup"><span data-stu-id="601e0-180">CommandType</span></span>  
 <span data-ttu-id="601e0-181">識別命令的類型。</span><span class="sxs-lookup"><span data-stu-id="601e0-181">Identifies the type of command.</span></span> <span data-ttu-id="601e0-182">此屬性對於指定您要執行之命令的類型相當實用。</span><span class="sxs-lookup"><span data-stu-id="601e0-182">This property is used for specifying the type of command you want to execute.</span></span> <span data-ttu-id="601e0-183">下表中的值會決定命令的類型。</span><span class="sxs-lookup"><span data-stu-id="601e0-183">The values in the following table determine the type of the command.</span></span> <span data-ttu-id="601e0-184">如需實用範例，請參閱[存取 .Net 環境中的 SQLXML 功能](accessing-sqlxml-functionality-in-the-net-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="601e0-184">For a working sample, see [Accessing SQLXML Functionality in the .NET Environment](accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
|<span data-ttu-id="601e0-185">值</span><span class="sxs-lookup"><span data-stu-id="601e0-185">Value</span></span>|<span data-ttu-id="601e0-186">描述</span><span class="sxs-lookup"><span data-stu-id="601e0-186">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="601e0-187">SqlXmlCommandType .Sql</span><span class="sxs-lookup"><span data-stu-id="601e0-187">SqlXmlCommandType.Sql</span></span>|<span data-ttu-id="601e0-188">執行 SQL 命令 (例如，`SELECT * FROM Employees FOR XML AUTO`)。</span><span class="sxs-lookup"><span data-stu-id="601e0-188">Executes an SQL command (for example, `SELECT * FROM Employees FOR XML AUTO`).</span></span>|  
|<span data-ttu-id="601e0-189">SqlXmlCommandType XPath</span><span class="sxs-lookup"><span data-stu-id="601e0-189">SqlXmlCommandType.XPath</span></span>|<span data-ttu-id="601e0-190">執行 XPath 命令 (例如，`Employees[@EmployeeID=1]`)。</span><span class="sxs-lookup"><span data-stu-id="601e0-190">Executes an XPath command (for example, `Employees[@EmployeeID=1]`).</span></span>|  
|<span data-ttu-id="601e0-191">SqlXmlCommandType 範本</span><span class="sxs-lookup"><span data-stu-id="601e0-191">SqlXmlCommandType.Template</span></span>|<span data-ttu-id="601e0-192">執行 XML 範本。</span><span class="sxs-lookup"><span data-stu-id="601e0-192">Executes an XML template.</span></span>|  
|<span data-ttu-id="601e0-193">SqlXmlCommandType. TemplateFile</span><span class="sxs-lookup"><span data-stu-id="601e0-193">SqlXmlCommandType.TemplateFile</span></span>|<span data-ttu-id="601e0-194">在指定的路徑上執行範本檔案。</span><span class="sxs-lookup"><span data-stu-id="601e0-194">Executes a template file at the specified path.</span></span>|  
|<span data-ttu-id="601e0-195">SqlXmlCommandType. UpdateGram</span><span class="sxs-lookup"><span data-stu-id="601e0-195">SqlXmlCommandType.UpdateGram</span></span>|<span data-ttu-id="601e0-196">執行 Updategram。</span><span class="sxs-lookup"><span data-stu-id="601e0-196">Executes an updategram.</span></span>|  
|<span data-ttu-id="601e0-197">SqlXmlCommandType. Diffgram</span><span class="sxs-lookup"><span data-stu-id="601e0-197">SqlXmlCommandType.Diffgram</span></span>|<span data-ttu-id="601e0-198">執行 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="601e0-198">Executes a DiffGram.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="601e0-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="601e0-199">See Also</span></span>  
 <span data-ttu-id="601e0-200">[SqlXmlParameter 物件 &#40;SQLXML Managed 類別&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md) </span><span class="sxs-lookup"><span data-stu-id="601e0-200">[SqlXmlParameter Object &#40;SQLXML Managed Classes&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md) </span></span>  
 [<span data-ttu-id="601e0-201">SqlXmlAdapter 物件 &#40;SQLXML Managed 類別&#41;</span><span class="sxs-lookup"><span data-stu-id="601e0-201">SqlXmlAdapter Object &#40;SQLXML Managed Classes&#41;</span></span>](sqlxml-managed-classes-sqlxmladapter-object.md)  
  
  
