---
title: 剖析資料 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- parsing [Integration Services]
- data parsing [Integration Services]
ms.assetid: 8893ea9d-634c-4309-b52c-6337222dcb39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3bd34cd83351e31313ae96ff5709ec999a60f2f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593478"
---
# <a name="parsing-data"></a><span data-ttu-id="21336-102">剖析資料</span><span class="sxs-lookup"><span data-stu-id="21336-102">Parsing Data</span></span>
  <span data-ttu-id="21336-103">封裝中的資料流程會在異質資料存放區之間擷取和載入資料，這樣可以使用各種不同的標準和自訂資料類型。</span><span class="sxs-lookup"><span data-stu-id="21336-103">Data flows in packages extract and load data between heterogeneous data stores, which may use a variety of standard and custom data types.</span></span> <span data-ttu-id="21336-104">在一個資料流程中， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 來源執行擷取資料、剖析字串資料並將資料轉換為 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料類型的工作。</span><span class="sxs-lookup"><span data-stu-id="21336-104">In a data flow, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sources do the work of extracting data, parsing string data, and converting data to an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type.</span></span> <span data-ttu-id="21336-105">後續轉換可以剖析資料以便將其轉換成不同的資料類型，或者建立資料類型不同的資料行副本。</span><span class="sxs-lookup"><span data-stu-id="21336-105">Subsequent transformations may parse data to convert it to a different data type, or create column copies with different data types.</span></span> <span data-ttu-id="21336-106">元件中使用的運算式同樣可以將引數和運算元轉換成不同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="21336-106">Expressions used in components may also cast arguments and operands to different data types.</span></span> <span data-ttu-id="21336-107">最後，當資料載入資料存放區時，目的地則可以剖析資料以便將其轉換成目的地使用的資料類型。</span><span class="sxs-lookup"><span data-stu-id="21336-107">Finally, when the data is loaded into a data store, the destination may parse the data to convert it to a data type that the destination uses.</span></span> <span data-ttu-id="21336-108">如需詳細資訊，請參閱 [Integration Services 資料類型](integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="21336-108">For more information, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
## <a name="types-of-parsing"></a><span data-ttu-id="21336-109">剖析的類型</span><span class="sxs-lookup"><span data-stu-id="21336-109">Types of Parsing</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="21336-110">提供兩種用於轉換資料的剖析類型：快速剖析和標準剖析。</span><span class="sxs-lookup"><span data-stu-id="21336-110">provides two types of parsing for converting data: Fast parse and Standard parse.</span></span>  
  
-   <span data-ttu-id="21336-111">快速剖析是一組快速而簡單的剖析常式，它不支援地區設定特定的資料類型轉換，僅支援最常用的日期和時間格式。</span><span class="sxs-lookup"><span data-stu-id="21336-111">Fast parse is a fast, simple set of parsing routines that does not support locale-specific data type conversions, and supports only the most frequently used date and time formats.</span></span> <span data-ttu-id="21336-112">如需相關資訊，請參閱 [Fast Parse](../fast-parse.md)。</span><span class="sxs-lookup"><span data-stu-id="21336-112">For more information, see [Fast Parse](../fast-parse.md).</span></span>  
  
-   <span data-ttu-id="21336-113">標準剖析是一組相當豐富的剖析常式，它支援由 Oleaut32.dll 和 Ole2dsip.dll 中可用的「自動」資料類型轉換 API 所提供的所有資料類型轉換。</span><span class="sxs-lookup"><span data-stu-id="21336-113">Standard parse is a rich set of parsing routines that supports all the data type conversions that are provided by the Automation data type conversion APIs available in Oleaut32.dll and Ole2dsip.dll.</span></span> <span data-ttu-id="21336-114">如需相關資訊，請參閱 [Standard Parse](../standard-parse.md)。</span><span class="sxs-lookup"><span data-stu-id="21336-114">For more information, see [Standard Parse](../standard-parse.md).</span></span>  
  
  
