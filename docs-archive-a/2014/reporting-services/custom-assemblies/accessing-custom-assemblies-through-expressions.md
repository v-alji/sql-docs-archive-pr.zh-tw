---
title: 透過運算式存取自訂組件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- expressions [Reporting Services], custom assemblies
- static member calls
- instance member calls [Reporting Services]
- calling class members
- custom assemblies [Reporting Services], expressions
ms.assetid: 917c4d47-1a95-4f54-98b1-e8cb2165d90f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 99497de0456d90fd522ce27c62fd5aa1b812059f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584287"
---
# <a name="accessing-custom-assemblies-through-expressions"></a><span data-ttu-id="4de2e-102">透過運算式存取自訂組件</span><span class="sxs-lookup"><span data-stu-id="4de2e-102">Accessing Custom Assemblies Through Expressions</span></span>
  <span data-ttu-id="4de2e-103">一旦您建立自訂組件，請將它提供給報表設計師或是報表伺服器、加入適當的安全性原則，以及將參考加入報表定義中的自訂組件，這樣您就可以使用報表運算式來存取組件中的類別成員。</span><span class="sxs-lookup"><span data-stu-id="4de2e-103">Once you have created a custom assembly, made it available to Report Designer or the report server, added the appropriate security policy, and added a reference to your custom assembly in your report definition, you can access the members of the classes in your assembly using report expressions.</span></span> <span data-ttu-id="4de2e-104">若要在運算式中參考自訂程式碼，您必須在組件中呼叫類別的成員。</span><span class="sxs-lookup"><span data-stu-id="4de2e-104">To refer to custom code in an expression, you must call the member of a class within the assembly.</span></span> <span data-ttu-id="4de2e-105">該如何完成，取決於此方法為靜態或以執行個體為基礎。</span><span class="sxs-lookup"><span data-stu-id="4de2e-105">How you do this depends on whether the method is static or instance-based.</span></span>  
  
## <a name="calling-static-members-from-a-report-definition-file"></a><span data-ttu-id="4de2e-106">呼叫報表定義檔案中的靜態成員</span><span class="sxs-lookup"><span data-stu-id="4de2e-106">Calling Static Members from a Report Definition File</span></span>  
 <span data-ttu-id="4de2e-107">靜態成員屬於類別或是類型本身，而且不屬於具現化物件。</span><span class="sxs-lookup"><span data-stu-id="4de2e-107">Static members belong to the class or type itself and not to an instantiated object.</span></span> <span data-ttu-id="4de2e-108">存取這些成員的方式是從類別直接呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="4de2e-108">These members can be accessed by directly calling them from the class.</span></span> <span data-ttu-id="4de2e-109">您應該盡可能使用靜態成員呼叫報表中的自訂涵數，因為靜態成員的表現最好。</span><span class="sxs-lookup"><span data-stu-id="4de2e-109">You should use static members to call custom functions in a report whenever possible, because static members perform best.</span></span> <span data-ttu-id="4de2e-110">若要呼叫靜態成員，您需要以運算式的形式加以參考，其格式為 =*Namespace.Class.Method*。</span><span class="sxs-lookup"><span data-stu-id="4de2e-110">To call a static member, you need to reference it as an expression that takes the form =*Namespace.Class.Method*.</span></span>  
  
#### <a name="to-call-static-members"></a><span data-ttu-id="4de2e-111">呼叫靜態成員</span><span class="sxs-lookup"><span data-stu-id="4de2e-111">To call static members</span></span>  
  
-   <span data-ttu-id="4de2e-112">若要呼叫靜態成員，請將運算式設定為等於成員的完整名稱，它包含命名空間、類別名稱和成員名稱。</span><span class="sxs-lookup"><span data-stu-id="4de2e-112">To call a static member, set your expression equal to the fully qualified name of the member, which includes the namespace, class name, and member name.</span></span> <span data-ttu-id="4de2e-113">下列範例會呼叫 **ToGBP** 方法，這個方法會將 **StandardCost** 欄位值從美元轉換為英鎊，並將其顯示在報表中：</span><span class="sxs-lookup"><span data-stu-id="4de2e-113">The following example calls the **ToGBP** method, which converts the **StandardCost** field value from dollars to pounds sterling and displays it in a report:</span></span>  
  
    ```  
    =CurrencyConversion.DollarCurrencyConversion.ToGBP(Fields!StandardCost.Value)  
    ```  
  
