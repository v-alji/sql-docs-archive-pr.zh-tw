---
title: 產生 SQL 指令碼 (複寫物件) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.generatesqlscript.f1
helpviewer_keywords:
- Generate SQL Script dialog box
ms.assetid: b7ccc34e-1c22-44b8-8eb5-f6423af3164e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 31a4b318eb3a4c0e5d9f79f43efdcf97c42957f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585833"
---
# <a name="generate-sql-script-replication-objects"></a><span data-ttu-id="1363e-102">產生 SQL 指令碼 (複寫物件)</span><span class="sxs-lookup"><span data-stu-id="1363e-102">Generate SQL Script (Replication Objects)</span></span>
  <span data-ttu-id="1363e-103">複寫指令碼包含要實作已編寫複寫元件之指令碼所必要的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 系統預存程序，例如發行集或訂閱。</span><span class="sxs-lookup"><span data-stu-id="1363e-103">A replication script contains the [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures necessary to implement the replication components scripted, such as a publication or subscription.</span></span> <span data-ttu-id="1363e-104">拓撲中的所有複寫元件都應作為損毀復原計畫的一部份來編寫指令碼，而指令碼也可以用於自動執行重複性工作。</span><span class="sxs-lookup"><span data-stu-id="1363e-104">All replication components in a topology should be scripted as part of a disaster recovery plan, and scripts can also be used to automate repetitive tasks.</span></span> <span data-ttu-id="1363e-105">複寫提供編寫複寫物件之指令碼的兩個對話方塊：</span><span class="sxs-lookup"><span data-stu-id="1363e-105">Replication offers two dialog boxes for scripting replication objects:</span></span>  
  
-   <span data-ttu-id="1363e-106">[產生 SQL 指令碼]，這可從 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中 [複寫] 資料夾和所有子資料夾的操作功能表中使用。</span><span class="sxs-lookup"><span data-stu-id="1363e-106">**Generate SQL Script**, which is available from the context menu of the **Replication** folder and all subfolders in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="1363e-107">此對話方塊可讓您撰寫 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上所有複寫物件的指令碼。</span><span class="sxs-lookup"><span data-stu-id="1363e-107">This dialog box allows you to script all replication objects on an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="1363e-108">[產生 SQL 指令碼 \<ObjectName>]，這可從發行集和訂閱的操作功能表使用。</span><span class="sxs-lookup"><span data-stu-id="1363e-108">**Generate SQL Script \<ObjectName>**, which is available from the context menu for publications and subscriptions.</span></span> <span data-ttu-id="1363e-109">此對話方塊可讓您編寫個別物件的指令碼。</span><span class="sxs-lookup"><span data-stu-id="1363e-109">This dialog box allows you to script individual objects.</span></span>  
  
 <span data-ttu-id="1363e-110">這些對話方塊會編寫 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]單一執行個體上之物件的指令碼；它們不會連接到其他執行個體來編寫相關物件的指令碼。</span><span class="sxs-lookup"><span data-stu-id="1363e-110">These dialog boxes script objects on a single instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; they do not connect to other instances to script related objects.</span></span>  
  
