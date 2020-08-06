---
title: 表格式)  (的資料分割表示 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: b606cd63-755c-4ac0-b19b-95b5363afbdf
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6a29f273a584f3e60c6cf6458751965158cf8704
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706797"
---
# <a name="partition-representation-tabular"></a><span data-ttu-id="2ac47-102">資料分割表示法 (表格式)</span><span class="sxs-lookup"><span data-stu-id="2ac47-102">Partition Representation (Tabular)</span></span>
  <span data-ttu-id="2ac47-103">您可以基於作業目的，將資料表分割成不同的資料列子集 (結合在一起時就會構成資料表)。其中每個子集都是資料表的資料分割。</span><span class="sxs-lookup"><span data-stu-id="2ac47-103">For operational purposes, a table can be divided in different subsets of rows that when combined together form the table; each of those subsets is a partition of the table.</span></span>  
  
## <a name="partition-representation"></a><span data-ttu-id="2ac47-104">資料分割表示法</span><span class="sxs-lookup"><span data-stu-id="2ac47-104">Partition Representation</span></span>  
 <span data-ttu-id="2ac47-105">就 AMO 物件而言，資料分割表示法與 <xref:Microsoft.AnalysisServices.Partition> 之間擁有一對一對應關聯性，而且不需要其他主要 AMO 物件。</span><span class="sxs-lookup"><span data-stu-id="2ac47-105">In terms of AMO objects a partition representation has a one to one mapping relationship with <xref:Microsoft.AnalysisServices.Partition> and no other main AMO objects are required</span></span>  
  
### <a name="partition-in-amo"></a><span data-ttu-id="2ac47-106">AMO 中的資料分割</span><span class="sxs-lookup"><span data-stu-id="2ac47-106">Partition in AMO</span></span>  
 <span data-ttu-id="2ac47-107">當使用 AMO 管理資料分割時，您需要尋找可代表表格式模型資料表的量值群組，並從該處工作。</span><span class="sxs-lookup"><span data-stu-id="2ac47-107">When using AMO to manage a partition in a you need to find the measure group that represents the Tabular Model table and work from there.</span></span>  
  
 <span data-ttu-id="2ac47-108">下列程式碼片段示範如何將資料分割加入至現有的表格式模型資料表。</span><span class="sxs-lookup"><span data-stu-id="2ac47-108">The following code snippet shows how to add a partition to an existing tabular model table.</span></span>  
  
```  
  
private void AddPartition(  
                     AMO.Cube modelCube  
                  ,  AMO.DataSource newDatasource  
                  ,  string mgName  
                  ,  string newPartitionName  
                  , string partitionSelectStatement  
                  , Boolean processPartition  
             )  
{  
    mgName = mgName.Trim();  
    newPartitionName = newPartitionName.Trim();  
    partitionSelectStatement = partitionSelectStatement.Trim();  
    //Validate Input  
    if (string.IsNullOrEmpty(newPartitionName) || string.IsNullOrWhiteSpace(newPartitionName))  
    {  
        MessageBox.Show(String.Format("Partition Name cannot be empty or blank"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
  
    if (modelCube.MeasureGroups[mgName].Partitions.ContainsName(newPartitionName))  
    {  
        MessageBox.Show(String.Format("Partition Name already defined. Duplicated names are not allowed"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
  
    if (string.IsNullOrEmpty(partitionSelectStatement) || string.IsNullOrWhiteSpace(partitionSelectStatement))  
    {  
        MessageBox.Show(String.Format("Select statement cannot be empty or blank"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
  
    //Input validated  
    string partitionID = newPartitionName; //Using partition name as the ID  
    AMO.Partition currentPartition = new AMO.Partition(partitionID, partitionID);  
    currentPartition.StorageMode = AMO.StorageMode.InMemory;  
    currentPartition.ProcessingMode = AMO.ProcessingMode.Regular;  
    currentPartition.Source = new AMO.QueryBinding(newDatasource.ID, partitionSelectStatement);  
    modelCube.MeasureGroups[mgName].Partitions.Add(currentPartition);  
    try  
    {  
        modelCube.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
        if (processPartition)  
        {  
            modelCube.MeasureGroups[mgName].Partitions[partitionID].Process(AMO.ProcessType.ProcessFull);  
            MessageBox.Show(String.Format("Partition successfully processed."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
        }  
  
    }  
    catch (AMO.AmoException amoXp)  
    {  
        MessageBox.Show(String.Format("AMO exception accessing the server.\nError message: {0}", amoXp.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        return;  
    }  
    catch (Exception)  
    {  
        throw;  
    }  
}  
  
```  
  
## <a name="amo2tabular-sample"></a><span data-ttu-id="2ac47-109">AMO2Tabular 範例</span><span class="sxs-lookup"><span data-stu-id="2ac47-109">AMO2Tabular sample</span></span>  
 <span data-ttu-id="2ac47-110">不過，若要了解如何使用 AMO 建立及操作資料分割表示法，請參閱「AMO 對表格式」範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="2ac47-110">However, to have an understanding on how to use AMO to create and manipulate partition representations see the source code of the AMO to Tabular sample.</span></span> <span data-ttu-id="2ac47-111">您可以在 Codeplex 上取得範例。</span><span class="sxs-lookup"><span data-stu-id="2ac47-111">The sample is available at Codeplex.</span></span> <span data-ttu-id="2ac47-112">有關此程式碼的重要注意事項：此程式碼的提供目的只是為了支援這裡所說明的邏輯概念，不應該用於實際執行環境，也不應該用於教學以外的其他用途。</span><span class="sxs-lookup"><span data-stu-id="2ac47-112">An important note about the code: the code is provided only as a support to the logical concepts explained here and should not be used in a production environment; nor should it be used for other purpose other than the pedagogical one.</span></span>  
  
  
