---
title: 建立資料處理延伸模組程式庫 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], namespace assignments
- library [Reporting Services]
- assigning namespaces to extensions
ms.assetid: 82f4b71b-dd39-467d-8d8c-6771eb2b12de
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3c14ed699e94c7d8ed0f6f3d727e9ba6e355b7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710390"
---
# <a name="creating-a-data-processing-extension-library"></a><span data-ttu-id="ee13d-102">建立資料處理延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="ee13d-102">Creating a Data Processing Extension Library</span></span>
  <span data-ttu-id="ee13d-103">每個您建立的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組都應該指派到唯一的命名空間，並內建於程式庫或是組件檔中。</span><span class="sxs-lookup"><span data-stu-id="ee13d-103">Each [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension you create should be assigned to a unique namespace and built into a library or assembly file.</span></span> <span data-ttu-id="ee13d-104">命名空間的正確名稱並不重要，但是它必須是唯一且未與其他延伸模組共用。</span><span class="sxs-lookup"><span data-stu-id="ee13d-104">The exact name of the namespace is not important, but it must be unique and not shared with any other extension.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="ee13d-105">為 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 隨附的資料處理延伸模組使用命名空間 <xref:Microsoft.ReportingServices.DataProcessing>。</span><span class="sxs-lookup"><span data-stu-id="ee13d-105">uses the namespace <xref:Microsoft.ReportingServices.DataProcessing> for the data processing extensions that ship with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="ee13d-106">您應該為公司的資料處理延伸模組建立自己的唯一命名空間。</span><span class="sxs-lookup"><span data-stu-id="ee13d-106">You should create your own unique namespaces for your company's data processing extensions.</span></span>  
  
 <span data-ttu-id="ee13d-107">下列範例示範開始 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組的程式碼，這是使用包含資料處理介面與任何公用程式類別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="ee13d-107">The following example shows the code to begin a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension, which uses the namespaces that contain the data processing interfaces and any utility classes.</span></span>  
  
```vb  
Imports System  
Imports Microsoft.ReportingServices.DataProcessing  
Imports Microsoft.ReportingServices.Interfaces  
  
Namespace CompanyName.ExtensionName  
   ...  
```  
  
```csharp  
using System;  
using Microsoft.ReportingServices.DataProcessing;  
using Microsoft.ReportingServices.Interfaces;  
  
namespace CompanyName.ExtensionName  
{  
   ...  
```  
  
 <span data-ttu-id="ee13d-108">編譯 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組時，您必須提供 Microsoft.ReportingServices.Interfaces.dll 的參考給編譯器，因為其中包含資料處理延伸模組介面。</span><span class="sxs-lookup"><span data-stu-id="ee13d-108">When compiling a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension, you must supply to the compiler a reference to Microsoft.ReportingServices.Interfaces.dll, because the data processing extension interfaces are contained there.</span></span> <span data-ttu-id="ee13d-109">需要 <xref:Microsoft.ReportingServices.DataProcessing> 命名空間實作資料處理延伸模組介面，而且需要 <xref:Microsoft.ReportingServices.Interfaces> 命名空間實作 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 介面。</span><span class="sxs-lookup"><span data-stu-id="ee13d-109">The <xref:Microsoft.ReportingServices.DataProcessing> namespace is needed to implement the data processing extension interfaces, and the <xref:Microsoft.ReportingServices.Interfaces> namespace is needed to implement the <xref:Microsoft.ReportingServices.Interfaces.IExtension> interface.</span></span> <span data-ttu-id="ee13d-110">例如，如果所有包含程式碼以實作用 C# 撰寫的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組之檔案，都在單一目錄中並且副檔名為 .cs，則會從該目錄發出下列命令，以編譯儲存在 CompanyName.ExtensionName.dll 中的檔案。</span><span class="sxs-lookup"><span data-stu-id="ee13d-110">For example, if all the files containing the code to implement a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension written in C# were in a single directory with the extension .cs, the following command would be issued from that directory to compile the files stored in CompanyName.ExtensionName.dll.</span></span>  
  
```csharp  
csc /t:library /out:CompanyName.ExtensionName.dll *.cs /r:System.dll /r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
 <span data-ttu-id="ee13d-111">下列程式碼範例示範將用於副檔名為 .vb 之 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 檔案的命令。</span><span class="sxs-lookup"><span data-stu-id="ee13d-111">The following code example shows the command that would be used for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] files with the extension .vb.</span></span>  
  
```vb  
vbc /t:library /out:CompanyName.ExtensionName.dll *.vb /r:System.dll /r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
> [!NOTE]  
>  <span data-ttu-id="ee13d-112">您也可以使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 來設計、開發和建立資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ee13d-112">You can also design, develop, and build your data processing extension using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="ee13d-113">如需有關在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中開發組件的詳細資訊，請參閱 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 文件集。</span><span class="sxs-lookup"><span data-stu-id="ee13d-113">For more information about developing assemblies in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], see your [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee13d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee13d-114">See Also</span></span>  
 <span data-ttu-id="ee13d-115">[Reporting Services 延伸模組](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="ee13d-115">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="ee13d-116">[實作資料處理延伸模組](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="ee13d-116">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="ee13d-117">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="ee13d-117">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