## <a name="generate-sql-script-options"></a><span data-ttu-id="1363e-111">產生 SQL 指令碼選項</span><span class="sxs-lookup"><span data-stu-id="1363e-111">Generate SQL Script Options</span></span>  
 <span data-ttu-id="1363e-112">**散發者屬性**</span><span class="sxs-lookup"><span data-stu-id="1363e-112">**Distributor properties**</span></span>  
 <span data-ttu-id="1363e-113">選取即可編寫預存程序的指令碼以：啟用或停用散發者；加入或卸除與散發者相關聯的發行者；以及建立或卸除散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="1363e-113">Select to script stored procedures to: enable or disable the Distributor; add or drop Publishers associated with the Distributor; and create or drop the distribution database.</span></span>  
  
 <span data-ttu-id="1363e-114">**下列資料來源中的發行集**</span><span class="sxs-lookup"><span data-stu-id="1363e-114">**Publications in the following data sources**</span></span>  
 <span data-ttu-id="1363e-115">選取即可編寫預存程序的指令碼以：啟用或停用發行；建立或卸除發行集、發行項、發送訂閱以及複寫作業。</span><span class="sxs-lookup"><span data-stu-id="1363e-115">Select to script stored procedures to: enable or disable publishing; and create or drop publications, articles, push subscriptions, and replication jobs.</span></span>  
  
 <span data-ttu-id="1363e-116">**下列資料來源中的訂閱**</span><span class="sxs-lookup"><span data-stu-id="1363e-116">**Subscriptions in the following data sources**</span></span>  
 <span data-ttu-id="1363e-117">選取即可編寫預存程序的指令碼，以建立或卸除提取訂閱與複寫作業。</span><span class="sxs-lookup"><span data-stu-id="1363e-117">Select to script stored procedures to create or drop pull subscriptions and replication jobs.</span></span>  
  
 <span data-ttu-id="1363e-118">**[若要建立或啟用元件]** 與 **[若要卸除或停用元件]**</span><span class="sxs-lookup"><span data-stu-id="1363e-118">**To create or enable the components** and **To drop or disable the components**</span></span>  
 <span data-ttu-id="1363e-119">指定指令碼是否應包含建立或卸除複寫物件的命令。</span><span class="sxs-lookup"><span data-stu-id="1363e-119">Specify whether the script should include commands for creating or dropping a replication object.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="1363e-120">建議您使用對話方塊來建立一組啟用和停用元件的指令碼。</span><span class="sxs-lookup"><span data-stu-id="1363e-120">recommends that you use the dialog box to create a set of scripts for enabling and disabling components.</span></span>  
  
 <span data-ttu-id="1363e-121">**複寫作業**</span><span class="sxs-lookup"><span data-stu-id="1363e-121">**Replication jobs**</span></span>  
 <span data-ttu-id="1363e-122">選取即可編寫複寫作業的指令碼，但預存程序呼叫除外。</span><span class="sxs-lookup"><span data-stu-id="1363e-122">Select to script replication jobs in addition to stored procedure calls.</span></span> <span data-ttu-id="1363e-123">只有從散發者編寫指令碼時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="1363e-123">This option is available only when scripting from a Distributor.</span></span>  
  
 <span data-ttu-id="1363e-124">複寫預存程序會在執行時建立必要的作業，因此不需要選取此選項。</span><span class="sxs-lookup"><span data-stu-id="1363e-124">Replication stored procedures create the necessary jobs when they are executed, so it is not required to select this option.</span></span> <span data-ttu-id="1363e-125">不過，保留建立作業的記錄，在萬一必須重新建立個別作業時非常有用。</span><span class="sxs-lookup"><span data-stu-id="1363e-125">However, it can be useful to have a record of the jobs created in case an individual job must be recreated.</span></span>  
  
## <a name="generate-sql-script-objectname-options"></a><span data-ttu-id="1363e-126">產生 SQL 指令碼 \<ObjectName> 選項</span><span class="sxs-lookup"><span data-stu-id="1363e-126">Generate SQL Script \<ObjectName> Options</span></span>  
 <span data-ttu-id="1363e-127">**[若要建立或啟用元件]** 與 **[若要卸除或停用元件]**</span><span class="sxs-lookup"><span data-stu-id="1363e-127">**To create or enable the components** and **To drop or disable the components**</span></span>  
 <span data-ttu-id="1363e-128">指定指令碼是否應包含建立或卸除複寫物件的命令。</span><span class="sxs-lookup"><span data-stu-id="1363e-128">Specify whether the script should include commands for creating or dropping a replication object.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="1363e-129">建議您使用對話方塊來建立一組啟用和停用元件的指令碼。</span><span class="sxs-lookup"><span data-stu-id="1363e-129">recommends that you use the dialog box, creating a set of scripts for enabling and disabling components.</span></span>  
  
 <span data-ttu-id="1363e-130">**複寫作業**</span><span class="sxs-lookup"><span data-stu-id="1363e-130">**Replication jobs**</span></span>  
 <span data-ttu-id="1363e-131">只能從 **[產生 SQL 指令碼]** 對話方塊使用此選項。</span><span class="sxs-lookup"><span data-stu-id="1363e-131">This option is available only from the **Generate SQL Script** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1363e-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1363e-132">See Also</span></span>  
 [<span data-ttu-id="1363e-133">編寫複寫指令碼</span><span class="sxs-lookup"><span data-stu-id="1363e-133">Scripting Replication</span></span>](scripting-replication.md)  
  
  
