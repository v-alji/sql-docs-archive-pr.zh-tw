---
title: 維度翻譯 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], translations
- multiple language support [Analysis Services]
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- LCIDs
- translations [Analysis Services], dimensions
ms.assetid: 38fc1e05-2ac9-4816-b52b-dfd19c3a43a2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f31773ad871ef7e3fc8f99d57e7a9099335b899
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706889"
---
# <a name="dimension-translations"></a><span data-ttu-id="c9be8-102">維度翻譯</span><span class="sxs-lookup"><span data-stu-id="c9be8-102">Dimension Translations</span></span>
  <span data-ttu-id="c9be8-103">翻譯是一種簡單的機制，用來將顯示的標籤和標題從某個語言變成另一個語言。</span><span class="sxs-lookup"><span data-stu-id="c9be8-103">A translation is a simple mechanism to change the displayed labels and captions from one language to another.</span></span> <span data-ttu-id="c9be8-104">每一個翻譯都會定義成一組值：具有翻譯文字的字串以及具有語言識別碼的數字。</span><span class="sxs-lookup"><span data-stu-id="c9be8-104">Each translation is defined as a pair of values: a string with the translated text, and a number with the language ID.</span></span> <span data-ttu-id="c9be8-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的所有物件都可使用翻譯。</span><span class="sxs-lookup"><span data-stu-id="c9be8-105">Translations are available for all objects in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="c9be8-106">維度也可以將屬性值翻譯。</span><span class="sxs-lookup"><span data-stu-id="c9be8-106">Dimensions can also have the attribute values translated.</span></span> <span data-ttu-id="c9be8-107">用戶端應用程式負責尋找使用者已定義的語言設定，並將所有標題和標籤切換成以該語言顯示。</span><span class="sxs-lookup"><span data-stu-id="c9be8-107">The client application is responsible for finding the language setting that the user has defined, and switch to display all captions and labels to that language.</span></span> <span data-ttu-id="c9be8-108">物件可以有您想要的任何翻譯數目。</span><span class="sxs-lookup"><span data-stu-id="c9be8-108">An object can have as many translations as you want.</span></span>  
  
 <span data-ttu-id="c9be8-109">簡單的 <xref:Microsoft.AnalysisServices.Translation> 物件是由語言識別碼和翻譯的標題所組成。</span><span class="sxs-lookup"><span data-stu-id="c9be8-109">A simple <xref:Microsoft.AnalysisServices.Translation> object is composed of: language ID number, and translated caption.</span></span> <span data-ttu-id="c9be8-110">語言識別碼是具有語言識別碼的 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="c9be8-110">The language ID number is an `Integer` with the language ID.</span></span> <span data-ttu-id="c9be8-111">翻譯的標題則是翻譯的文字。</span><span class="sxs-lookup"><span data-stu-id="c9be8-111">The translated caption is the translated text.</span></span>  
  
 <span data-ttu-id="c9be8-112">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，維度轉譯是維度名稱的特定語言標記法、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件名稱或其成員之一，例如標題、成員或階層層級。</span><span class="sxs-lookup"><span data-stu-id="c9be8-112">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], a dimension translation is a language-specific representation of the name of a dimension, the name of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object or one of its members, such as a caption, member, or hierarchy level.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="c9be8-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]也支援 cube 物件的翻譯。</span><span class="sxs-lookup"><span data-stu-id="c9be8-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] also supports translations of cube objects.</span></span>  
  
 <span data-ttu-id="c9be8-114">翻譯會針對可支援多種語言的用戶端應用程式，提供伺服器支援。</span><span class="sxs-lookup"><span data-stu-id="c9be8-114">Translations provide server support for client applications that can support multiple languages.</span></span> <span data-ttu-id="c9be8-115">通常，檢視 Cube 及其維度的使用者來自許多不同國家 (地區)。</span><span class="sxs-lookup"><span data-stu-id="c9be8-115">Frequently, users from different countries view a cube and its dimensions.</span></span> <span data-ttu-id="c9be8-116">可將 Cube 及其維度的各種元素翻譯成不同語言則十分有用，如此這些使用者就可檢視和了解 Cube。</span><span class="sxs-lookup"><span data-stu-id="c9be8-116">It is useful to be able to translate various elements of a cube and its dimensions into a different language so that these users can view and understand the cube.</span></span> <span data-ttu-id="c9be8-117">例如，法國的商務使用者使用法文地區設定的工作站存取 Cube 時，就可用法文查看物件屬性值。</span><span class="sxs-lookup"><span data-stu-id="c9be8-117">For example, a business user in France can access a cube from a workstation with a French locale setting, and see the object property values in French.</span></span> <span data-ttu-id="c9be8-118">而德國的商務使用者使用德文地區設定的工作站存取相同 Cube 時，就可用德文查看相同的物件屬性值。</span><span class="sxs-lookup"><span data-stu-id="c9be8-118">However, a business user in Germany who accesses the same cube from a workstation with a German locale setting sees the same object property values in German.</span></span>  
  
 <span data-ttu-id="c9be8-119">用戶端電腦的定序和語言資訊是以地區設定識別碼 (LCID) 的格式予以儲存。</span><span class="sxs-lookup"><span data-stu-id="c9be8-119">The collation and language information for the client computer is stored in the form of a locale identifier (LCID).</span></span> <span data-ttu-id="c9be8-120">連接時，用戶端將 LCID 傳遞至 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c9be8-120">Upon connection, the client passes the LCID to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="c9be8-121">執行個體會使用 LCID 來決定在提供 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件的中繼資料時要使用的翻譯集。</span><span class="sxs-lookup"><span data-stu-id="c9be8-121">The instance uses the LCID to determine which set of translations to use when providing metadata for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects.</span></span> <span data-ttu-id="c9be8-122">如果 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件不包含指定的翻譯，則使用預設語言來傳回內容給用戶端。</span><span class="sxs-lookup"><span data-stu-id="c9be8-122">If an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object does not contain the specified translation, the default language is used to return the content back to the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9be8-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9be8-123">See Also</span></span>  
 <span data-ttu-id="c9be8-124">[Cube 翻譯](../multidimensional-models-olap-logical-cube-objects/cube-translations.md) </span><span class="sxs-lookup"><span data-stu-id="c9be8-124">[Cube Translations](../multidimensional-models-olap-logical-cube-objects/cube-translations.md) </span></span>  
 <span data-ttu-id="c9be8-125">[翻譯 &#40;Analysis Services&#41;](../translations-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="c9be8-125">[Translations &#40;Analysis Services&#41;](../translations-analysis-services.md) </span></span>  
 [<span data-ttu-id="c9be8-126">全球化秘訣和最佳作法 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c9be8-126">Globalization Tips and Best Practices &#40;Analysis Services&#41;</span></span>](../globalization-tips-and-best-practices-analysis-services.md)  
  
  
