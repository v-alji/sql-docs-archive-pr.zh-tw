---
title: 開發自訂 Foreach 列舉值的使用者介面 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services], custom foreach enumerators
- custom foreach enumerators [Integration Services], developing custom user interface
ms.assetid: 8aa4aa80-c9ba-42b3-ba87-ae5ea5d3cac3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 500c67f1ee4577190d7a24286bbfeed0347e92fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596206"
---
# <a name="developing-a-user-interface-for-a-custom-foreach-enumerator"></a><span data-ttu-id="8521e-102">開發自訂 ForEach 列舉值的使用者介面</span><span class="sxs-lookup"><span data-stu-id="8521e-102">Developing a User Interface for a Custom ForEach Enumerator</span></span>
  <span data-ttu-id="8521e-103">在您已覆寫可提供自訂功能的基底類別之屬性與方法的實作之後，可能會想要針對 Foreach 列舉值建立自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="8521e-103">After you have overridden the implementation of the properties and methods of the base class to provide your custom functionality, you may want to create a custom user interface for your Foreach enumerator.</span></span> <span data-ttu-id="8521e-104">如果您未建立自訂使用者介面，使用者可以使用 [屬性] 視窗來設定新的自訂 Foreach 列舉值。</span><span class="sxs-lookup"><span data-stu-id="8521e-104">If you do not create a custom user interface, users can only configure the new custom Foreach enumerator by using the Properties window.</span></span>  
  
 <span data-ttu-id="8521e-105">在自訂的使用者介面專案或是組件中，您可以建立可實作 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI> 的類別。</span><span class="sxs-lookup"><span data-stu-id="8521e-105">In a custom user interface project or assembly, you create a class that implements <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI>.</span></span> <span data-ttu-id="8521e-106">這個類別衍生自 System.Windows.Forms.UserControl，通常它是用於建立複合控制項，以主控其他的 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="8521e-106">This class derives from System.Windows.Forms.UserControl, which is typically used to create a composite control to host other Windows Forms controls.</span></span> <span data-ttu-id="8521e-107">在 **Foreach 迴圈編輯器**中，您建立的控制項是顯示在 [集合] 索引標籤的 [列舉值設定] 區域中。</span><span class="sxs-lookup"><span data-stu-id="8521e-107">The control that you create is displayed in the **Enumerator configuration** area of the **Collection** tab of the **Foreach Loop Editor**.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8521e-108">在簽署和組建自訂使用者介面，以及在全域組件快取中安裝它之後 (如[建立、部署和偵錯自訂物件](../building-deploying-and-debugging-custom-objects.md)所述)，請記得在 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> 的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> 屬性中提供這個類別的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="8521e-108">After signing and building your custom user interface and installing it in the global assembly cache as described in [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md), remember to provide the fully qualified name of this class in the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>.</span></span>  
  
## <a name="coding-the-user-interface-control-class"></a><span data-ttu-id="8521e-109">撰寫使用者介面控制項類別的程式碼</span><span class="sxs-lookup"><span data-stu-id="8521e-109">Coding the User Interface Control Class</span></span>  
  
### <a name="initializing-the-user-interface"></a><span data-ttu-id="8521e-110">初始化使用者介面</span><span class="sxs-lookup"><span data-stu-id="8521e-110">Initializing the User Interface</span></span>  
 <span data-ttu-id="8521e-111">您會覆寫 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.Initialize%2A> 方法來快取主機物件的參考，以及連線管理員集合與定義在封裝中之變數的參考。</span><span class="sxs-lookup"><span data-stu-id="8521e-111">You override the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.Initialize%2A> method to cache references to the host object, and to the collections of connection managers and variables defined in the package.</span></span>  
  
### <a name="setting-properties-on-the-user-interface-control"></a><span data-ttu-id="8521e-112">在使用者介面控制項上設定屬性</span><span class="sxs-lookup"><span data-stu-id="8521e-112">Setting Properties on the User Interface Control</span></span>  
 <span data-ttu-id="8521e-113">衍生使用者介面類別的 UserControl 類別，是用來作為複合控制項以主控其他的 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="8521e-113">The UserControl class, from which the user interface class is derived, is intended for use as a composite control to host other Windows Forms controls.</span></span> <span data-ttu-id="8521e-114">因為這個類別會主控其他的控制項，所以您可以設計自訂使用者介面，方法是在任何 Windows Form 應用程式中，拖放控制項、排列它們、設定其屬性以及在執行階段回應其事件。</span><span class="sxs-lookup"><span data-stu-id="8521e-114">Because this class hosts other controls, you can design your custom user interface by dragging and dropping controls, arranging them, setting their properties, and responding at run time to their events as in any Windows Forms application.</span></span>  
  
### <a name="saving-settings"></a><span data-ttu-id="8521e-115">節省設定</span><span class="sxs-lookup"><span data-stu-id="8521e-115">Saving Settings</span></span>  
 <span data-ttu-id="8521e-116">您會覆寫 <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.SaveSettings%2A> 方法，以便在使用者關閉編輯器時，從控制項將使用者選取的值複製到列舉值的屬性。</span><span class="sxs-lookup"><span data-stu-id="8521e-116">You override the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.SaveSettings%2A> method to copy the values selected by the user from the controls to the properties of the enumerator when the user closes the editor.</span></span>  
  
<span data-ttu-id="8521e-117">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="8521e-117">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="8521e-118">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="8521e-118">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="8521e-119">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="8521e-119">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="8521e-120">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="8521e-120">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8521e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8521e-121">See Also</span></span>  
 <span data-ttu-id="8521e-122">[建立自訂 Foreach 列舉值](creating-a-custom-foreach-enumerator.md) </span><span class="sxs-lookup"><span data-stu-id="8521e-122">[Creating a Custom Foreach Enumerator](creating-a-custom-foreach-enumerator.md) </span></span>  
 [<span data-ttu-id="8521e-123">撰寫自訂 Foreach 列舉值的程式碼</span><span class="sxs-lookup"><span data-stu-id="8521e-123">Coding a Custom Foreach Enumerator</span></span>](coding-a-custom-foreach-enumerator.md)  
  
  
