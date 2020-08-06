---
title: 工作1：建立知識庫和定義域 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 7d74a60b-8933-4038-bcbb-4e9dcc4f70e9
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce1b22e3d677e831a1d518dacc1267ad0e6be236
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699058"
---
# <a name="task-1-creating-a-knowledge-base-and-domains"></a><span data-ttu-id="ef5ed-102">工作 1：建立知識庫和定義域</span><span class="sxs-lookup"><span data-stu-id="ef5ed-102">Task 1: Creating a Knowledge Base and Domains</span></span>
  <span data-ttu-id="ef5ed-103">在這項工作中，您會建立**供應商**知識庫，並建立用於清理資料和比對資料以移除重複專案的定義域。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-103">In this task, you create the **Suppliers** knowledge base and create domains that is used for cleansing data and matching data to remove duplicates.</span></span>  
  
1.  <span data-ttu-id="ef5ed-104">啟動**Data Quality Client**。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-104">Launch **Data Quality Client**.</span></span> <span data-ttu-id="ef5ed-105">按一下 [**開始**]，指向 [**所有程式**]，按一下 [ **Microsoft SQL Server 2012**，按一下 [ **Data Quality Services**]，然後按一下 [ **Data Quality Client**]。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-105">Click **Start**, point to **All Programs**, click **Microsoft SQL Server 2012**, click **Data Quality Services**, and then click **Data Quality Client**.</span></span>  
  
2.  <span data-ttu-id="ef5ed-106">在 [**連接到伺服器**] 對話方塊中，選取安裝 DQS 的資料庫伺服器實例，然後按一下 [**連接]**。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-106">In the **Connect to Server** dialog box, select the database server instance on which the DQS is installed, and click **Connect**.</span></span>  
  
     <span data-ttu-id="ef5ed-107">![[連接到伺服器] 對話方塊](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-01.jpg "連接到伺服器對話方塊")</span><span class="sxs-lookup"><span data-stu-id="ef5ed-107">![Connect to Server Dialog Box](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-01.jpg "Connect to Server Dialog Box")</span></span>  
  
3.  <span data-ttu-id="ef5ed-108">在 [Data Quality Client] 首頁的 [**知識庫管理**] 窗格中，按一下 [**新增知識庫**]。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-108">In the Data Quality Client home page, in the **Knowledge Base Management** pane, click **New Knowledge Base**.</span></span>  
  
     <span data-ttu-id="ef5ed-109">![知識庫管理 - 新增知識庫](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-02.jpg "知識庫管理 - 新增知識庫")</span><span class="sxs-lookup"><span data-stu-id="ef5ed-109">![Knowledge Base Management - New KB](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-02.jpg "Knowledge Base Management - New KB")</span></span>  
  
4.  <span data-ttu-id="ef5ed-110">輸入 [**供應商**] 做為知識庫的**名稱**。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-110">Enter **Suppliers** for **Name** of the knowledge base.</span></span>  
  
     <span data-ttu-id="ef5ed-111">![新增知識庫 - 定義域管理](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-03.jpg "新增知識庫 - 定義域管理")</span><span class="sxs-lookup"><span data-stu-id="ef5ed-111">![New Knowledge Base - Domain Management](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-03.jpg "New Knowledge Base - Domain Management")</span></span>  
  
5.  <span data-ttu-id="ef5ed-112">確認 [**從欄位建立知識庫**] 設定為 [**無**]，因為您是從頭開始建立**供應商**知識庫。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-112">Confirm that **Create Knowledge Base from** field is set to **None** since you are creating the **Suppliers** knowledge base from scratch.</span></span>  
  
