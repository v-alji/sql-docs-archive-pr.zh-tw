---
title: 發行集資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.publicationdatabase.f1
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 511e5f2e2caa934313ba96fb3dbc4cadddace968
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585294"
---
# <a name="publication-database"></a><span data-ttu-id="f072c-102">發行集資料庫</span><span class="sxs-lookup"><span data-stu-id="f072c-102">Publication Database</span></span>
  <span data-ttu-id="f072c-103">發行集資料庫是在發行者上的資料庫，它是要被複寫之資料和資料庫物件的來源。</span><span class="sxs-lookup"><span data-stu-id="f072c-103">The publication database is the database on the Publisher that is the source of data and database objects to be replicated.</span></span> <span data-ttu-id="f072c-104">必須啟用用於複寫的每個發行集資料庫。</span><span class="sxs-lookup"><span data-stu-id="f072c-104">Each publication database used in replication must be enabled.</span></span> <span data-ttu-id="f072c-105">當 **系統管理員 (sysadmin)** 固定伺服器角色的成員執行下列各項動作時，會啟用資料庫：</span><span class="sxs-lookup"><span data-stu-id="f072c-105">The database is enabled when a member of the **sysadmin** fixed server role:</span></span>  
  
-   <span data-ttu-id="f072c-106">使用新增發行集精靈在該資料庫上建立發行集。</span><span class="sxs-lookup"><span data-stu-id="f072c-106">Creates a publication on that database using the New Publication Wizard.</span></span>  
  
-   <span data-ttu-id="f072c-107">選取 **[發行者屬性]** 對話方塊中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="f072c-107">Selects the database in the **Publisher Properties** dialog box.</span></span>  
  
-   <span data-ttu-id="f072c-108">執行 **sp_replicationdboption** 並將 [發行]  選項 (適用於快照集或交易式發行集) 或 [合併發行]  選項 (適用於合併式發行集) 設定為 [True]  。</span><span class="sxs-lookup"><span data-stu-id="f072c-108">Executes **sp_replicationdboption** and sets the option **publish** (for snapshot or transactional publications) or **merge publish** (for merge publications) to **True**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f072c-109">選項。</span><span class="sxs-lookup"><span data-stu-id="f072c-109">Options</span></span>  
 <span data-ttu-id="f072c-110">**資料庫**</span><span class="sxs-lookup"><span data-stu-id="f072c-110">**Databases**</span></span>  
 <span data-ttu-id="f072c-111">選取包含您要發行之資料與資料庫物件的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="f072c-111">Select the name of the database that contains the data and database objects that you want to publish.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f072c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f072c-112">See Also</span></span>  
 <span data-ttu-id="f072c-113">[發行資料和資料庫物件](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="f072c-113">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="f072c-114">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="f072c-114">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="f072c-115">[檢視及修改散發者和發行者屬性](view-and-modify-distributor-and-publisher-properties.md) </span><span class="sxs-lookup"><span data-stu-id="f072c-115">[View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md) </span></span>  
 [<span data-ttu-id="f072c-116">sp_replicationdboption &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f072c-116">sp_replicationdboption &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)  
  
  
