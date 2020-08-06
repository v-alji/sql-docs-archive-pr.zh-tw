---
title: 使用 XMLA 建立資料採礦查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: 8f6b6008-006c-4792-9bd1-64c30dc3fd41
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0e85b17db0781671fab0874706f12fdac95b30b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605952"
---
# <a name="create-a-data-mining-query-by-using-xmla"></a><span data-ttu-id="79db9-102">使用 XMLA 建立資料採礦查詢</span><span class="sxs-lookup"><span data-stu-id="79db9-102">Create a Data Mining Query by Using XMLA</span></span>
  <span data-ttu-id="79db9-103">您可以使用 AMO、DMX 或 XML/A 來針對資料採礦物件建立各種查詢。</span><span class="sxs-lookup"><span data-stu-id="79db9-103">You can create a variety of queries against data mining objects by using AMO, DMX, or XML/A.</span></span>  
  
 <span data-ttu-id="79db9-104">XML 用於 Analysis Services 伺服器與所有用戶端之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="79db9-104">XML is used for communication between the Analysis Services server and all clients.</span></span> <span data-ttu-id="79db9-105">因此，雖然一般而言，使用 DMX 建立內容查詢更為容易，但是您可以使用 XML/A 中的 DISCOVER 和 COMMAND 陳述式撰寫查詢，方法是，使用支援 SOAP 通訊協定的用戶端，或在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中建立 XML/A 查詢。</span><span class="sxs-lookup"><span data-stu-id="79db9-105">Therefore, although it is generally much easier to create content queries by using DMX, you can write queries by using the DISCOVER and COMMAND statements in XML/A, either by using a client that supports the SOAP protocol, or by creating an XML/A query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="79db9-106">本主題說明如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中提供的 XML/A 範本，根據目前伺服器上所儲存的採礦模型，建立模型內容查詢。</span><span class="sxs-lookup"><span data-stu-id="79db9-106">This topic explains how to use the XML/A templates that are available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create a model content query against a mining model stored on the current server.</span></span>  
  
## <a name="querying-data-mining-schema-rowsets-by-using-xmla"></a><span data-ttu-id="79db9-107">使用 XML/A 查詢資料採礦結構描述資料列集</span><span class="sxs-lookup"><span data-stu-id="79db9-107">Querying Data Mining Schema Rowsets by Using XML/A</span></span>  
  
#### <a name="to-open-an-xmla-template"></a><span data-ttu-id="79db9-108">開啟 XML/A 範本</span><span class="sxs-lookup"><span data-stu-id="79db9-108">To open an XML/A template</span></span>  
  
1.  <span data-ttu-id="79db9-109">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 [檢視]  功能表上，按一下 [範本總管] 。</span><span class="sxs-lookup"><span data-stu-id="79db9-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="79db9-110">按一下 Cube 圖示，即可開啟 Analysis Services 範本的清單。</span><span class="sxs-lookup"><span data-stu-id="79db9-110">Click the cube icon to open the list of Analysis Services templates.</span></span>  
  
3.  <span data-ttu-id="79db9-111">在範本類別目錄的清單中，依序展開 [XMLA]\*\*\*\* 和 [結構描述資料列集]\*\*\*\*，然後按兩下 [探索結構描述資料列集]\*\*\*\*，以便在適當的程式碼編輯器中開啟範本。</span><span class="sxs-lookup"><span data-stu-id="79db9-111">In the list of template categories, expand **XMLA**, expand **Schema Rowsets**, and double-click **Discover Schema Rowsets** to open the template in the appropriate code editor.</span></span>  
  
