---
title: 建立連結的定義域 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.linkeddomain.f1
ms.assetid: fd99d422-c53d-4d7c-9cdd-303c703683b6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 17e91197ecb8cb6ad68769937a8d385d8c73a778
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594697"
---
# <a name="create-a-linked-domain"></a><span data-ttu-id="c6477-102">建立連結的定義域</span><span class="sxs-lookup"><span data-stu-id="c6477-102">Create a Linked Domain</span></span>
  <span data-ttu-id="c6477-103">此主題描述如何在 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中的知識庫內建立連結的定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-103">This topic describes how to create a linked domain in a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="c6477-104">連結的定義域是從另一個定義域 (之前已經存在的定義域) 建立而來，而且會從它連結的定義域繼承所有值、規則和屬性，除了名稱和描述以外。</span><span class="sxs-lookup"><span data-stu-id="c6477-104">A linked domain is created from another, previously existing domain, and inherits all values, rules, and properties from the domain that it is linked to, with the exception of the name and the description.</span></span> <span data-ttu-id="c6477-105">您可以將一組連結的定義域當做一個定義域來管理。</span><span class="sxs-lookup"><span data-stu-id="c6477-105">You can manage a set of linked domains as one.</span></span> <span data-ttu-id="c6477-106">藉由連結一個定義域與另一個定義域，您所建立的定義域就會從另一個定義域繼承其內容。</span><span class="sxs-lookup"><span data-stu-id="c6477-106">By linking one domain to the other, you create a domain that inherits its contents from another domain.</span></span>  
  
## <a name="scenarios"></a><span data-ttu-id="c6477-107">案例</span><span class="sxs-lookup"><span data-stu-id="c6477-107">Scenarios</span></span>  
 <span data-ttu-id="c6477-108">連結的定義域在以下情況下特別有用。</span><span class="sxs-lookup"><span data-stu-id="c6477-108">Linked domains are particularly useful in the following scenarios.</span></span>  
  
