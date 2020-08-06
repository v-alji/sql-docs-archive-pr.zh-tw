---
title: " (MDX) 的使用者自訂成員屬性 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- custom member properties [MDX]
ms.assetid: b64cc581-e784-42c4-bec8-932abd687423
author: minewiskan
ms.author: owend
ms.openlocfilehash: 75e5df5a0677ee205b5517f4c7ca89a390426971
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698623"
---
# <a name="user-defined-member-properties-mdx"></a><span data-ttu-id="3eeba-102">使用者自訂成員屬性 (MDX)</span><span class="sxs-lookup"><span data-stu-id="3eeba-102">User-Defined Member Properties (MDX)</span></span>
  <span data-ttu-id="3eeba-103">使用者自訂成員屬性可以做為屬性關聯性，增加到維度中的特定具名層級。</span><span class="sxs-lookup"><span data-stu-id="3eeba-103">User-defined member properties can be added to a specific named level in a dimension as attribute relationships.</span></span> <span data-ttu-id="3eeba-104">階層的 `(All)` 層級或階層本身無法增加使用者自訂成員屬性。</span><span class="sxs-lookup"><span data-stu-id="3eeba-104">User-defined member properties cannot be added to the `(All)` level of a hierarchy, or to the hierarchy itself.</span></span>  
  
## <a name="creating-user-defined-member-properties"></a><span data-ttu-id="3eeba-105">建立使用者自訂成員屬性</span><span class="sxs-lookup"><span data-stu-id="3eeba-105">Creating User-Defined Member Properties</span></span>  
 <span data-ttu-id="3eeba-106">您可以透過使用者介面或以程式設計的方式，將使用者自訂成員屬性增加到伺服器維度或 Cube：</span><span class="sxs-lookup"><span data-stu-id="3eeba-106">User-defined member properties can be added to server-based dimensions or cubes either through the user interface or programmatically:</span></span>  
  
-   <span data-ttu-id="3eeba-107">若要透過使用者介面加入使用者定義成員屬性，您可以使用 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中的維度設計師。</span><span class="sxs-lookup"><span data-stu-id="3eeba-107">To add user-defined member properties through the user interface, you use Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="3eeba-108">如需詳細資訊，請參閱 [定義屬性關聯性](../attribute-relationships-define.md)。</span><span class="sxs-lookup"><span data-stu-id="3eeba-108">For more information, see [Define Attribute Relationships](../attribute-relationships-define.md).</span></span>  
  
