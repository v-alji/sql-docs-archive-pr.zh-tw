---
title: 驗證對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackagevalidate.f1
- sql12.ssis.ssms.isprojectvalidate.f1
ms.assetid: 134e14ce-4f8d-4a20-889a-918014c841d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 69e29d106dc9f4f100bf191911c5c34e0250be8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592175"
---
# <a name="validate-dialog-box"></a><span data-ttu-id="67ea7-102">驗證對話方塊</span><span class="sxs-lookup"><span data-stu-id="67ea7-102">Validate Dialog Box</span></span>
  <span data-ttu-id="67ea7-103">使用 **[驗證]** 對話方塊檢查 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案或封裝中的常見問題。</span><span class="sxs-lookup"><span data-stu-id="67ea7-103">Use the **Validate** dialog box to check for common problems in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a project or package.</span></span>  
  
 <span data-ttu-id="67ea7-104">如果有問題，就會在對話方塊上方顯示一個訊息。</span><span class="sxs-lookup"><span data-stu-id="67ea7-104">If there is a problem, a message is displayed at the top of the dialog box.</span></span> <span data-ttu-id="67ea7-105">否則，「就緒」這個詞會顯示在上方。</span><span class="sxs-lookup"><span data-stu-id="67ea7-105">Otherwise, the term Ready displays at the top.</span></span>  
  
 <span data-ttu-id="67ea7-106">**您想要做什麼事？**</span><span class="sxs-lookup"><span data-stu-id="67ea7-106">**What do you want to do?**</span></span>  
  
-   <span data-ttu-id="67ea7-107">[開啟 [驗證] 對話方塊](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="67ea7-107">[Open the Validate dialog box](#open_dialog)</span></span>  
  
-   <span data-ttu-id="67ea7-108">[設定 [一般] 頁面上的選項](#general)</span><span class="sxs-lookup"><span data-stu-id="67ea7-108">[Set the options on the General page](#general)</span></span>  
  
##  <a name="open-the-validate-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="67ea7-109">開啟 [驗證] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="67ea7-109">Open the Validate dialog box</span></span>  
  
1.  <span data-ttu-id="67ea7-110">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="67ea7-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="67ea7-111">您正在連線到裝載 SSISDB 資料庫的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="67ea7-111">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="67ea7-112">在 [物件總管] 中，展開樹狀目錄以顯示 **[Integration Services 目錄]** 節點。</span><span class="sxs-lookup"><span data-stu-id="67ea7-112">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="67ea7-113">展開 **[SSISDB]** 節點。</span><span class="sxs-lookup"><span data-stu-id="67ea7-113">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="67ea7-114">展開包含您要驗證之專案或封裝的資料夾。</span><span class="sxs-lookup"><span data-stu-id="67ea7-114">Expand the folder that contains the project or package you want to validate.</span></span>  
  
5.  <span data-ttu-id="67ea7-115">以滑鼠右鍵按一下封裝，然後按一下 [驗證]  。</span><span class="sxs-lookup"><span data-stu-id="67ea7-115">Right-click the package or package, and then click **Validate**.</span></span>  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> <span data-ttu-id="67ea7-116">設定 [一般] 頁面上的選項</span><span class="sxs-lookup"><span data-stu-id="67ea7-116">Set the options on the General page</span></span>  
 <span data-ttu-id="67ea7-117">**環境**</span><span class="sxs-lookup"><span data-stu-id="67ea7-117">**Environment**</span></span>  
 <span data-ttu-id="67ea7-118">選取您要用來驗證專案或封裝的環境。</span><span class="sxs-lookup"><span data-stu-id="67ea7-118">Select the environment that you want to use to validate the project or package.</span></span>  
  
 <span data-ttu-id="67ea7-119">**32 位元執行階段**</span><span class="sxs-lookup"><span data-stu-id="67ea7-119">**32-bit runtime**</span></span>  
 <span data-ttu-id="67ea7-120">選擇使用 32 位元執行階段執行封裝。</span><span class="sxs-lookup"><span data-stu-id="67ea7-120">Select to use a 32-bit runtime to execute a package.</span></span>  
  
 <span data-ttu-id="67ea7-121">**[參數]** 索引標籤會列出您用來驗證專案或封裝的參數值。</span><span class="sxs-lookup"><span data-stu-id="67ea7-121">The **Parameters** tab lists the parameter values that you use to validate the project or package.</span></span> <span data-ttu-id="67ea7-122">以下是在 [參數] 索引標籤上的選項。</span><span class="sxs-lookup"><span data-stu-id="67ea7-122">The following are the options on the Parameters tab.</span></span>  
  
 <span data-ttu-id="67ea7-123">**容器**</span><span class="sxs-lookup"><span data-stu-id="67ea7-123">**Container**</span></span>  
 <span data-ttu-id="67ea7-124">列出包含參數的物件。</span><span class="sxs-lookup"><span data-stu-id="67ea7-124">Lists the object that contains the parameter.</span></span>  
  
 <span data-ttu-id="67ea7-125">**參數**</span><span class="sxs-lookup"><span data-stu-id="67ea7-125">**Parameter**</span></span>  
 <span data-ttu-id="67ea7-126">列出參數的名稱</span><span class="sxs-lookup"><span data-stu-id="67ea7-126">Lists the name of the parameters</span></span>  
  
 <span data-ttu-id="67ea7-127">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="67ea7-127">**Value**</span></span>  
 <span data-ttu-id="67ea7-128">列出參數值。</span><span class="sxs-lookup"><span data-stu-id="67ea7-128">Lists the parameter value.</span></span>  
  
 <span data-ttu-id="67ea7-129">**[連接管理員]** 索引標籤會列出您用來驗證專案或封裝的連接管理員屬性值。</span><span class="sxs-lookup"><span data-stu-id="67ea7-129">The **Connection Managers** tab lists the connection manager property values that you use to validate the project or package.</span></span>  
  
 <span data-ttu-id="67ea7-130">以下是在 **[連接管理員]** 索引標籤上的選項。</span><span class="sxs-lookup"><span data-stu-id="67ea7-130">The following are the options on the **Connection Managers** tab.</span></span>  
  
 <span data-ttu-id="67ea7-131">**容器**</span><span class="sxs-lookup"><span data-stu-id="67ea7-131">**Container**</span></span>  
 <span data-ttu-id="67ea7-132">列出包含連接管理員的物件。</span><span class="sxs-lookup"><span data-stu-id="67ea7-132">Lists the object that contains the connection manager.</span></span>  
  
 <span data-ttu-id="67ea7-133">**名稱**</span><span class="sxs-lookup"><span data-stu-id="67ea7-133">**Name**</span></span>  
 <span data-ttu-id="67ea7-134">列出連接管理員名稱。</span><span class="sxs-lookup"><span data-stu-id="67ea7-134">Lists the connection manager name.</span></span>  
  
 <span data-ttu-id="67ea7-135">**屬性名稱**</span><span class="sxs-lookup"><span data-stu-id="67ea7-135">**Property name**</span></span>  
 <span data-ttu-id="67ea7-136">列出連接管理員屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="67ea7-136">Lists the name of the connection manager property.</span></span>  
  
 <span data-ttu-id="67ea7-137">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="67ea7-137">**Value**</span></span>  
 <span data-ttu-id="67ea7-138">列出指派給連接管理員屬性的值。</span><span class="sxs-lookup"><span data-stu-id="67ea7-138">Lists the value assigned to the connection manager property.</span></span>  
  
  