4.  <span data-ttu-id="79db9-112">在 [連接到 Analysis Services]\*\*\*\* 對話方塊中，填妥連接資訊，再按一下 [連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="79db9-112">In the **Connect to Analysis Services** dialog box, complete the connection information and then click **Connect**.</span></span> <span data-ttu-id="79db9-113">此時會開啟一個新的查詢編輯器視窗，其中含有 [探索結構描述資料列集]\*\*\*\* 範本。</span><span class="sxs-lookup"><span data-stu-id="79db9-113">A new query editor window opens, populated with the **Discover Schema Rowsets** template.</span></span>  
  
#### <a name="to-discover-column-names-from-the-mining-model-content-schema-rowset"></a><span data-ttu-id="79db9-114">從 MINING MODEL CONTENT 結構描述資料列集探索資料行名稱</span><span class="sxs-lookup"><span data-stu-id="79db9-114">To discover column names from the MINING MODEL CONTENT schema rowset</span></span>  
  
1.  <span data-ttu-id="79db9-115">在 [探索結構描述資料列集]\*\*\*\* 範本開啟時，按一下 [執行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="79db9-115">With the **Discover Schema Rowsets** template open, click **Execute**.</span></span>  
  
     <span data-ttu-id="79db9-116">在 [結果]\*\*\*\* 窗格中會傳回結構描述資料列集的清單，其中包含目前執行個體提供之所有資料列集的資料列集名稱和資料列集資料行。</span><span class="sxs-lookup"><span data-stu-id="79db9-116">A list of schema rowsets is returned in the **Results** pane that contains the rowset names and rowset columns for all rowsets available on the current instance.</span></span>  
  
2.  <span data-ttu-id="79db9-117">在 [**查詢**] 窗格中，將游標放在後面， **\<Restriction List>** 然後按 enter 以加入新的行。</span><span class="sxs-lookup"><span data-stu-id="79db9-117">In the **Query** pane, place the cursor after **\<Restriction List>** and press ENTER to add a new line.</span></span>  
  
3.  <span data-ttu-id="79db9-118">將游標放在空白行，然後輸入\*\* \<SchemaName> DMSCHEMA_MINING_MODEL_CONTENT \</SchemaName> \*\*</span><span class="sxs-lookup"><span data-stu-id="79db9-118">Place the cursor on the blank line and type **\<SchemaName>DMSCHEMA_MINING_MODEL_CONTENT\</SchemaName>**</span></span>  
  
     <span data-ttu-id="79db9-119">完整的限制區段應顯示如下：</span><span class="sxs-lookup"><span data-stu-id="79db9-119">The complete section for restrictions should appear as follows:</span></span>  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<SchemaName>DMSCHEMA_MINING_MODEL_CONTENT</SchemaName>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
4.  <span data-ttu-id="79db9-120">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="79db9-120">Click **Execute**.</span></span>  
  
     <span data-ttu-id="79db9-121">[結果]\*\*\*\* 窗格會顯示指定之結構描述資料列集的資料行名稱清單。</span><span class="sxs-lookup"><span data-stu-id="79db9-121">The **Results** pane shows a list of column names for the specified schema rowset.</span></span>  
  
#### <a name="to-create-a-content-query-using-the-mining-model-content-schema-rowset"></a><span data-ttu-id="79db9-122">使用 MINING MODEL CONTENT 結構描述資料列集建立內容查詢</span><span class="sxs-lookup"><span data-stu-id="79db9-122">To create a content query using the MINING MODEL CONTENT schema rowset</span></span>  
  
1.  <span data-ttu-id="79db9-123">在 [探索結構描述資料列集]\*\*\*\* 範本中，取代要求類型標籤內的文字來變更要求類型。</span><span class="sxs-lookup"><span data-stu-id="79db9-123">In the **Discover Schema Rowsets** template, change the request type by replacing the text inside the request type tags.</span></span>  
  
     <span data-ttu-id="79db9-124">取代這一行：</span><span class="sxs-lookup"><span data-stu-id="79db9-124">Replace this line:</span></span>  
  
     `<RequestType>DISCOVER_SCHEMA_ROWSETS</RequestType>`  
  
     <span data-ttu-id="79db9-125">成為下列這行：</span><span class="sxs-lookup"><span data-stu-id="79db9-125">with the following line:</span></span>  
  
     <span data-ttu-id="79db9-126">**\<RequestType>DMSCHEMA_MINING_MODEL_CONTENT\</RequestType>**</span><span class="sxs-lookup"><span data-stu-id="79db9-126">**\<RequestType>DMSCHEMA_MINING_MODEL_CONTENT\</RequestType>**</span></span>  
  
2.  <span data-ttu-id="79db9-127">將新的條件加入到限制清單中，以便將限制清單變更為依名稱指定採礦模型。</span><span class="sxs-lookup"><span data-stu-id="79db9-127">Change the restriction list to specify a mining model by name, by adding a new condition to the restriction lists.</span></span>  
  
3.  <span data-ttu-id="79db9-128">在範本中，將游標放在 `<Restriction List>` 後面，然後按 ENTER 即可加入新的一行。</span><span class="sxs-lookup"><span data-stu-id="79db9-128">In the template, place the cursor after `<Restriction List>` and press ENTER to add a new line.</span></span>  
  
4.  <span data-ttu-id="79db9-129">將游標放在空行上，然後輸入 **<MODEL_NAME>My model name</MODEL_NAME>**</span><span class="sxs-lookup"><span data-stu-id="79db9-129">Place the cursor on the blank line and type **<MODEL_NAME>My model name</MODEL_NAME>**</span></span>  
  
     <span data-ttu-id="79db9-130">完整的限制區段應顯示如下：</span><span class="sxs-lookup"><span data-stu-id="79db9-130">The complete section for restrictions should appear as follows:</span></span>  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<MODEL_NAME>My model name</MODEL_NAME>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
5.  <span data-ttu-id="79db9-131">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="79db9-131">Click **Execute**.</span></span>  
  
     <span data-ttu-id="79db9-132">[結果] 窗格會顯示結構描述定義，以及指定之模型的值。</span><span class="sxs-lookup"><span data-stu-id="79db9-132">The Results pane displays the schema definition, together with the values for the specified model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79db9-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79db9-133">See Also</span></span>  
 <span data-ttu-id="79db9-134">[&#40;Analysis Services 的採礦模型內容-資料採礦&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="79db9-134">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="79db9-135">資料採礦結構描述資料列集</span><span class="sxs-lookup"><span data-stu-id="79db9-135">Data Mining Schema Rowsets</span></span>](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) 
  
  
