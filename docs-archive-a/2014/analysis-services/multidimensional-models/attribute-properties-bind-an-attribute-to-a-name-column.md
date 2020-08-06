---
title: 將屬性系結至名稱資料行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- binding attributes [Analysis Services]
- name columns [Analysis Services]
- attributes [Analysis Services], binding
ms.assetid: 467f0cf3-8691-476d-a7fb-a5df4e374eaf
author: minewiskan
ms.author: owend
ms.openlocfilehash: e25c59d34744e7a067c2b3e83d248c4674772737
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605917"
---
# <a name="bind-an-attribute-to-a-name-column"></a><span data-ttu-id="06002-102">繫結屬性與名稱資料行</span><span class="sxs-lookup"><span data-stu-id="06002-102">Bind an Attribute to a Name Column</span></span>
  <span data-ttu-id="06002-103">此程序描述如何使用維度設計師中的 **[屬性]** 窗格，及使用 **[物件繫結]** 對話方塊，手動繫結屬性與名稱資料行。</span><span class="sxs-lookup"><span data-stu-id="06002-103">This procedure describes how to bind an attribute to a name column manually by using the **Attributes** pane in the Dimension Designer and by using the **Object Binding** dialog box.</span></span>  
  
### <a name="to-bind-an-attribute-to-a-name-column"></a><span data-ttu-id="06002-104">繫結屬性與名稱資料行</span><span class="sxs-lookup"><span data-stu-id="06002-104">To bind an attribute to a name column</span></span>  
  
1.  <span data-ttu-id="06002-105">在維度設計師中，開啟您要在其中建立屬性的維度。</span><span class="sxs-lookup"><span data-stu-id="06002-105">In Dimension Designer, open the dimension in which you want to create the attribute.</span></span>  
  
2.  <span data-ttu-id="06002-106">在 [維度結構]\*\*\*\* 索引標籤的 [屬性]\*\*\*\* 窗格上，以滑鼠右鍵按一下您要設定的屬性，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="06002-106">On the **Dimension Structure** tab, in the **Attributes** pane, right-click the attribute that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="06002-107">在 [屬性]\*\*\*\* 視窗中，找出 [NameColumn]\*\*\*\* 屬性，然後選取 [(新增)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="06002-107">In the **Properties** window, locate the **NameColumn** property, and then select **(new)**.</span></span>  
  
4.  <span data-ttu-id="06002-108">在 **[物件繫結]** 對話方塊中，針對 **[繫結類型]** 選取 **[資料行繫結]**。</span><span class="sxs-lookup"><span data-stu-id="06002-108">In the **Object Binding** dialog box, for **Binding type**, select **Column binding**.</span></span>  
  
5.  <span data-ttu-id="06002-109">在 **[來源資料行]** 清單中，選取屬性要繫結的資料行，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="06002-109">In the **Source column** list, select the column to which the attribute will be bound, and then click **OK**.</span></span>  
  
  
