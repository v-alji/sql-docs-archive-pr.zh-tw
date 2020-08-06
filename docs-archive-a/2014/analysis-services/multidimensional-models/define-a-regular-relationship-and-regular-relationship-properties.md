---
title: 定義一般關聯性和一般關聯性屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- granularity attribute
- relationships [Analysis Services], regular relationships
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b4f49e219a85d5577fb1acddfe14e7afd3b105d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599700"
---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a><span data-ttu-id="03c29-102">定義一般關聯性及一般關聯性屬性</span><span class="sxs-lookup"><span data-stu-id="03c29-102">Define a Regular Relationship and Regular Relationship Properties</span></span>
  <span data-ttu-id="03c29-103">當您定義新的 Cube 維度或新的量值群組時，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會嘗試偵測是否有一般關聯性，然後將維度使用方式設定設為 `Regular`。</span><span class="sxs-lookup"><span data-stu-id="03c29-103">When you define a new cube dimension or a new measure group, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will try to detect if a regular relationship exists and then set the dimension usage setting to `Regular`.</span></span> <span data-ttu-id="03c29-104">在 Cube 設計師的 [維度使用方式]\*\*\*\* 索引標籤上，您可以檢視或編輯一般維度關聯性。</span><span class="sxs-lookup"><span data-stu-id="03c29-104">You can view or edit a regular dimension relationship on the **Dimension Usage** tab of Cube Designer.</span></span>  
  
 <span data-ttu-id="03c29-105">當您定義 Cube 維度與量值群組的關聯性時，會同時為該關聯性指定資料粒度屬性。</span><span class="sxs-lookup"><span data-stu-id="03c29-105">When you define the relationship of a cube dimension to a measure group, you also specify the granularity attribute for that relationship.</span></span> <span data-ttu-id="03c29-106">資料粒度屬性會針對該維度定義 Cube 中可用之詳細資料的最低層級，這通常是維度的索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="03c29-106">The granularity attribute defines the lowest level of detail available in the cube for that dimension, which is generally the key attribute for the dimension.</span></span> <span data-ttu-id="03c29-107">然而，有時您可能會想要在特定量值群組中，將特定 Cube 維度的資料粒度設定為不同的資料粒度。</span><span class="sxs-lookup"><span data-stu-id="03c29-107">However, sometimes you may want to set the granularity of a particular cube dimension in a particular measure group to a different grain.</span></span> <span data-ttu-id="03c29-108">例如，如果您使用的是 [銷售配額] 或 [預算] 量值群組，則可能會想要將 [時間] 維度的資料粒度屬性設定為 [月] 屬性而不是 [日] 屬性。</span><span class="sxs-lookup"><span data-stu-id="03c29-108">For example, you may want to set the granularity attribute for the Time dimension to the Month attribute instead of to the Day attribute, if you are using a Sales Quotas or a Budget measure group.</span></span> <span data-ttu-id="03c29-109">當您將資料粒度屬性指定為索引鍵屬性以外的屬性時，則必須確定維度中的其他所有屬性都是透過屬性關聯性直接或間接連結至另一個屬性。</span><span class="sxs-lookup"><span data-stu-id="03c29-109">When you specify the granularity attribute to be an attribute other than the key attribute, you must guarantee that all other attributes in the dimension are directly or indirectly linked to this other attribute through attribute relationships.</span></span> <span data-ttu-id="03c29-110">否則， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 將無法正確地彙總資料。</span><span class="sxs-lookup"><span data-stu-id="03c29-110">If not, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will be unable to aggregate data correctly.</span></span>  
  
  
