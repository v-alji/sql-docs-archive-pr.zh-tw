---
title: 步驟 2：建立損毀的檔案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cd0b18dc-66c3-4d88-86ef-8e40cb660fae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0dd5fbe942774192881489e9ea430672f9da5083
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595177"
---
# <a name="step-2-creating-a-corrupted-file"></a><span data-ttu-id="cb4a3-102">步驟 2:建立損毀的檔案</span><span class="sxs-lookup"><span data-stu-id="cb4a3-102">Step 2: Creating a Corrupted File</span></span>
  <span data-ttu-id="cb4a3-103">若要示範組態和轉換錯誤的處理，您必須建立處理時會造成元件失敗的範例一般檔案。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-103">In order to demonstrate the configuration and handling of transformation errors, you will have to create a sample flat file that when processed causes a component to fail.</span></span>  
  
 <span data-ttu-id="cb4a3-104">在這項工作中，您會建立現有的範例一般檔案的副本。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-104">In this task, you will create a copy of an existing sample flat file.</span></span> <span data-ttu-id="cb4a3-105">然後您會在記事本開啟檔案及編輯 [CurrencyID]\*\*\*\* 資料行，以確定在轉換查閱期間，它無法產生相符者。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-105">You will then open the file in Notepad and edit the **CurrencyID** column to ensure that it will fail to produce a match during the transformations lookup.</span></span> <span data-ttu-id="cb4a3-106">在處理新檔案時，查閱失敗會造成 [貨幣索引鍵查閱] 轉換失敗，因而使得其餘的封裝也失敗。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-106">When the new file is processed, the lookup failure will cause the Currency Key Lookup transformation to fail and therefore fail the rest of the package.</span></span> <span data-ttu-id="cb4a3-107">在您建立損毀範例檔案之後，將執行封裝來檢視封裝失敗。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-107">After you have created the corrupted sample file, you will run the package to view the package failure.</span></span>  
  
### <a name="to-create-a-corrupted-sample-flat-file"></a><span data-ttu-id="cb4a3-108">若要建立損毀範例一般檔案</span><span class="sxs-lookup"><span data-stu-id="cb4a3-108">To create a corrupted sample flat file</span></span>  
  
1.  <span data-ttu-id="cb4a3-109">在記事本或任何其他文字編輯器中開啟 Currency_VEB.txt 檔。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-109">In Notepad or any other text editor, open the Currency_VEB.txt file.</span></span>  
  
     <span data-ttu-id="cb4a3-110">範例資料隨附在 SSIS 課程封裝中。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-110">The sample data is included with the SSIS Lesson packages.</span></span> <span data-ttu-id="cb4a3-111">若要下載範例資料和課程封裝，請執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-111">To download the sample data and the lesson packages, do the following.</span></span>  
  
    1.  <span data-ttu-id="cb4a3-112">流覽至[Integration Services 的產品範例](https://go.microsoft.com/fwlink/?LinkID=267527)。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-112">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkID=267527).</span></span>  
  
    2.  <span data-ttu-id="cb4a3-113">按一下 [**下載**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-113">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="cb4a3-114">按一下 SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-114">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
2.  <span data-ttu-id="cb4a3-115">使用文字編輯器的 [尋找和取代] 功能來尋找的所有實例 `VEB` ，並將其取代為 `BAD` 。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-115">Use the text editor's find and replace feature to find all instances of `VEB` and replace them with `BAD`.</span></span>  
  
3.  <span data-ttu-id="cb4a3-116">在與其他範例資料檔案相同的資料夾中，將修改過的檔案儲存為 `Currency_BAD.txt` 。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-116">In the same folder as the other sample data files, save the modified file as `Currency_BAD.txt`.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="cb4a3-117">請確定與 `Currency_BAD.txt` 其他範例資料檔案儲存在相同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-117">Make sure that `Currency_BAD.txt` is saved the same folder as the other sample data files.</span></span>  
  
4.  <span data-ttu-id="cb4a3-118">關閉文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-118">Close your text editor.</span></span>  
  
### <a name="to-verify-that-an-error-will-occur-during-run-time"></a><span data-ttu-id="cb4a3-119">若要確認在執行階段會發生錯誤</span><span class="sxs-lookup"><span data-stu-id="cb4a3-119">To verify that an error will occur during run time</span></span>  
  
1.  <span data-ttu-id="cb4a3-120">在 [偵錯] 功能表上，按一下 [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-120">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="cb4a3-121">在資料流程的第三次反覆運算中，[查閱貨幣索引鍵] 轉換會嘗試處理 Currency_BAD.txt 檔，但轉換會失敗。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-121">On the third iteration of the data flow, the Lookup Currency Key transformation tries to process the Currency_BAD.txt file, and the transformation will fail.</span></span> <span data-ttu-id="cb4a3-122">轉換失敗將造成整個封裝失敗。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-122">The failure of the transformation will cause the whole package to fail.</span></span>  
  
2.  <span data-ttu-id="cb4a3-123">在 [偵錯] 功能表上，按一下 [停止偵錯]。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-123">On the **Debug** menu, click **Stop Debugging**.</span></span>  
  
3.  <span data-ttu-id="cb4a3-124">在設計介面中，按一下 [執行結果]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-124">On the design surface, click the **Execution Results** tab.</span></span>  
  
4.  <span data-ttu-id="cb4a3-125">瀏覽記錄並確認已發生下列無法處理的錯誤：</span><span class="sxs-lookup"><span data-stu-id="cb4a3-125">Browse through the log and verify that the following unhandled error occurred:</span></span>  
  
     `[Lookup Currency Key[27]] Error: Row yielded no match during lookup.`  
  
    > [!NOTE]  
    >  <span data-ttu-id="cb4a3-126">數字 27 是元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-126">The number 27 is the ID of the component.</span></span> <span data-ttu-id="cb4a3-127">當您建立資料流程時會指派此值，您封裝中的值可能不同。</span><span class="sxs-lookup"><span data-stu-id="cb4a3-127">This value is assigned when you build the data flow, and the value in your package may be different.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="cb4a3-128">後續步驟</span><span class="sxs-lookup"><span data-stu-id="cb4a3-128">Next Steps</span></span>  
 [<span data-ttu-id="cb4a3-129">步驟 3：新增錯誤流程重新導向</span><span class="sxs-lookup"><span data-stu-id="cb4a3-129">Step 3: Adding Error Flow Redirection</span></span>](lesson-4-3-adding-error-flow-redirection.md)  
  
  