### <a name="mapping-multiple-fields-to-domains-that-share-values-rules-and-properties"></a><span data-ttu-id="c6477-109">將多個欄位對應到共用值、規則和屬性的定義域</span><span class="sxs-lookup"><span data-stu-id="c6477-109">Mapping multiple fields to domains that share values, rules, and properties</span></span>  
 <span data-ttu-id="c6477-110">您不能將兩個欄位對應到相同定義域，但是可以將一個欄位對應到定義域，然後將第二個欄位對應到與第一個定義域連結的定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-110">You cannot map two fields to the same domain, but you could map one field to a domain and then map a second field to a domain linked to the first domain.</span></span> <span data-ttu-id="c6477-111">這樣做會將欄位對應到擁有相同內容和屬性 (名稱和描述除外) 的兩個不同定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-111">Doing so maps the fields to two different domains that have the same contents and properties (except name and description).</span></span> <span data-ttu-id="c6477-112">如需詳細資訊，請參閱 [Map two fields to linked domains](#Map)。</span><span class="sxs-lookup"><span data-stu-id="c6477-112">For more information, see [Map two fields to linked domains](#Map).</span></span>  
  
### <a name="controlling-data-flow-to-composite-domains"></a><span data-ttu-id="c6477-113">控制與複合定義域之間的資料流程</span><span class="sxs-lookup"><span data-stu-id="c6477-113">Controlling data flow to composite domains</span></span>  
 <span data-ttu-id="c6477-114">連結的定義域可讓您控制欄位與複合定義域之間的資料流程。</span><span class="sxs-lookup"><span data-stu-id="c6477-114">Linked domains enable you to control the data flow between fields and composite domains.</span></span> <span data-ttu-id="c6477-115">當某個欄位的資料流向複合定義域中，以及另一個非常類似的欄位中的資料未流向此複合定義域時，您可以加以區分。</span><span class="sxs-lookup"><span data-stu-id="c6477-115">You can differentiate when data from one field flows into a composite domain, and when data from another, very similar field does not flow into the composite domain.</span></span> <span data-ttu-id="c6477-116">當您要這樣做時，您會指定在兩個連結的定義域中，一個定義域是複合定義域的一部分，另一個定義域則否。</span><span class="sxs-lookup"><span data-stu-id="c6477-116">You do so by specifying that of two linked domains, one is part of a composite domain, and one is not.</span></span> <span data-ttu-id="c6477-117">從定義域的觀點來看，連結的定義域是相同的。</span><span class="sxs-lookup"><span data-stu-id="c6477-117">From a domain perspective, linked domains are identical.</span></span> <span data-ttu-id="c6477-118">它們包含相同的知識。</span><span class="sxs-lookup"><span data-stu-id="c6477-118">They contain the same knowledge.</span></span> <span data-ttu-id="c6477-119">但是從複合定義域的觀點來看，連結的定義域是不同的。</span><span class="sxs-lookup"><span data-stu-id="c6477-119">However, from a composite-domain perspective, linked domains are different.</span></span> <span data-ttu-id="c6477-120">其中一個會參與複合定義域，另一個則否。</span><span class="sxs-lookup"><span data-stu-id="c6477-120">One participates in the composite domain; the other does not.</span></span>  
  
 <span data-ttu-id="c6477-121">範例是包含以下欄位的記錄：客戶名字、客戶姓氏和父親的名字。</span><span class="sxs-lookup"><span data-stu-id="c6477-121">An example is a record that contains the following fields: Customer First Name, Customer Last Name, and Father's First Name.</span></span> <span data-ttu-id="c6477-122">假設您將客戶名字和父親的名字對應到「名字」定義域，並讓「名字」定義域和「姓氏」定義域成為「完整名稱」複合定義域的一部分。</span><span class="sxs-lookup"><span data-stu-id="c6477-122">Suppose you map both customer first name and father's first name to a First Name domain, and make the First Name domain and the Last Name domain a part of a Full Name composite domain.</span></span> <span data-ttu-id="c6477-123">問題是父親的名字將會加入至複合定義域，而且不含姓氏。</span><span class="sxs-lookup"><span data-stu-id="c6477-123">The problem is that the father's first name will be added to the composite domain without a last name.</span></span> <span data-ttu-id="c6477-124">但是，如果您將兩個名字欄位中的每一個都連結到定義域，並連結這兩個定義域，然後您可以將「客戶名字」定義域加入至「完整名稱」複合定義域，而不將「父親的名字」欄位加入至複合定義域，以免「父親的名字」被加入至複合定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-124">If, however, you link each of the two first name fields to a domain, and link the two domains, then you can add the Customer First Name domain to the Full Name composite domain, and not add the Father's First Name field to the composite domain, thereby preventing the Father's First Name from being added to the composite domain.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c6477-125">開始之前</span><span class="sxs-lookup"><span data-stu-id="c6477-125">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="c6477-126">必要條件</span><span class="sxs-lookup"><span data-stu-id="c6477-126">Prerequisites</span></span>  
 <span data-ttu-id="c6477-127">若要建立連結的定義域，您必須擁有知識庫以及您想要連結的現有定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-127">To create a linked domain, you must have a knowledge base and an existing domain that you want to link to.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c6477-128">Security</span><span class="sxs-lookup"><span data-stu-id="c6477-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c6477-129">權限</span><span class="sxs-lookup"><span data-stu-id="c6477-129">Permissions</span></span>  
 <span data-ttu-id="c6477-130">您必須擁有 DQS_MAIN 資料庫的 dqs_kb_editor 角色或 dqs_administrator 角色，才能建立連結的定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-130">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to create a linked domain.</span></span>  
  
##  <a name="create-a-linked-domain"></a><a name="Create"></a><span data-ttu-id="c6477-131">建立連結的定義域</span><span class="sxs-lookup"><span data-stu-id="c6477-131">Create a Linked Domain</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="c6477-132">[執行 Data Quality Client 應用程式](../../2014/data-quality-services/run-the-data-quality-client-application.md)。</span><span class="sxs-lookup"><span data-stu-id="c6477-132">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="c6477-133">在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面上，開啟或建立知識庫。</span><span class="sxs-lookup"><span data-stu-id="c6477-133">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open or create a knowledge base.</span></span> <span data-ttu-id="c6477-134">選取 **[定義域管理]** 當做活動，然後按一下 **[開啟]** 或 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="c6477-134">Select **Domain Management** as the activity, and then click **Open** or **Create**.</span></span> <span data-ttu-id="c6477-135">如需相關資訊，請參閱 [建立知識庫](../../2014/data-quality-services/create-a-knowledge-base.md) 或 [開啟知識庫](../../2014/data-quality-services/open-a-knowledge-base.md)。</span><span class="sxs-lookup"><span data-stu-id="c6477-135">For more information, see [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md) or [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
3.  <span data-ttu-id="c6477-136">從 **[定義域管理]** 頁面的 **[定義域清單]** 中，以滑鼠右鍵按一下您想要與新的定義域連結的定義域，然後按一下 **[建立連結的定義域]**。</span><span class="sxs-lookup"><span data-stu-id="c6477-136">From the **Domain list** on the **Domain Management** page, right-click the domain that you want to link a new domain to, and then click **Create Linked Domain**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c6477-137">並沒有專門用來建立連結的定義域的圖示。</span><span class="sxs-lookup"><span data-stu-id="c6477-137">There is not an icon dedicated to creating a linked domain.</span></span> <span data-ttu-id="c6477-138">若要這樣做，您只能使用內容功能表中的命令。</span><span class="sxs-lookup"><span data-stu-id="c6477-138">You can only do so using the command in the context menu.</span></span>  
  
4.  <span data-ttu-id="c6477-139">在 **[建立定義域]** 對話方塊中，輸入知識庫特有的名稱以及最多 256 個字元的描述。</span><span class="sxs-lookup"><span data-stu-id="c6477-139">In the **Create Domain** dialog box, enter a name that is unique to the knowledge base and a description of up to 256 characters.</span></span> <span data-ttu-id="c6477-140">確認連結到的定義域名稱正確無誤。</span><span class="sxs-lookup"><span data-stu-id="c6477-140">Verify that the name of the domain linked to is correct.</span></span>  
  
5.  <span data-ttu-id="c6477-141">按一下 **[確定]** ，完成建立連結的定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-141">Click **OK** to complete creation of the linked domain.</span></span>  
  
6.  <span data-ttu-id="c6477-142">必要時，您可以在 [定義域屬性] 索引標籤中變更連結的定義域的名稱或描述。</span><span class="sxs-lookup"><span data-stu-id="c6477-142">If necessary, you can change the name or description of the linked domain in the Domain Properties tab.</span></span>  
  
7.  <span data-ttu-id="c6477-143">按一下 **[完成]** ，完成定義域管理活動，如＜ [結束定義域管理活動](../../2014/data-quality-services/end-the-domain-management-activity.md)＞中所述。</span><span class="sxs-lookup"><span data-stu-id="c6477-143">Click **Finish** to complete the domain management activity, as described in [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md).</span></span>  
  
##  <a name="map-two-fields-to-linked-domains"></a><a name="Map"></a> <span data-ttu-id="c6477-144">Map two fields to linked domains</span><span class="sxs-lookup"><span data-stu-id="c6477-144">Map two fields to linked domains</span></span>  
  
1.  <span data-ttu-id="c6477-145">開啟知識探索活動中的知識庫，並將知識庫對應到資料庫及資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="c6477-145">Open a knowledge base to the knowledge discovery activity, and map the knowledge base to the database and table or view.</span></span>  
  
2.  <span data-ttu-id="c6477-146">將一個欄位對應到定義域，然後嘗試將第二個欄位對應的相同的定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-146">Map one field to a domain, and then attempt to map a second field to the same domain.</span></span>  
  
3.  <span data-ttu-id="c6477-147">如果快顯視窗指出此定義域已在使用中，請按一下 [是] 建立連結的定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-147">In the popup indicating that the domain is already in use, click Yes to create a linked domain.</span></span>  
  
4.  <span data-ttu-id="c6477-148">在 [建立定義域] 對話方塊中，輸入定義域名稱和描述，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="c6477-148">In the Create Domain dialog box, enter a domain name and description, and then click OK.</span></span>  
  
##  <a name="follow-up-after-creating-a-linked-domain"></a><a name="FollowUp"></a> <span data-ttu-id="c6477-149">後續操作：建立連結的定義域之後</span><span class="sxs-lookup"><span data-stu-id="c6477-149">Follow Up: After Creating a Linked Domain</span></span>  
 <span data-ttu-id="c6477-150">在建立連結的定義域之後，您可以針對定義域執行其他定義域管理工作、執行知識探索來將知識加入至定義域，或者將比對原則加入至定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-150">After you create a linked domain, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="c6477-151">如需詳細資訊，請參閱[執行知識探索](../../2014/data-quality-services/perform-knowledge-discovery.md)、[管理定義域](../../2014/data-quality-services/managing-a-domain.md)或[建立比對原則](../../2014/data-quality-services/create-a-matching-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="c6477-151">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
##  <a name="behavior-of-a-linked-domain"></a><a name="Behavior"></a> <span data-ttu-id="c6477-152">連結的定義域行為</span><span class="sxs-lookup"><span data-stu-id="c6477-152">Behavior of a Linked Domain</span></span>  
 <span data-ttu-id="c6477-153">您可以為連結的定義域變更設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c6477-153">You can change the settings for a linked domain as follows:</span></span>  
  
-   <span data-ttu-id="c6477-154">您可以變更連結的定義域的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="c6477-154">You can change the name and description of a linked domain.</span></span>  
  
-   <span data-ttu-id="c6477-155">若要針對 **[資料類型]**、 **[使用前置值]** 或 **[設定輸出格式為]** 屬性變更定義域屬性，請選取您連結到的定義域，並在 **[定義域屬性]** 索引標籤中針對該定義域變更這些設定。</span><span class="sxs-lookup"><span data-stu-id="c6477-155">To change the domain properties for the **Data Type**, **Use Leading Values**, or **Format Output To** properties, select the domain that you linked to, and change those settings in the **Domain Properties** tab for that domain.</span></span> <span data-ttu-id="c6477-156">您不能在連結的定義域的屬性中變更這些設定。</span><span class="sxs-lookup"><span data-stu-id="c6477-156">You cannot change those settings in the properties of the linked domain.</span></span> <span data-ttu-id="c6477-157">如需相關資訊，請參閱 [建立定義域](../../2014/data-quality-services/create-a-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="c6477-157">For more information, see [Create a Domain](../../2014/data-quality-services/create-a-domain.md).</span></span>  
  
-   <span data-ttu-id="c6477-158">[定義域管理] 頁面上 **[參考資料]**、 **[定義域規則]**、 **[定義域值]** 和 **[以詞彙為主的關聯]** 索引標籤中的設定可以針對連結的定義域或是連結到的定義域來變更，而且另一個定義域將會繼承變更。</span><span class="sxs-lookup"><span data-stu-id="c6477-158">Settings in the **Reference Data**, **Domain Rules**, **Domain Values**, and **Term-based Relations** tabs of the Domain Management page can be changed for either the linked domain or the domain that it was linked to, and the changes will be inherited by the other domain.</span></span>  
  
 <span data-ttu-id="c6477-159">連結的定義域具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="c6477-159">Linked domains have the following characteristics:</span></span>  
  
-   <span data-ttu-id="c6477-160">您不能取消連結兩個定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-160">You cannot unlink two domains.</span></span> <span data-ttu-id="c6477-161">若要移除連結，請刪除其中一個連結的定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-161">To remove the link, delete one of the linked domains.</span></span>  
  
-   <span data-ttu-id="c6477-162">當您在 [定義域管理] 頁面上的定義域清單中選取連結的定義域時，於包含 **[值]** 資料表的窗格中識別連結的定義域的字串會包含指示，指出此定義域是連結的定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-162">When you select a linked domain in the domain list of the Domain Management page, the string identifying the linked domain in the pane containing the **Value** table contains an indication that the domain is a linked domain.</span></span>  
  
-   <span data-ttu-id="c6477-163">如果您刪除另一個定義域所連結到的定義域，將會一併刪除兩個定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-163">If you delete a domain that another domain is linked to, both domains will be deleted.</span></span> <span data-ttu-id="c6477-164">但是，您可以刪除連結的定義域，而且將不會刪除連結到的定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-164">You can, however, delete a linked domain, and the domain linked to will not be deleted.</span></span>  
  
-   <span data-ttu-id="c6477-165">連結的定義域不能連結到本身與另一個定義域連結的定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-165">A linked domain cannot be linked to a domain that itself is linked to another domain.</span></span>  
  
-   <span data-ttu-id="c6477-166">您不能建立與複合定義域之間的連結的定義域或連結的複合定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-166">You cannot create a linked domain or a linked composite domain to a composite domain.</span></span>  
  
-   <span data-ttu-id="c6477-167">當您在任何 [定義域管理] 索引標籤中按兩下連結的定義域時，將會開啟此定義域進行編輯，而且在名稱字串中會指示它是連結的定義域。</span><span class="sxs-lookup"><span data-stu-id="c6477-167">When you double-click a linked domain in any of the Domain Management tabs, the domain will be opened to editing with an indication in the name string that it is a linked domain.</span></span>  
  
  
