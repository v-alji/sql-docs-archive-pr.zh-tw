---
title: 透過 Reporting Services 使用外部資料集 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- DataSet objects [Reporting Services]
- data processing extensions [Reporting Services], custom DataSet objects
- custom DataSet objects [Reporting Services]
- external DataSet objects [Reporting Services]
ms.assetid: 11daa013-ec17-4760-80e3-6d84cd8d5722
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2f41ba4461386e235cefe66819318106d0e72904
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708937"
---
# <a name="using-an-external-dataset-with-reporting-services"></a><span data-ttu-id="54d46-102">透過 Reporting Services 使用外部資料集</span><span class="sxs-lookup"><span data-stu-id="54d46-102">Using an External Dataset with Reporting Services</span></span>
  <span data-ttu-id="54d46-103">**DataSet** 物件是支援 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 已中斷連線之分散式資料案例的關鍵。</span><span class="sxs-lookup"><span data-stu-id="54d46-103">The **DataSet** object is central to supporting disconnected, distributed data scenarios with [!INCLUDE[vstecado](../../../includes/vstecado-md.md)].</span></span> <span data-ttu-id="54d46-104">**DataSet** 物件是常駐記憶體的資料表示，可提供與資料來源無關的一致性關聯式程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="54d46-104">The **DataSet** object is a memory-resident representation of data that provides a consistent relational programming model regardless of the data source.</span></span> <span data-ttu-id="54d46-105">它可與多個不同的資料來源一起使用、與 XML 資料一起使用，或管理應用程式的本機資料。</span><span class="sxs-lookup"><span data-stu-id="54d46-105">It can be used with multiple different data sources, with XML data, or to manage data local to the application.</span></span> <span data-ttu-id="54d46-106">**DataSet** 物件表示一組完整的資料，包括相關資料表、條件約束及資料表間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="54d46-106">The **DataSet** object represents a complete set of data, including related tables, constraints, and relationships among the tables.</span></span> <span data-ttu-id="54d46-107">因為 **DataSet** 物件具有儲存和公開資料的多樣性，所以通常會在報告您的資料之前，先將該資料處理和轉換成 **DataSet** 物件。</span><span class="sxs-lookup"><span data-stu-id="54d46-107">Because of the **DataSet** object's versatility in storing and exposing data, your data may often be processed and transformed into a **DataSet** object before any reporting on that data occurs.</span></span>  
  
 <span data-ttu-id="54d46-108">透過 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組，您可以整合由外部應用程式建立的任何自訂 **DataSet** 物件。</span><span class="sxs-lookup"><span data-stu-id="54d46-108">With [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extensions, you can integrate any custom **DataSet** objects that are created by external applications.</span></span> <span data-ttu-id="54d46-109">若要完成這項動作，您可以在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中建立自訂資料處理延伸模組，以作為 **DataSet** 物件與報表伺服器之間的橋樑。</span><span class="sxs-lookup"><span data-stu-id="54d46-109">To accomplish this, you create a custom data processing extension in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] that acts like a bridge between your **DataSet** object and the report server.</span></span> <span data-ttu-id="54d46-110">大部分處理這個 **DataSet** 物件的程式碼，都是包含在您建立的 **DataReader** 類別中。</span><span class="sxs-lookup"><span data-stu-id="54d46-110">Most of the code for processing this **DataSet** object is contained in the **DataReader** class that you create.</span></span>  
  
 <span data-ttu-id="54d46-111">向報表伺服器公開 **DataSet** 物件的第一個步驟，是在可以擴展 **DataSet** 物件的 **DataReader** 類別中，為提供者實作特定方法。</span><span class="sxs-lookup"><span data-stu-id="54d46-111">The first step in exposing your **DataSet** object to the report server is to implement a provider specific method in your **DataReader** class that can populate a **DataSet** object.</span></span> <span data-ttu-id="54d46-112">下列範例示範如何使用 **DataReader** 類別中的提供者特定方法，將靜態資料載入 **DataSet** 物件。</span><span class="sxs-lookup"><span data-stu-id="54d46-112">The following example shows how to load static data into a **DataSet** object by using a provider-specific method in your **DataReader** class.</span></span>  
  
