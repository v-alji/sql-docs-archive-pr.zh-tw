---
title: 字元對應轉換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.charactertrans.f1
helpviewer_keywords:
- mutually exclusive mapping [Integration Services]
- mapping data [Integration Services]
- string functions
- Character Map transformation [Integration Services]
ms.assetid: e0f50eb6-b893-400f-bb8c-fb3072cc2620
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b5fc31e1a3500a7a7b023e43a968e70e5b438dec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597246"
---
# <a name="character-map-transformation"></a><span data-ttu-id="db601-102">字元對應轉換</span><span class="sxs-lookup"><span data-stu-id="db601-102">Character Map Transformation</span></span>
  <span data-ttu-id="db601-103">「字元對應」轉換會套用字串函數，例如從小寫轉換成大寫、字元資料。</span><span class="sxs-lookup"><span data-stu-id="db601-103">The Character Map transformation applies string functions, such as conversion from lowercase to uppercase, to character data.</span></span> <span data-ttu-id="db601-104">此轉換只能在字串資料類型的資料行資料上操作。</span><span class="sxs-lookup"><span data-stu-id="db601-104">This transformation operates only on column data with a string data type.</span></span>  
  
 <span data-ttu-id="db601-105">「字元對應」轉換可就地轉換資料行資料，或將資料行加入至轉換輸出，並將轉換的資料放入新的資料行。</span><span class="sxs-lookup"><span data-stu-id="db601-105">The Character Map transformation can convert column data in place or add a column to the transformation output and put the converted data in the new column.</span></span> <span data-ttu-id="db601-106">您可以將不同組的對應作業套用至同一輸入資料行，並將結果放入不同的資料行。</span><span class="sxs-lookup"><span data-stu-id="db601-106">You can apply different sets of mapping operations to the same input column and put the results in different columns.</span></span> <span data-ttu-id="db601-107">例如，您可以將同一資料行轉換成大寫和小寫，並將結果放入兩個不同的資料行。</span><span class="sxs-lookup"><span data-stu-id="db601-107">For example, you can convert the same column to uppercase and lowercase and put the results in two different columns.</span></span>  
  
 <span data-ttu-id="db601-108">在某些情況下，對應可能會造成資料遭到截斷。</span><span class="sxs-lookup"><span data-stu-id="db601-108">Mapping can, under some circumstances, cause data to be truncated.</span></span> <span data-ttu-id="db601-109">例如，當單一位元組字元對應到使用多位元組表示法的字元時，即可能發生截斷。</span><span class="sxs-lookup"><span data-stu-id="db601-109">For example, truncation can occur when single-byte characters are mapped to characters with a multibyte representation.</span></span> <span data-ttu-id="db601-110">「字元對應」轉換包含錯誤輸出，可用來將截斷的資料導向不同的輸出。</span><span class="sxs-lookup"><span data-stu-id="db601-110">The Character Map transformation includes an error output, which can be used to direct truncated data to separate output.</span></span> <span data-ttu-id="db601-111">如需詳細資訊，請參閱 [處理資料中的錯誤](../error-handling-in-data.md)。</span><span class="sxs-lookup"><span data-stu-id="db601-111">For more information, see [Error Handling in Data](../error-handling-in-data.md).</span></span>  
  
 <span data-ttu-id="db601-112">這個轉換有一個輸入、一個輸出與一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="db601-112">This transformation has one input, one output, and one error output.</span></span>  
  
## <a name="mapping-operations"></a><span data-ttu-id="db601-113">對應作業</span><span class="sxs-lookup"><span data-stu-id="db601-113">Mapping Operations</span></span>  
 <span data-ttu-id="db601-114">下表描述「字元對應」轉換支援的對應作業。</span><span class="sxs-lookup"><span data-stu-id="db601-114">The following table describes the mapping operations that the Character Map transformation supports.</span></span>  
  
