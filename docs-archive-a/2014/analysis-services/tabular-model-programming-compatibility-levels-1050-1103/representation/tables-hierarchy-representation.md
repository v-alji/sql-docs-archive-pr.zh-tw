---
title: " (表格式) 的階層標記法 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 1d53dda1-f2c8-4a9b-8ec7-78f43ca1d7db
author: minewiskan
ms.author: owend
ms.openlocfilehash: 83d91be5152c4e7f1345cee8756abbe57c0016f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592888"
---
# <a name="hierarchy-representation-tabular"></a><span data-ttu-id="df39f-102">階層表示法 (表格式)</span><span class="sxs-lookup"><span data-stu-id="df39f-102">Hierarchy Representation (Tabular)</span></span>
  <span data-ttu-id="df39f-103">在表格式模型中，階層是根據使用者選取的值從一個屬性到另一個屬性的導覽路徑。</span><span class="sxs-lookup"><span data-stu-id="df39f-103">In tabular models a hierarchy is navigation path from one attribute to another based on values selected by the user.</span></span>  
  
## <a name="hierarchy-representation"></a><span data-ttu-id="df39f-104">階層表示法</span><span class="sxs-lookup"><span data-stu-id="df39f-104">Hierarchy Representation</span></span>  
  
### <a name="hierarchy-in-amo"></a><span data-ttu-id="df39f-105">AMO 中的階層</span><span class="sxs-lookup"><span data-stu-id="df39f-105">Hierarchy in AMO</span></span>  
 <span data-ttu-id="df39f-106">當您使用 AMO 管理表格式模型資料表時，物件與 AMO 中的階層會有一對一的相符關係。</span><span class="sxs-lookup"><span data-stu-id="df39f-106">When using AMO to manage a tabular model table, there is a one-to-one object match for a hierarchy in AMO.</span></span> <span data-ttu-id="df39f-107">階層是以 <xref:Microsoft.AnalysisServices.Hierarchy> 物件表示。</span><span class="sxs-lookup"><span data-stu-id="df39f-107">A hierarchy is represented by the <xref:Microsoft.AnalysisServices.Hierarchy> object.</span></span>  
  
 <span data-ttu-id="df39f-108">下列程式碼片段示範如何將階層加入至現有的表格式模型。</span><span class="sxs-lookup"><span data-stu-id="df39f-108">The following code snippet shows how to add a hierarchy to an existing tabular model.</span></span> <span data-ttu-id="df39f-109">此程式碼假設您擁有 AMO 資料庫物件 newDatabase 及 AMO Cube 物件 modelCube。</span><span class="sxs-lookup"><span data-stu-id="df39f-109">The code assumes you have an AMO database object, newDatabase, and an AMO cube object, modelCube.</span></span>  
  
```  
  
private void addHierarchy(  
                    AMO.Database newDatabase  
                 ,  AMO.Cube modelCube  
                 ,  string tableName  
                 ,  string hierarchyName  
                 ,  string levelsText  
             )  
{  
    //Validate input  
    if (string.IsNullOrEmpty(hierarchyName) || string.IsNullOrEmpty(levelsText))  
    {  
        MessageBox.Show(String.Format("Hierarchy Name or Layout must be provided."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        return;  
    }  
  
    if (!overwriteHierarchy.Checked && newDatabase.Dimensions[tableName].Hierarchies.Contains(hierarchyName))  
    {  
        MessageBox.Show(String.Format("Hierarchy already exists.\nGive a new name or enable overwriting"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        return;  
    }  
  
    try  
    {  
        if (newDatabase.Dimensions[tableName].Hierarchies.Contains(hierarchyName))  
        {  
            //Hierarchy exists... deleting it to write it later  
            newDatabase.Dimensions[tableName].Hierarchies.Remove(hierarchyName, true);  
            newDatabase.Dimensions[tableName].Update(AMO.UpdateOptions.AlterDependents);  
        }  
        AMO.Hierarchy currentHierarchy = newDatabase.Dimensions[tableName].Hierarchies.Add(hierarchyName, hierarchyName);  
        currentHierarchy.AllMemberName = string.Format("(All of {0})", hierarchyName);  
        //Parse hierarchyLayout  
        using (StringReader levels = new StringReader(levelsText))  
        {  
            //Each line:  
            //  must come with: The columnId of the attribute in the dimension --> this represents the SourceAttributeID  
            //  optional: A display name for the Level (if this argument doesn't come the default is the SourceAttributeID)  
            string line;  
            while ((line = levels.ReadLine()) != null)  
            {  
                if (string.IsNullOrEmpty(line) || string.IsNullOrWhiteSpace(line)) continue;  
                line = line.Trim();  
                string[] hierarchyData = line.Split(',');  
                if (string.IsNullOrEmpty(hierarchyData[0])) continue; //first argument cannot be empty or blank,   
                                                                      //assume is a blank line and ignore it  
                string levelSourceAttributeID = hierarchyData[0].Trim();  
                string levelID = (hierarchyData.Length > 1 && !string.IsNullOrEmpty(hierarchyData[1])) ? hierarchyData[1].Trim() : levelSourceAttributeID;  
                currentHierarchy.Levels.Add(levelID).SourceAttributeID = levelSourceAttributeID;  
            }  
        }  
        newDatabase.Dimensions[tableName].Update(AMO.UpdateOptions.AlterDependents);  
  
    }  
    catch (Exception ex)  
    {  
        MessageBox.Show(String.Format("Error creating hierarchy [{0}].\nError message: {1}", newHierarchyName.Text, ex.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        if (newDatabase.Dimensions[tableName].Hierarchies.Contains(hierarchyName))  
        {  
            //Hierarchy was created but exception prevented complete hierarchy to be written... deleting incomplete hierarchy  
            newDatabase.Dimensions[tableName].Hierarchies.Remove(hierarchyName, true);  
            newDatabase.Dimensions[tableName].Update(AMO.UpdateOptions.AlterDependents);  
        }  
  
    }  
    newDatabase.Dimensions[tableName].Process(AMO.ProcessType.ProcessFull);  
    modelCube.MeasureGroups[tableName].Process(AMO.ProcessType.ProcessFull);  
}  
  
```  
  
  
