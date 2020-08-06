---
title: 資料警示訊息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6819720c-d848-4b90-9b51-89501b4f4645
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d50c3dd24c0057f695a9318c5eef7ad9e7540a45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597651"
---
# <a name="data-alert-messages"></a><span data-ttu-id="2a346-102">資料警示訊息</span><span class="sxs-lookup"><span data-stu-id="2a346-102">Data Alert Messages</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="2a346-103">資料警示會以電子郵件傳遞兩種類型的資料警示訊息：含有資料警示結果的訊息以及含有錯誤描述的訊息。</span><span class="sxs-lookup"><span data-stu-id="2a346-103">data alerts deliver two types of data alert messages by email: Messages with data alert results and messages with error descriptions.</span></span> <span data-ttu-id="2a346-104">包含結果的訊息會通知所有收件者共同感興趣以及對業務決策相當重要的報表資料變更。</span><span class="sxs-lookup"><span data-stu-id="2a346-104">Messages with results keep all recipients informed about changes in report data that is of common interest and important to business decisions.</span></span> <span data-ttu-id="2a346-105">如果由於某種原因發生錯誤而無法提供結果，則會改為傳送錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="2a346-105">If for some reason an error occurs and the results are not available, the error message is sent instead.</span></span>

 <span data-ttu-id="2a346-106">資料警示定義的擁有者還可以在 [資料警示管理員] 中檢視資料警示執行個體的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2a346-106">The owner of the data alert definition also can view information about the data alert instance in Data Alert Manager.</span></span> <span data-ttu-id="2a346-107">如需相關資訊，請參閱 [Data Alert Manager for SharePoint Users](../../2014/reporting-services/data-alert-manager-for-sharepoint-users.md)。</span><span class="sxs-lookup"><span data-stu-id="2a346-107">For more information, see [Data Alert Manager for SharePoint Users](../../2014/reporting-services/data-alert-manager-for-sharepoint-users.md).</span></span>

##  <a name="data-alert-messages"></a><a name="DataAlertMessages"></a><span data-ttu-id="2a346-108">資料警示訊息</span><span class="sxs-lookup"><span data-stu-id="2a346-108">Data Alert Messages</span></span>
 <span data-ttu-id="2a346-109">下圖顯示含有結果的資料警示訊息以及含有錯誤描述的警示訊息。</span><span class="sxs-lookup"><span data-stu-id="2a346-109">The following pictures show a data alert message with results and an alert message with an error description.</span></span>

 <span data-ttu-id="2a346-110">**結果訊息**</span><span class="sxs-lookup"><span data-stu-id="2a346-110">**Results message**</span></span>

 <span data-ttu-id="2a346-111">![包含結果的資料警示電子郵件訊息](media/rs-alertmessageresults.gif "包含結果的資料警示電子郵件訊息")</span><span class="sxs-lookup"><span data-stu-id="2a346-111">![Data alert e-mail message with results](media/rs-alertmessageresults.gif "Data alert e-mail message with results")</span></span>

 <span data-ttu-id="2a346-112">**錯誤訊息**</span><span class="sxs-lookup"><span data-stu-id="2a346-112">**Error message**</span></span>

 <span data-ttu-id="2a346-113">![包含錯誤訊息的資料警示訊息](media/rs-alertmessageerrror.gif "包含錯誤訊息的資料警示訊息")</span><span class="sxs-lookup"><span data-stu-id="2a346-113">![Data alert message with error message](media/rs-alertmessageerrror.gif "Data alert message with error message")</span></span>

 <span data-ttu-id="2a346-114">這些訊息包含相同類型的資訊。</span><span class="sxs-lookup"><span data-stu-id="2a346-114">The messages include the same types of information.</span></span>

1.  <span data-ttu-id="2a346-115">**代表** 包含建立資料警示定義的建立者名稱。</span><span class="sxs-lookup"><span data-stu-id="2a346-115">**On behalf of** contains the name of the person who created the data alert definition.</span></span>

2.  <span data-ttu-id="2a346-116">如果您在警示定義中提供了描述，該描述會顯示於 **代表**下方。</span><span class="sxs-lookup"><span data-stu-id="2a346-116">If you provided a description in the alert definition, it displays below **On behalf of**.</span></span>

3.  <span data-ttu-id="2a346-117">**警示結果** 會以表格格式顯示報表資料摘要中符合警示定義中所指定規則的資料列，或是顯示錯誤描述。</span><span class="sxs-lookup"><span data-stu-id="2a346-117">**Alert Results** display the rows in the report data feed that satisfy the rules specified in the alert definition in a tabular format or display an error description.</span></span> <span data-ttu-id="2a346-118">顯示的資料列數並無限制。</span><span class="sxs-lookup"><span data-stu-id="2a346-118">There is no limit on the number of rows that displays.</span></span>

