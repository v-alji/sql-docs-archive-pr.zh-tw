---
title: 連接到 Microsoft SQL Server 平行處理資料倉儲 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlparadatawh.f1
ms.assetid: 98c879ee-7257-40c9-bc85-6766bd3b4885
author: minewiskan
ms.author: owend
ms.openlocfilehash: 082d6b34077d1bde11b527d3bfff907073eed16e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593016"
---
# <a name="connect-to-a-microsoft-sql-server-parallel-data-warehouse-ssas"></a><span data-ttu-id="9e302-102">連接到 Microsoft SQL Server Parallel Data Warehouse (SSAS)</span><span class="sxs-lookup"><span data-stu-id="9e302-102">Connect to a Microsoft SQL Server Parallel Data Warehouse (SSAS)</span></span>
  <span data-ttu-id="9e302-103">[資料表匯入精靈]\*\*\*\* 的這個頁面可讓您指定連接到 Microsoft SQL Server 平行處理資料倉儲 (PDW) 的設定。</span><span class="sxs-lookup"><span data-stu-id="9e302-103">This page of the **Table Import Wizard** enables you to specify settings to connect to a Microsoft SQL Server Parallel Data Warehouse (PDW).</span></span> <span data-ttu-id="9e302-104">若要從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]存取精靈，請按一下 **[模型]** 功能表上的 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="9e302-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="9e302-105">SQL Server PDW 是具有高擴充性的應用裝置，以極低成本透過大量平行處理提供效能。</span><span class="sxs-lookup"><span data-stu-id="9e302-105">SQL Server PDW is a highly scalable appliance that delivers performance at low cost through massively parallel processing.</span></span> <span data-ttu-id="9e302-106">如需有關 SQL Server PDW 的詳細資訊，請參閱 [SQL Server 2008 R2 Parallel Data Warehouse](https://go.microsoft.com/fwlink/?LinkId=150895)網站。</span><span class="sxs-lookup"><span data-stu-id="9e302-106">For more information about SQL Server PDW, see the web site [SQL Server 2008 R2 Parallel Data Warehouse](https://go.microsoft.com/fwlink/?LinkId=150895).</span></span> <span data-ttu-id="9e302-107">您可以使用 SQL Server 驗證連接到資料倉儲。</span><span class="sxs-lookup"><span data-stu-id="9e302-107">You connect to the data warehouse by using SQL Server Authentication.</span></span> <span data-ttu-id="9e302-108">若要連接至資料來源，您必須先在電腦上安裝適當的提供者。</span><span class="sxs-lookup"><span data-stu-id="9e302-108">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e302-109">在這個頁面中選取資料庫時，會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="9e302-109">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="9e302-110">不過，如果在 [模擬資訊] 頁面中指定的使用者未具備從所選取資料庫讀取的權限，則匯入將不會成功。</span><span class="sxs-lookup"><span data-stu-id="9e302-110">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="9e302-111">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="9e302-111">UI element list</span></span>  
 <span data-ttu-id="9e302-112">**易記連接名稱**</span><span class="sxs-lookup"><span data-stu-id="9e302-112">**Friendly connection name**</span></span>  
 <span data-ttu-id="9e302-113">為此資料來源連接輸入唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="9e302-113">Type a unique name for this data source connection.</span></span> <span data-ttu-id="9e302-114">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="9e302-114">This is a required field.</span></span>  
  
 <span data-ttu-id="9e302-115">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="9e302-115">**Server name**</span></span>  
 <span data-ttu-id="9e302-116">輸入要連接的伺服器名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="9e302-116">Type the name, or IP address, of the server to connect to.</span></span>  
  
 <span data-ttu-id="9e302-117">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="9e302-117">**User name**</span></span>  
 <span data-ttu-id="9e302-118">為資料庫連接指定使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="9e302-118">Specify a user name for the database connection.</span></span>  
  
 <span data-ttu-id="9e302-119">這個使用者名稱是在建構資料來源的連接字串時使用。</span><span class="sxs-lookup"><span data-stu-id="9e302-119">This user name is used when constructing the connection string for the data source.</span></span> <span data-ttu-id="9e302-120">這些認證也會在預覽和篩選 [資料表屬性] 視窗和 [匯入精靈] 中的資料時使用。</span><span class="sxs-lookup"><span data-stu-id="9e302-120">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="9e302-121">這些認證不會用來匯入或重新整理資料，而是會使用 [模擬資訊] 頁面上指定的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="9e302-121">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="9e302-122">**密碼**</span><span class="sxs-lookup"><span data-stu-id="9e302-122">**Password**</span></span>  
 <span data-ttu-id="9e302-123">為資料庫連接指定密碼。</span><span class="sxs-lookup"><span data-stu-id="9e302-123">Specify a password for the database connection.</span></span>  
  
 <span data-ttu-id="9e302-124">**儲存密碼**</span><span class="sxs-lookup"><span data-stu-id="9e302-124">**Save my password**</span></span>  
 <span data-ttu-id="9e302-125">指定是否要儲存您在 **[密碼]** 方塊中輸入的密碼。</span><span class="sxs-lookup"><span data-stu-id="9e302-125">Specify whether the password you have entered in the **Password** box is stored.</span></span>  
  
 <span data-ttu-id="9e302-126">**資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="9e302-126">**Database name**</span></span>  
 <span data-ttu-id="9e302-127">從資料庫清單中選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="9e302-127">Select a database from the list of databases.</span></span>  
  
 <span data-ttu-id="9e302-128">**進階**</span><span class="sxs-lookup"><span data-stu-id="9e302-128">**Advanced**</span></span>  
 <span data-ttu-id="9e302-129">使用 **[設定進階屬性]** 對話方塊設定其他連接屬性。</span><span class="sxs-lookup"><span data-stu-id="9e302-129">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="9e302-130">如需詳細資訊，請參閱[設定進階屬性 &#40;SSAS&#41;](set-advanced-properties-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="9e302-130">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="9e302-131">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="9e302-131">**Test Connection**</span></span>  
 <span data-ttu-id="9e302-132">嘗試使用目前的設定建立與資料來源之間的連接。</span><span class="sxs-lookup"><span data-stu-id="9e302-132">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="9e302-133">此作業會顯示一則訊息，指出連接是否成功。</span><span class="sxs-lookup"><span data-stu-id="9e302-133">A message displays and indicates whether the connection is successful.</span></span>  
  
  
