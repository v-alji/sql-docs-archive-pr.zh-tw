---
title: 管理 Oracle 資料表空間 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], managing tablespaces
- tablespaces [SQL Server replication]
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a3624aed38a7a5bf75e0c0807aa8d3657156264f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702757"
---
# <a name="manage-oracle-tablespaces"></a><span data-ttu-id="9728f-102">管理 Oracle 資料表空間</span><span class="sxs-lookup"><span data-stu-id="9728f-102">Manage Oracle Tablespaces</span></span>
  <span data-ttu-id="9728f-103">資料表空間是資料庫的儲存單位，大致相當於 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="9728f-103">A tablespace is a unit of database storage that is roughly equivalent to a file group in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9728f-104">資料表空間允許在個別群組中儲存和管理資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="9728f-104">Tablespaces allow storage and management of database objects within individual groups.</span></span> <span data-ttu-id="9728f-105">如需詳細資訊，請參閱 Oracle 文件集。</span><span class="sxs-lookup"><span data-stu-id="9728f-105">For more information, see the Oracle documentation.</span></span>  
  
 <span data-ttu-id="9728f-106">將資料表設定為 Oracle 發行集的一部分，您可以在儲存複寫記錄資訊時選擇性地指定使用現有的 Oracle 資料表空間。</span><span class="sxs-lookup"><span data-stu-id="9728f-106">When you configure a table as part of an Oracle publication, you can optionally specify an existing Oracle tablespace to be used when storing replication logging information.</span></span> <span data-ttu-id="9728f-107">如果未指定，則複寫物件的資料表空間為與複寫管理使用者結構描述相關的預設資料表空間，該複寫管理使用者結構描述在設定「發行者」時設定。</span><span class="sxs-lookup"><span data-stu-id="9728f-107">If unspecified, the tablespace for the replication objects is the default tablespace associated with the replication administrative user schema that was configured when configuring the Publisher.</span></span>  
  
 <span data-ttu-id="9728f-108">**為發行項記錄資料表指定資料表空間**：</span><span class="sxs-lookup"><span data-stu-id="9728f-108">**To specify a tablespace for an article logging table**:</span></span>  
  
-   <span data-ttu-id="9728f-109">在 **[發行項屬性]** 對話方塊中指定資料表空間。</span><span class="sxs-lookup"><span data-stu-id="9728f-109">Specify a tablespace in the **Article Properties** dialog box.</span></span> <span data-ttu-id="9728f-110">如需有關存取這個對話方塊的詳細資訊，請參閱＜ [View and Modify Publication Properties](../publish/view-and-modify-publication-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9728f-110">For more information about accessing this dialog box, see [View and Modify Publication Properties](../publish/view-and-modify-publication-properties.md).</span></span>  
  
-   <span data-ttu-id="9728f-111">使用 [sp_changearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9728f-111">Use [sp_changearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql).</span></span> <span data-ttu-id="9728f-112">若要使用 **sp_changearticle**，請指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="9728f-112">To use **sp_changearticle**, specify the following:</span></span>  
  
    -   <span data-ttu-id="9728f-113">參數的 Oracle 發行者名稱 **@publisher** 。</span><span class="sxs-lookup"><span data-stu-id="9728f-113">The name of the Oracle Publisher for the parameter **@publisher**.</span></span>  
  
    -   <span data-ttu-id="9728f-114">參數的 Oracle 發行集名稱 **@publication** 。</span><span class="sxs-lookup"><span data-stu-id="9728f-114">The name of the Oracle publication for the parameter **@publication**.</span></span>  
  
    -   <span data-ttu-id="9728f-115">參數的發行項名稱 **@article** 。</span><span class="sxs-lookup"><span data-stu-id="9728f-115">The name of the article for the parameter **@article**.</span></span>  
  
    -   <span data-ttu-id="9728f-116">參數的 ' 資料表空間 ' 值 **@property** 。</span><span class="sxs-lookup"><span data-stu-id="9728f-116">A value of 'tablespace' for the parameter **@property**.</span></span>  
  
    -   <span data-ttu-id="9728f-117">參數的資料表空間名稱 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="9728f-117">The name of the tablespace for the parameter **@value**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9728f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9728f-118">See Also</span></span>  
 <span data-ttu-id="9728f-119">[設定 Oracle 發行者](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="9728f-119">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 [<span data-ttu-id="9728f-120">在 Oracle 發行者端建立的物件</span><span class="sxs-lookup"><span data-stu-id="9728f-120">Objects Created on the Oracle Publisher</span></span>](objects-created-on-the-oracle-publisher.md)  
  
  
