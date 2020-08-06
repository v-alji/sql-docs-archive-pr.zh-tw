---
title: 授與資料來源物件的許可權 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.datasources.f1
helpviewer_keywords:
- read/write permissions
- user access rights [Analysis Services], data sources
- security [Analysis Services], data sources
- connection strings [Analysis Services]
- data sources [Analysis Services], security
ms.assetid: b4e302d3-c93b-4383-aa4a-37d15c129830
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0a7de676f5863187c2c137e056392a605af474f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703345"
---
# <a name="grant-permissions-on-a-data-source-object-analysis-services"></a><span data-ttu-id="70f7d-102">授與資料來源物件的權限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="70f7d-102">Grant permissions on a data source object (Analysis Services)</span></span>
  <span data-ttu-id="70f7d-103">通常，大部分的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 使用者都不需要存取 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案的基礎資料來源。</span><span class="sxs-lookup"><span data-stu-id="70f7d-103">Typically, most users of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] do not require access to the data sources that underlie an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="70f7d-104">使用者通常只會查詢 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫內的資料。</span><span class="sxs-lookup"><span data-stu-id="70f7d-104">Users ordinarily just query the data within an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="70f7d-105">不過，在資料採礦的內容中，例如要執行以採礦模型為基礎的預測時，使用者就必須聯結採礦模型的所獲得 (Learned) 資料與使用者提供的資料。</span><span class="sxs-lookup"><span data-stu-id="70f7d-105">However, in the context of data mining, such as performing predictions based on a mining model, a user has to join the learned data of a mining model with user-provided data.</span></span> <span data-ttu-id="70f7d-106">若要連接到包含使用者所提供資料的資料來源，使用者要使用包含 [OPENQUERY &#40;DMX&#41;](/sql/dmx/source-data-query-openquery) 和 [OPENROWSET &#40;DMX&#41;](/sql/dmx/source-data-query-openrowset) 子句的資料採礦延伸模組 (DMX) 查詢。</span><span class="sxs-lookup"><span data-stu-id="70f7d-106">To connect to the data source that contains the user-provided data, the user uses a Data Mining Extensions (DMX) query that contains either the [OPENQUERY &#40;DMX&#41;](/sql/dmx/source-data-query-openquery) and [OPENROWSET &#40;DMX&#41;](/sql/dmx/source-data-query-openrowset) clause.</span></span>  
  
 <span data-ttu-id="70f7d-107">若要執行連接到資料來源的 DMX 查詢，使用者必須存取 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫內的資料來源物件。</span><span class="sxs-lookup"><span data-stu-id="70f7d-107">To execute a DMX query that connects to a data source, the user must have access to the data source object within the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="70f7d-108">根據預設，只有伺服器管理員或資料庫管理員擁有存取資料來源物件的權限。</span><span class="sxs-lookup"><span data-stu-id="70f7d-108">By default, only Server Administrators or Database Administrators have access to data source objects.</span></span> <span data-ttu-id="70f7d-109">這表示除非管理員授與權限，否則使用者無法存取資料來源物件。</span><span class="sxs-lookup"><span data-stu-id="70f7d-109">This means that a user cannot access a data source object unless an administrator grants permissions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="70f7d-110">基於安全性的考量，在 OPENROWSET 子句中使用開放式連接字串來提交 DMX 查詢的功能已停用。</span><span class="sxs-lookup"><span data-stu-id="70f7d-110">For security reasons, the submission of DMX queries by using an open connection string in the OPENROWSET clause is disabled.</span></span>  
  
## <a name="set-read-permissions-to-a-data-source"></a><span data-ttu-id="70f7d-111">設定資料來源的讀取權限</span><span class="sxs-lookup"><span data-stu-id="70f7d-111">Set Read permissions to a data source</span></span>  
 <span data-ttu-id="70f7d-112">資料庫角色可以不被授與資料來源物件的任何存取權限，也可以被授與讀取權限。</span><span class="sxs-lookup"><span data-stu-id="70f7d-112">A database role can be granted either no access permissions on a data source object or read permissions.</span></span>  
  
1.  <span data-ttu-id="70f7d-113">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的執行個體，在物件總管中展開適當資料庫的 [角色]\*\*\*\*，然後按一下資料庫角色 (或建立新的資料庫角色)。</span><span class="sxs-lookup"><span data-stu-id="70f7d-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], expand **Roles** for the appropriate database in Object explorer, and then click a database role (or create a new database role).</span></span>  
  
2.  <span data-ttu-id="70f7d-114">在 [資料來源存取]\*\*\*\* 窗格的 [資料來源]\*\*\*\* 清單中尋找資料來源物件，然後在該資料來源的 [存取]\*\*\*\* 清單中選取 [讀取]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="70f7d-114">In the **Data Source Access** pane, locate the data source object in the **Data Source** list, and then select the **Read** in the **Access** list for the data source.</span></span> <span data-ttu-id="70f7d-115">如果這個選項無法使用，請檢查 [一般]\*\*\*\* 窗格，以查看是否已選取 [完整控制權]。</span><span class="sxs-lookup"><span data-stu-id="70f7d-115">If this option is unavailable, check the **General** pane to see if Full Control is selected.</span></span> <span data-ttu-id="70f7d-116">[完整控制權] 已經提供權限，您無法覆寫資料來源的權限。</span><span class="sxs-lookup"><span data-stu-id="70f7d-116">Full Control is already providing permission, you cannot override permissions on the data source.</span></span>  
  
## <a name="working-with-the-connection-string-used-by-a-data-source-object"></a><span data-ttu-id="70f7d-117">使用資料來源物件使用的連接字串</span><span class="sxs-lookup"><span data-stu-id="70f7d-117">Working With the Connection String Used by a Data Source Object</span></span>  
 <span data-ttu-id="70f7d-118">資料來源物件會包含用於連接到基礎資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="70f7d-118">The data source object contains the connection string that is used to connect to the underlying data source.</span></span> <span data-ttu-id="70f7d-119">此連接字串可指定下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="70f7d-119">This connection string can specify one of the following:</span></span>  
  
-   <span data-ttu-id="70f7d-120">**指定使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="70f7d-120">**Specify a user name and password**</span></span>  
  
     <span data-ttu-id="70f7d-121">如果資料來源物件使用的連接字串有指定使用者名稱和密碼，您可能需要建立多個資料來源物件，使每一個有不同的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="70f7d-121">If the connection string that a data source object uses specifies a user name and password, you may want to create multiple data source objects, each with different user accounts.</span></span> <span data-ttu-id="70f7d-122">建立多個資料來源物件可讓使用者存取特定資料來源物件，及防止該些使用者存取其他資料來源物件。</span><span class="sxs-lookup"><span data-stu-id="70f7d-122">Creating multiple data source objects lets users access certain data source objects and prevents those users from accessing other data source objects.</span></span> <span data-ttu-id="70f7d-123">這些其他資料來源物件可由 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 本身用於處理物件，例如 Cube 和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="70f7d-123">These other data source objects can be used by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] itself for processing objects, such as cubes and mining models.</span></span>  
  