### <a name="important-information-regarding-static-fields-and-properties"></a><span data-ttu-id="4de2e-114">有關靜態欄位與屬性的重要資訊</span><span class="sxs-lookup"><span data-stu-id="4de2e-114">Important Information Regarding Static Fields and Properties</span></span>  
 <span data-ttu-id="4de2e-115">目前，會在相同的應用程式網域中執行所有的報表。</span><span class="sxs-lookup"><span data-stu-id="4de2e-115">Currently, all reports are executed in the same application domain.</span></span> <span data-ttu-id="4de2e-116">這表示含有使用者特定的靜態資料會向相同報表的其他執行個體公開此資料。</span><span class="sxs-lookup"><span data-stu-id="4de2e-116">This means that reports with user-specific, static data expose this data to other instances of the same report.</span></span> <span data-ttu-id="4de2e-117">這個情況可能會使一個使用者的靜態資料，可供目前執行特定報表的所有使用者使用。</span><span class="sxs-lookup"><span data-stu-id="4de2e-117">This condition might make it possible for the static data of one user to be available to all users currently running a particular report.</span></span> <span data-ttu-id="4de2e-118">基於這個理由，強烈建議您不要在自訂組件或是在 **Code** 元素中使用靜態欄位或是屬性；請改在報表中用執行個體欄位或是屬性。</span><span class="sxs-lookup"><span data-stu-id="4de2e-118">For this reason, it is highly recommended that you not use static fields or properties in custom assemblies or in the **Code** element; instead, use instance fields or properties in your reports.</span></span> <span data-ttu-id="4de2e-119">靜態方法仍然可以使用，因為它們不會儲存狀態或是資料。</span><span class="sxs-lookup"><span data-stu-id="4de2e-119">Static methods can still be used, because they do not store state or data.</span></span>  
  
## <a name="calling-instance-members-from-a-report-definition-file"></a><span data-ttu-id="4de2e-120">呼叫報表定義檔案中的執行個體成員</span><span class="sxs-lookup"><span data-stu-id="4de2e-120">Calling Instance Members from a Report Definition File</span></span>  
 <span data-ttu-id="4de2e-121">如果您的自訂組件包含需要在報表定義中存取的執行個體成員，則必須將類別的執行個體名稱加入報表。</span><span class="sxs-lookup"><span data-stu-id="4de2e-121">If your custom assembly contains instance members that you need to access in a report definition, you must add an instance name for your class to the report.</span></span> <span data-ttu-id="4de2e-122">您可以使用 [報表屬性]\*\*\*\* 對話方塊的 [程式碼]\*\*\*\* 索引標籤，來為類別新增執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="4de2e-122">You can add an instance name for a class using the **Code** tab of the **Report Properties** dialog.</span></span> <span data-ttu-id="4de2e-123">如需詳細資訊，請參閱[報表設計師中運算式的自訂程式碼及組件參考 &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4de2e-123">For more information about adding instances of classes to a report, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
 <span data-ttu-id="4de2e-124">若要呼叫靜態成員，您需要將它參考為採用 = Code 格式的運算式 *。InstanceName. 方法*。</span><span class="sxs-lookup"><span data-stu-id="4de2e-124">To call a static member, you need to reference it as an expression that takes the form = Code *.InstanceName.Method*.</span></span>  
  
#### <a name="to-call-instance-members"></a><span data-ttu-id="4de2e-125">呼叫執行個體成員</span><span class="sxs-lookup"><span data-stu-id="4de2e-125">To call instance members</span></span>  
  
-   <span data-ttu-id="4de2e-126">若要呼叫自訂組件的執行個體成員，您必須參考 **Code** 關鍵字，加上執行個體名稱及方法。</span><span class="sxs-lookup"><span data-stu-id="4de2e-126">To call an instance member of a custom assembly, you must reference the **Code** keyword followed by the instance name and the method.</span></span> <span data-ttu-id="4de2e-127">下列範例會呼叫 **ToEUR** 執行個體方法，這個方法會將 **StandardCost** 欄位值從美元轉換為歐元，並將其顯示在報表中：</span><span class="sxs-lookup"><span data-stu-id="4de2e-127">The following example calls an instance method **ToEUR** which converts the **StandardCost** field value from dollars to euros and displays it in a report:</span></span>  
  
    ```  
    =Code.m_myDollarCoversion.ToEUR(Fields!StandardCost.Value)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4de2e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4de2e-128">See Also</span></span>  
 [<span data-ttu-id="4de2e-129">將自訂組件與報表搭配使用</span><span class="sxs-lookup"><span data-stu-id="4de2e-129">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
