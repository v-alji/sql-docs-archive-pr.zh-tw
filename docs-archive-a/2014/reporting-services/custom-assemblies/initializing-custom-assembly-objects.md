---
title: 初始化自訂組件物件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- initializing custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], initializing
- OnInit method
ms.assetid: 26fd74dc-d02f-40f7-aeb3-50ce05e9e6b9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2aba0bd8b71b26651067a2370728dcdff521ceaa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595795"
---
# <a name="initializing-custom-assembly-objects"></a><span data-ttu-id="9a656-102">初始化自訂組件物件</span><span class="sxs-lookup"><span data-stu-id="9a656-102">Initializing Custom Assembly Objects</span></span>
  <span data-ttu-id="9a656-103">在某些情況下，您可能需要在初始化自訂組件類別時，初始化其中的屬性與欄位值。</span><span class="sxs-lookup"><span data-stu-id="9a656-103">In some cases, you may need to initialize property and field values in your custom assembly classes when you instantiate them.</span></span> <span data-ttu-id="9a656-104">您很可能需要使用報表全域物件集合中可用的值，來初始化自訂類別。</span><span class="sxs-lookup"><span data-stu-id="9a656-104">You will most likely need to initialize your custom classes with values available to you from the report's global object collections.</span></span> <span data-ttu-id="9a656-105">您可以透過覆寫報表之 **Code** 物件的 **OnInit** 方法來完成。</span><span class="sxs-lookup"><span data-stu-id="9a656-105">You do this by overriding the **OnInit** method of the **Code** object of a report.</span></span> <span data-ttu-id="9a656-106">若要存取 **OnInit**，請使用報表定義的 **Code** 項目。</span><span class="sxs-lookup"><span data-stu-id="9a656-106">To access **OnInit**, use the **Code** element of the report definition.</span></span> <span data-ttu-id="9a656-107">有兩個技術可初始化您計劃在報表中使用的自訂組件中類別之屬性或欄位值。您可以使用 **OnInit** 來宣告和建立類別的新執行個體，或者您可以使用 **OnInit** 來呼叫公開可用的方法。</span><span class="sxs-lookup"><span data-stu-id="9a656-107">There are two techniques for initializing property or field values of the classes in a custom assembly that you plan to use in your report: You can either declare and create a new instance of your class using **OnInit**, or you can call a publicly available method using **OnInit**.</span></span>  
  
## <a name="global-object-collections-and-initialization"></a><span data-ttu-id="9a656-108">全域物件集合與初始化</span><span class="sxs-lookup"><span data-stu-id="9a656-108">Global Object Collections and Initialization</span></span>  
 <span data-ttu-id="9a656-109">有幾個集合可供您初始化自訂類別變數。</span><span class="sxs-lookup"><span data-stu-id="9a656-109">Several collections are available to you for initializing your custom class variables.</span></span> <span data-ttu-id="9a656-110">您可以使用 **Globals** 和 **User** 集合。</span><span class="sxs-lookup"><span data-stu-id="9a656-110">You can use the **Globals** and **User** collections.</span></span> <span data-ttu-id="9a656-111">叫用 **OnInit** 方法時，無法在報表生命週期內使用 **Parameters**、**Fields** 和 **ReportItems** 集合。</span><span class="sxs-lookup"><span data-stu-id="9a656-111">The **Parameters**, **Fields** and **ReportItems** collections are not available to you at the point in the report lifecycle when the **OnInit** method is invoked.</span></span> <span data-ttu-id="9a656-112">若要使用共用集合 **Globals** 或 **User**，您需要加入 **Report** 物件參考。</span><span class="sxs-lookup"><span data-stu-id="9a656-112">To use the shared collections, **Globals** or **User**, you need to include the **Report** object reference.</span></span> <span data-ttu-id="9a656-113">例如，若要根據存取報表之使用者的目前語言來初始化您的自訂類別，您的 **Code** 項目可能看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="9a656-113">For example, to initialize your custom class based on the current language of the user accessing the report, your **Code** element might look like the following:</span></span>  
  
```  
<Code>  
   Dim m_myClass As MyClass  
  
   Protected Overrides Sub OnInit()  
      m_myClass = new MyClass(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 <span data-ttu-id="9a656-114">如前所示，有一種方法可以初始化類別的屬性和欄位值，就是呼叫覆寫的建構函式，以宣告類別並建立該類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="9a656-114">One way to initialize the property and field values of a class as shown previously is to declare your class and create a new instance of it by calling an overridden constructor.</span></span>  
  
 <span data-ttu-id="9a656-115">在自訂組件中初始化類別之屬性與欄位值的另一種方法，是呼叫從 **OnInit** 方法定義之公開可用的方法。</span><span class="sxs-lookup"><span data-stu-id="9a656-115">Another way to initialize the property and field values of the classes in your custom assemblies is to call a publicly available method that you define from the **OnInit** method.</span></span> <span data-ttu-id="9a656-116">您必須先為報表定義檔案中的類別加入執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="9a656-116">You first need to add an instance name for your class in the report definition file.</span></span> <span data-ttu-id="9a656-117">一旦您加入適當的組件參考與執行個體名稱，就可以呼叫初始化方法以初始化類別的屬性與欄位值。</span><span class="sxs-lookup"><span data-stu-id="9a656-117">Once you have added the appropriate assembly reference and instance name, you can call your initialization method to initialize property and field values for your class.</span></span> <span data-ttu-id="9a656-118">您的 **OnInit** 方法可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="9a656-118">Your **OnInit** method might look like the following:</span></span>  
  
```  
<Code>  
   Protected Overrides Sub OnInit()  
      m_myClass.MyInitializationMethod(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 <span data-ttu-id="9a656-119">如需新增自訂類別的組件參考與執行個體名稱的詳細資訊，請參閱[將組件參考新增至報表 &#40;SSRS&#41;](../report-design/add-an-assembly-reference-to-a-report-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9a656-119">For more information about adding an assembly reference and instance name for your custom class, see [Add an Assembly Reference to a Report &#40;SSRS&#41;](../report-design/add-an-assembly-reference-to-a-report-ssrs.md).</span></span>  
  
 <span data-ttu-id="9a656-120">如需全域物件集合的詳細資訊，請參閱[運算式中的內建集合 &#40;報表產生器及 SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="9a656-120">For more information about the global object collections, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a656-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a656-121">See Also</span></span>  
 [<span data-ttu-id="9a656-122">將自訂組件與報表搭配使用</span><span class="sxs-lookup"><span data-stu-id="9a656-122">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
