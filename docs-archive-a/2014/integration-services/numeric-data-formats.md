---
title: 數值資料格式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- integer data types [Integration Services]
- numeric data formats for fast parse
- locale-sensitive parsing [Integration Services]
- fast parse [Integration Services]
ms.assetid: fa3975ce-9d21-408a-857d-f85e30af27b0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc54a331c3762e31ba9d9a431aaca7eda6374d8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596093"
---
# <a name="numeric-data-formats"></a><span data-ttu-id="89de1-102">數值資料格式</span><span class="sxs-lookup"><span data-stu-id="89de1-102">Numeric Data Formats</span></span>
  <span data-ttu-id="89de1-103">快速剖析提供一組快速、簡易且區分區域設定的常式集，以剖析資料。</span><span class="sxs-lookup"><span data-stu-id="89de1-103">Fast parse provides a fast, simple, locale-insensitive set of routines for parsing data.</span></span> <span data-ttu-id="89de1-104">快速剖析僅支援整數資料類型的有限格式集。</span><span class="sxs-lookup"><span data-stu-id="89de1-104">Fast parse supports only a limited set of formats for integer data types.</span></span>  
  
## <a name="integer-data-types"></a><span data-ttu-id="89de1-105">整數資料類型</span><span class="sxs-lookup"><span data-stu-id="89de1-105">Integer Data Types</span></span>  
 <span data-ttu-id="89de1-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 所提供的整數資料類型為 DT_I1、DT_UI1、DT_I2、DT_UI2、DT_I4、DT_UI4、DT_I8 及 DT_UI8。</span><span class="sxs-lookup"><span data-stu-id="89de1-106">The integer data types that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] provides are DT_I1, DT_UI1, DT_I2, DT_UI2, DT_I4, DT_UI4, DT_I8, and DT_UI8.</span></span> <span data-ttu-id="89de1-107">如需詳細資訊，請參閱 [Integration Services 資料類型](data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="89de1-107">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="89de1-108">快速剖析支援整數資料類型的下列格式：</span><span class="sxs-lookup"><span data-stu-id="89de1-108">Fast parse supports the following formats for integer data types:</span></span>  
  
-   <span data-ttu-id="89de1-109">含或不含開頭與尾端空格或定位點。</span><span class="sxs-lookup"><span data-stu-id="89de1-109">Zero or more leading and trailing spaces or tab stops.</span></span> <span data-ttu-id="89de1-110">例如，值「  123  」為有效。</span><span class="sxs-lookup"><span data-stu-id="89de1-110">For example, the value "  123  " is valid.</span></span> <span data-ttu-id="89de1-111">全部為空格的值會評估為零。</span><span class="sxs-lookup"><span data-stu-id="89de1-111">A value that is all spaces evaluates to zero.</span></span>  
  
-   <span data-ttu-id="89de1-112">開頭正號、負號或均不含。</span><span class="sxs-lookup"><span data-stu-id="89de1-112">A leading plus sign, minus sign, or neither.</span></span> <span data-ttu-id="89de1-113">例如，值 +123、-123 及 123 有效。</span><span class="sxs-lookup"><span data-stu-id="89de1-113">For example, the values +123, -123, and 123 are valid.</span></span>  
  
-   <span data-ttu-id="89de1-114">一個或多個印度-阿拉伯數字 (0-9)。</span><span class="sxs-lookup"><span data-stu-id="89de1-114">One or more Hindu-Arabic numerals (0-9).</span></span> <span data-ttu-id="89de1-115">例如，值 345 有效。</span><span class="sxs-lookup"><span data-stu-id="89de1-115">For example, the value 345 is valid.</span></span> <span data-ttu-id="89de1-116">不支援其他語言的數字。</span><span class="sxs-lookup"><span data-stu-id="89de1-116">Other language numerals are not supported.</span></span>  
  
 <span data-ttu-id="89de1-117">不支援的資料格式包括：</span><span class="sxs-lookup"><span data-stu-id="89de1-117">Non-supported data formats include the following:</span></span>  
  
-   <span data-ttu-id="89de1-118">特殊字元。</span><span class="sxs-lookup"><span data-stu-id="89de1-118">Special characters.</span></span> <span data-ttu-id="89de1-119">例如，不支援貨幣字元 $，因此無法剖析值 $20。</span><span class="sxs-lookup"><span data-stu-id="89de1-119">For example, the currency character $ is not supported, and the value $20 cannot be parsed.</span></span>  
  
-   <span data-ttu-id="89de1-120">空白字元，如換行字元、歸位字元及不中斷空格。</span><span class="sxs-lookup"><span data-stu-id="89de1-120">White-space characters such as line feed, carriage returns, and non-breaking spaces.</span></span> <span data-ttu-id="89de1-121">例如，無法剖析值「&#xA0;</ph>123」。</span><span class="sxs-lookup"><span data-stu-id="89de1-121">For example, the value " 123" cannot be parsed.</span></span>  
  
-   <span data-ttu-id="89de1-122">整數的十六進位表示法。</span><span class="sxs-lookup"><span data-stu-id="89de1-122">Hexadecimal representations of integers.</span></span> <span data-ttu-id="89de1-123">例如，無法剖析值 2EE。</span><span class="sxs-lookup"><span data-stu-id="89de1-123">For example, the value 2EE cannot be parsed.</span></span>  
  
-   <span data-ttu-id="89de1-124">整數的科學記號標記法。</span><span class="sxs-lookup"><span data-stu-id="89de1-124">Scientific notation representation of integers.</span></span> <span data-ttu-id="89de1-125">例如，無法剖析值 1E+10。</span><span class="sxs-lookup"><span data-stu-id="89de1-125">For example, the value 1E+10 cannot be parsed.</span></span>  
  
 <span data-ttu-id="89de1-126">下列格式是整數的輸出資料格式：</span><span class="sxs-lookup"><span data-stu-id="89de1-126">The following formats are output data formats for integers:</span></span>  
  
-   <span data-ttu-id="89de1-127">減號代表負數，不含符號則代表正數。</span><span class="sxs-lookup"><span data-stu-id="89de1-127">A minus sign for negative numbers and nothing for positive ones.</span></span>  
  
-   <span data-ttu-id="89de1-128">無空白。</span><span class="sxs-lookup"><span data-stu-id="89de1-128">No white spaces.</span></span>  
  
-   <span data-ttu-id="89de1-129">一個或多個印度-阿拉伯數字 (0-9)。</span><span class="sxs-lookup"><span data-stu-id="89de1-129">One or more Hindu-Arabic numerals (0-9).</span></span>  
  
  
