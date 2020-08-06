---
title: 將批註式 XDR 架構轉換為對等的 XSD 架構 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XDR schemas, converting schemas
- annotated XSD schemas, converting schemas
- XDR to XSD Converter tool [SQLXML]
- XDR schemas [SQLXML], converting
- converting annotated schemas
- mapping schema [SQLXML], conversions
- XSD schemas [SQLXML], converting schemas
ms.assetid: 151c94a8-66d3-4c46-a5ff-a22df456940a
author: rothja
ms.author: jroth
ms.openlocfilehash: c36eb17aacb61a47fad0f389de9a3c216202827d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597729"
---
# <a name="converting-annotated-xdr-schemas-to-equivalent-xsd-schemas-sqlxml-40"></a><span data-ttu-id="c0e90-102">將註解式 XDR 結構描述轉換為等效 XSD 結構描述 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="c0e90-102">Converting Annotated XDR Schemas to Equivalent XSD Schemas (SQLXML 4.0)</span></span>
  <span data-ttu-id="c0e90-103">XML 結構描述定義 (XSD) 語言是 XML-Data Reduced (XDR) 結構描述定義語言的後續版本。</span><span class="sxs-lookup"><span data-stu-id="c0e90-103">The XML Schema Definition (XSD) language is the successor to the XML-Data Reduced (XDR) schema definition language.</span></span> <span data-ttu-id="c0e90-104">透過在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 中導入的 XSD 支援，系統會假設新的註解式結構描述是使用 XSD 建立的。</span><span class="sxs-lookup"><span data-stu-id="c0e90-104">With the introduction of XSD support in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, it is assumed that new annotated schemas are created using XSD.</span></span> <span data-ttu-id="c0e90-105">SQLXML 4.0 包含 XDR 轉成 XSD 轉換器工具，這項工具是設計來協助您將現有的註解式 XDR 結構描述轉換成對等的 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="c0e90-105">SQLXML 4.0 includes an XDR to XSD converter tool that is designed to help you convert your existing annotated XDR schemas to equivalent XSD schemas.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c0e90-106">只有當您想要將註解式 XDR 結構描述轉換成 XSD 以便搭配 SQLXML 4.0 使用時，才應該使用這項工具。</span><span class="sxs-lookup"><span data-stu-id="c0e90-106">Use this tool only when you want to convert annotated XDR schemas to XSD for use with SQLXML 4.0.</span></span> <span data-ttu-id="c0e90-107">這不是一般用途的 XDR 轉成 XSD 轉換器工具。</span><span class="sxs-lookup"><span data-stu-id="c0e90-107">This is not a general purpose XDR to XSD converter tool.</span></span> <span data-ttu-id="c0e90-108">在其他環境中使用時，轉換的 XSD 結構描述可能會與原始 XDR 結構描述具有不同的行為。</span><span class="sxs-lookup"><span data-stu-id="c0e90-108">The converted XSD schemas may not behave the same as the original XDR schemas when used in other environments.</span></span>  
  
 <span data-ttu-id="c0e90-109">如果輸入 XDR 檔案在 XML 宣告內部指定了編碼，這就會成為所產生之 XSD 輸出檔案的編碼。</span><span class="sxs-lookup"><span data-stu-id="c0e90-109">If the input XDR file specifies the encoding within the XML declaration, this becomes the encoding of the XSD output file that is generated.</span></span>  
  
 <span data-ttu-id="c0e90-110">轉換器工具 (Cvtschema.exe) 會安裝在 Program Files\SQLXML 4.0\bin 資料夾中，而且它是在命令提示字元中執行。</span><span class="sxs-lookup"><span data-stu-id="c0e90-110">The converter tool (Cvtschema.exe) is installed in the Program Files\SQLXML 4.0\bin folder and is executed at the command prompt.</span></span>  
  
 <span data-ttu-id="c0e90-111">下面是一般語法：</span><span class="sxs-lookup"><span data-stu-id="c0e90-111">This is the general syntax:</span></span>  
  
