---
title: 定義事實關聯性和事實關聯性屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- fact dimensions [Analysis Services]
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 15f67a4bdf699bbc6443fc76ce54bcfb35831827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698644"
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a><span data-ttu-id="a7f47-102">定義事實關聯性及事實關聯性屬性</span><span class="sxs-lookup"><span data-stu-id="a7f47-102">Define a Fact Relationship and Fact Relationship Properties</span></span>
  <span data-ttu-id="a7f47-103">當您定義新的 Cube 維度或新的量值群組時，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會嘗試偵測是否有事實維度關聯性，然後將維度使用方式設定設為 `Fact`。</span><span class="sxs-lookup"><span data-stu-id="a7f47-103">When you define a new cube dimension or a new measure group, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will try to detect if a fact dimension relationship exists and then set the dimension usage setting to `Fact`.</span></span> <span data-ttu-id="a7f47-104">您可以在 Cube 設計師的 [維度使用方式]\*\*\*\* 索引標籤上，檢視或編輯事實維度關聯性。</span><span class="sxs-lookup"><span data-stu-id="a7f47-104">You can view or edit a fact dimension relationship on the **Dimension Usage** tab of Cube Designer.</span></span> <span data-ttu-id="a7f47-105">維度和量值群組之間的事實關聯性具有下列條件約束：</span><span class="sxs-lookup"><span data-stu-id="a7f47-105">The fact relationship between a dimension and a measure group has the following constraints:</span></span>  
  
-   <span data-ttu-id="a7f47-106">Cube 維度只能與特定量值群組有單一事實關聯性。</span><span class="sxs-lookup"><span data-stu-id="a7f47-106">A cube dimension can have only one fact relationship to a particular measure group.</span></span>  
  
-   <span data-ttu-id="a7f47-107">Cube 維度可以與多個量值群組有不同的事實關聯性。</span><span class="sxs-lookup"><span data-stu-id="a7f47-107">A cube dimension can have separate fact relationships to multiple measure groups.</span></span>  
  
-   <span data-ttu-id="a7f47-108">關聯性的資料粒度屬性必須是維度的索引鍵屬性 (例如，交易號碼)。</span><span class="sxs-lookup"><span data-stu-id="a7f47-108">The granularity attribute for the relationship must be the key attribute (such as Transaction Number) for the dimension.</span></span> <span data-ttu-id="a7f47-109">這會在維度和事實資料表的事實之間建立一對一關聯性。</span><span class="sxs-lookup"><span data-stu-id="a7f47-109">This creates a one-to-one relationship between the dimension and facts in the fact table.</span></span>  
  
  
