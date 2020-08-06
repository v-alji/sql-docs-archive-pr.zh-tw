---
title: 在資料流程路徑編輯器中查看路徑中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- metadata [Integration Services]
- paths [Integration Services], metadata
ms.assetid: 25cf8bdd-8691-4caa-96b6-3081b2f37dea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d84e14c2bc42ac4b831a4d1a3321d3e8b4acf6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584628"
---
# <a name="view-path-metadata-in-the-data-flow-path-editor"></a><span data-ttu-id="2f498-102">在資料流程路徑編輯器中檢視路徑中繼資料</span><span class="sxs-lookup"><span data-stu-id="2f498-102">View Path Metadata in the Data Flow Path Editor</span></span>
  <span data-ttu-id="2f498-103">路徑會連接兩個資料流程元件。</span><span class="sxs-lookup"><span data-stu-id="2f498-103">Paths connect two data flow components.</span></span> <span data-ttu-id="2f498-104">資料流程必須包含至少兩個已連接的資料流程元件，您才能檢視路徑中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2f498-104">Before you can view path metadata, the data flow must contain at least two connected data flow components.</span></span> <span data-ttu-id="2f498-105">如需詳細資訊，請參閱 [在資料流程中加入或刪除元件](data-flow/add-or-delete-a-component-in-a-data-flow.md) 和 [連接資料流程中的元件](data-flow/connect-components-in-a-data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="2f498-105">For more information, see [Add or Delete a Component in a Data Flow](data-flow/add-or-delete-a-component-in-a-data-flow.md) and [Connect Components in a Data Flow](data-flow/connect-components-in-a-data-flow.md).</span></span>  
  
### <a name="to-view-path-metadata"></a><span data-ttu-id="2f498-106">若要檢視路徑中繼資料</span><span class="sxs-lookup"><span data-stu-id="2f498-106">To view path metadata</span></span>  
  
1.  <span data-ttu-id="2f498-107">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="2f498-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="2f498-108">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="2f498-108">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="2f498-109">按一下 [資料流程]\*\*\*\* 索引標籤，然後按兩下路徑。</span><span class="sxs-lookup"><span data-stu-id="2f498-109">Click the **Data Flow** tab and double-click a path.</span></span>  
  
4.  <span data-ttu-id="2f498-110">在 **[資料流程路徑編輯器]** 對話方塊中，按一下 **[中繼資料]**。</span><span class="sxs-lookup"><span data-stu-id="2f498-110">In **Data Flow Path Editor** dialog box, click **Metadata**.</span></span>  
  
5.  <span data-ttu-id="2f498-111">檢視路徑中繼資料，包括每個資料行的資料行名稱、資料類型、有效位數、小數位數、長度、字碼頁，以及來源元件名稱。</span><span class="sxs-lookup"><span data-stu-id="2f498-111">View path metadata, including the column names, data type, precision, scale, length, code page, and the name of the source component of each column.</span></span>  
  
6.  <span data-ttu-id="2f498-112">若要複製中繼資料，請按一下 **[複製至剪貼簿]**。</span><span class="sxs-lookup"><span data-stu-id="2f498-112">To copy the metadata, click **Copy to Clipboard**.</span></span>  
  
7.  <span data-ttu-id="2f498-113">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="2f498-113">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f498-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f498-114">See Also</span></span>  
 <span data-ttu-id="2f498-115">[Integration Services 路徑](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="2f498-115">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 [<span data-ttu-id="2f498-116">資料流程</span><span class="sxs-lookup"><span data-stu-id="2f498-116">Data Flow</span></span>](data-flow/data-flow.md)  
  
  
