---
title: 使用 XSINIL 參數為 NULL 值產生項目 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, null values
- null values [SQL Server], XML
- ELEMENTS directive
- XSINIL parameter
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 602de12b5aa9be8997fbd49a2f23e0b73444aac0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710422"
---
# <a name="generate-elements-for-null-values-with-the-xsinil-parameter"></a><span data-ttu-id="b7e4e-102">使用 XSINIL 參數為 NULL 值產生元素</span><span class="sxs-lookup"><span data-stu-id="b7e4e-102">Generate Elements for NULL Values with the XSINIL Parameter</span></span>
  <span data-ttu-id="b7e4e-103">**ELEMENTS** 指示詞可建構 XML，在其中每個資料行值都對應到 XML 中的元素。</span><span class="sxs-lookup"><span data-stu-id="b7e4e-103">The **ELEMENTS** directive constructs XML in which each column value maps to an element in the XML.</span></span> <span data-ttu-id="b7e4e-104">若資料行值為 NULL，則不會加入任何元素。</span><span class="sxs-lookup"><span data-stu-id="b7e4e-104">If the column value is NULL, no element is added.</span></span> <span data-ttu-id="b7e4e-105">若在 ELEMENTS 指示詞上指定選擇性的 **XSINIL** 參數，您可以要求也為 NULL 值建立元素。</span><span class="sxs-lookup"><span data-stu-id="b7e4e-105">By specifying the optional **XSINIL** parameter on the ELEMENTS directive, you can request that an element also be created for the NULL value.</span></span> <span data-ttu-id="b7e4e-106">在此情況下，對於每個 NULL 資料行值，會傳回一個 **xsi:nil** 屬性設定成 TRUE 的元素。</span><span class="sxs-lookup"><span data-stu-id="b7e4e-106">In this case, an element that has the **xsi:nil** attribute set to TRUE is returned for each NULL column value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e4e-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7e4e-107">See Also</span></span>  
 [<span data-ttu-id="b7e4e-108">搭配 FOR XML 使用 RAW 模式</span><span class="sxs-lookup"><span data-stu-id="b7e4e-108">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
