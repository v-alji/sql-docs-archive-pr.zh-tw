---
title: 將伺服器設定為執行 Off By Default 原則 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 41c3022d-ab13-443e-ac64-ba1d64584f79
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c0842a30b7d0bbcd1b01ee9e98ed1ed9a74f0f35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591969"
---
# <a name="configure-a-server-to-run-the-off-by-default-policy"></a><span data-ttu-id="8536b-102">將伺服器設定為執行 Off By Default 原則</span><span class="sxs-lookup"><span data-stu-id="8536b-102">Configure a Server to Run the Off By Default Policy</span></span>
  <span data-ttu-id="8536b-103">現在，您有一個名為 Off By Default 的原則。</span><span class="sxs-lookup"><span data-stu-id="8536b-103">Now you have a policy named Off By Default.</span></span> <span data-ttu-id="8536b-104">在這項工作中，您將檢查伺服器是否符合這個原則的需求。</span><span class="sxs-lookup"><span data-stu-id="8536b-104">In this task, you will check to see whether your server complies with the requirements of this policy.</span></span>  
  
### <a name="to-run-the-off-by-default-policy"></a><span data-ttu-id="8536b-105">執行 Off By Default 原則</span><span class="sxs-lookup"><span data-stu-id="8536b-105">To run the Off By Default policy</span></span>  
  
1.  <span data-ttu-id="8536b-106">在物件總管中，以滑鼠右鍵按一下 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，指向 [原則]\*\*\*\*，然後按一下 [評估]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8536b-106">In Object Explorer, right-click your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], point to **Policies**, and then click **Evaluate**.</span></span>  
  
2.  <span data-ttu-id="8536b-107">在 [評估原則]\*\*\*\* 對話方塊中，您可以從另一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體或檔案中選取原則。</span><span class="sxs-lookup"><span data-stu-id="8536b-107">In the **Evaluate Policies** dialog box you can select policies from another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or from a file.</span></span> <span data-ttu-id="8536b-108">在這個步驟中，請將 [來源]\*\*\*\* 保持設定為 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8536b-108">For this step, leave **Source** set to your instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
3.  <span data-ttu-id="8536b-109">在 [原則]\*\*\*\* 區段中，選取 [預設關閉]\*\*\*\* 原則。</span><span class="sxs-lookup"><span data-stu-id="8536b-109">In the **Policies** section, select the **Off By Default** policy.</span></span>  
  
4.  <span data-ttu-id="8536b-110">若要查看伺服器是否符合此原則，請按一下 [評估]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8536b-110">To see whether the server is in compliance with the policy, click **Evaluate**.</span></span>  
  
5.  <span data-ttu-id="8536b-111">如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 符合此原則，您將會在 [結果]\*\*\*\* 區域中看見含有核取記號的綠色圓圈。</span><span class="sxs-lookup"><span data-stu-id="8536b-111">In the **Results** area, you will see a green circle with a check mark if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] complies with the policy.</span></span> <span data-ttu-id="8536b-112">如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 不符合此原則，您就會看見含有 X 的紅色圓圈。</span><span class="sxs-lookup"><span data-stu-id="8536b-112">You will see a red circle with an X if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not comply with the policy.</span></span>  
  
6.  <span data-ttu-id="8536b-113">在 [目標詳細資料]\*\*\*\* 區域中，您將會在錯誤發生時於 [訊息]\*\*\*\* 資料行中看到其他資訊。</span><span class="sxs-lookup"><span data-stu-id="8536b-113">In the **Target Details** area, you will see additional information in the **Message** column if an error occurs.</span></span> <span data-ttu-id="8536b-114">在 [訊息]\*\*\*\* 資料行中，按一下 [檢視]\*\*\*\* 查看報表，其中包含所檢查之每個 Facet 屬性的檢查結果。</span><span class="sxs-lookup"><span data-stu-id="8536b-114">In the **Message** column, click **View** to see a report that contains the results of the check for each facet property that was checked.</span></span>  
  
7.  <span data-ttu-id="8536b-115">原則描述會顯示在頁面底部，而且 [其他說明]\*\*\*\* 區段會顯示您已針對此原則設定的超連結。</span><span class="sxs-lookup"><span data-stu-id="8536b-115">The policy description is displayed at the bottom of the page, and the **Additional help** section displays the hyperlink that you have configured for the policy.</span></span> <span data-ttu-id="8536b-116">按一下訊息超連結，即可開啟您在建立此原則時指定的網頁。</span><span class="sxs-lookup"><span data-stu-id="8536b-116">Click the message hyperlink to open the Web page that you specified when you created the policy.</span></span>  
  
8.  <span data-ttu-id="8536b-117">關閉瀏覽器，然後關閉 [結果詳細檢視]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8536b-117">Close the browser, and then close the **Results Detailed View** dialog box.</span></span>  
  
9. <span data-ttu-id="8536b-118">如果伺服器不符合原則，而且您想要停用 Database Mail，請按一下 [評估結果]\*\*\*\* 頁面中的 [套用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8536b-118">If the server is out of compliance and you want to disable Database Mail, click **Apply** in the **Evaluation Results** page.</span></span>  
  
10. <span data-ttu-id="8536b-119">關閉 [結果詳細檢視]\*\*\*\* 和 [評估原則]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8536b-119">Close both the **Results Detailed View** and the **Evaluate Policies** dialog boxes.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="8536b-120">下一課</span><span class="sxs-lookup"><span data-stu-id="8536b-120">Next Lesson</span></span>  
 [<span data-ttu-id="8536b-121">第 2 課：建立和套用命名標準原則</span><span class="sxs-lookup"><span data-stu-id="8536b-121">Lesson 2: Create and Apply a Naming Standards Policy</span></span>](lesson-2-create-and-apply-a-naming-standards-policy.md)  
  
  
