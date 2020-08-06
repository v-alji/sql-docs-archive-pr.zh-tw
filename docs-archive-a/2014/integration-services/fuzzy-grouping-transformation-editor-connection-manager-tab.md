---
title: '[模糊群組轉換編輯器] ([連接管理員] 索引標籤) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.connection.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 47b1446d-5331-473c-9cb5-a98b1f55bf5f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b2a8b0af9f36fdd386f7da375184fd4e4ec5c4be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599064"
---
# <a name="fuzzy-grouping-transformation-editor-connection-manager-tab"></a><span data-ttu-id="f857c-102">模糊群組轉換編輯器 (連接管理員索引標籤)</span><span class="sxs-lookup"><span data-stu-id="f857c-102">Fuzzy Grouping Transformation Editor (Connection Manager Tab)</span></span>
  <span data-ttu-id="f857c-103">使用 **[模糊群組轉換編輯器]** 對話方塊的 **[連接管理員]** 索引標籤，來選取現有的連接或建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="f857c-103">Use the **Connection Manager** tab of the **Fuzzy Grouping Transformation Editor** dialog box to select an existing connection or create a new one.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f857c-104">連接所指定的伺服器必須正在執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f857c-104">The server specified by the connection must be running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f857c-105">模糊群組轉換會在 tempdb 中建立暫存資料物件，而這個物件可能會與轉換的完整輸出一樣大。</span><span class="sxs-lookup"><span data-stu-id="f857c-105">The Fuzzy Grouping transformation creates temporary data objects in tempdb that may be as large as the full input to the transformation.</span></span> <span data-ttu-id="f857c-106">當轉換執行時，它會對這些暫存物件發出伺服器查詢。</span><span class="sxs-lookup"><span data-stu-id="f857c-106">While the transformation executes, it issues server queries against these temporary objects.</span></span> <span data-ttu-id="f857c-107">這樣會影響伺服器的整體效能。</span><span class="sxs-lookup"><span data-stu-id="f857c-107">This can affect overall server performance.</span></span>  
  
 <span data-ttu-id="f857c-108">若要深入了解模糊群組轉換，請參閱＜ [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="f857c-108">To learn more about the Fuzzy Grouping transformation, see [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f857c-109">選項。</span><span class="sxs-lookup"><span data-stu-id="f857c-109">Options</span></span>  
 <span data-ttu-id="f857c-110">**[無快取]**</span><span class="sxs-lookup"><span data-stu-id="f857c-110">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="f857c-111">使用清單方塊來選取現有的 OLE DB 連接管理員，或使用 [新增]\*\*\*\* 按鈕來建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="f857c-111">Select an existing OLE DB connection manager by using the list box, or create a new connection by using the **New** button.</span></span>  
  
 <span data-ttu-id="f857c-112">**新增**</span><span class="sxs-lookup"><span data-stu-id="f857c-112">**New**</span></span>  
 <span data-ttu-id="f857c-113">使用 [設定 OLE DB 連接管理員]  對話方塊來建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="f857c-113">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f857c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f857c-114">See Also</span></span>  
 <span data-ttu-id="f857c-115">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f857c-115">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="f857c-116">使用模糊群組轉換來識別相似的資料列</span><span class="sxs-lookup"><span data-stu-id="f857c-116">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