|<span data-ttu-id="db601-115">作業</span><span class="sxs-lookup"><span data-stu-id="db601-115">Operation</span></span>|<span data-ttu-id="db601-116">描述</span><span class="sxs-lookup"><span data-stu-id="db601-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db601-117">位元組反轉</span><span class="sxs-lookup"><span data-stu-id="db601-117">Byte reversal</span></span>|<span data-ttu-id="db601-118">反轉位元組的順序。</span><span class="sxs-lookup"><span data-stu-id="db601-118">Reverses byte order.</span></span>|  
|<span data-ttu-id="db601-119">全形</span><span class="sxs-lookup"><span data-stu-id="db601-119">Full width</span></span>|<span data-ttu-id="db601-120">將半形字元對應到全形字元。</span><span class="sxs-lookup"><span data-stu-id="db601-120">Maps half-width characters to full-width characters.</span></span>|  
|<span data-ttu-id="db601-121">半形</span><span class="sxs-lookup"><span data-stu-id="db601-121">Half width</span></span>|<span data-ttu-id="db601-122">將全形字元對應到半形字元。</span><span class="sxs-lookup"><span data-stu-id="db601-122">Maps full-width characters to half-width characters.</span></span>|  
|<span data-ttu-id="db601-123">平假名</span><span class="sxs-lookup"><span data-stu-id="db601-123">Hiragana</span></span>|<span data-ttu-id="db601-124">將片假名字元對應到平假名字元。</span><span class="sxs-lookup"><span data-stu-id="db601-124">Maps katakana characters to hiragana characters.</span></span>|  
|<span data-ttu-id="db601-125">片假名</span><span class="sxs-lookup"><span data-stu-id="db601-125">Katakana</span></span>|<span data-ttu-id="db601-126">將平假名字元對應到片假名字元。</span><span class="sxs-lookup"><span data-stu-id="db601-126">Maps hiragana characters to katakana characters.</span></span>|  
|<span data-ttu-id="db601-127">語言大小寫</span><span class="sxs-lookup"><span data-stu-id="db601-127">Linguistic casing</span></span>|<span data-ttu-id="db601-128">套用語言大小寫取代系統規則。</span><span class="sxs-lookup"><span data-stu-id="db601-128">Applies linguistic casing instead of the system rules.</span></span> <span data-ttu-id="db601-129">語言大小寫是指 Win32 API 針對突厥語系與其他地區設定所提供的 Unicode 簡易大小寫對應功能。</span><span class="sxs-lookup"><span data-stu-id="db601-129">Linguistic casing refers to functionality provided by the Win32 API for Unicode simple case mapping of Turkic and other locales.</span></span>|  
|<span data-ttu-id="db601-130">小寫</span><span class="sxs-lookup"><span data-stu-id="db601-130">Lowercase</span></span>|<span data-ttu-id="db601-131">將字元轉換成小寫。</span><span class="sxs-lookup"><span data-stu-id="db601-131">Converts characters to lowercase.</span></span>|  
|<span data-ttu-id="db601-132">簡體中文</span><span class="sxs-lookup"><span data-stu-id="db601-132">Simplified Chinese</span></span>|<span data-ttu-id="db601-133">將繁體中文字元對應到簡體中文字元。</span><span class="sxs-lookup"><span data-stu-id="db601-133">Maps traditional Chinese characters to simplified Chinese characters.</span></span>|  
|<span data-ttu-id="db601-134">繁體中文</span><span class="sxs-lookup"><span data-stu-id="db601-134">Traditional Chinese</span></span>|<span data-ttu-id="db601-135">將簡體中文字元對應到繁體中文字元。</span><span class="sxs-lookup"><span data-stu-id="db601-135">Maps simplified Chinese characters to traditional Chinese characters.</span></span>|  
|<span data-ttu-id="db601-136">大寫</span><span class="sxs-lookup"><span data-stu-id="db601-136">Uppercase</span></span>|<span data-ttu-id="db601-137">將字元轉換成大寫。</span><span class="sxs-lookup"><span data-stu-id="db601-137">Converts characters to uppercase.</span></span>|  
  
## <a name="mutually-exclusive-mapping-operations"></a><span data-ttu-id="db601-138">互斥對應作業</span><span class="sxs-lookup"><span data-stu-id="db601-138">Mutually Exclusive Mapping Operations</span></span>  
 <span data-ttu-id="db601-139">轉換中可執行一項以上的作業。</span><span class="sxs-lookup"><span data-stu-id="db601-139">More than one operation can be performed in a transformation.</span></span> <span data-ttu-id="db601-140">不過，某些對應作業彼此互斥。</span><span class="sxs-lookup"><span data-stu-id="db601-140">However, some mapping operations are mutually exclusive.</span></span> <span data-ttu-id="db601-141">下表列出當您在同一資料行上使用多項作業時適用的限制。</span><span class="sxs-lookup"><span data-stu-id="db601-141">The following table lists restrictions that apply when you use multiple operations on the same column.</span></span> <span data-ttu-id="db601-142">作業 A 和作業 B 資料行中的作業為互斥。</span><span class="sxs-lookup"><span data-stu-id="db601-142">Operations in the columns Operation A and Operation B are mutually exclusive.</span></span>  
  
