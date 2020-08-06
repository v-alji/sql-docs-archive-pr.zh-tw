---
title: 在交易式發行集中發行預存程式的執行 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 44310d45a7049701a6aecfa73301b15b0021ac6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592603"
---
# <a name="publish-the-execution-of-a-stored-procedure-in-a-transactional-publication-sql-server-management-studio"></a><span data-ttu-id="79e91-102">在交易式發行集中發行預存程序的執行項 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="79e91-102">Publish the Execution of a Stored Procedure in a Transactional Publication (SQL Server Management Studio)</span></span>
  <span data-ttu-id="79e91-103">指定應在 [發行項屬性 - \<Article>] 對話方塊中發佈預存程序的執行 (而不僅是其定義)。</span><span class="sxs-lookup"><span data-stu-id="79e91-103">Specify that the execution of a stored procedure (rather than just its definition) should be published in the **Article Properties - \<Article>** dialog box.</span></span> <span data-ttu-id="79e91-104">[新增發行集精靈] 與 [發行集屬性 - \<Publication>] 對話方塊中都有此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="79e91-104">This dialog box is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="79e91-105">如需使用精靈及存取對話方塊的詳細資訊，請參閱[建立發行集](create-a-publication.md)和[檢視及修改發行集屬性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="79e91-105">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
 <span data-ttu-id="79e91-106">初始化訂閱時，會將程序的定義 (CREATE PROCEDURE 陳述式) 複寫到訂閱者；在發行者端執行程序時，複寫會在訂閱者端執行對應的程序。</span><span class="sxs-lookup"><span data-stu-id="79e91-106">The definition of the procedure (the CREATE PROCEDURE statement) is replicated to the Subscriber when the subscription is initialized; when the procedure is executed at the Publisher, replication executes the corresponding procedure at the Subscriber.</span></span>  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a><span data-ttu-id="79e91-107">若要發行預存程序的執行</span><span class="sxs-lookup"><span data-stu-id="79e91-107">To publish the execution of a stored procedure</span></span>  
  
1.  <span data-ttu-id="79e91-108">在 [新增發行集精靈] 的 [發行項] 頁面上，或在 [發行集屬性 - \<Publication>] 對話方塊中，選取一項預存程序。</span><span class="sxs-lookup"><span data-stu-id="79e91-108">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a stored procedure.</span></span>  
  
2.  <span data-ttu-id="79e91-109">按一下 **[發行項屬性]** ，然後再按 **[設定反白顯示預存程序的屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="79e91-109">Click **Article Properties**, and then click **Set Properties of Highlighted Stored Procedure**.</span></span>  
  
3.  <span data-ttu-id="79e91-110">在 [發行項屬性 - \<Article>] 對話方塊中，針對 [複寫] 選項指定下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="79e91-110">In the **Article Properties - \<Article>** dialog box, specify one of the following values for the **Replicate** option:</span></span>  
  
    -   <span data-ttu-id="79e91-111">**[預存程序的執行]**</span><span class="sxs-lookup"><span data-stu-id="79e91-111">**Execution of the stored procedure**</span></span>  
  
    -   <span data-ttu-id="79e91-112">**[SP 的序列式交易執行]**</span><span class="sxs-lookup"><span data-stu-id="79e91-112">**Execution in a serialized transaction of the SP**</span></span>  
  
         <span data-ttu-id="79e91-113">這是建議選項，因為它只會在程序於可序列化的交易內執行時複寫程序執行。</span><span class="sxs-lookup"><span data-stu-id="79e91-113">This is the recommended option, because it replicates the procedure execution only if the procedure is executed within the context of a serializable transaction.</span></span> <span data-ttu-id="79e91-114">如果預存程序在序列化交易外部執行，則對已發行資料表中所做的資料變更會複寫為一連串的資料管理語言 (DML) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="79e91-114">If the stored procedure is executed outside of a serializable transaction, changes to data in published tables are replicated as a series of data manipulation language (DML) statements.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="79e91-115">如果位於 [發行集屬性 - \<Publication>] 對話方塊中，請按一下 [確定] 以儲存並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="79e91-115">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79e91-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79e91-116">See Also</span></span>  
 [<span data-ttu-id="79e91-117">在異動複寫中發行預存程序執行</span><span class="sxs-lookup"><span data-stu-id="79e91-117">Publishing Stored Procedure Execution in Transactional Replication</span></span>](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
