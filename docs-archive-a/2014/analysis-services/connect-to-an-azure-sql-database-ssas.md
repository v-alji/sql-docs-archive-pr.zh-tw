---
title: 連接到 Azure SQL Database (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlazure.f1
ms.assetid: 4e0344e9-1822-4698-ad22-05f1f341ced7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 91ae6f0f5ab95d3013b6348bd43ddb746fff1c22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593013"
---
# <a name="connect-to-an-azure-sql-database-ssas"></a><span data-ttu-id="e30ec-102">連接到 Azure SQL 資料庫 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="e30ec-102">Connect to an Azure SQL Database (SSAS)</span></span>
  <span data-ttu-id="e30ec-103">**[資料表匯入精靈]** 的這個頁面可讓您連接到 [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e30ec-103">This page of the **Table Import Wizard** enables you to connect to a [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="e30ec-104">若要從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]存取精靈，請按一下 **[模型]** 功能表上的 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="e30ec-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e30ec-105">如果您要連接到 Azure DataMarket 資料集，請參閱[連接到報表或資料摘要 &#40;SSAS&#41;](connect-to-a-report-or-data-feed-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="e30ec-105">If you are connecting to an Azure DataMarket dataset, see [Connect to a Report or Data Feed &#40;SSAS&#41;](connect-to-a-report-or-data-feed-ssas.md).</span></span>  
  
 <span data-ttu-id="e30ec-106">[!INCLUDE[ssSDS](../includes/sssds-md.md)] 是裝載型的關聯式資料庫，您可以使用 SQL Server 驗證與其連接。</span><span class="sxs-lookup"><span data-stu-id="e30ec-106">The [!INCLUDE[ssSDS](../includes/sssds-md.md)] is a hosted, relational database that you connect to by using SQL Server Authentication.</span></span> <span data-ttu-id="e30ec-107">如需有關 [!INCLUDE[ssSDS](../includes/sssds-md.md)]的詳細資訊，請參閱 [SQL 資料庫](https://go.microsoft.com/fwlink/?LinkID=157856)網站。</span><span class="sxs-lookup"><span data-stu-id="e30ec-107">For more information about [!INCLUDE[ssSDS](../includes/sssds-md.md)], see the web site [SQL Database](https://go.microsoft.com/fwlink/?LinkID=157856).</span></span> <span data-ttu-id="e30ec-108">若要連接至資料來源，您必須先在電腦上安裝適當的提供者。</span><span class="sxs-lookup"><span data-stu-id="e30ec-108">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e30ec-109">在這個頁面中選取資料庫時，會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="e30ec-109">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="e30ec-110">不過，如果在 [模擬資訊] 頁面中指定的使用者未具備從所選取資料庫讀取的權限，則匯入將不會成功。</span><span class="sxs-lookup"><span data-stu-id="e30ec-110">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="e30ec-111">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="e30ec-111">UI element list</span></span>  
 <span data-ttu-id="e30ec-112">**易記連接名稱**</span><span class="sxs-lookup"><span data-stu-id="e30ec-112">**Friendly connection name**</span></span>  
 <span data-ttu-id="e30ec-113">為此資料來源連接輸入唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="e30ec-113">Type a unique name for this data source connection.</span></span> <span data-ttu-id="e30ec-114">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="e30ec-114">This is a required field.</span></span>  
  
 <span data-ttu-id="e30ec-115">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="e30ec-115">**Server name**</span></span>  
 <span data-ttu-id="e30ec-116">輸入要連接的伺服器名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e30ec-116">Type the name, or IP address, of the server to connect to.</span></span>  
  
 <span data-ttu-id="e30ec-117">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="e30ec-117">**User name**</span></span>  
 <span data-ttu-id="e30ec-118">為資料庫連接指定使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="e30ec-118">Specify a user name for the database connection.</span></span>  
  
 <span data-ttu-id="e30ec-119">這個使用者名稱是在建構資料來源的連接字串時使用。</span><span class="sxs-lookup"><span data-stu-id="e30ec-119">This user name is used when constructing the connection string for the data source.</span></span> <span data-ttu-id="e30ec-120">這些認證也會在預覽和篩選 [資料表屬性] 視窗和 [匯入精靈] 中的資料時使用。</span><span class="sxs-lookup"><span data-stu-id="e30ec-120">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="e30ec-121">這些認證不會用來匯入或重新整理資料，而是會使用 [模擬資訊] 頁面上指定的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="e30ec-121">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="e30ec-122">**密碼**</span><span class="sxs-lookup"><span data-stu-id="e30ec-122">**Password**</span></span>  
 <span data-ttu-id="e30ec-123">為資料庫連接指定密碼。</span><span class="sxs-lookup"><span data-stu-id="e30ec-123">Specify a password for the database connection.</span></span>  
  
 <span data-ttu-id="e30ec-124">**儲存密碼**</span><span class="sxs-lookup"><span data-stu-id="e30ec-124">**Save my password**</span></span>  
 <span data-ttu-id="e30ec-125">指定是否要儲存您在 **[密碼]** 方塊中輸入的密碼。</span><span class="sxs-lookup"><span data-stu-id="e30ec-125">Specify whether the password you have entered in the **Password** box is stored.</span></span>  
  
 <span data-ttu-id="e30ec-126">**資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="e30ec-126">**Database name**</span></span>  
 <span data-ttu-id="e30ec-127">從資料庫清單中選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="e30ec-127">Select a database from the list of databases.</span></span>  
  
 <span data-ttu-id="e30ec-128">**進階**</span><span class="sxs-lookup"><span data-stu-id="e30ec-128">**Advanced**</span></span>  
 <span data-ttu-id="e30ec-129">使用 **[設定進階屬性]** 對話方塊設定其他連接屬性。</span><span class="sxs-lookup"><span data-stu-id="e30ec-129">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="e30ec-130">如需詳細資訊，請參閱[設定進階屬性 &#40;SSAS&#41;](set-advanced-properties-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="e30ec-130">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="e30ec-131">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="e30ec-131">**Test Connection**</span></span>  
 <span data-ttu-id="e30ec-132">嘗試使用目前的設定建立與資料來源之間的連接。</span><span class="sxs-lookup"><span data-stu-id="e30ec-132">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="e30ec-133">顯示一則訊息，指出連接是否成功。</span><span class="sxs-lookup"><span data-stu-id="e30ec-133">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
