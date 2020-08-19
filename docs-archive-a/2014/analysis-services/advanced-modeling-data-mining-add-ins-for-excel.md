---
title: 適用于 Excel) 的 Advanced 模型 (資料採礦增益集 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures, creating
ms.assetid: 042270a3-6ec7-4b52-b2ba-2adb6c4740d5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 771eb6111765b558995ee3b0eb98196c63951567
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593239"
---
# <a name="advanced-modeling-data-mining-add-ins-for-excel"></a>進階模型 (適用於 Excel 的資料採礦增益集)
  您可以使用 [ **先進** 的資料模型化] 選項來建立自訂資料採礦結構和模型，其參數與嚮導所建立的參數不同。 本章節描述的兩個精靈可幫助您建立全新的資料採礦結構，以及要套用到現有資料採礦結構的新採礦模型。  
  
## <a name="create-mining-structure"></a>建立採礦結構  
 ![資料採礦功能區中的建立採礦結構按鈕](media/dmc-createstruct.gif "資料採礦功能區中的建立採礦結構按鈕")  
  
 [ **建立採礦結構] Wizard** 可協助您建立新的資料採礦結構。 結構就是擷取自指定之資料來源的資料集合。  採礦結構可以使用來源的新資料來更新，但是當您建立採礦結構時，就會定義資料類型和名稱，而這些資訊會定義資料用於分析的方式。  
  
 您可以使用下列資料來源來建立結構：Excel 資料表、Excel 範圍，或是外部資料來源中已經定義為 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料來源檢視的任何資料。  
  
 對於每一個結構而言，您可以選擇將某些資料擱在一邊，以便將這些資料用於測試和驗證。 藉由在設定資料來源時建立此 *維持資料集* ，您可以確保以結構為基礎的所有模型都可以使用一致的資料集進行測試。  
  
 在建立採礦結構之後，您可以加入多個模型以套用不同的分析方法。  
  
 如需有關如何使用 [ **建立採礦結構] Wizard**的詳細資訊，請參閱 [&#40;SQL Server 資料採礦增益集建立採礦結構&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)。  
  
## <a name="add-model-to-structure"></a>將模型加入結構  
 ![將模型加入到結構按鈕中](media/dmc-addmodel.gif "將模型加入到結構按鈕中")  
  
 當您將新模型加入結構時，可使用不同演算法或不同參數來分析資料。 如果您想要使用資料採礦用戶端工具中未公開的其中一種演算法來建立模型，這個選項就特別有用。  
  
 例如，您可以使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 支援的任何演算法，包括：  
  
-   線性迴歸  
  
-   時序群集  
  
-   巢狀資料集的關聯分析  
  
 若要查看有何種可用的採礦結構，您可以 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 按一下 [ **管理模型** ] 或 **[流覽]** 來流覽中儲存的模型和結構。  
  
 但是，僅限於在目前工作階段期間建立的資料採礦結構，或是已儲存至 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的採礦結構。  
  
 如需詳細資訊，請參閱 [將模型加入結構 &#40;適用于 Excel 的資料採礦增益集&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)。  
  
## <a name="see-also"></a>另請參閱  
 [&#40;SQL Server 資料採礦增益集來管理模型&#41;](manage-models-sql-server-data-mining-add-ins.md)   
 [在 Excel 中流覽模型 &#40;SQL Server 資料採礦增益集&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
