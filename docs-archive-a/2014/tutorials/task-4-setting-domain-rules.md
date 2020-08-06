---
title: 工作4：設定定義域規則 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3a7162ba-cf2f-481f-830d-bb6a02823827
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 42bdbd0228fdd3515f68ce830581f445242768e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585685"
---
# <a name="task-4-setting-domain-rules"></a><span data-ttu-id="582b0-102">工作 4：設定定義域規則</span><span class="sxs-lookup"><span data-stu-id="582b0-102">Task 4: Setting Domain Rules</span></span>
  <span data-ttu-id="582b0-103">在這項工作中，您會建立**連絡人電子郵件**網域的規則，以驗證電子郵件地址的結尾是否為\*\* \@ adventure-works.com\*\*。</span><span class="sxs-lookup"><span data-stu-id="582b0-103">In this task, you create a rule for the **Contact Email** domain to verify if the email address ends with **\@adventure-works.com**.</span></span> <span data-ttu-id="582b0-104">如需此頁面的詳細資訊，請參閱[建立定義域規則](https://msdn.microsoft.com/library/hh510397.aspx)主題。</span><span class="sxs-lookup"><span data-stu-id="582b0-104">See [Creating a Domain Rule](https://msdn.microsoft.com/library/hh510397.aspx) topic for more details on the page.</span></span>  
  
1.  <span data-ttu-id="582b0-105">按一下 [**網域] 清單**中的 [**連絡人電子郵件**]。</span><span class="sxs-lookup"><span data-stu-id="582b0-105">Click **Contact Email** in the **Domain list**.</span></span>  
  
2.  <span data-ttu-id="582b0-106">切換至右窗格中的 [**定義域規則**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="582b0-106">Switch to the **Domain Rules** tab in the right pane.</span></span>  
  
     <span data-ttu-id="582b0-107">![[加入新的定義域規則] 工具列按鈕](../../2014/tutorials/media/et-settingdomainrules-01.jpg "[加入新的定義域規則] 工具列按鈕")</span><span class="sxs-lookup"><span data-stu-id="582b0-107">![Add a New Domain Rule Toolbar Button](../../2014/tutorials/media/et-settingdomainrules-01.jpg "Add a New Domain Rule Toolbar Button")</span></span>  
  
3.  <span data-ttu-id="582b0-108">在右窗格中，按一下工具列上的 [**加入新的定義域規則**] 按鈕 (查看影像) 新增規則。</span><span class="sxs-lookup"><span data-stu-id="582b0-108">In the right pane, click **Add a new domain rule** button on the toolbar (see the image) to add a rule.</span></span>  
  
4.  <span data-ttu-id="582b0-109">輸入 [**規則名稱**的**電子郵件驗證**]，然後按**enter**。</span><span class="sxs-lookup"><span data-stu-id="582b0-109">Type **Email Validation** for the **rule name** and press **ENTER**.</span></span> <span data-ttu-id="582b0-110">[作用中] 核取方塊預設為核取**狀態**。</span><span class="sxs-lookup"><span data-stu-id="582b0-110">The **Active** check box should be checked by default.</span></span> <span data-ttu-id="582b0-111">這個控制項可讓您暫時停用規則。</span><span class="sxs-lookup"><span data-stu-id="582b0-111">This control allows you to deactivate a rule temporarily.</span></span>  
  
5.  <span data-ttu-id="582b0-112">在 [**建立規則**] 窗格中，按一下**向下箭**號，然後選取 [**值結尾為**]。</span><span class="sxs-lookup"><span data-stu-id="582b0-112">In the **Build a Rule** pane, click **down arrow**, and select **Value ends with**.</span></span>  
  
6.  <span data-ttu-id="582b0-113">在文字方塊中輸入\*\* \@ adventure-works.com\*\* ，然後按**tab**鍵。</span><span class="sxs-lookup"><span data-stu-id="582b0-113">Type **\@adventure-works.com** in the text box and press **TAB**.</span></span> <span data-ttu-id="582b0-114">您可以在 [**建立規則**] 窗格中，按一下 **[將新條件新增至選取的子句**] 工具列按鈕來新增更多條件。</span><span class="sxs-lookup"><span data-stu-id="582b0-114">You can add more conditions by clicking **Add a new condition to the selected clause** toolbar button in the **Build a Rule** pane.</span></span>  
  
     <span data-ttu-id="582b0-115">![電子郵件驗證規則](../../2014/tutorials/media/et-settingdomainrules-02.jpg "電子郵件驗證規則")</span><span class="sxs-lookup"><span data-stu-id="582b0-115">![Email Validation Rule](../../2014/tutorials/media/et-settingdomainrules-02.jpg "Email Validation Rule")</span></span>  
  
7.  <span data-ttu-id="582b0-116">在右窗格中，按一下工具列上的 **[在測試資料上執行選取的定義域規則**] 按鈕，對範例資料測試規則。</span><span class="sxs-lookup"><span data-stu-id="582b0-116">Click **Run the selected domain rule on test data** button on the toolbar in the right pane to test the rule against sample data.</span></span>  
  
     <span data-ttu-id="582b0-117">![[在測試資料上執行定義域規則] 工具列按鈕](../../2014/tutorials/media/et-settingdomainrules-03.jpg "[在測試資料上執行定義域規則] 工具列按鈕")</span><span class="sxs-lookup"><span data-stu-id="582b0-117">![Run the Domain Rule on Test Data Toolbar Button](../../2014/tutorials/media/et-settingdomainrules-03.jpg "Run the Domain Rule on Test Data Toolbar Button")</span></span>  
  
8.  <span data-ttu-id="582b0-118">在 [**測試定義域規則**] 對話方塊中，按一下工具列上**的 [加入定義域規則的新測試詞彙**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="582b0-118">In the **Test Domain Rule** dialog box, click **Adds a new testing term for the domain rule** button on the toolbar.</span></span>  
  
     <span data-ttu-id="582b0-119">![[測試定義域規則] 對話方塊](../../2014/tutorials/media/et-settingdomainrules-04.jpg "[測試定義域規則] 對話方塊")</span><span class="sxs-lookup"><span data-stu-id="582b0-119">![Test Domain Rule Dialog Box](../../2014/tutorials/media/et-settingdomainrules-04.jpg "Test Domain Rule Dialog Box")</span></span>  
  
9. <span data-ttu-id="582b0-120">在 [**連絡人電子郵件**] 資料行中，輸入**frank7 \@ adventure-works.com** (有效的值) 。</span><span class="sxs-lookup"><span data-stu-id="582b0-120">Type **frank7\@adventure-works.com** (a valid value) in the **Contact Email** column.</span></span>  
  
10. <span data-ttu-id="582b0-121">重複先前的兩個步驟，將**joe2 \@ adventure-work.com** (不正確值，而不是 ' ) 。</span><span class="sxs-lookup"><span data-stu-id="582b0-121">Repeat previous two steps to add **joe2\@adventure-work.com** (an invalid value with no 's').</span></span>  
  
11. <span data-ttu-id="582b0-122">按一下 [上一步] 按鈕 (在工具列上) 的**所有詞彙測試定義域規則**，以根據規則測試輸入資料。</span><span class="sxs-lookup"><span data-stu-id="582b0-122">Click the last button (**Test the domain rule on all the terms**) on the toolbar to test the input data against the rule.</span></span>  
  
     <span data-ttu-id="582b0-123">![[對所有詞彙測試定義域規則] 工具列按鈕](../../2014/tutorials/media/et-settingdomainrules-05.jpg "[對所有詞彙測試定義域規則] 工具列按鈕")</span><span class="sxs-lookup"><span data-stu-id="582b0-123">![Test the Domain Rule on All Terms Toolbar Button](../../2014/tutorials/media/et-settingdomainrules-05.jpg "Test the Domain Rule on All Terms Toolbar Button")</span></span>  
  
12. <span data-ttu-id="582b0-124">請注意，第一個輸入顯示為有效的項目，第二個輸入則顯示為無效的項目。</span><span class="sxs-lookup"><span data-stu-id="582b0-124">Notice that the first entry is shown as a valid item and the second one as an invalid item.</span></span>  
  
     <span data-ttu-id="582b0-125">![測試定義域規則結果](../../2014/tutorials/media/et-settingdomainrules-06.jpg "測試定義域規則結果")</span><span class="sxs-lookup"><span data-stu-id="582b0-125">![Test Domain Rule Results](../../2014/tutorials/media/et-settingdomainrules-06.jpg "Test Domain Rule Results")</span></span>  
  
13. <span data-ttu-id="582b0-126">按一下 [**關閉**] 以關閉 [**測試定義域規則**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="582b0-126">Click **Close** to close the **Test Domain Rule** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="582b0-127">後續步驟</span><span class="sxs-lookup"><span data-stu-id="582b0-127">Next Step</span></span>  
 [<span data-ttu-id="582b0-128">工作 5：設定以詞彙為主的關聯</span><span class="sxs-lookup"><span data-stu-id="582b0-128">Task 5: Setting Term Based Relationships</span></span>](../../2014/tutorials/task-5-setting-term-based-relationships.md)  
  
  
