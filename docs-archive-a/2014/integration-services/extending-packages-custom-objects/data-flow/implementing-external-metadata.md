---
title: 實作外部中繼資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnected validation [Integration Services]
- connected validation [Integration Services]
- custom data flow components [Integration Services], validating
- validation [Integration Services], components
- metadata [Integration Services]
- data flow components [Integration Services], validating
- data flow components [Integration Services], external metadata
- custom data flow components [Integration Services], external metadata
- external metadata [Integration Services]
ms.assetid: 8f5bd3ed-3e79-43a4-b6c1-435e4c2cc8cc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a6b77229c528bc08057e662a4b3761d1daf732f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688065"
---
# <a name="implementing-external-metadata"></a><span data-ttu-id="1618e-102">實作外部中繼資料</span><span class="sxs-lookup"><span data-stu-id="1618e-102">Implementing External Metadata</span></span>
  <span data-ttu-id="1618e-103">當元件從資料來源中斷連接時，可以使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100> 介面，針對其外部資料來源的資料行，驗證輸入及輸出資料行集合中的資料行。</span><span class="sxs-lookup"><span data-stu-id="1618e-103">When a component is disconnected from its data source, you can validate the columns in the input and output column collections against the columns at its external data source by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100> interface.</span></span> <span data-ttu-id="1618e-104">這個介面可讓您維護在外部資料來源的資料行快照，並將這些資料行對應到元件的輸入和輸出資料行集合中的資料行。</span><span class="sxs-lookup"><span data-stu-id="1618e-104">This interface lets you maintain a snapshot of the columns at the external data source and map these columns to the columns in the input and output column collection of the component.</span></span>  
  
 <span data-ttu-id="1618e-105">實作外部中繼資料行會增加元件開發的負擔與複雜性，因為您必須維護和驗證其他的資料行集合，但是能夠避免因驗證而往返於伺服器的昂貴成本，因此這個開發工作仍是非常值得的。</span><span class="sxs-lookup"><span data-stu-id="1618e-105">Implementing external metadata columns adds a layer of overhead and complexity to component development, because you must maintain and validate against an additional column collection, but the ability to avoid expensive round trips to the server for validation may make this development work worthwhile.</span></span>  
  
## <a name="populating-external-metadata-columns"></a><span data-ttu-id="1618e-106">擴展外部中繼資料行</span><span class="sxs-lookup"><span data-stu-id="1618e-106">Populating External Metadata Columns</span></span>  
 <span data-ttu-id="1618e-107">外部中繼資料行通常會在建立對應的輸入或輸出資料行時加入集合。</span><span class="sxs-lookup"><span data-stu-id="1618e-107">External metadata columns are typically added to the collection when the corresponding input or output column is created.</span></span> <span data-ttu-id="1618e-108">新資料行是透過呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.New%2A> 方法來建立。</span><span class="sxs-lookup"><span data-stu-id="1618e-108">New columns are created by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.New%2A> method.</span></span> <span data-ttu-id="1618e-109">接著會設定資料行的屬性以符合外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="1618e-109">The properties of the column are then set to match the external data source.</span></span>  
  
 <span data-ttu-id="1618e-110">外部中繼資料行是透過將外部中繼資料行的識別碼指派到輸入或輸出資料行的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> 屬性，以對應至相對應的輸入或輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="1618e-110">The external metadata column is mapped to the corresponding input or output column by assigning the ID of the external metadata column to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> property of the input or output column.</span></span> <span data-ttu-id="1618e-111">這可讓您透過使用集合的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.GetObjectByID%2A> 方法，輕易地找到特定輸入或輸出資料行的外部中繼資料行。</span><span class="sxs-lookup"><span data-stu-id="1618e-111">This lets you locate the external metadata column easily for a specific input or output column by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.GetObjectByID%2A> method of the collection.</span></span>  
  
 <span data-ttu-id="1618e-112">下列範例顯示如何建立外部中繼資料行，然後透過設定 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> 屬性將資料行對應至輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="1618e-112">The following example shows how to create an external metadata column and then map the column to an output column by setting the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> property.</span></span>  
  
```csharp  
public void CreateExternalMetaDataColumn(IDTSOutput100 output, int outputColumnID )  
{  
    IDTSOutputColumn100 oColumn = output.OutputColumnCollection.GetObjectByID(outputColumnID);  
    IDTSExternalMetadataColumn100 eColumn = output.ExternalMetadataColumnCollection.New();  
  
    eColumn.DataType = oColumn.DataType;  
    eColumn.Precision = oColumn.Precision;  
    eColumn.Scale = oColumn.Scale;  
    eColumn.Length = oColumn.Length;  
    eColumn.CodePage = oColumn.CodePage;  
  
    oColumn.ExternalMetadataColumnID = eColumn.ID;  
}  
```  
  
```vb  
Public Sub CreateExternalMetaDataColumn(ByVal output As IDTSOutput100, ByVal outputColumnID As Integer)   
 Dim oColumn As IDTSOutputColumn100 = output.OutputColumnCollection.GetObjectByID(outputColumnID)   
 Dim eColumn As IDTSExternalMetadataColumn100 = output.ExternalMetadataColumnCollection.New   
 eColumn.DataType = oColumn.DataType   
 eColumn.Precision = oColumn.Precision   
 eColumn.Scale = oColumn.Scale   
 eColumn.Length = oColumn.Length   
 eColumn.CodePage = oColumn.CodePage   
 oColumn.ExternalMetadataColumnID = eColumn.ID   
End Sub  
```  
  
