---
title: 記錄和編寫 Analysis Services 資料庫的腳本 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- XML for Analysis, scripts
- XMLA, scripts
- scripts [Analysis Services], databases
- documenting databases
- databases [Analysis Services], documenting
- databases [Analysis Services], scripts
ms.assetid: 125044e2-8d36-4733-8743-8bb68ff9aa4e
author: minewiskan
ms.author: owend
ms.openlocfilehash: cfe008b0d6903d7d012eb57d41d6e50240202ec8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599695"
---
# <a name="document-and-script-an-analysis-services-database"></a><span data-ttu-id="f7ffd-102">記錄和編寫 Analysis Services 資料庫的指令碼</span><span class="sxs-lookup"><span data-stu-id="f7ffd-102">Document and Script an Analysis Services Database</span></span>
  <span data-ttu-id="f7ffd-103">部署 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫之後，您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來輸出資料庫或資料庫所含之物件的中繼資料，作為 XML for Analysis (XMLA) 指令碼。</span><span class="sxs-lookup"><span data-stu-id="f7ffd-103">After an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database is deployed, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to output the metadata of the database, or of an object contained in the database, as an XML for Analysis (XMLA) script.</span></span> <span data-ttu-id="f7ffd-104">您可以將此指令碼輸出到新的 **[XMLA 查詢編輯器]** 視窗、到檔案或到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="f7ffd-104">You can output this script to a new **XMLA Query Editor** window, to a file, or to the Clipboard.</span></span> <span data-ttu-id="f7ffd-105">如需 XMLA 的詳細資訊，請參閱[Analysis Services 指令碼語言 &#40;ASSL&#41; 參考](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)。</span><span class="sxs-lookup"><span data-stu-id="f7ffd-105">For more information about XMLA, see [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).</span></span>  
  
 <span data-ttu-id="f7ffd-106">產生的 XMLA 指令碼會使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 指令碼語言 (ASSL) 元素，來定義指令碼所包含的物件。</span><span class="sxs-lookup"><span data-stu-id="f7ffd-106">The generated XMLA script uses [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language (ASSL) elements to define the objects contained by the script.</span></span> <span data-ttu-id="f7ffd-107">如果您產生 CREATE 指令碼，則所產生的 XMLA 指令碼會包含 XMLA **Create** 命令和 ASSL 元素，您可用它們在執行個體上建立整個 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫結構。</span><span class="sxs-lookup"><span data-stu-id="f7ffd-107">If you generated a CREATE script, the resulting XMLA script contains an XMLA **Create** command and ASSL elements that can be used to create the entire [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database structure on an instance.</span></span> <span data-ttu-id="f7ffd-108">如果您產生 ALTER 指令碼，則所產生的 XMLA 指令碼會包含 XMLA **Alter** 命令和 ASSL 元素，您可用它們將現有的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫結構還原至建立指令碼時的資料庫狀態。</span><span class="sxs-lookup"><span data-stu-id="f7ffd-108">If you generated an ALTER script, the resulting XMLA script contains an XMLA **Alter** command and ASSL elements that can be used to restore the structure of an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database to the state of the database at the time the script was created.</span></span>  
  
 <span data-ttu-id="f7ffd-109">您有許多方式可以使用從 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫產生的 XMLA 指令碼，包括：</span><span class="sxs-lookup"><span data-stu-id="f7ffd-109">You can use the generated XMLA script from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in many ways, including:</span></span>  
  
-   <span data-ttu-id="f7ffd-110">若要維護可讓您重新建立所有資料庫物件和權限的備份指令碼。</span><span class="sxs-lookup"><span data-stu-id="f7ffd-110">To maintain a backup script that allows you to recreate all the database objects and permissions.</span></span>  
  
-   <span data-ttu-id="f7ffd-111">若要建立或更新資料庫開發的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f7ffd-111">To create or update database development code.</span></span>  
  
-   <span data-ttu-id="f7ffd-112">若要從現有的結構描述中建立測試或開發環境。</span><span class="sxs-lookup"><span data-stu-id="f7ffd-112">To create a test or development environment from an existing schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7ffd-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7ffd-113">See Also</span></span>  
 <span data-ttu-id="f7ffd-114">[修改或刪除 Analysis Services 資料庫](modify-or-delete-an-analysis-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="f7ffd-114">[Modify or Delete an Analysis Services Database](modify-or-delete-an-analysis-services-database.md) </span></span>  
 <span data-ttu-id="f7ffd-115">[&#40;XMLA&#41;的 Alter 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="f7ffd-115">[Alter Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) </span></span>  
 [<span data-ttu-id="f7ffd-116">Create 元素 &#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="f7ffd-116">Create Element &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)  
  
  
