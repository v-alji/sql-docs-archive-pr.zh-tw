---
title: 標準剖析 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- standard parse [Integration Services]
- locales [Integration Services]
ms.assetid: dfe835b1-ea52-4e18-a23a-5188c5b6f013
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7cacff710870d372d6bbf8345e05397857c13a00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703138"
---
# <a name="standard-parse"></a><span data-ttu-id="83832-102">Standard Parse</span><span class="sxs-lookup"><span data-stu-id="83832-102">Standard Parse</span></span>
  <span data-ttu-id="83832-103">標準剖析是一組區分地區設定的剖析常式，它支援 Oleaut32.dll 和 Ole2dsip.dll 中可用的 Automation 資料類型轉換 API 所提供的所有資料類型轉換。</span><span class="sxs-lookup"><span data-stu-id="83832-103">Standard parse is a locale-sensitive set of parsing routines that support all the data type conversions provided by the Automation data type conversion APIs that are available in Oleaut32.dll and Ole2dsip.dll.</span></span> <span data-ttu-id="83832-104">標準剖析相當於 OLE DB 剖析 API。</span><span class="sxs-lookup"><span data-stu-id="83832-104">Standard parse is equivalent to the OLE DB parsing APIs.</span></span>  
  
 <span data-ttu-id="83832-105">標準剖析提供對國際性資料之資料類型轉換的支援，它應在「快速剖析」不支援資料格式時使用。</span><span class="sxs-lookup"><span data-stu-id="83832-105">Standard parse provides support for data type conversion of international data, and it should be used if the data format is not supported by Fast parse.</span></span> <span data-ttu-id="83832-106">如需 Automation 資料類型轉換 API 的詳細資訊，請參閱 [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=79427)中的＜資料類型轉換 API＞。</span><span class="sxs-lookup"><span data-stu-id="83832-106">For more information about the Automation data type conversion API, see "Data Type Conversion APIs" in the [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=79427).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83832-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83832-107">See Also</span></span>  
 [<span data-ttu-id="83832-108">Fast Parse</span><span class="sxs-lookup"><span data-stu-id="83832-108">Fast Parse</span></span>](../../2014/integration-services/fast-parse.md)  
  
  
