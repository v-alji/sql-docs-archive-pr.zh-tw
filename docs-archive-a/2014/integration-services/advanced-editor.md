---
title: 進階編輯器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.advancededitor.columnmappings.f1
- sql12.dts.designer.advancededitor.inputcolumns.f1
- sql12.dts.designer.advancededitor.columnproperties.f1
- sql12.dts.designer.advancededitor.componentproperties.f1
- sql12.dts.designer.advancededitor.connections.f1
ms.assetid: 5ad0ac71-fa8b-4c26-bd42-e6ef00c87571
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f4897f2589acdeb93efecbdf9aacde07d21ca42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593535"
---
# <a name="advanced-editor"></a><span data-ttu-id="e5fac-102">進階編輯器</span><span class="sxs-lookup"><span data-stu-id="e5fac-102">Advanced Editor</span></span>
  <span data-ttu-id="e5fac-103">使用 **[進階編輯器]** 對話方塊設定所選取之 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="e5fac-103">Use the **Advanced Editor** dialog box to configure to configure properties for the selected [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="e5fac-104">具有可設定屬性的大多數 **物件，都可以使用** [進階編輯器] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e5fac-104">The **Advanced Editor** is available for most [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] objects that have configurable properties.</span></span> <span data-ttu-id="e5fac-105">針對未公開自訂使用者介面的物件，這是唯一可用的編輯器。</span><span class="sxs-lookup"><span data-stu-id="e5fac-105">It is the only editor available for those objects that do not expose a custom user interface.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="e5fac-106">資料流程物件具有可以在元件層級、輸入和輸出層級，以及輸入和輸出資料行層級設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="e5fac-106">data flow objects have properties that can be set at the component level, the input and output level, and the input and output column level.</span></span> <span data-ttu-id="e5fac-107">**[進階編輯器]** 會列舉所選取物件的所有通用及自訂屬性，並在下列 5 個索引標籤中最多 4 個索引標籤上顯示：</span><span class="sxs-lookup"><span data-stu-id="e5fac-107">The **Advanced Editor** enumerates all the common and custom properties of the selected object and displays them on up to four of the following five tabs as applicable:</span></span>  
  
-   <span data-ttu-id="e5fac-108">**連線管理員** -- 此索引標籤可用於設定連接屬性</span><span class="sxs-lookup"><span data-stu-id="e5fac-108">**Connection Managers** -- use this tab to set connection properties</span></span>  
  
-   <span data-ttu-id="e5fac-109">**元件屬性** -- 此索引標籤可用於設定元件層級屬性</span><span class="sxs-lookup"><span data-stu-id="e5fac-109">**Component Properties** -- use this tab to set component-level properties</span></span>  
  
-   <span data-ttu-id="e5fac-110">**資料行對應** -- 此索引標籤可用於將可用的資料行對應為輸出資料行</span><span class="sxs-lookup"><span data-stu-id="e5fac-110">**Column Mappings** -- use this tab to map available columns as output columns</span></span>  
  
-   <span data-ttu-id="e5fac-111">**輸入資料行** -- 此索引標籤可用於選取輸入資料行</span><span class="sxs-lookup"><span data-stu-id="e5fac-111">**Input Columns** -- use this tab to select input columns</span></span>  
  
-   <span data-ttu-id="e5fac-112">**輸入與輸出屬性** -- 此索引標籤可用於設定輸入與輸出屬性，並可加入及移除輸出、選取或移除輸入與輸出的資料行，以及設定輸入與輸出的屬性</span><span class="sxs-lookup"><span data-stu-id="e5fac-112">**Input and Output Properties** -- use this tab to set input and output properties; and to add and remove outputs, select or remove columns for inputs and outputs, and set properties for inputs and outputs</span></span>  
  
 <span data-ttu-id="e5fac-113">顯示的屬性會因元件而異。</span><span class="sxs-lookup"><span data-stu-id="e5fac-113">The properties displayed vary by component.</span></span> <span data-ttu-id="e5fac-114">如需有關 **[進階編輯器]** 可能顯示之屬性的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="e5fac-114">For more information on the properties that may be displayed in the **Advanced Editor**, see the following topics:</span></span>  
  
-   [<span data-ttu-id="e5fac-115">Common Properties</span><span class="sxs-lookup"><span data-stu-id="e5fac-115">Common Properties</span></span>](../../2014/integration-services/common-properties.md)  
  
-   [<span data-ttu-id="e5fac-116">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="e5fac-116">Transformation Custom Properties</span></span>](data-flow/transformations/transformation-custom-properties.md)  
  
-   [<span data-ttu-id="e5fac-117">路徑屬性</span><span class="sxs-lookup"><span data-stu-id="e5fac-117">Path Properties</span></span>](../../2014/integration-services/path-properties.md)  
  
 <span data-ttu-id="e5fac-118">如需有關正在編輯之特定元件的詳細資訊，請參閱＜ [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 物件及概念＞文件集＜資料流程元素＞一節中的該元件描述：</span><span class="sxs-lookup"><span data-stu-id="e5fac-118">For more information about the specific component that you are editing, see the description of the component in the Data Flow Elements section of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Objects and Concepts documentation:</span></span>  
  
-   [<span data-ttu-id="e5fac-119">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="e5fac-119">Integration Services Transformations</span></span>](data-flow/transformations/integration-services-transformations.md)  
  
## <a name="see-also"></a><span data-ttu-id="e5fac-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5fac-120">See Also</span></span>  
 [<span data-ttu-id="e5fac-121">Integration Services 錯誤和訊息參考</span><span class="sxs-lookup"><span data-stu-id="e5fac-121">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