-   <span data-ttu-id="70f7d-124">**指定 Windows 驗證**</span><span class="sxs-lookup"><span data-stu-id="70f7d-124">**Specify Windows Authentication**</span></span>  
  
     <span data-ttu-id="70f7d-125">如果資料來源物件使用的連接字串指定 Windows 驗證，則 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 必須能夠模擬用戶端。</span><span class="sxs-lookup"><span data-stu-id="70f7d-125">If the connection string that a data source object uses specifies Windows Authentication, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] must be able to impersonate the client.</span></span> <span data-ttu-id="70f7d-126">如果資料來源是在遠端電腦上，就必須使用 Kerberos 驗證來建立兩部電腦之間的信任以進行模擬，否則查詢通常會失敗。</span><span class="sxs-lookup"><span data-stu-id="70f7d-126">If the data source is on a remote computer, the two computers must be trusted for impersonation by using Kerberos authentication, or the query will typically fail.</span></span> <span data-ttu-id="70f7d-127">如需詳細資訊，請參閱 [設定 Analysis Services 進行 Kerberos 限制委派](../instances/configure-analysis-services-for-kerberos-constrained-delegation.md) 。</span><span class="sxs-lookup"><span data-stu-id="70f7d-127">See [Configure Analysis Services for Kerberos constrained delegation](../instances/configure-analysis-services-for-kerberos-constrained-delegation.md) for more information.</span></span>  
  
     <span data-ttu-id="70f7d-128">如果用戶端不容許模擬 (透過 OLE DB 和其他用戶端元件的模擬層級屬性)， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 將會嘗試與基礎資料來源建立匿名連線。</span><span class="sxs-lookup"><span data-stu-id="70f7d-128">If the client does not allow for impersonation (through the Impersonation Level property in OLE DB and other client components), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will try to make an anonymous connection to the underlying data source.</span></span> <span data-ttu-id="70f7d-129">匿名連線遠端資料來源很少成功，因為大部分的資料來源都不接受匿名連線)。</span><span class="sxs-lookup"><span data-stu-id="70f7d-129">Anonymous connections to remote data sources rarely succeed, as most data sources do not accept anonymous connections).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70f7d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70f7d-130">See Also</span></span>  
 <span data-ttu-id="70f7d-131">[多維度模型中的資料來源](data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="70f7d-131">[Data Sources in Multidimensional Models](data-sources-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="70f7d-132">[連接字串屬性 &#40;Analysis Services&#41;](../instances/connection-string-properties-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="70f7d-132">[Connection String Properties &#40;Analysis Services&#41;](../instances/connection-string-properties-analysis-services.md) </span></span>  
 <span data-ttu-id="70f7d-133">[Analysis Services 支援的驗證方法](../instances/authentication-methodologies-supported-by-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="70f7d-133">[Authentication methodologies supported by Analysis Services](../instances/authentication-methodologies-supported-by-analysis-services.md) </span></span>  
 <span data-ttu-id="70f7d-134">[將維度資料的自訂存取權授與 &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="70f7d-134">[Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) </span></span>  
 <span data-ttu-id="70f7d-135">[授與 cube 或模型許可權 &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="70f7d-135">[Grant cube or model permissions &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md) </span></span>  
 [<span data-ttu-id="70f7d-136">授與資料格資料的自訂存取權 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="70f7d-136">Grant custom access to cell data &#40;Analysis Services&#41;</span></span>](grant-custom-access-to-cell-data-analysis-services.md)  
  
  
