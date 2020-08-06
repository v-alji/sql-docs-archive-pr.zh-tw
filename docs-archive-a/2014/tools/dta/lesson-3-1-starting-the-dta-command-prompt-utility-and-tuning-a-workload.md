---
title: 啟動 dta 命令提示字元公用程式和微調工作負載 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: f34a5acf-1f3b-4484-a770-6470cb925ab0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4b2b1755a2ce8299556ab7d0ae14c89d3b2c8554
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686629"
---
# <a name="starting-the-dta-command-prompt-utility-and-tuning-a-workload"></a><span data-ttu-id="b6483-102">啟動 dta 命令提示字元公用程式和微調工作負載</span><span class="sxs-lookup"><span data-stu-id="b6483-102">Starting the dta Command Prompt Utility and Tuning a Workload</span></span>
  <span data-ttu-id="b6483-103"> 這項工作會帶您逐步啟動 **dta** 公用程式、檢視它的說明，再從命令提示字元之下，使用它來微調工作負載。</span><span class="sxs-lookup"><span data-stu-id="b6483-103">This task guides you through starting the **dta** utility, viewing its Help, and then using it to tune a workload from the command prompt.</span></span> <span data-ttu-id="b6483-104">它會使用您為 Database Engine Tuning Advisor 圖形化使用者介面所建立的工作負載 Myscript.sql， (GUI) 練習[微調工作負載](lesson-1-1-tuning-a-workload.md)。</span><span class="sxs-lookup"><span data-stu-id="b6483-104">It uses the workload, MyScript.sql, which you created for the Database Engine Tuning Advisor graphical user interface (GUI) practice [Tuning a Workload](lesson-1-1-tuning-a-workload.md).</span></span>  
  
 <span data-ttu-id="b6483-105">本教學課程使用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="b6483-105">The tutorial uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="b6483-106">基於安全性的考量，依預設，不會安裝範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="b6483-106">For security reasons, the sample databases are not installed by default.</span></span> <span data-ttu-id="b6483-107">若要安裝範例資料庫，請參閱＜ [安裝 SQL Server 範例和範例資料庫](http://sqlserversamples.codeplex.com)＞。</span><span class="sxs-lookup"><span data-stu-id="b6483-107">To install the sample databases, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
 <span data-ttu-id="b6483-108">下列工作將帶您逐步開啟命令提示字元、啟動 **dta** 命令提示字元公用程式、檢視其語法說明，以及微調您在 [微調工作負載](lesson-1-1-tuning-a-workload.md)中所建立的簡單工作負載 MyScript.sql。</span><span class="sxs-lookup"><span data-stu-id="b6483-108">The following tasks guide you through opening a command prompt, starting the **dta** command prompt utility, viewing its syntax Help, and tuning a simple workload, MyScript.sql, which you created in [Tuning a Workload](lesson-1-1-tuning-a-workload.md).</span></span>  
  
### <a name="to-start-the-dta-command-prompt-utility-and-view-help"></a><span data-ttu-id="b6483-109">若要啟動 dta 命令提示字元公用程式和檢視說明</span><span class="sxs-lookup"><span data-stu-id="b6483-109">To start the dta command prompt utility and view Help</span></span>  
  
1.  <span data-ttu-id="b6483-110">在 [開始]\*\*\*\* 功能表上，依序指向 [所有程式]\*\*\*\* 和 [附屬應用程式]\*\*\*\*，再按一下 [命令提示字元]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b6483-110">On the **Start** menu, point to **All Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="b6483-111">在命令提示字元之下，輸入下列字串，再按 ENTER 鍵：</span><span class="sxs-lookup"><span data-stu-id="b6483-111">At the command prompt, type the following, and press ENTER:</span></span>  
  
    ```  
    dta -? | more  
    ```  
  
     <span data-ttu-id="b6483-112">這個命令的 `| more` 部份是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="b6483-112">The `| more` part of this command is optional.</span></span> <span data-ttu-id="b6483-113">不過，您可以利用它來逐頁閱讀公用程式的語法說明。</span><span class="sxs-lookup"><span data-stu-id="b6483-113">However, using it enables you to page through the syntax help for the utility.</span></span> <span data-ttu-id="b6483-114">按 ENTER 鍵會在說明文字中，每次前進一行，按空白鍵則會每次前進一頁。</span><span class="sxs-lookup"><span data-stu-id="b6483-114">Press ENTER to advance the help text by the line, or press the SPACEBAR to advance it by the page.</span></span>  
  
### <a name="to-tune-a-simple-workload-by-using-the-dta-command-prompt-utility"></a><span data-ttu-id="b6483-115">若要利用 dta 命令提示字元公用程式來微調簡單的工作負載</span><span class="sxs-lookup"><span data-stu-id="b6483-115">To tune a simple workload by using the dta command prompt utility</span></span>  
  
1.  <span data-ttu-id="b6483-116">在命令提示字元之下，導覽到儲存 MyScript.sql 檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="b6483-116">At the command prompt, navigate to the directory where you have stored the MyScript.sql file.</span></span>  
  
2.  <span data-ttu-id="b6483-117">在命令提示字元之下，輸入下列字串，再按 ENTER 鍵來執行命令，以及啟動微調工作階段 (請注意，當剖析命令時，這個公用程式會區分大小寫)：</span><span class="sxs-lookup"><span data-stu-id="b6483-117">At the command prompt, type the following, and press ENTER to run the command and start the tuning session (note that the utility is case-sensitive when it parses commands):</span></span>  
  
    ```  
    dta -S YourServerName\YourSQLServerInstanceName -E -D AdventureWorks2012 -if MyScript.sql -s MySession2 -of MySession2OutputScript.sql -ox MySession2Output.xml -fa IDX_IV -fp NONE -fk NONE  
    ```  
  
     <span data-ttu-id="b6483-118">其中 `-S` 指定您的伺服器名稱以及安裝了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b6483-118">where `-S` specifies the name of your server and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance where the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database is installed.</span></span> <span data-ttu-id="b6483-119">`-E` 設定值指定您要使用執行個體的信任連接，當您利用 Windows 網域帳戶來連接時，適合採用這個方式。</span><span class="sxs-lookup"><span data-stu-id="b6483-119">The setting `-E` specifies that you want to use a trusted connection to the instance, which is appropriate if you are connecting with a Windows domain account.</span></span> <span data-ttu-id="b6483-120">`-D` 設定值指定您要微調的資料庫， `-if` 指定工作負載檔案， `-s` 指定工作階段名稱， `-of` 指定工具要將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 建議指令碼寫入其中的檔案， `-ox` 指定工具要將 XML 格式的建議寫入其中的檔案。</span><span class="sxs-lookup"><span data-stu-id="b6483-120">The setting `-D` specifies the database that you want to tune, `-if` specifies the workload file, `-s` specifies the session name, `-of` specifies the file to which you want the tool to write the [!INCLUDE[tsql](../../includes/tsql-md.md)] recommendations script, and `-ox` specifies the file to which you want the tool to write the recommendations in XML format.</span></span> <span data-ttu-id="b6483-121">最後三個參數依照下列方式來指定微調選項： `-fa IDX_IV` 指定 Database Engine Tuning Advisor 只應考慮加入索引 (叢集和非叢集) 和索引檢視； `-fp NONE` 指定在分析期間，完全不應考慮任何資料分割策略； `-fk NONE` 指定 Database Engine Tuning Advisor 在產生建議時，不需要保留資料庫中任何現有的實體設計結構。</span><span class="sxs-lookup"><span data-stu-id="b6483-121">The last three switches specify tuning options as follows: `-fa IDX_IV` specifies that Database Engine Tuning Advisor should only consider adding indexes (both clustered and nonclustered) and indexed views; `-fp NONE` specifies that no partition strategy should be considered during analysis; and `-fk NONE` specifies that no existing physical design structures in the database must be kept when Database Engine Tuning Advisor makes its recommendations.</span></span>  
  
3.  <span data-ttu-id="b6483-122">在 Database Engine Tuning Advisor 微調好工作負載之後，它會顯示一則訊息，指出微調工作階段已順利完成。</span><span class="sxs-lookup"><span data-stu-id="b6483-122">After Database Engine Tuning Advisor finishes tuning the workload, it displays a message indicating that your tuning session completed successfully.</span></span> <span data-ttu-id="b6483-123">您可以利用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來開啟 MySession2OutputScript.sql 和 MySession2Output.xml 檔，以檢視微調結果。</span><span class="sxs-lookup"><span data-stu-id="b6483-123">You can view the tuning results, by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to open the files MySession2OutputScript.sql and MySession2Output.xml.</span></span> <span data-ttu-id="b6483-124">另外，您也可以在 Database Engine Tuning Advisor GUI 中開啟 MySession2 微調工作階段，依照 [檢視微調建議](lesson-1-2-viewing-tuning-recommendations.md) 和 [檢視微調報表](lesson-1-3-viewing-tuning-reports.md)中的相同方式來檢視其建議和報表。</span><span class="sxs-lookup"><span data-stu-id="b6483-124">Alternatively, you can also open the MySession2 tuning session in the Database Engine Tuning Advisor GUI and view its recommendations and reports in the same way that you did in [Viewing Tuning Recommendations](lesson-1-2-viewing-tuning-recommendations.md) and [Viewing Tuning Reports](lesson-1-3-viewing-tuning-reports.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="b6483-125">總結</span><span class="sxs-lookup"><span data-stu-id="b6483-125">Summary</span></span>  
 <span data-ttu-id="b6483-126">您已在命令提示字元之下，利用 **dta** 公用程式完成了簡單工作負載的微調。</span><span class="sxs-lookup"><span data-stu-id="b6483-126">You have completed tuning a simple workload from the command prompt by using the **dta** utility.</span></span> <span data-ttu-id="b6483-127">這個工具也提供了許多其他微調選項。</span><span class="sxs-lookup"><span data-stu-id="b6483-127">This tool provides many other tuning options.</span></span> <span data-ttu-id="b6483-128">如需詳細資訊，請參閱工具說明 (**dta -?**) 和參考主題 [dta 公用程式](dta-utility.md) 。</span><span class="sxs-lookup"><span data-stu-id="b6483-128">Refer to the tool Help (**dta -?**) and the reference topic [dta Utility](dta-utility.md) for more information.</span></span>  
  
## <a name="after-you-finish-this-tutorial"></a><span data-ttu-id="b6483-129">完成這個教學課程之後</span><span class="sxs-lookup"><span data-stu-id="b6483-129">After You Finish This Tutorial</span></span>  
 <span data-ttu-id="b6483-130">完成這個教學課程中的課程之後，請參閱下列主題，以取得有關 Database Engine Tuning Advisor 的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="b6483-130">After you finish the lessons in this tutorial, refer to the following topics for more information about Database Engine Tuning Advisor:</span></span>  
  
-   <span data-ttu-id="b6483-131">＜[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md) ＞提供如何利用這個工具來執行工作的描述。</span><span class="sxs-lookup"><span data-stu-id="b6483-131">[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md) for descriptions of how to perform tasks with this tool.</span></span>  
  
-   <span data-ttu-id="b6483-132">＜[dta Utility](dta-utility.md) ＞提供有關命令提示字元公用程式的參考資料，以及可用來控制公用程式作業的選擇性 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="b6483-132">[dta Utility](dta-utility.md) for reference material on the command prompt utility and the optional XML file you can use to control the operation of the utility.</span></span>  
  
 <span data-ttu-id="b6483-133">若要返回教學課程的開頭，請參閱 [教學課程：Database Engine Tuning Advisor](tutorial-database-engine-tuning-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="b6483-133">To return to the start of the tutorial, see [Tutorial: Database Engine Tuning Advisor](tutorial-database-engine-tuning-advisor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6483-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6483-134">See Also</span></span>  
 [<span data-ttu-id="b6483-135">Database Engine 教學課程</span><span class="sxs-lookup"><span data-stu-id="b6483-135">Database Engine Tutorials</span></span>](../../relational-databases/database-engine-tutorials.md)  
  
  