6.  <span data-ttu-id="ef5ed-113">確認已針對**活動**選取 [**定義域管理**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-113">Confirm that **Domain Management** is selected for the **Activity** and click **Next**.</span></span> <span data-ttu-id="ef5ed-114">[定義域管理] 活動可讓您在知識庫中建立和管理定義域。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-114">The Domain Management activity lets you create and manage domains in the knowledge base.</span></span>  
  
7.  <span data-ttu-id="ef5ed-115">在 [**定義域管理**] 視窗中，按一下 [**建立定義域**] 工具列按鈕來建立定義域。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-115">In the **Domain Management** window, click **Create a domain** toolbar button to create a domain.</span></span>  
  
     <span data-ttu-id="ef5ed-116">![[建立定義域] 工具列按鈕](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-04.jpg "[建立定義域] 工具列按鈕")</span><span class="sxs-lookup"><span data-stu-id="ef5ed-116">![Create Domain Toolbar Button](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-04.jpg "Create Domain Toolbar Button")</span></span>  
  
8.  <span data-ttu-id="ef5ed-117">在 [**建立定義域**] 對話方塊中，輸入 [**供應商識別碼**] 作為 [**功能變數名稱**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-117">In the **Create Domain** dialog box, type **Supplier ID** for the **Domain Name**, and click **OK**.</span></span>  
  
     <span data-ttu-id="ef5ed-118">![[建立定義域] 對話方塊](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-05.jpg "[建立定義域] 對話方塊")</span><span class="sxs-lookup"><span data-stu-id="ef5ed-118">![Create Domain Dialog Box](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-05.jpg "Create Domain Dialog Box")</span></span>  
  
9. <span data-ttu-id="ef5ed-119">重複上述步驟來建立以下包含所有預設值的定義域。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-119">Repeat previous step to create the following domains with all the default settings.</span></span> <span data-ttu-id="ef5ed-120">為了讓教學課程保持簡單，您可以將所有定義域的**資料類型**設定為 [**字串**]。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-120">To keep the tutorial simple, you set the **Data Type** of all the domains as **String**.</span></span> <span data-ttu-id="ef5ed-121">其他允許的資料類型包括：整數、小數和日期。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-121">The other allowed data types are: Integer, Decimal, and Date.</span></span> <span data-ttu-id="ef5ed-122">選取 [**使用前置值**] 選項時 (預設) ，所有同義字都會取代為輸出中同義字群組的前置值。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-122">When the **Use Leading Values** option is selected (default), all synonyms are replaced with the leading value of the synonym group in the output.</span></span> <span data-ttu-id="ef5ed-123">將 [正規化**字串**] 選項設定 (預設值) 會移除定義域值中的任何特殊字元。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-123">Setting **Normalize String** option (default) removes any special characters in the domain values.</span></span> <span data-ttu-id="ef5ed-124">[**格式化輸出至**] 選項可讓您選取當定義域中的資料值為輸出時所套用的格式。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-124">The **Format Output to** option lets you select the formatting that is applied when the data values in the domain are output.</span></span> <span data-ttu-id="ef5ed-125">選取 [**啟用檢查**器] (預設) ，以在擴展定義域時針對所有字串值執行拼寫檢查。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-125">Select **Enable Speller** (default) to run Speller on all string values when populating the domain.</span></span> <span data-ttu-id="ef5ed-126">[**語言**] 設定會指定您想要套用之**拼寫**器的語言版本。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-126">The **Language** setting specifies which language version of the **Speller** you want to apply.</span></span> <span data-ttu-id="ef5ed-127">選取 [**停用語法錯誤演算法**] 以填入定義域，而不檢查字串值是否有語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-127">Select **Disable Syntax Error Algorithms** to populate the domain without checking string values for syntax errors.</span></span> <span data-ttu-id="ef5ed-128">如需詳細資訊，請參閱 MSDN library 中的[建立網域](https://msdn.microsoft.com/library/hh510401.aspx)主題。</span><span class="sxs-lookup"><span data-stu-id="ef5ed-128">See [Create a Domain](https://msdn.microsoft.com/library/hh510401.aspx) topic in the MSDN library for more details.</span></span>  
  
    -   <span data-ttu-id="ef5ed-129">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="ef5ed-129">Supplier Name</span></span>  
  
    -   <span data-ttu-id="ef5ed-130">連絡人電子郵件</span><span class="sxs-lookup"><span data-stu-id="ef5ed-130">Contact Email</span></span>  
  
    -   <span data-ttu-id="ef5ed-131">[地址行]</span><span class="sxs-lookup"><span data-stu-id="ef5ed-131">Address Line</span></span>  
  
    -   <span data-ttu-id="ef5ed-132">城市</span><span class="sxs-lookup"><span data-stu-id="ef5ed-132">City</span></span>  
  
    -   <span data-ttu-id="ef5ed-133">州</span><span class="sxs-lookup"><span data-stu-id="ef5ed-133">State</span></span>  
  
    -   <span data-ttu-id="ef5ed-134">國家/地區</span><span class="sxs-lookup"><span data-stu-id="ef5ed-134">Country</span></span>  
  
    -   <span data-ttu-id="ef5ed-135">Zip</span><span class="sxs-lookup"><span data-stu-id="ef5ed-135">Zip</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="ef5ed-136">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ef5ed-136">Next Step</span></span>  
 [<span data-ttu-id="ef5ed-137">工作 2：手動新增定義域值</span><span class="sxs-lookup"><span data-stu-id="ef5ed-137">Task 2: Adding Domain Values Manually</span></span>](../../2014/tutorials/task-2-adding-domain-values-manually.md)  
  
  
