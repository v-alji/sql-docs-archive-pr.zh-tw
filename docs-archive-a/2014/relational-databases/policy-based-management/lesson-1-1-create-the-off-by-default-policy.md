---
title: 建立 Off By Default 原則 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 98fde3c5-297c-4d95-981e-95700bbf5ccd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 16d0893c155627a41149263b5ce7b21a4a217b74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591970"
---
# <a name="create-the-off-by-default-policy"></a><span data-ttu-id="0dd56-102">建立依預設為關閉的原則</span><span class="sxs-lookup"><span data-stu-id="0dd56-102">Create the Off By Default Policy</span></span>
  <span data-ttu-id="0dd56-103">這項工作會建立名為 Mail Off 並且以介面區組態 Facet 為基礎的條件。</span><span class="sxs-lookup"><span data-stu-id="0dd56-103">This task creates a condition named Mail Off that is based on the Surface Area Configuration facet.</span></span> <span data-ttu-id="0dd56-104">然後，它會建立名為 Off By Default 的原則。</span><span class="sxs-lookup"><span data-stu-id="0dd56-104">Then, it creates a policy named Off By Default.</span></span>  
  
### <a name="to-create-the-mail-off-condition"></a><span data-ttu-id="0dd56-105">建立 Mail Off 條件</span><span class="sxs-lookup"><span data-stu-id="0dd56-105">To create the Mail Off condition</span></span>  
  
