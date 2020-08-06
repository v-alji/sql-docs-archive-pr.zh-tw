---
title: 快取轉換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.cachetrans.f1
helpviewer_keywords:
- Cache transform
ms.assetid: a5683fc8-9c32-4634-819e-e9815627e4f1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 34be3252a3caf344c95e13ae45cc485a8c4ffdc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597248"
---
# <a name="cache-transform"></a><span data-ttu-id="af4a9-102">快取轉換</span><span class="sxs-lookup"><span data-stu-id="af4a9-102">Cache Transform</span></span>
  <span data-ttu-id="af4a9-103">「快取轉換」轉換會藉由將資料從資料流程中連接的資料來源寫入至快取連接管理員的方式，產生「查閱轉換」的參考資料集。</span><span class="sxs-lookup"><span data-stu-id="af4a9-103">The Cache Transform transformation generates a reference dataset for the Lookup Transformation by writing data from a connected data source in the data flow to a Cache connection manager.</span></span> <span data-ttu-id="af4a9-104">「查閱轉換」會藉由聯結已連接資料來源輸入資料行中的資料與參考資料庫中的資料行來執行查閱。</span><span class="sxs-lookup"><span data-stu-id="af4a9-104">The Lookup transformation performs lookups by joining data in input columns from a connected data source with columns in the reference database.</span></span>  
  
 <span data-ttu-id="af4a9-105">當您想要設定「查閱轉換」以完整快取模式執行時，可以使用快取連接管理員。</span><span class="sxs-lookup"><span data-stu-id="af4a9-105">You can use the Cache connection manager when you want to configure the Lookup Transformation to run in the full cache mode.</span></span> <span data-ttu-id="af4a9-106">在這個模式中，參考資料集會在「查閱轉換」執行之前載入快取中。</span><span class="sxs-lookup"><span data-stu-id="af4a9-106">In this mode, the reference dataset is loaded into cache before the Lookup Transformation runs.</span></span>  
  
 <span data-ttu-id="af4a9-107">如需如何透過快取連線管理員和「快取轉換」轉換設定完整快取模式中「查閱轉換」的指示，請參閱 [使用快取連線管理員以完整快取模式實作查閱轉換](../../connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="af4a9-107">For instructions on how to configure the Lookup transformation in full cache mode with the Cache connection manager and Cache Transform transformation, see [Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](../../connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="af4a9-108">如需快取參考資料集的詳細資訊，請參閱 [查閱轉換](lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="af4a9-108">For more information on caching the reference dataset, see [Lookup Transformation](lookup-transformation.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af4a9-109">「快取轉換」只會將唯一的資料列寫入快取連接管理員。</span><span class="sxs-lookup"><span data-stu-id="af4a9-109">The Cache Transform writes only unique rows to the Cache connection manager.</span></span>  
  
 <span data-ttu-id="af4a9-110">在單一封裝中，只有「快取轉換」可以將資料寫入至相同的快取連接管理員。</span><span class="sxs-lookup"><span data-stu-id="af4a9-110">In a single package, only one Cache Transform can write data to the same Cache connection manager.</span></span> <span data-ttu-id="af4a9-111">如果封裝包含多個「快取轉換」，則在封裝執行時呼叫的第一個「快取轉換」會將資料寫入連接管理員。</span><span class="sxs-lookup"><span data-stu-id="af4a9-111">If the package contains multiple Cache Transforms, the first Cache Transform that is called when the package runs, writes the data to the connection manager.</span></span> <span data-ttu-id="af4a9-112">後續「快取轉換」的寫入作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="af4a9-112">The write operations of subsequent Cache Transforms fail.</span></span>  
  
 <span data-ttu-id="af4a9-113">如需詳細資訊，請參閱 [快取連線管理員](../../connection-manager/cache-connection-manager.md) 和 [快取連線管理員編輯器](../../cache-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="af4a9-113">For more information, see [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) and [Cache Connection Manager Editor](../../cache-connection-manager-editor.md).</span></span>  
  
## <a name="configuration-of-the-cache-transform"></a><span data-ttu-id="af4a9-114">快取轉換的組態</span><span class="sxs-lookup"><span data-stu-id="af4a9-114">Configuration of the Cache Transform</span></span>  
 <span data-ttu-id="af4a9-115">您可以將快取連接管理員設定為將資料儲存至快取檔案 (.caw)。</span><span class="sxs-lookup"><span data-stu-id="af4a9-115">You can configure the Cache connection manager to save the data to a cache file (.caw).</span></span>  
  
 <span data-ttu-id="af4a9-116">您可以利用下列方式設定「快取轉換」：</span><span class="sxs-lookup"><span data-stu-id="af4a9-116">You can configure the Cache Transform in the following ways:</span></span>  
  
-   <span data-ttu-id="af4a9-117">指定快取連接管理員。</span><span class="sxs-lookup"><span data-stu-id="af4a9-117">Specify the Cache connection manager.</span></span>  
  
-   <span data-ttu-id="af4a9-118">將「快取轉換」中的輸入資料行對應至快取連接管理員中的目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="af4a9-118">Map the input columns in the Cache Transform to destination columns in the Cache connection manager.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="af4a9-119">每個輸入資料行都必須對應至目的地資料行，而資料行資料類型也必須相符；</span><span class="sxs-lookup"><span data-stu-id="af4a9-119">Each input column must be mapped to a destination column, and the column data types must match.</span></span> <span data-ttu-id="af4a9-120">否則，「 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 設計師」會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="af4a9-120">Otherwise, [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Designer displays an error message.</span></span>  
  
     <span data-ttu-id="af4a9-121">您可以使用 [快取連線管理員編輯器]  修改資料行資料類型、名稱和其他資料行屬性。</span><span class="sxs-lookup"><span data-stu-id="af4a9-121">You can use the **Cache Connection Manager Editor** to modify column data types, names, and other column properties.</span></span>  
  
 <span data-ttu-id="af4a9-122">您可以透過 [ [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 設計師] 設定屬性。</span><span class="sxs-lookup"><span data-stu-id="af4a9-122">You can set properties through [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Designer.</span></span> <span data-ttu-id="af4a9-123">如需可在 [進階編輯器]  對話方塊中設定之屬性的詳細資訊，請參閱[轉換自訂屬性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="af4a9-123">For more information about the properties that you can set in the **Advanced Editor** dialog box, see [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="af4a9-124">如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="af4a9-124">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af4a9-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af4a9-125">See Also</span></span>  
 <span data-ttu-id="af4a9-126">[Integration Services 轉換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="af4a9-126">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 [<span data-ttu-id="af4a9-127">資料流程</span><span class="sxs-lookup"><span data-stu-id="af4a9-127">Data Flow</span></span>](../data-flow.md)  
  
  