|<span data-ttu-id="db601-143">作業 A</span><span class="sxs-lookup"><span data-stu-id="db601-143">Operation A</span></span>|<span data-ttu-id="db601-144">作業 B</span><span class="sxs-lookup"><span data-stu-id="db601-144">Operation B</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="db601-145">小寫</span><span class="sxs-lookup"><span data-stu-id="db601-145">Lowercase</span></span>|<span data-ttu-id="db601-146">大寫</span><span class="sxs-lookup"><span data-stu-id="db601-146">Uppercase</span></span>|  
|<span data-ttu-id="db601-147">平假名</span><span class="sxs-lookup"><span data-stu-id="db601-147">Hiragana</span></span>|<span data-ttu-id="db601-148">片假名</span><span class="sxs-lookup"><span data-stu-id="db601-148">Katakana</span></span>|  
|<span data-ttu-id="db601-149">半形</span><span class="sxs-lookup"><span data-stu-id="db601-149">Half width</span></span>|<span data-ttu-id="db601-150">全形</span><span class="sxs-lookup"><span data-stu-id="db601-150">Full width</span></span>|  
|<span data-ttu-id="db601-151">繁體中文</span><span class="sxs-lookup"><span data-stu-id="db601-151">Traditional Chinese</span></span>|<span data-ttu-id="db601-152">簡體中文</span><span class="sxs-lookup"><span data-stu-id="db601-152">Simplified Chinese</span></span>|  
|<span data-ttu-id="db601-153">小寫</span><span class="sxs-lookup"><span data-stu-id="db601-153">Lowercase</span></span>|<span data-ttu-id="db601-154">平假名、片假名、半形、全形</span><span class="sxs-lookup"><span data-stu-id="db601-154">Hiragana, katakana, half width, full width</span></span>|  
|<span data-ttu-id="db601-155">大寫</span><span class="sxs-lookup"><span data-stu-id="db601-155">Uppercase</span></span>|<span data-ttu-id="db601-156">平假名、片假名、半形、全形</span><span class="sxs-lookup"><span data-stu-id="db601-156">Hiragana, katakana, half width, full width</span></span>|  
  
## <a name="configuration-of-the-character-map-transformation"></a><span data-ttu-id="db601-157">字元對應轉換的組態</span><span class="sxs-lookup"><span data-stu-id="db601-157">Configuration of the Character Map Transformation</span></span>  
 <span data-ttu-id="db601-158">您可以利用下列方式設定「字元對應」轉換：</span><span class="sxs-lookup"><span data-stu-id="db601-158">You configure the Character Map transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="db601-159">指定要轉換的資料行。</span><span class="sxs-lookup"><span data-stu-id="db601-159">Specify the columns to convert.</span></span>  
  
-   <span data-ttu-id="db601-160">指定套用至各資料行的作業。</span><span class="sxs-lookup"><span data-stu-id="db601-160">Specify the operations to apply to each column.</span></span>  
  
 <span data-ttu-id="db601-161">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="db601-161">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="db601-162">如需有關 **[字元對應轉換編輯器]** 對話方塊中可設定屬性的詳細資訊，請參閱 [Character Map Transformation Editor](../../character-map-transformation-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="db601-162">For more information about the properties that you can set in the **Character Map Transformation Editor** dialog box, see [Character Map Transformation Editor](../../character-map-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="db601-163">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="db601-163">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="db601-164">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="db601-164">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="db601-165">Common Properties</span><span class="sxs-lookup"><span data-stu-id="db601-165">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="db601-166">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="db601-166">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="db601-167">如需有關如何設定屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="db601-167">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="db601-168">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="db601-168">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="db601-169">排序合併和合併聯結轉換的資料</span><span class="sxs-lookup"><span data-stu-id="db601-169">Sort Data for the Merge and Merge Join Transformations</span></span>](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
  