```  
cvtschema XDRFileName, [-y], [-w] [-?]  
```  
  
 <span data-ttu-id="c0e90-112">其中：</span><span class="sxs-lookup"><span data-stu-id="c0e90-112">Where:</span></span>  
  
 <span data-ttu-id="c0e90-113">XDRFileName</span><span class="sxs-lookup"><span data-stu-id="c0e90-113">XDRFileName</span></span>  
 <span data-ttu-id="c0e90-114">這是要轉換成 XSD 之 XDR 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="c0e90-114">Is the name of the XDR file that is to be converted to XSD.</span></span> <span data-ttu-id="c0e90-115">此工具會讀取輸入 XDR 檔案並且在目前的工作目錄中建立 XSD 輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="c0e90-115">The tool reads the input XDR file and creates an XSD output file in the current working directory.</span></span> <span data-ttu-id="c0e90-116">如果輸入檔案具有 .xdr 或 .xml 副檔名，系統就會使用相同的名稱與 .xsd 副檔名來建立輸出 XSD 檔案。</span><span class="sxs-lookup"><span data-stu-id="c0e90-116">If the input file has an .xdr or .xml extension, the output XSD file is created with the same name but with an .xsd extension.</span></span> <span data-ttu-id="c0e90-117">如果輸入檔案具有 .xml 或 .xdr 以外的副檔名 (或者遺漏副檔名)，系統就會使用相同的名稱來建立輸出檔案，並將 .xsd 副檔名附加至輸入檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="c0e90-117">If the input file extension is other than .xml or .xdr (or if the extension is missing), the output file is created with the same name and the .xsd extension is appended to the input file name.</span></span> <span data-ttu-id="c0e90-118">例如，如果輸入 XDR 檔案名稱為 SampleFile.abc，產生的 XSD 就會儲存成 SampleFile.abc.xsd。</span><span class="sxs-lookup"><span data-stu-id="c0e90-118">For example, if the input XDR file name is SampleFile.abc, the resulting XSD is saved as SampleFile.abc.xsd.</span></span>  
  
 <span data-ttu-id="c0e90-119">-y</span><span class="sxs-lookup"><span data-stu-id="c0e90-119">-y</span></span>  
 <span data-ttu-id="c0e90-120">(選擇性) 使用轉換器工具所產生的 XSD 檔案來覆寫現有的 XSD 檔案。</span><span class="sxs-lookup"><span data-stu-id="c0e90-120">(Optional) Overwrites the existing XSD file with the XSD file that is generated by the converter tool.</span></span> <span data-ttu-id="c0e90-121">如果沒有指定旗標，此工具會提示您指定是否要覆寫現有的 XSD 檔案，並提供變更輸出檔案名稱的選項。</span><span class="sxs-lookup"><span data-stu-id="c0e90-121">If the flag is not specified, the tool prompts you to specify whether you want to overwrite the existing XSD file and gives you the option to change the output file name.</span></span>  
  
 <span data-ttu-id="c0e90-122">-w</span><span class="sxs-lookup"><span data-stu-id="c0e90-122">-w</span></span>  
 <span data-ttu-id="c0e90-123">(選擇性) 傳回在轉換程序中由此工具產生的非嚴重警告。</span><span class="sxs-lookup"><span data-stu-id="c0e90-123">(Optional) Returns nonfatal warnings that are generated in the conversion process by the tool.</span></span> <span data-ttu-id="c0e90-124">根據預設，此工具只會針對嚴重錯誤顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="c0e90-124">By default, the tool displays messages only for fatal errors.</span></span>  
  
 <span data-ttu-id="c0e90-125">-?</span><span class="sxs-lookup"><span data-stu-id="c0e90-125">-?</span></span>  
 <span data-ttu-id="c0e90-126">傳回您可以使用 `cvtschema` 來指定的選項清單，以及相關說明。</span><span class="sxs-lookup"><span data-stu-id="c0e90-126">Returns a list of options that you can specify with `cvtschema`, along with an explanation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e90-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0e90-127">See Also</span></span>  
 <span data-ttu-id="c0e90-128">[將 XSD 資料類型對應到 XPath 資料類型 &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="c0e90-128">[Mapping XSD Data Types to XPath Data Types &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="c0e90-129">&#40;SQLXML 4.0&#41;的 XSD 注釋</span><span class="sxs-lookup"><span data-stu-id="c0e90-129">XSD Annotations &#40;SQLXML 4.0&#41;</span></span>](../../sqlxml-annotated-xsd-schemas-using/xsd-annotations-sqlxml-4-0.md)  
  
  