1.  <span data-ttu-id="0dd56-106">在物件總管中，依序展開 [管理]\*\*\*\*、[原則管理]\*\*\*\* 和 [Facet]\*\*\*\*、以滑鼠右鍵按一下 [介面區組態]\*\*\*\*，然後按一下 [新增條件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0dd56-106">In Object Explorer, expand **Management**, expand **Policy Management**, expand **Facets**, right-click **Surface Area Configuration**, and then click **New Condition**.</span></span>  
  
2.  <span data-ttu-id="0dd56-107">在 [建立新條件]\*\*\*\* 對話方塊的 [名稱]\*\*\*\* 方塊中，輸入 **Mail Off**。</span><span class="sxs-lookup"><span data-stu-id="0dd56-107">In the **Create New Condition** dialog box, in the **Name** box, type **Mail Off**.</span></span>  
  
3.  <span data-ttu-id="0dd56-108">在 [Facet]\*\*\*\* 方塊中，確認已選取 [介面區組態]\*\*\*\* Facet。</span><span class="sxs-lookup"><span data-stu-id="0dd56-108">In the **Facet** box, confirm that **Surface Area Configuration** facet is selected.</span></span>  
  
4.  <span data-ttu-id="0dd56-109">在 [運算式]\*\*\*\* 區域的 [欄位]\*\*\*\* 方塊中，選取 **\@DatabaseMailEnabled**、在 [運算子]\*\*\*\* 方塊中選取 [=]\*\*\*\*，然後在 [值]\*\*\*\* 中選取 [False]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0dd56-109">In the **Expression** area, in the **Field** box, select **\@DatabaseMailEnabled**, in the **Operator** box select **=**, and in the **Value** select **False**.</span></span>  
  
5.  <span data-ttu-id="0dd56-110">在 [描述]\*\*\*\* 頁面上，輸入條件的描述，然後按一下 [確定]\*\*\*\* 建立條件。</span><span class="sxs-lookup"><span data-stu-id="0dd56-110">On the **Description** page, type a description of the condition, and then click **OK** to create the condition.</span></span>  
  
### <a name="to-create-the-off-by-default-policy"></a><span data-ttu-id="0dd56-111">建立 Off By Default 原則</span><span class="sxs-lookup"><span data-stu-id="0dd56-111">To create the Off By Default policy</span></span>  
  
1.  <span data-ttu-id="0dd56-112">在物件總管中，以滑鼠右鍵按一下 [介面區組態]\*\*\*\*，然後按一下 [新增原則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0dd56-112">In Object Explorer, right-click **Surface Area Configuration**, and then click **New Policy**.</span></span>  
  
2.  <span data-ttu-id="0dd56-113">在 [建立新原則]\*\*\*\* 對話方塊的 [名稱]\*\*\*\* 方塊中，輸入 **Off By Default**。</span><span class="sxs-lookup"><span data-stu-id="0dd56-113">In the **Create New Policy** dialog box, in the **Name** box, type **Off By Default**.</span></span>  
  
3.  <span data-ttu-id="0dd56-114">將 [已啟用]\*\*\*\* 核取方塊保持不核取狀態。</span><span class="sxs-lookup"><span data-stu-id="0dd56-114">Leave the **Enabled** checkbox unchecked.</span></span> <span data-ttu-id="0dd56-115">[已啟用]\*\*\*\* 核取方塊會套用至自動原則，而且這個原則會視需要執行。</span><span class="sxs-lookup"><span data-stu-id="0dd56-115">The **Enabled** checkbox applies to automated policies, and this policy will be executed on demand.</span></span>  
  
4.  <span data-ttu-id="0dd56-116">在 [檢查條件]\*\*\*\* 核取方塊中，向下捲動至 [介面區組態]\*\*\*\* 區域，然後選取 [Mail Off]\*\*\*\* 當作要檢查的條件。</span><span class="sxs-lookup"><span data-stu-id="0dd56-116">In the **Check condition** checkbox, scroll down to the **Surface Area Configuration** area, and then select **Mail Off** as the condition to check.</span></span>  
  
5.  <span data-ttu-id="0dd56-117">[針對目標]\*\*\*\* 方塊將呈現空白，因為這是伺服器範圍的原則。</span><span class="sxs-lookup"><span data-stu-id="0dd56-117">The **Against targets** box will be blank because this is a server-scoped policy.</span></span>  
  
6.  <span data-ttu-id="0dd56-118">在 [評估模式]\*\*\*\* 核取方塊中，選取 [視需要]\*\*\*\* 當作評估模式。</span><span class="sxs-lookup"><span data-stu-id="0dd56-118">In the **Evaluation Mode** checkbox, select **On demand** as the evaluation mode.</span></span>  
  
7.  <span data-ttu-id="0dd56-119">在 [伺服器限制]\*\*\*\* 核取方塊中，選取 [無]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0dd56-119">In the **Server restriction** checkbox, select **None**.</span></span>  
  
8.  <span data-ttu-id="0dd56-120">在 [描述]\*\*\*\* 頁面上，輸入原則的描述。</span><span class="sxs-lookup"><span data-stu-id="0dd56-120">On the **Description** page, type a description of the policy.</span></span>  
  
9. <span data-ttu-id="0dd56-121">您可以在 [其他說明超連結]\*\*\*\* 區域中，提供原則的網頁超連結。</span><span class="sxs-lookup"><span data-stu-id="0dd56-121">You can provide a hyperlink to a Web page for your policies in the **Additional help hyperlink** area.</span></span> <span data-ttu-id="0dd56-122">在 [要顯示的文字]\*\*\*\* 方塊中，輸入要針對超連結顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="0dd56-122">In the **Text to display** box, type the text that will appear for the hyperlink.</span></span>  
  
10. <span data-ttu-id="0dd56-123">在 [位址]\*\*\*\* 方塊中，輸入說明頁面的超連結，例如公司 IT 部門的首頁。</span><span class="sxs-lookup"><span data-stu-id="0dd56-123">In the **Address** box, type a hyperlink to a Help page, such as the home page for the IT department of your company.</span></span>  
  
11. <span data-ttu-id="0dd56-124">若要透過開啟網頁確認位址，請按一下 [測試連結]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0dd56-124">To confirm the address by opening the Web page, click **Test Link**.</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="0dd56-125">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="0dd56-125">Next Task in Lesson</span></span>  
 [<span data-ttu-id="0dd56-126">將伺服器設定為執行 Off By Default 原則</span><span class="sxs-lookup"><span data-stu-id="0dd56-126">Configure a Server to Run the Off By Default Policy</span></span>](lesson-1-2-configure-a-server-to-run-the-off-by-default-policy.md)  
  
  
