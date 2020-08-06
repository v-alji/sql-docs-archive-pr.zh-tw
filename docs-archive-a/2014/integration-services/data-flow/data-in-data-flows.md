---
title: 資料流程中的資料 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting data types [Integration Services]
- comparing data
- data types [Integration Services], data flow
- parsing [Integration Services]
- string comparisons
- data flow [Integration Services], data options
ms.assetid: 8a9d6186-eb52-48e3-997e-021f24d458a3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a073db65768c413b6cbe648c757ad75d80bd318e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708513"
---
# <a name="data-in-data-flows"></a><span data-ttu-id="f0f08-102">資料流程中的資料</span><span class="sxs-lookup"><span data-stu-id="f0f08-102">Data in Data Flows</span></span>
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="f0f08-103">提供一組資料流程中使用的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f0f08-103">provides a set of data types that are used in data flows.</span></span>  
  
## <a name="data-type-conversion"></a><span data-ttu-id="f0f08-104">資料類型轉換</span><span class="sxs-lookup"><span data-stu-id="f0f08-104">Data Type Conversion</span></span>  
 <span data-ttu-id="f0f08-105">加入資料流程中的來源可以將來源資料轉換為 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="f0f08-105">The source that you add to a data flow converts the source data to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types.</span></span> <span data-ttu-id="f0f08-106">後續轉換可以將資料轉換為不同的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料類型，而根據載入資料之資料存放區的類型，目的地可以將最終 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料類型轉換為目的地資料存放區所要求的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f0f08-106">Subsequent transformations may convert the data to different [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, and depending on the type of data store into which data is loaded, destinations may convert the final [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type to the data type required by the destination data store.</span></span> <span data-ttu-id="f0f08-107">如需詳細資訊，請參閱 [Integration Services 資料類型](integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f0f08-107">For more information, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="f0f08-108">如果要將資料轉換為 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料類型，資料流程元件會剖析資料。</span><span class="sxs-lookup"><span data-stu-id="f0f08-108">To convert the data to an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type, a data flow component parses the data.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="f0f08-109">提供快速剖析與標準剖析兩種資料剖析類型。</span><span class="sxs-lookup"><span data-stu-id="f0f08-109">provides two types of data parsing: fast parse and standard parse.</span></span> <span data-ttu-id="f0f08-110">大部分的資料流程元件僅可以使用標準剖析；但是，「一般檔案」來源和「資料轉換」既可以使用快速剖析，也可以使用標準剖析。</span><span class="sxs-lookup"><span data-stu-id="f0f08-110">Most data flow components can use only standard parsing; however, the Flat File source and the Data Conversion transformation can use either fast parse or standard parse.</span></span> <span data-ttu-id="f0f08-111">如需詳細資訊，請參閱 [剖析資料](parsing-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f0f08-111">For more information, see [Parsing Data](parsing-data.md).</span></span>  
  
## <a name="data-type-comparison"></a><span data-ttu-id="f0f08-112">資料類型比較</span><span class="sxs-lookup"><span data-stu-id="f0f08-112">Data Type Comparison</span></span>  
 <span data-ttu-id="f0f08-113">許多轉換會比較資料值。</span><span class="sxs-lookup"><span data-stu-id="f0f08-113">Many transformations compare data values.</span></span> <span data-ttu-id="f0f08-114">例如，「彙總」轉換對值進行比較是為了彙總一組資料列的值，「排序」轉換對值進行比較是為了將其排序，而「查閱」轉換則是在個別參考資料表中將值互相進行比較。</span><span class="sxs-lookup"><span data-stu-id="f0f08-114">For example, the Aggregate transformation compares values for the purpose of aggregating values across a set of data rows, the Sort transformation compares values in order to sort them, and the Lookup transformation compares values against values in a separate reference table.</span></span> <span data-ttu-id="f0f08-115">為了指定應如何比較字串，轉換會包含一組比較選項，例如是否忽略區分大小寫、如何處理日語文字中的假名類型，以及是否忽略字串中的空白字元。</span><span class="sxs-lookup"><span data-stu-id="f0f08-115">To specify how strings should be compared, the transformation includes a set of comparison options such as whether to ignore case sensitivity, how to handle kana types in Japanese text, and whether to ignore white-space characters in the string.</span></span> <span data-ttu-id="f0f08-116">如需詳細資訊，請參閱 [Comparing String Data](comparing-string-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f0f08-116">For more information, see [Comparing String Data](comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="f0f08-117">運算式評估工具還會在評估變數、優先順序條件約束及轉換所使用的運算式時，對資料值進行比較。</span><span class="sxs-lookup"><span data-stu-id="f0f08-117">The expression evaluator also compares data values when it evaluates the expressions that variables, precedence constraints, and transformations use.</span></span>  
  
## <a name="data-flow-troubleshooting"></a><span data-ttu-id="f0f08-118">資料流程疑難排解</span><span class="sxs-lookup"><span data-stu-id="f0f08-118">Data Flow Troubleshooting</span></span>  
 <span data-ttu-id="f0f08-119">將封裝部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目錄之後，您可以在執行期間分析封裝中的資料流程，以檢查效能或尋找其他問題。</span><span class="sxs-lookup"><span data-stu-id="f0f08-119">Once you have deployed a package to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] catalog, you can analyze the data flow in the package during execution to check performance or look for other issues.</span></span> <span data-ttu-id="f0f08-120">可使用標準報表查看封裝狀態及記錄，並可以查詢資料庫檢視以取得執行封裝的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f0f08-120">Standard reports are available that allow you to view package status and history, and you can query database views that provide detailed information about package execution.</span></span> <span data-ttu-id="f0f08-121">您還可以在執行期間動態地加入及刪除資料點選，以鎖定您封裝的某個特定元件。</span><span class="sxs-lookup"><span data-stu-id="f0f08-121">You also can dynamically add and remove data taps during execution to target specific components of your package.</span></span> <span data-ttu-id="f0f08-122">如需詳細資訊，請參閱 [資料流程分析](data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="f0f08-122">For more information, see [Analysis of Data Flow](data-flow.md).</span></span>  
  
  
