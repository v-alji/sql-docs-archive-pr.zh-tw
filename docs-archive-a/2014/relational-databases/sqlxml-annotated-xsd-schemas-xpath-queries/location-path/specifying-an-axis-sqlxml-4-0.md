---
title: 指定 (SQLXML 4.0) 的軸 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], axes
- XPath queries [SQLXML], location paths
- self axis
- attribute axis [SQLXML]
- axis [SQLXML]
- child axis
- parent axis
- location path for XPath query
- axes [SQLXML]
ms.assetid: 65631795-3389-40cf-90ea-85e9438956c5
author: rothja
ms.author: jroth
ms.openlocfilehash: 5e43281fe31d323a7eea19e749b80b59458752b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596586"
---
# <a name="specifying-an-axis-sqlxml-40"></a><span data-ttu-id="14619-102">指定軸 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="14619-102">Specifying an Axis (SQLXML 4.0)</span></span>
    
-   <span data-ttu-id="14619-103">軸會指定位置步驟與內容節點所選取之節點間的樹狀結構關聯性。</span><span class="sxs-lookup"><span data-stu-id="14619-103">The axis specifies the tree relationship between the nodes selected by the location step and the context node.</span></span> <span data-ttu-id="14619-104">支援下列軸：`child`</span><span class="sxs-lookup"><span data-stu-id="14619-104">The following axes are supported:  `child`</span></span>  
  
     <span data-ttu-id="14619-105">包含內容節點的子系。</span><span class="sxs-lookup"><span data-stu-id="14619-105">Contains the child of the context node.</span></span>  
  
     <span data-ttu-id="14619-106">下列 XPath 運算式 (位置路徑) 從目前的內容節點選取所有子系 **\<Customer>** ：</span><span class="sxs-lookup"><span data-stu-id="14619-106">The following XPath expression (location path) selects from the current context node all the **\<Customer>** children:</span></span>  
  
    ```  
    child::Customer  
    ```  
  
     <span data-ttu-id="14619-107">在下列 XPath 查詢中，`child` 為軸。</span><span class="sxs-lookup"><span data-stu-id="14619-107">In the following XPath query, `child` is the axis.</span></span> <span data-ttu-id="14619-108">`Customer` 為節點測試。</span><span class="sxs-lookup"><span data-stu-id="14619-108">`Customer` is the node test.</span></span>  
  
-   `parent`  
  
     <span data-ttu-id="14619-109">包含內容節點的父系。</span><span class="sxs-lookup"><span data-stu-id="14619-109">Contains the parent of the context node.</span></span>  
  
     <span data-ttu-id="14619-110">下列 XPath 運算式會選取子系的所有父系 **\<Customer>** **\<Order>** ：</span><span class="sxs-lookup"><span data-stu-id="14619-110">The following XPath expression selects all the **\<Customer>** parents of the **\<Order>** children:</span></span>  
  
    ```  
    child::Customer/child::Order[parent::Customer/@customerID="ALFKI"]  
    ```  
  
     <span data-ttu-id="14619-111">這與指定 `child::Customer` 相同。</span><span class="sxs-lookup"><span data-stu-id="14619-111">This is the same as specifying `child::Customer`.</span></span> <span data-ttu-id="14619-112">在此 XPath 查詢中，`child` 和 `parent` 為軸。</span><span class="sxs-lookup"><span data-stu-id="14619-112">In this XPath query, `child` and `parent` are the axes.</span></span> <span data-ttu-id="14619-113">`Customer` 和 `Order` 為節點測試。</span><span class="sxs-lookup"><span data-stu-id="14619-113">`Customer` and `Order` are the node tests.</span></span>  
  
-   `attribute`  
  
     <span data-ttu-id="14619-114">包含內容節點的屬性。</span><span class="sxs-lookup"><span data-stu-id="14619-114">Contains the attribute of the context node.</span></span>  
  
     <span data-ttu-id="14619-115">下列 XPath 運算式會選取內容節點的**CustomerID**屬性：</span><span class="sxs-lookup"><span data-stu-id="14619-115">The following XPath expression selects the **CustomerID** attribute of the context node:</span></span>  
  
    ```  
    attribute::CustomerID  
    ```  
  
-   `self`  
  
     <span data-ttu-id="14619-116">包含內容節點本身。</span><span class="sxs-lookup"><span data-stu-id="14619-116">Contains the context node itself.</span></span>  
  
     <span data-ttu-id="14619-117">下列 XPath 運算式會選取目前的節點（如果它是 **\<Order>** 節點）：</span><span class="sxs-lookup"><span data-stu-id="14619-117">The following XPath expression selects the current node if it is the **\<Order>** node:</span></span>  
  
    ```  
    self::Order  
    ```  
  
     <span data-ttu-id="14619-118">在此 XPath 查詢中，`self` 為軸，而 `Order` 為節點測試。</span><span class="sxs-lookup"><span data-stu-id="14619-118">In this XPath query, `self` is the axis and `Order` is the node test.</span></span>  
  
  
