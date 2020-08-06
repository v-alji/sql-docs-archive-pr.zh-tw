---
title: 建立傳遞延伸模組程式庫 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], namespace assignments
- library [Reporting Services]
- assigning namespaces to extensions
ms.assetid: 63b32f93-4bab-4b07-bd72-39a47aca1cda
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c9891c2b0c1bb9c7d495b3ab1f8f2267ce04b79f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708930"
---
# <a name="creating-a-delivery-extension-library"></a><span data-ttu-id="e606d-102">建立傳遞延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="e606d-102">Creating a Delivery Extension Library</span></span>
  <span data-ttu-id="e606d-103">每個您建立的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 傳遞延伸模組都應該指派到唯一的命名空間，並內建於程式庫或是組件檔中。</span><span class="sxs-lookup"><span data-stu-id="e606d-103">Each [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension you create should be assigned to a unique namespace and built into a library or assembly file.</span></span> <span data-ttu-id="e606d-104">命名空間的正確名稱並不重要，但是它必須是唯一且未與其他延伸模組共用。</span><span class="sxs-lookup"><span data-stu-id="e606d-104">The exact name of the namespace is not important, but it must be unique and not shared with any other extension.</span></span> <span data-ttu-id="e606d-105">您應該為公司的傳遞延伸模組建立自己的唯一命名空間。</span><span class="sxs-lookup"><span data-stu-id="e606d-105">You should create your own unique namespaces for your company's delivery extensions.</span></span>  
  
 <span data-ttu-id="e606d-106">下列範例示範開始 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 傳遞延伸模組的程式碼，這是使用包含傳遞介面與任何公用程式類別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="e606d-106">The following example shows the code to begin a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, which uses the namespaces that contain the delivery interfaces and any utility classes.</span></span>  
  
```vb  
Imports System  
Imports Microsoft.ReportingServices.Interfaces  
  
Namespace CompanyName.ExtensionName  
   ...  
```  
  
```csharp  
using System;  
using Microsoft.ReportingServices.Interfaces;  
  
namespace CompanyName.ExtensionName  
{  
   ...  
```  
  
 <span data-ttu-id="e606d-107">編譯 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 傳遞延伸模組時，您必須提供 Microsoft.ReportingServices.Interfaces.dll 的參考給編譯器，因為其中包含傳遞延伸模組介面與類別。</span><span class="sxs-lookup"><span data-stu-id="e606d-107">When compiling a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, you must supply to the compiler a reference to Microsoft.ReportingServices.Interfaces.dll, because the delivery extension interfaces and classes are contained there.</span></span> <span data-ttu-id="e606d-108">需要 <xref:Microsoft.ReportingServices.Interfaces> 命名空間實作 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 介面、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 介面等等。</span><span class="sxs-lookup"><span data-stu-id="e606d-108">The <xref:Microsoft.ReportingServices.Interfaces> namespace is needed to implement the <xref:Microsoft.ReportingServices.Interfaces.IExtension> interface, the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interface, and more.</span></span> <span data-ttu-id="e606d-109">例如，如果所有包含程式碼以實作用 C# 撰寫的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 傳遞延伸模組之檔案，都在單一目錄中並且副檔名為 .cs，則會從該目錄發出下列命令，以編譯儲存在 CompanyName.ExtensionName.dll 中的檔案。</span><span class="sxs-lookup"><span data-stu-id="e606d-109">For example, if all the files containing the code to implement a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension written in C# were in a single directory with the extension .cs, the following command would be issued from that directory to compile the files stored in CompanyName.ExtensionName.dll.</span></span>  
  
```csharp  
csc /t:library /out:CompanyName.ExtensionName.dll *.cs /r:System.dll   
/r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
 <span data-ttu-id="e606d-110">下列程式碼範例示範將用於副檔名為 .vb 之 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 檔案的命令。</span><span class="sxs-lookup"><span data-stu-id="e606d-110">The following code example shows the command that would be used for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] files with the extension .vb.</span></span>  
  
```vb  
vbc /t:library /out:CompanyName.ExtensionName.dll *.vb /r:System.dll   
/r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
> [!NOTE]  
>  <span data-ttu-id="e606d-111">您也可以使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 來設計、開發和建立傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="e606d-111">You can also design, develop, and build your delivery extension using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="e606d-112">如需有關在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中開發組件的詳細資訊，請參閱 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 文件集。</span><span class="sxs-lookup"><span data-stu-id="e606d-112">For more information about developing assemblies in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], see your [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e606d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e606d-113">See Also</span></span>  
 <span data-ttu-id="e606d-114">[Reporting Services 延伸模組](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="e606d-114">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="e606d-115">[實作傳遞延伸模組](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="e606d-115">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="e606d-116">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="e606d-116">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
