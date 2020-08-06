---
title: OData 來源屬性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4fde5bb0-6d78-4ec4-8f0b-67f91c53fe99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8139f79ed595ca3e6204f96823f6bc95e6fb40df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708501"
---
# <a name="odata-source-properties"></a><span data-ttu-id="e35ef-102">OData 來源屬性</span><span class="sxs-lookup"><span data-stu-id="e35ef-102">OData Source Properties</span></span>
  <span data-ttu-id="e35ef-103">當您以滑鼠右鍵按一下資料流程中的 [OData 來源]\*\*\*\* 並按一下 [屬性]\*\*\*\* 時，您將會看到 [OData 來源]\*\*\*\* 元件的屬性出現在 [屬性]\*\*\*\* 視窗中。</span><span class="sxs-lookup"><span data-stu-id="e35ef-103">When you right-click **OData Source** in the data flow and click **Properties**, you will see properties for the **OData Source** component in the **Properties** window.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e35ef-104">屬性</span><span class="sxs-lookup"><span data-stu-id="e35ef-104">Property</span></span>|<span data-ttu-id="e35ef-105">描述</span><span class="sxs-lookup"><span data-stu-id="e35ef-105">Description</span></span>|  
|<span data-ttu-id="e35ef-106">CollectionName</span><span class="sxs-lookup"><span data-stu-id="e35ef-106">CollectionName</span></span>|<span data-ttu-id="e35ef-107">您想要從 OData 服務擷取的集合名稱。</span><span class="sxs-lookup"><span data-stu-id="e35ef-107">Name of the collection you wish to retrieve from the OData service.</span></span> <span data-ttu-id="e35ef-108">當 **UseResourcePath** 為 False 時，便會使用 **CollectionName** 屬性。</span><span class="sxs-lookup"><span data-stu-id="e35ef-108">The **CollectionName** property is used when **UseResourcePath** is False.</span></span><br /><br /> <span data-ttu-id="e35ef-109">此屬性具有運算式功能，可在執行階段設定值。</span><span class="sxs-lookup"><span data-stu-id="e35ef-109">This property is expression-able, allowing the value to be set at runtime.</span></span> <span data-ttu-id="e35ef-110">不過，如果集合的中繼資料不符合在設計階段所使用的中繼資料，將會發生驗證錯誤，導致資料流程執行失敗。</span><span class="sxs-lookup"><span data-stu-id="e35ef-110">However, if the metadata of the collection does not match the metadata that was used at design time, a validation error will occur, causing the data flow execution to fail.</span></span>|  
|<span data-ttu-id="e35ef-111">DefaultStringLength</span><span class="sxs-lookup"><span data-stu-id="e35ef-111">DefaultStringLength</span></span>|<span data-ttu-id="e35ef-112">這個值會針對沒有最大長度的字串資料行指定預設長度。</span><span class="sxs-lookup"><span data-stu-id="e35ef-112">This value specifies default length for string columns that have no max length.</span></span><br /><br /> <span data-ttu-id="e35ef-113">**預設值：** 4000</span><span class="sxs-lookup"><span data-stu-id="e35ef-113">**Default:** 4000</span></span>|  
|<span data-ttu-id="e35ef-114">查詢</span><span class="sxs-lookup"><span data-stu-id="e35ef-114">Query</span></span>|<span data-ttu-id="e35ef-115">OData 查詢參數。</span><span class="sxs-lookup"><span data-stu-id="e35ef-115">The OData query parameters.</span></span> <span data-ttu-id="e35ef-116">此屬性具有運算式功能，而且可在執行階段設定。</span><span class="sxs-lookup"><span data-stu-id="e35ef-116">This property is expression-able and can be set at runtime.</span></span>|  
|<span data-ttu-id="e35ef-117">ResourcePath</span><span class="sxs-lookup"><span data-stu-id="e35ef-117">ResourcePath</span></span>|<span data-ttu-id="e35ef-118">當您需要指定完整資源路徑時請使用這個屬性，而不要選取集合名稱。</span><span class="sxs-lookup"><span data-stu-id="e35ef-118">Use this property when you need to specify a full resource path, rather than just selecting a collection name.</span></span> <span data-ttu-id="e35ef-119">當 **UseResourcePath** 為 True 時，便會使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="e35ef-119">This property is used when **UseResourcePath** is True.</span></span>|  
|<span data-ttu-id="e35ef-120">CollectionName</span><span class="sxs-lookup"><span data-stu-id="e35ef-120">UseResourcePath</span></span>|<span data-ttu-id="e35ef-121">當設定為 True 時， **ResourcePath** 值會附加至基底 URL，以判斷 OData 摘要位置。</span><span class="sxs-lookup"><span data-stu-id="e35ef-121">When set to True, the **ResourcePath** value is appended to the base URL to determine the OData feed location.</span></span> <span data-ttu-id="e35ef-122">當設定為 False 時，便會使用 **CollectionName** 值。</span><span class="sxs-lookup"><span data-stu-id="e35ef-122">When set to False, the **CollectionName** value is used.</span></span><br /><br /> <span data-ttu-id="e35ef-123">**預設：** False</span><span class="sxs-lookup"><span data-stu-id="e35ef-123">**Default:** False</span></span>|  
  
  