```vb  
'Private members of the DataReader class  
Private m_dataSet As System.Data.DataSet  
Private m_currentRow As Integer  
  
'Method to create a dataset  
Friend Sub CreateDataSet()  
   ' Create a dataset.  
   Dim ds As New System.Data.DataSet("myDataSet")  
   ' Create a data table.   
   Dim dt As New System.Data.DataTable("myTable")  
   ' Create a data column and set various properties.   
   Dim dc As New System.Data.DataColumn()  
   dc.DataType = System.Type.GetType("System.Decimal")  
   dc.AllowDBNull = False  
   dc.Caption = "Number"  
   dc.ColumnName = "Number"  
   dc.DefaultValue = 25  
   ' Add the column to the table.   
   dt.Columns.Add(dc)  
   ' Add 10 rows and set values.   
   Dim dr As System.Data.DataRow  
   Dim i As Integer  
   For i = 0 To 9  
      dr = dt.NewRow()  
      dr("Number") = i + 1  
      ' Be sure to add the new row to the DataRowCollection.   
      dt.Rows.Add(dr)  
   Next i  
  
   ' Fill the dataset.  
   ds.Tables.Add(dt)  
  
   ' Use a private variable to store the dataset in your  
   ' DataReader.  
   m_dataSet = ds  
  
   ' Set the current row to -1.  
   m_currentRow = - 1  
End Sub 'CreateDataSet  
```  
  
```csharp  
// Private members of the DataReader class  
private System.Data.DataSet m_dataSet;  
private int m_currentRow;  
  
// Method to create a dataset  
internal void CreateDataSet()  
{  
   // Create a dataset.  
   System.Data.DataSet ds = new System.Data.DataSet("myDataSet");  
   // Create a data table.   
   System.Data.DataTable dt = new System.Data.DataTable("myTable");  
   // Create a data column and set various properties.   
   System.Data.DataColumn dc = new System.Data.DataColumn();   
   dc.DataType = System.Type.GetType("System.Decimal");   
   dc.AllowDBNull = false;   
   dc.Caption = "Number";   
   dc.ColumnName = "Number";   
   dc.DefaultValue = 25;   
   // Add the column to the table.   
   dt.Columns.Add(dc);   
   // Add 10 rows and set values.   
   System.Data.DataRow dr;   
   for(int i = 0; i < 10; i++)  
   {   
      dr = dt.NewRow();   
      dr["Number"] = i + 1;   
      // Be sure to add the new row to the DataRowCollection.   
      dt.Rows.Add(dr);  
   }  
  
   // Fill the dataset.  
   ds.Tables.Add(dt);  
  
   // Use a private variable to store the dataset in your  
   // DataReader.  
   m_dataSet = ds;  
  
   // Set the current row to -1.  
   m_currentRow = -1;  
}  
```  
  
```csharp  
public bool Read()  
{  
   m_currentRow++;  
   if (m_currentRow >= m_dataSet.Tables[0].Rows.Count)   
   {  
      return (false);  
   }   
   else   
   {  
      return (true);  
   }  
}  
  
public int FieldCount  
{  
   // Return the count of the number of columns, which in  
   // this case is the size of the column metadata  
   // array.  
   get { return m_dataSet.Tables[0].Columns.Count; }  
}  
  
public string GetName(int i)  
{  
   return m_dataSet.Tables[0].Columns[i].ColumnName;  
}  
  
public Type GetFieldType(int i)  
{  
   // Return the actual Type class for the data type.  
   return m_dataSet.Tables[0].Columns[i].DataType;  
}  
  
public Object GetValue(int i)  
{  
   return m_dataSet.Tables[0].Rows[m_currentRow][i];  
}  
  
public int GetOrdinal(string name)  
{  
   // Look for the ordinal of the column with the same name and return it.  
   // Returns -1 if not found.  
   return m_dataSet.Tables[0].Columns[name].Ordinal;  
}  
```  
  
 <span data-ttu-id="54d46-113">一旦您建立或是擷取資料集，就可以在實作 **DataReader** 類別的 **Read**、**GetValue**、**GetName**、**GetOrdinal**、**GetFieldType** 和 **FieldCount** 成員時，使用 **DataSet** 物件。</span><span class="sxs-lookup"><span data-stu-id="54d46-113">Once you create or retrieve your dataset, you can use the **DataSet** object in your implementations of the **Read**, **GetValue**, **GetName**, **GetOrdinal**, **GetFieldType**, and **FieldCount** members of the **DataReader** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54d46-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54d46-114">See Also</span></span>  
 <span data-ttu-id="54d46-115">[Reporting Services 延伸模組](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="54d46-115">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="54d46-116">[實作資料處理延伸模組](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="54d46-116">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="54d46-117">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="54d46-117">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