-   <span data-ttu-id="3eeba-109">若要以程式設計方式加入使用者定義的成員屬性，您的應用程式可以使用分析管理物件 (AMO)，或 XML for Analysis (XMLA) 及 Analysis Services 指令碼語言 (ASSL) 的組合。</span><span class="sxs-lookup"><span data-stu-id="3eeba-109">To add user-defined member properties programmatically, your application can use either Analysis Manager Objects (AMO) or a combination of XML for Analysis (XMLA) and Analysis Services Scripting Language (ASSL).</span></span> <span data-ttu-id="3eeba-110">如需詳細資訊，請參閱 [屬性關聯性](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="3eeba-110">For more information, see [Attribute Relationships](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
## <a name="retrieving-user-defined-member-properties"></a><span data-ttu-id="3eeba-111">擷取使用者自訂成員屬性</span><span class="sxs-lookup"><span data-stu-id="3eeba-111">Retrieving User-Defined Member Properties</span></span>  
 <span data-ttu-id="3eeba-112">您可以使用 `PROPERTIES` 關鍵字或[properties](/sql/mdx/properties-mdx)函數來抓取使用者自訂成員屬性。</span><span class="sxs-lookup"><span data-stu-id="3eeba-112">You can retrieve user-defined member properties using either the `PROPERTIES` keyword or the [Properties](/sql/mdx/properties-mdx) function.</span></span>  
  
### <a name="using-the-properties-keyword-to-retrieve-user-defined-member-properties"></a><span data-ttu-id="3eeba-113">使用 PROPERTIES 關鍵字擷取使用者自訂成員屬性</span><span class="sxs-lookup"><span data-stu-id="3eeba-113">Using the PROPERTIES Keyword to Retrieve User-Defined Member Properties</span></span>  
 <span data-ttu-id="3eeba-114">擷取使用者自訂成員屬性的語法，跟用以擷取內建層級成員屬性的語法類似，如以下語法所示：</span><span class="sxs-lookup"><span data-stu-id="3eeba-114">The syntax that retrieves user-defined member properties is similar to that used to retrieve intrinsic level member properties, as shown in the following syntax:</span></span>  
  
 `DIMENSION PROPERTIES [Dimension.]Level.<Custom_Member_Property>`  
  
 <span data-ttu-id="3eeba-115">`PROPERTIES` 關鍵字會在座標軸規格的集合運算式後面出現。</span><span class="sxs-lookup"><span data-stu-id="3eeba-115">The `PROPERTIES` keyword appears after the set expression of the axis specification.</span></span> <span data-ttu-id="3eeba-116">例如，以下的 MDX 查詢 `PROPERTIES` 關鍵字會擷取 `List Price` 與 `Dealer Price` 使用者自訂成員屬性，並且在識別 1 月份銷售之產品的集合運算式之後顯示：</span><span class="sxs-lookup"><span data-stu-id="3eeba-116">For example, the following MDX query the `PROPERTIES` keyword retrieves the `List Price` and `Dealer Price` user-defined member properties and appears after the set expression that identifies the products sold in January:</span></span>  
  
```  
SELECT   
   CROSSJOIN([Ship Date].[Calendar].[Calendar Year].Members,   
             [Measures].[Sales Amount]) ON COLUMNS,  
   NON EMPTY Product.Product.MEMBERS  
   DIMENSION PROPERTIES   
              Product.Product.[List Price],  
              Product.Product.[Dealer Price]  ON ROWS  
FROM [Adventure Works]  
WHERE ([Date].[Month of Year].[January])   
```  
  
### <a name="using-the-properties-function-to-retrieve-user-defined-member-properties"></a><span data-ttu-id="3eeba-117">使用 Properties 函數擷取使用者自訂成員屬性</span><span class="sxs-lookup"><span data-stu-id="3eeba-117">Using the Properties Function to Retrieve User-Defined Member Properties</span></span>  
 <span data-ttu-id="3eeba-118">或者，您可以使用 `Properties` 函數來存取自訂成員屬性。</span><span class="sxs-lookup"><span data-stu-id="3eeba-118">Alternatively, you can access custom member properties with the `Properties` function.</span></span> <span data-ttu-id="3eeba-119">例如，以下的 MDX 查詢就是使用 `WITH` 關鍵字，建立包含 `List Price` 成員屬性的導出成員：</span><span class="sxs-lookup"><span data-stu-id="3eeba-119">For example, the following MDX query uses the `WITH` keyword to create a calculated member consisting of the `List Price` member property:</span></span>  
  
```  
WITH   
   MEMBER [Measures].[Product List Price] AS  
   [Product].[Product].CurrentMember.Properties("List Price")  
SELECT   
   [Measures].[Product List Price] on COLUMNS,  
   [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="3eeba-120">如需建立導出成員的詳細資訊，請參閱[在 MDX 中建立導出成員 &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md)。</span><span class="sxs-lookup"><span data-stu-id="3eeba-120">For more information about building calculated members, see [Building Calculated Members in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eeba-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3eeba-121">See Also</span></span>  
 <span data-ttu-id="3eeba-122">[使用成員屬性 &#40;MDX&#41;](mdx-member-properties.md) </span><span class="sxs-lookup"><span data-stu-id="3eeba-122">[Using Member Properties &#40;MDX&#41;](mdx-member-properties.md) </span></span>  
 [<span data-ttu-id="3eeba-123">Properties &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="3eeba-123">Properties &#40;MDX&#41;</span></span>](/sql/mdx/properties-mdx)  
  
  
