---
title: 合併 (XMLA) 的資料分割 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- merging partitions [XMLA]
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
ms.assetid: 657e1d4d-6d50-40f8-a771-7b20c9d865f8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 65840066d3e95571db511a2015a1bee64aa8d922
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594764"
---
# <a name="merging-partitions-xmla"></a><span data-ttu-id="42b76-102">合併資料分割 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="42b76-102">Merging Partitions (XMLA)</span></span>
  <span data-ttu-id="42b76-103">如果資料分割具有相同的匯總設計與結構，您可以使用 XML for Analysis (XMLA) 中的[MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla)命令來合併資料分割。</span><span class="sxs-lookup"><span data-stu-id="42b76-103">If partitions have the same aggregation design and structure, you can merge the partition by using the [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) command in XML for Analysis (XMLA).</span></span> <span data-ttu-id="42b76-104">合併資料分割是管理資料分割時要執行的一項重要的動作，特別是那些包含依日期分割的歷程記錄資料之資料分割。</span><span class="sxs-lookup"><span data-stu-id="42b76-104">Merging partitions is an important action to perform when you manage partitions, especially those partitions that contain historical data partitioned by date.</span></span>  
  
 <span data-ttu-id="42b76-105">例如，財務 Cube 可能使用兩個資料分割：</span><span class="sxs-lookup"><span data-stu-id="42b76-105">For example, a financial cube may use two partitions:</span></span>  
  
-   <span data-ttu-id="42b76-106">一個資料分割代表今年的財務資料，基於效能目的使用即時關聯式 OLAP (ROLAP) 儲存設定。</span><span class="sxs-lookup"><span data-stu-id="42b76-106">One partition represents financial data for the current year, using real-time relational OLAP (ROLAP) storage settings for performance.</span></span>  
  
-   <span data-ttu-id="42b76-107">另一個資料分割包含往年的財務資料，基於儲存目的使用多維度 OLAP (MOLAP) 儲存設定。</span><span class="sxs-lookup"><span data-stu-id="42b76-107">Another partition contains financial data for previous years, using multidimensional OLAP (MOLAP) storage settings for storage.</span></span>  
  
 <span data-ttu-id="42b76-108">兩個資料分割使用不同的儲存設定，但是使用相同的彙總設計。</span><span class="sxs-lookup"><span data-stu-id="42b76-108">Both partitions use different storage settings, but use the same aggregation design.</span></span> <span data-ttu-id="42b76-109">您不需要在年底時處理跨多年歷程記錄資料的 Cube，只要改用 `MergePartitions` 命令將今年的資料分割合併到往年的資料分割中。</span><span class="sxs-lookup"><span data-stu-id="42b76-109">Instead of processing the cube across years of historical data at the end of the year, you can instead use the `MergePartitions` command to merge the partition for the current year into the partition for previous years.</span></span> <span data-ttu-id="42b76-110">如此便可保存資料，而不需要將時間耗費在 Cube 的完整處理上。</span><span class="sxs-lookup"><span data-stu-id="42b76-110">This preserves the aggregation data without requiring a potentially time-consuming full processing of the cube.</span></span>  
  
## <a name="specifying-partitions-to-merge"></a><span data-ttu-id="42b76-111">指定要合併的資料分割</span><span class="sxs-lookup"><span data-stu-id="42b76-111">Specifying Partitions to Merge</span></span>  
 <span data-ttu-id="42b76-112">當 `MergePartitions` 命令執行時，會將儲存在[source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)屬性中指定之來源分割區的匯總資料，加入[目標](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla)屬性中指定的目標資料分割。</span><span class="sxs-lookup"><span data-stu-id="42b76-112">When the `MergePartitions` command runs, the aggregation data stored in the source partitions specified in the [Source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) property is added to the target partition specified in the [Target](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="42b76-113">`Source` 屬性可包含一個以上的資料分割物件參考。</span><span class="sxs-lookup"><span data-stu-id="42b76-113">The `Source` property can contain more than one partition object reference.</span></span> <span data-ttu-id="42b76-114">不過，`Target` 屬性則不可以。</span><span class="sxs-lookup"><span data-stu-id="42b76-114">However, the `Target` property cannot.</span></span>  
  
 <span data-ttu-id="42b76-115">為了能夠成功合併，在 `Source` 與 `Target` 中指定的資料分割，必須由相同的量值群組包含，並使用相同的彙總設計。</span><span class="sxs-lookup"><span data-stu-id="42b76-115">To be successfully merged, the partitions specified in both the `Source` and `Target` must be contained by the same measure group and use the same aggregation design.</span></span> <span data-ttu-id="42b76-116">否則，系統將發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="42b76-116">Otherwise, an error occurs.</span></span>  
  
 <span data-ttu-id="42b76-117">在 `Source` 中指定的資料分割會在 `MergePartitions` 命令成功完成後刪除。</span><span class="sxs-lookup"><span data-stu-id="42b76-117">The partitions specified in the `Source` are deleted after the `MergePartitions` command is successfully completed.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="42b76-118">範例</span><span class="sxs-lookup"><span data-stu-id="42b76-118">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="42b76-119">描述</span><span class="sxs-lookup"><span data-stu-id="42b76-119">Description</span></span>  
 <span data-ttu-id="42b76-120">下列範例會將「**艾德工作」 DW**範例資料庫**中 [** **Customer** count] 量值群組內的所有資料分割，合併 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 到**Customers_2004**的資料分割中。</span><span class="sxs-lookup"><span data-stu-id="42b76-120">The following example merges all the partitions in the **Customer Counts** measure group of the **Adventure Works** cube in the **Adventure Works DW** sample [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database into the **Customers_2004** partition.</span></span>  
  
### <a name="code"></a><span data-ttu-id="42b76-121">程式碼</span><span class="sxs-lookup"><span data-stu-id="42b76-121">Code</span></span>  
  
```  
<MergePartitions xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2001</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2002</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2003</PartitionID>  
    </Source>  
  </Sources>  
  <Target>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2004</PartitionID>  
  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a><span data-ttu-id="42b76-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42b76-122">See Also</span></span>  
 [<span data-ttu-id="42b76-123">在 Analysis Services 中使用 XMLA 進行開發</span><span class="sxs-lookup"><span data-stu-id="42b76-123">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