4.  <span data-ttu-id="2a346-119">**移至報表** 是建立警示定義所在報表的連結。</span><span class="sxs-lookup"><span data-stu-id="2a346-119">**Go to report** is a link to the report that the alert definition is built upon.</span></span> <span data-ttu-id="2a346-120">如果因為報表移動或刪除而導致連結無效，則會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="2a346-120">If the link is not valid because the report was moved or deleted, an error message displays.</span></span>

5.  <span data-ttu-id="2a346-121">[規則]\*\*\*\* 會列出警示定義中的規則和子句。</span><span class="sxs-lookup"><span data-stu-id="2a346-121">**Rule(s)** lists the rules and clauses in the alert definition.</span></span> <span data-ttu-id="2a346-122">這項資訊有助於驗證和了解警示結果，並且識別資料警示定義中您可能想要變更以縮小或擴大結果的規則。</span><span class="sxs-lookup"><span data-stu-id="2a346-122">This information helps you verify and understand the alert results and identify rules in the data alert definition that you might want to change to narrow or broaden results.</span></span>

6.  <span data-ttu-id="2a346-123">**報表參數** 會列出報表執行時使用的參數和參數值。</span><span class="sxs-lookup"><span data-stu-id="2a346-123">**Report parameters** list the parameters and parameter values that were used when the report was run.</span></span> <span data-ttu-id="2a346-124">參數和參數值有助於了解警示結果。</span><span class="sxs-lookup"><span data-stu-id="2a346-124">Parameters and parameter values help you understand the alert results.</span></span>

7.  <span data-ttu-id="2a346-125">**內容值** 會列出位於報表資料區域外之報表項目的名稱和值。</span><span class="sxs-lookup"><span data-stu-id="2a346-125">**Contextual values** list the names and values of report items that are outside of the report data regions.</span></span> <span data-ttu-id="2a346-126">這些項目通常是文字方塊。</span><span class="sxs-lookup"><span data-stu-id="2a346-126">The items are typically text boxes.</span></span> <span data-ttu-id="2a346-127">例如，含有常值的文字方塊 (像是報表的主旨或描述)。</span><span class="sxs-lookup"><span data-stu-id="2a346-127">For example, a text box with a constant value such as the subject or description of a report.</span></span>

 <span data-ttu-id="2a346-128">兩種訊息類型的唯一區別在於項目 5，也就是 **警示結果**。</span><span class="sxs-lookup"><span data-stu-id="2a346-128">The only difference between the two message types is item 5, **Alert Results**.</span></span> <span data-ttu-id="2a346-129">如果在建立資料警示執行個體或資料警示訊息時發生錯誤， **警示結果** 會顯示描述問題的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="2a346-129">If an error occurs when a data alert instance or data alert message is created, **Alert Results** displays an error message that describes the problem.</span></span> <span data-ttu-id="2a346-130">錯誤訊息會傳送至所有收件者，讓他們知道無法提供預期收到或是做出業務決策所倚賴的警示結果。</span><span class="sxs-lookup"><span data-stu-id="2a346-130">The error message, sent to all recipients, let them know that the alert results that they are expecting and might rely on to make business decisions are not available.</span></span>

 

##  <a name="related-tasks"></a><a name="HowTo"></a> <span data-ttu-id="2a346-131">相關工作</span><span class="sxs-lookup"><span data-stu-id="2a346-131">Related Tasks</span></span>
 <span data-ttu-id="2a346-132">本節列出的程序說明如何建立和編輯資料警示定義，以提供可在資料警示訊息中看見的大部分資訊。</span><span class="sxs-lookup"><span data-stu-id="2a346-132">This section lists procedures that show you how to create and edit the data alert definitions that provide much of the information that you see in data alert messages.</span></span>

-   [<span data-ttu-id="2a346-133">在資料警示設計工具中建立資料警示</span><span class="sxs-lookup"><span data-stu-id="2a346-133">Create a Data Alert in Data Alert Designer</span></span>](create-a-data-alert-in-data-alert-designer.md)

-   [<span data-ttu-id="2a346-134">在警示設計工具中編輯資料警示</span><span class="sxs-lookup"><span data-stu-id="2a346-134">Edit a Data Alert in Alert Designer</span></span>](edit-a-data-alert-in-alert-designer.md)



## <a name="see-also"></a><span data-ttu-id="2a346-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a346-135">See Also</span></span>
 <span data-ttu-id="2a346-136">資料警示[設計](../../2014/reporting-services/data-alert-designer.md)工具[Reporting Services 資料警示](../ssms/agent/alerts.md)</span><span class="sxs-lookup"><span data-stu-id="2a346-136">[Data Alert Designer](../../2014/reporting-services/data-alert-designer.md) [Reporting Services Data Alerts](../ssms/agent/alerts.md)</span></span>


