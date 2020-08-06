---
title: " (表格式) 的透視標記法 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 6d2636c4-dae4-448f-a1d4-dbee739e177c
author: minewiskan
ms.author: owend
ms.openlocfilehash: ca8a66d3134748fd524dc0c6b524d944213533e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594228"
---
# <a name="perspective-representation-tabular"></a><span data-ttu-id="ba0c0-102">檢視方塊表示法 (表格式)</span><span class="sxs-lookup"><span data-stu-id="ba0c0-102">Perspective Representation (Tabular)</span></span>
  <span data-ttu-id="ba0c0-103">檢視方塊是一種針對用戶端應用程式簡化或聚焦至模型之較小部分的機制。</span><span class="sxs-lookup"><span data-stu-id="ba0c0-103">A perspective is a mechanism to simplify or focus the model into a smaller portion of it for the client application.</span></span>  
  
 <span data-ttu-id="ba0c0-104">如需如何建立和操作透視圖標記法的詳細說明，請參閱[ (表格式) 的觀點標記法](perspective-representation-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="ba0c0-104">See [Perspective Representation (Tabular)](perspective-representation-tabular.md) for a detailed explanation on how to create and manipulate the perspective representation.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="ba0c0-105">檢視方塊並非安全性機制。使用者仍然可透過其他介面存取檢視方塊外部的物件。</span><span class="sxs-lookup"><span data-stu-id="ba0c0-105">Perspectives are not a security mechanism; objects outside the perspective can still be accessed by the user through other interfaces.</span></span>  
  
## <a name="perspective-representation"></a><span data-ttu-id="ba0c0-106">檢視方塊表示法</span><span class="sxs-lookup"><span data-stu-id="ba0c0-106">Perspective Representation</span></span>  
 <span data-ttu-id="ba0c0-107">就 AMO 物件而言，檢視方塊表示法與 <xref:Microsoft.AnalysisServices.Perspective> 之間擁有一對一對應關聯性，而且不需要其他主要 AMO 物件。</span><span class="sxs-lookup"><span data-stu-id="ba0c0-107">In terms of AMO objects a perspective representation has a one to one mapping relationship with <xref:Microsoft.AnalysisServices.Perspective> and no other main AMO objects are required.</span></span>  
  
### <a name="perspective-in-amo"></a><span data-ttu-id="ba0c0-108">AMO 中的檢視方塊</span><span class="sxs-lookup"><span data-stu-id="ba0c0-108">Perspective in AMO</span></span>  
 <span data-ttu-id="ba0c0-109">下列程式碼片段示範如何在表格式模型中建立檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="ba0c0-109">The following code snippet shows how to create a perspective in a Tabular model.</span></span> <span data-ttu-id="ba0c0-110">這個程式碼片段的主要元素是 perspectiveElements；這個物件是表格式模型中公開給使用者之所有物件的圖形表示法。</span><span class="sxs-lookup"><span data-stu-id="ba0c0-110">The key element in this piece of code is the perspectiveElements; this object is a graphical representation of all the objects in the tabular model that are exposed to the user.</span></span> <span data-ttu-id="ba0c0-111">*perspectiveElements*包含4個數據行，而在此案例中，只有資料行1、2和3是相關的。</span><span class="sxs-lookup"><span data-stu-id="ba0c0-111">*perspectiveElements* contains 4 columns and for this scenario only columns 1, 2 and 3 are relevant.</span></span> <span data-ttu-id="ba0c0-112">資料行 1 包含顯示之元素的類型 elementTypeValue；資料行 2 包含元素的完整名稱 (可能需要加以剖析才能進入檢視方塊中的元素)；資料行 3 包含核取方塊項目 checkedElement，此項目會分辨元素是否屬於檢視方塊的一部分。</span><span class="sxs-lookup"><span data-stu-id="ba0c0-112">Column 1 contains the type of element displayed -elementTypeValue-; column 2 contains the complete name of the element --, that probably will need to parsed to enter the element in the perspective; column 3 contains a checkbox item -checkedElement- that tells if the element is part of the perspective or not.</span></span>  
  
```  
  
private void updatePerspective_Click(  
                     AMO.Cube modelCube  
                  ,  DataGridView perspectiveElements  
                  ,  string updatedPerspectiveID  
             )  
{  
    //Update is done by delete first, create new and insert after  
    //if perspective doesn't exist then create first and insert after  
    updatedPerspectiveID = updatedPerspectiveID.Trim();  
    if (modelCube.Perspectives.Contains(updatedPerspectiveID))  
    {  
        modelCube.Perspectives.Remove(updatedPerspectiveID, true);  
        newDatabase.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
    }  
    AMO.Perspective currentPerspective = modelCube.Perspectives.Add(updatedPerspectiveID, updatedPerspectiveID);  
  
    foreach (DataGridViewRow currentDGVRow in perspectiveElements.Rows)  
    {  
        bool checkedElement = (bool)currentDGVRow.Cells[3].Value;  
        if (checkedElement)  
        {  
            string elementTypeValue = currentDGVRow.Cells[1].Value.ToString();  
            string elementNameValue = currentDGVRow.Cells[2].Value.ToString();  
            switch (elementTypeValue)  
            {  
                case "Column: Attribute":  
                case "Column: Calculated Column":  
                    {  
                        string perspectiveDimensionName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string perspectiveDimensionAttributeName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        AMO.PerspectiveDimension currentPerspectiveDimension;  
                        if (!currentPerspective.Dimensions.Contains(perspectiveDimensionName))  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions.Add(perspectiveDimensionName);  
                        }  
                        else  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions[perspectiveDimensionName];  
                        }  
                        if (!currentPerspectiveDimension.Attributes.Contains(perspectiveDimensionAttributeName))  
                        {  
                            currentPerspectiveDimension.Attributes.Add(perspectiveDimensionAttributeName);  
                        }  
                    }  
                    break;  
                case "Hierarchy":  
                    {  
                        string perspectiveDimensionName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string perspectiveDimensionHierarchyName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        AMO.PerspectiveDimension currentPerspectiveDimension;  
                        if (!currentPerspective.Dimensions.Contains(perspectiveDimensionName))  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions.Add(perspectiveDimensionName);  
                        }  
                        else  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions[perspectiveDimensionName];  
                        }  
                        if (!currentPerspectiveDimension.Hierarchies.Contains(perspectiveDimensionHierarchyName))  
                        {  
                            currentPerspectiveDimension.Hierarchies.Add(perspectiveDimensionHierarchyName);  
                        }  
                    }  
                    break;  
                case "Measure":  
                    {  
                        string perspectiveMeasureGroupName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string measureName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        string perspectiveMeasureName = string.Format("[Measures].[{0}]", measureName);  
                        AMO.PerspectiveCalculation currentPerspectiveCalculation = new AMO.PerspectiveCalculation(perspectiveMeasureName, AMO.PerspectiveCalculationType.Member);  
                        if (!currentPerspective.Calculations.Contains(perspectiveMeasureName))  
                        {  
                            currentPerspective.Calculations.Add(currentPerspectiveCalculation);  
                        }  
                        if (modelCube.MdxScripts["MdxScript"].CalculationProperties.Contains(string.Format("KPIs.[{0}]", measureName)))  
                        {//Current Measure is also a KPI ==> will be added to the KPIs collection of the perspective  
                            AMO.PerspectiveKpi currentPerspectiveKpi = new AMO.PerspectiveKpi(perspectiveMeasureName);  
                            if (!currentPerspective.Kpis.Contains(perspectiveMeasureName))  
                            {  
                                currentPerspective.Kpis.Add(currentPerspectiveKpi);  
                            }  
                        }  
                    }  
                    break;  
                default:  
                    break;  
            }  
        }  
    }  
  
    newDatabase.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.CreateOrReplace);  
    MessageBox.Show(String.Format("Perpective successfully updated."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
}  
  
```  
  
## <a name="amo2tabular-sample"></a><span data-ttu-id="ba0c0-113">AMO2Tabular 範例</span><span class="sxs-lookup"><span data-stu-id="ba0c0-113">AMO2Tabular sample</span></span>  
 <span data-ttu-id="ba0c0-114">不過，若要了解如何使用 AMO 建立及操作檢視方塊表示法，請參閱「AMO 對表格式」範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="ba0c0-114">However, to have an understanding on how to use AMO to create and manipulate perspective representations see the source code of the AMO to Tabular sample.</span></span> <span data-ttu-id="ba0c0-115">您可以在 Codeplex 上取得範例。</span><span class="sxs-lookup"><span data-stu-id="ba0c0-115">The sample is available at Codeplex.</span></span> <span data-ttu-id="ba0c0-116">有關此程式碼的重要注意事項：此程式碼的提供目的只是為了支援這裡所說明的邏輯概念，不應該用於實際執行環境，也不應該用於教學以外的其他用途。</span><span class="sxs-lookup"><span data-stu-id="ba0c0-116">An important note about the code: the code is provided only as a support to the logical concepts explained here and should not be used in a production environment; nor should it be used for other purpose other than the pedagogical one.</span></span>  
  
  