## <a name="validating-with-external-metadata-columns"></a><span data-ttu-id="1618e-113">驗證外部中繼資料行</span><span class="sxs-lookup"><span data-stu-id="1618e-113">Validating with External Metadata Columns</span></span>  
 <span data-ttu-id="1618e-114">對於維護外部中繼資料行集合的元件，驗證將需要額外的步驟，因為您必須針對其他的資料行集合來驗證。</span><span class="sxs-lookup"><span data-stu-id="1618e-114">Validation requires additional steps for components that maintain an external metadata column collection, because you must validate against an additional collection of columns.</span></span> <span data-ttu-id="1618e-115">驗證可以分成連接式驗證或中斷連接式驗證。</span><span class="sxs-lookup"><span data-stu-id="1618e-115">Validation can be divided into connected validation or disconnected validation.</span></span>  
  
### <a name="connected-validation"></a><span data-ttu-id="1618e-116">連接式驗證</span><span class="sxs-lookup"><span data-stu-id="1618e-116">Connected Validation</span></span>  
 <span data-ttu-id="1618e-117">當元件連接至外部資料來源時，會直接針對外部資料來源，驗證輸入或輸出集合中的資料行。</span><span class="sxs-lookup"><span data-stu-id="1618e-117">When a component is connected to an external data source, the columns in the input or output collections are verified directly against the external data source.</span></span> <span data-ttu-id="1618e-118">此外，也必須驗證外部中繼資料集合中的資料行。</span><span class="sxs-lookup"><span data-stu-id="1618e-118">Additionally, the columns in the external metadata collection must be validated.</span></span> <span data-ttu-id="1618e-119">這是必要的，因為透過使用 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中的 [進階編輯器] 即可修改外部中繼資料集合，而且對集合的變更是無法偵測的。</span><span class="sxs-lookup"><span data-stu-id="1618e-119">This is required because the external metadata collection can be modified by using the **Advanced Editor** in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], and changes made to the collection are not detectable.</span></span> <span data-ttu-id="1618e-120">因此，在連接時，元件必須確定外部中繼資料資料行集合中的資料行會持續反映外部資料來源的資料行。</span><span class="sxs-lookup"><span data-stu-id="1618e-120">Therefore, when connected, components must make sure that the columns in the external metadata column collection continue to reflect the columns at the external data source.</span></span>  
  
 <span data-ttu-id="1618e-121">您可以將集合的屬性設定為，以選擇隱藏**進階編輯器**中的外部元資料集合 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.IsUsed%2A> `false` 。</span><span class="sxs-lookup"><span data-stu-id="1618e-121">You may choose to hide the external metadata collection in the **Advanced Editor** by setting the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.IsUsed%2A> property of the collection to `false`.</span></span> <span data-ttu-id="1618e-122">然而這也可能會隱藏編輯器的 [資料行對應]  索引標籤，它可讓使用者從輸入或輸出集合將資料行對應到外部中繼資料行集合中的資料行。</span><span class="sxs-lookup"><span data-stu-id="1618e-122">However this also hides the **Column Mapping** tab of the editor, which lets users map columns from the input or output collection to the columns in the external metadata column collection.</span></span> <span data-ttu-id="1618e-123">將此屬性設定為 `false` 並不會防止開發人員以程式設計方式修改集合，但是確實可以為專用於 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 的元件之外部中繼資料行集合提供一層保護。</span><span class="sxs-lookup"><span data-stu-id="1618e-123">Setting this property to `false` does not prevent developers from programmatically modifying the collection, but it does provide a level of protection for the external metadata column collection of a component that is used exclusively in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="disconnected-validation"></a><span data-ttu-id="1618e-124">中斷連接式驗證</span><span class="sxs-lookup"><span data-stu-id="1618e-124">Disconnected Validation</span></span>  
 <span data-ttu-id="1618e-125">當元件和外部資料來源中斷連接時，因為輸入或輸出集合中的資料行會直接針對外部中繼資料集合中的資料行 (而非針對外部來源) 進行驗證，驗證就較為簡單。</span><span class="sxs-lookup"><span data-stu-id="1618e-125">When a component is disconnected from an external data source, validation is simplified because the columns in the input or output collection are verified directly against the columns in the external metadata collection and not against the external source.</span></span> <span data-ttu-id="1618e-126">當元件連至其外部資料來源的連接尚未建立時，或是當 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> 屬性為 `false` 時，元件應該執行中斷連接式驗證。</span><span class="sxs-lookup"><span data-stu-id="1618e-126">A component should perform disconnected validation when the connection to its external data source has not been established, or when the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> property is `false`.</span></span>  
  
 <span data-ttu-id="1618e-127">下列程式碼範例示範元件的實作，以針對其外部中繼資料行集合執行驗證。</span><span class="sxs-lookup"><span data-stu-id="1618e-127">The following code example demonstrates an implementation of a component that performs validation against its external metadata column collection.</span></span>  
  
```csharp  
public override DTSValidationStatus Validate()  
{  
    if( this.isConnected && ComponentMetaData.ValidateExternalMetaData )  
    {  
        // TODO: Perform connected validation.  
    }  
    else  
    {  
        // TODO: Perform disconnected validation.  
    }  
}  
```  
  
```vb  
Public  Overrides Function Validate() As DTSValidationStatus   
 If Me.isConnected AndAlso ComponentMetaData.ValidateExternalMetaData Then   
  ' TODO: Perform connected validation.  
 Else   
  ' TODO: Perform disconnected validation.  
 End If   
End Function  
```  
  
<span data-ttu-id="1618e-128">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="1618e-128">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1618e-129">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="1618e-129">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1618e-130">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="1618e-130">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1618e-131">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="1618e-131">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1618e-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1618e-132">See Also</span></span>  
 [<span data-ttu-id="1618e-133">資料流程</span><span class="sxs-lookup"><span data-stu-id="1618e-133">Data Flow</span></span>](../../data-flow/data-flow.md)  
  
  
