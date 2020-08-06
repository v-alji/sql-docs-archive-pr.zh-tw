---
title: 文字編輯器的選項 (-XML-其他頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 1a9509f0-c663-4b31-b396-7f5dc4371651
author: rothja
ms.author: jroth
ms.openlocfilehash: d937368d30122442ccbc40372a6b8e1cabc141e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686470"
---
# <a name="options-text-editor---xml---miscellaneous-page"></a><span data-ttu-id="fadae-102">選項 (文字編輯器 - XML - 其他頁面)</span><span class="sxs-lookup"><span data-stu-id="fadae-102">Options (Text Editor - XML - Miscellaneous Page)</span></span>

<span data-ttu-id="fadae-103">[選項]\*\*\*\* 對話方塊，可以讓您變更 XML 編輯器的自動完成和結構描述設定。</span><span class="sxs-lookup"><span data-stu-id="fadae-103">The **Options** dialog box lets you change the autocompletion and schema settings for the XML Editor.</span></span> <span data-ttu-id="fadae-104">在 [工具]\*\*\*\* 功能表上，按一下 [選項]\*\*\*\*，展開 [文字編輯器]\*\*\*\* 資料夾，按一下 [XML]\*\*\*\*，然後按一下 [其他]\*\*\*\*，即可使用這些設定。</span><span class="sxs-lookup"><span data-stu-id="fadae-104">These settings are available when, on the **Tools** menu, you click **Options**, expand the **Text Editor** folder, click **XML** and then click **Miscellaneous** .</span></span>  
  
## <a name="auto-insert"></a><span data-ttu-id="fadae-105">自動插入</span><span class="sxs-lookup"><span data-stu-id="fadae-105">Auto Insert</span></span>  
 <span data-ttu-id="fadae-106">**結尾標記**</span><span class="sxs-lookup"><span data-stu-id="fadae-106">**Close tags**</span></span>  
 <span data-ttu-id="fadae-107">文字編輯器在撰寫 XML 元素時會加入結尾標記。</span><span class="sxs-lookup"><span data-stu-id="fadae-107">The Text Editor adds close tags when authoring XML elements.</span></span> <span data-ttu-id="fadae-108">如果選取元素開始標記，編輯器會插入相符的結尾標記，包括相符的命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="fadae-108">If an element start tag is selected, the editor inserts the matching close tag, including a matching namespace prefix.</span></span> <span data-ttu-id="fadae-109">依預設，這個核取方塊為已選取。</span><span class="sxs-lookup"><span data-stu-id="fadae-109">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="fadae-110">**屬性引號**</span><span class="sxs-lookup"><span data-stu-id="fadae-110">**Attribute quotes**</span></span>  
 <span data-ttu-id="fadae-111">撰寫 XML 屬性時，編輯器會插入 `="``"` 字元，並將插入號 (**^)** 置於引號內。</span><span class="sxs-lookup"><span data-stu-id="fadae-111">When authoring XML attributes, the editor inserts the `="``"` characters and positions the caret (**^)** inside the quotation marks.</span></span> <span data-ttu-id="fadae-112">依預設，這個核取方塊為已選取。</span><span class="sxs-lookup"><span data-stu-id="fadae-112">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="fadae-113">**命名空間宣告**</span><span class="sxs-lookup"><span data-stu-id="fadae-113">**Namespace declarations**</span></span>  
 <span data-ttu-id="fadae-114">編輯器在需要時會自動插入命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="fadae-114">The editor automatically inserts namespace declarations wherever they are needed.</span></span> <span data-ttu-id="fadae-115">依預設，這個核取方塊為已選取。</span><span class="sxs-lookup"><span data-stu-id="fadae-115">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="fadae-116">**其他標記 (註解、CDATA)**</span><span class="sxs-lookup"><span data-stu-id="fadae-116">**Other markup (Comments, CDATA)**</span></span>  
 <span data-ttu-id="fadae-117">註解、CDATA、DOCTYPE、處理指示，以及其他自動完成的標記。</span><span class="sxs-lookup"><span data-stu-id="fadae-117">Comments, CDATA, DOCTYPE, processing instructions, and other markup is autocompleted.</span></span> <span data-ttu-id="fadae-118">依預設，這個核取方塊為已選取。</span><span class="sxs-lookup"><span data-stu-id="fadae-118">This check box is selected by default.</span></span>  
  
## <a name="network"></a><span data-ttu-id="fadae-119">網路</span><span class="sxs-lookup"><span data-stu-id="fadae-119">Network</span></span>  
 <span data-ttu-id="fadae-120">**自動下載 DTD 和結構描述**</span><span class="sxs-lookup"><span data-stu-id="fadae-120">**Automatically download DTDs and schemas**</span></span>  
 <span data-ttu-id="fadae-121">結構描述和文件類型定義 (DTD) 會從 HTTP 位置自動下載。</span><span class="sxs-lookup"><span data-stu-id="fadae-121">Schemas and document type definitions (DTDs) are automatically downloaded from HTTP locations.</span></span> <span data-ttu-id="fadae-122">此功能使用 System.Net 並啟用 Autoproxy 伺服器偵測。</span><span class="sxs-lookup"><span data-stu-id="fadae-122">This feature uses System.Net with autoproxy server detection enabled.</span></span> <span data-ttu-id="fadae-123">依預設，這個核取方塊為已選取。</span><span class="sxs-lookup"><span data-stu-id="fadae-123">This check box is selected by default.</span></span>  
  
## <a name="outlining"></a><span data-ttu-id="fadae-124">大綱</span><span class="sxs-lookup"><span data-stu-id="fadae-124">Outlining</span></span>  
 <span data-ttu-id="fadae-125">**檔案開啟時進入大綱模式**</span><span class="sxs-lookup"><span data-stu-id="fadae-125">**Enter outlining mode when files open**</span></span>  
 <span data-ttu-id="fadae-126">檔案開啟時啟動大綱功能。</span><span class="sxs-lookup"><span data-stu-id="fadae-126">Turns on the outlining feature when a file is opened.</span></span> <span data-ttu-id="fadae-127">依預設，這個核取方塊為已選取。</span><span class="sxs-lookup"><span data-stu-id="fadae-127">This check box is selected by default.</span></span>  
  
## <a name="caching"></a><span data-ttu-id="fadae-128">Caching</span><span class="sxs-lookup"><span data-stu-id="fadae-128">Caching</span></span>  
 <span data-ttu-id="fadae-129">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="fadae-129">**Schemas**</span></span>  
 <span data-ttu-id="fadae-130">指定結構描述快取的位置。</span><span class="sxs-lookup"><span data-stu-id="fadae-130">Specifies the location of the schema cache.</span></span> <span data-ttu-id="fadae-131">瀏覽按鈕 (...) 會在新視窗中開啟目前的結構描述快取位置。</span><span class="sxs-lookup"><span data-stu-id="fadae-131">The Browse button (...) opens the current schema cache location in a new window.</span></span> <span data-ttu-id="fadae-132">預設位置為 *\<Management Studio install directory>* \xml\schemas。</span><span class="sxs-lookup"><span data-stu-id="fadae-132">The default location is *\<Management Studio install directory>* \Xml\Schemas.</span></span>  
