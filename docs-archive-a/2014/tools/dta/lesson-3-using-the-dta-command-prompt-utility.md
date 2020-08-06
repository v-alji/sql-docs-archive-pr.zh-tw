---
title: 第3課：使用 dta 命令提示字元公用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: 30f27f4d-8852-4b12-ba62-57f63e496f1d
author: stevestein
ms.author: sstein
ms.openlocfilehash: abbde02cd73e01937e6d0669c10f2db28da8a76e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686626"
---
# <a name="lesson-3-using-the-dta-command-prompt-utility"></a><span data-ttu-id="f99ba-102">第 3 課：使用 dta 命令提示字元公用程式</span><span class="sxs-lookup"><span data-stu-id="f99ba-102">Lesson 3: Using the dta Command Prompt Utility</span></span>
  <span data-ttu-id="f99ba-103">除了 Database Engine Tuning Advisor 所提供的功能，**dta** 命令提示字元公用程式還提供額外的功能。</span><span class="sxs-lookup"><span data-stu-id="f99ba-103">The **dta** command-prompt utility offers functionality in addition to that provided by the Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="f99ba-104">您可以利用您愛用的 XML 工具和 Database Engine Tuning Advisor XML 結構描述來建立這個公用程式的輸入檔。</span><span class="sxs-lookup"><span data-stu-id="f99ba-104">You can use your favorite XML tools to create input files for the utility by using the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="f99ba-105">這個結構描述會在您安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時一併安裝，並且位於：C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd。</span><span class="sxs-lookup"><span data-stu-id="f99ba-105">This schema is installed when you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and can be found at: C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd.</span></span>  
  
 <span data-ttu-id="f99ba-106">您也可以透過 [Microsoft 網站](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409)，線上取得 Database Engine Tuning Advisor XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="f99ba-106">The Database Engine Tuning Advisor XML schema is also available online at [this Microsoft Web site](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409).</span></span>  
  
 <span data-ttu-id="f99ba-107">在微調選項的設定上，Database Engine Tuning Advisor XML 結構描述非常靈活。</span><span class="sxs-lookup"><span data-stu-id="f99ba-107">The Database Engine Tuning Advisor XML schema provides more flexibility to set tuning options.</span></span> <span data-ttu-id="f99ba-108">例如，它可讓您進行「假設」分析。</span><span class="sxs-lookup"><span data-stu-id="f99ba-108">For example, it enables you to perform "what-if" analysis.</span></span> <span data-ttu-id="f99ba-109">「假設」分析包括針對您要微調的資料庫來指定一組現有的實體設計結構和假設的實體設計結構，再利用 Database Engine Tuning Advisor 來分析它，以了解這個假設的實體設計是否能改進查詢處理效能。</span><span class="sxs-lookup"><span data-stu-id="f99ba-109">"What-if" analysis involves specifying a set of existing and hypothetical physical design structures for the database you want to tune, and then analyzing it with the Database Engine Tuning Advisor to find out whether this hypothetical physical design will improve query processing performance.</span></span> <span data-ttu-id="f99ba-110">這類分析的好處是既能夠評估新的組態，又免除了實際實作的負擔。</span><span class="sxs-lookup"><span data-stu-id="f99ba-110">This type of analysis provides the advantage of evaluating the new configuration without incurring the overhead of actually implementing it.</span></span> <span data-ttu-id="f99ba-111">如果假設的實體設計所改進的效能不符需求，您很容易改變它，再分析它，直到產生的結果符合需求的組態出現為止。</span><span class="sxs-lookup"><span data-stu-id="f99ba-111">If your hypothetical physical design does not provide the performance improvements you want, it is easy to change it and analyze it again until you reach the configuration that produces the results you need.</span></span>  
  
 <span data-ttu-id="f99ba-112">此外，在使用 Database Engine Tuning Advisor XML 結構描述和 **dta** 命令提示字元公用程式時，您也可以將 Database Engine Tuning Advisor 功能納入指令碼中，再搭配其他資料庫設計工具來使用它。</span><span class="sxs-lookup"><span data-stu-id="f99ba-112">In addition, using the Database Engine Tuning Advisor XML schema and the **dta** command-prompt utility, you can incorporate Database Engine Tuning Advisor functionality into scripts and use it with other database design tools.</span></span>  
  
 <span data-ttu-id="f99ba-113">如何使用 Database Engine Tuning Advisor 的 XML 輸入功能不在這個課程的範圍內。</span><span class="sxs-lookup"><span data-stu-id="f99ba-113">Using the XML input functionality of Database Engine Tuning Advisor is beyond the scope of this lesson.</span></span>  
  
 <span data-ttu-id="f99ba-114">這個課程介紹基本的 **dta** 命令提示字元公用程式語法、存取說明的方法，以及微調簡單工作負載的練習。</span><span class="sxs-lookup"><span data-stu-id="f99ba-114">This lesson provides an introduction to the basic **dta** command-prompt utility syntax, how to access help, and practice for tuning simple workloads.</span></span>  
  
 <span data-ttu-id="f99ba-115">它包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="f99ba-115">It contains the following topic:</span></span>  
  
-   <span data-ttu-id="f99ba-116">啟動**dta**命令提示字元公用程式和微調工作負載</span><span class="sxs-lookup"><span data-stu-id="f99ba-116">Starting the **dta** Command Prompt Utility and Tuning a Workload</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="f99ba-117">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="f99ba-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="f99ba-118">啟動 dta 命令提示字元公用程式和微調工作負載</span><span class="sxs-lookup"><span data-stu-id="f99ba-118">Starting the dta Command Prompt Utility and Tuning a Workload</span></span>](lesson-1-1-tuning-a-workload.md)  
  
  
