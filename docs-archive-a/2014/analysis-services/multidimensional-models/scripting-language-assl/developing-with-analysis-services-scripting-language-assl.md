---
title: 使用 Analysis Services 指令碼語言進行開發 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services Scripting Language
- ASSL
ms.assetid: ce9aca4d-b7ad-451e-bb7f-20c2b0c03f29
author: minewiskan
ms.author: owend
ms.openlocfilehash: fbb64c120e67d5b4ac12e7bd77f0e0c4e5736757
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596357"
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a><span data-ttu-id="ac3ea-102">使用 Analysis Services 指令碼語言 (ASSL) 開發</span><span class="sxs-lookup"><span data-stu-id="ac3ea-102">Developing with Analysis Services Scripting Language (ASSL)</span></span>
  <span data-ttu-id="ac3ea-103">Analysis Services 指令碼語言 (ASSL) 是 XMLA 的延伸模組，它會加入物件定義語言和命令語言，以便直接在伺服器上建立及管理 Analysis Services 結構。</span><span class="sxs-lookup"><span data-stu-id="ac3ea-103">Analysis Services Scripting Language (ASSL) is an extension to XMLA that adds an object definition language and command language for creating and managing Analysis Services structures directly on the server.</span></span> <span data-ttu-id="ac3ea-104">您可以在自訂應用程式中使用 ASSL，以便透過 XMLA 通訊協定與 Analysis Services 通訊。</span><span class="sxs-lookup"><span data-stu-id="ac3ea-104">You can use ASSL in custom application to communicate with Analysis Services over the XMLA protocol.</span></span> <span data-ttu-id="ac3ea-105">ASSL 是由兩個部分所組成：</span><span class="sxs-lookup"><span data-stu-id="ac3ea-105">ASSL is made up of two parts:</span></span>  
  
-   <span data-ttu-id="ac3ea-106">資料定義語言 (DDL) 或是物件定義語言會定義及描述 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 的執行個體，以及執行個體包含的資料庫與資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="ac3ea-106">A Data Definition Language (DDL), or object definition language, defines and describes an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], as well as the databases and database objects that the instance contains.</span></span>  
  
-   <span data-ttu-id="ac3ea-107">將動作命令 (例如 `Create`、`Alter` 或 `Process`) 傳送到 Analysis Services 執行個體的命令語言。</span><span class="sxs-lookup"><span data-stu-id="ac3ea-107">A command language that sends action commands, such as `Create`, `Alter`, or `Process`, to an instance of Analysis Services.</span></span> <span data-ttu-id="ac3ea-108">[XML for Analysis &#40;XMLA&#41; 參考](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)中會討論此命令語言。</span><span class="sxs-lookup"><span data-stu-id="ac3ea-108">This command language is discussed in the [XML for Analysis  &#40;XMLA&#41; Reference](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference).</span></span>  
  
 <span data-ttu-id="ac3ea-109">若要檢視在 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] 中描述多維度方案的 ASSL，您可以在專案層級使用 [檢視程式碼] 命令。</span><span class="sxs-lookup"><span data-stu-id="ac3ea-109">To view the ASSL that describes a multidimensional solution in [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], you can use the View Code command at the project level.</span></span> <span data-ttu-id="ac3ea-110">您也可以在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 中使用 XMLA 查詢編輯器來建立或編輯 ASSL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="ac3ea-110">You can also create or edit ASSL script in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] using the XMLA query editor.</span></span> <span data-ttu-id="ac3ea-111">您建立的指令碼可在伺服器上用來管理物件或執行命令。</span><span class="sxs-lookup"><span data-stu-id="ac3ea-111">The scripts you build can be used to manage objects or run commands on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac3ea-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac3ea-112">See Also</span></span>  
 <span data-ttu-id="ac3ea-113">[ASSL 物件和物件特性](assl-objects-and-object-characteristics.md) </span><span class="sxs-lookup"><span data-stu-id="ac3ea-113">[ASSL Objects and Object Characteristics](assl-objects-and-object-characteristics.md) </span></span>  
 <span data-ttu-id="ac3ea-114">[ASSL XML 慣例](assl-xml-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="ac3ea-114">[ASSL XML Conventions](assl-xml-conventions.md) </span></span>  
 [<span data-ttu-id="ac3ea-115">資料來源和繫結 &#40;SSAS 多維度&#41;</span><span class="sxs-lookup"><span data-stu-id="ac3ea-115">Data Sources and Bindings &#40;SSAS Multidimensional&#41;</span></span>](../data-sources-and-bindings-ssas-multidimensional.md)  
  
  
