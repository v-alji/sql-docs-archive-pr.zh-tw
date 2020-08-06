---
title: 連接到 Oracle Database (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connoracledb.f1
ms.assetid: 9bd177fb-8539-46cd-bf96-189ade52c2a1
author: minewiskan
ms.author: owend
ms.openlocfilehash: b0260983f5060ecba7f618975e805ff63c507d5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593004"
---
# <a name="connect-to-an-oracle-database-ssas"></a><span data-ttu-id="7f683-102">連接到 Oracle 資料庫 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="7f683-102">Connect to an Oracle Database (SSAS)</span></span>
  <span data-ttu-id="7f683-103">**[資料表匯入精靈]** 的這個頁面可讓您指定連接到 Oracle 資料庫的設定。</span><span class="sxs-lookup"><span data-stu-id="7f683-103">This page of the **Table Import Wizard** enables you to specify settings to connect to an Oracle database.</span></span> <span data-ttu-id="7f683-104">若要從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]存取精靈，請按一下 **[模型]** 功能表上的 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="7f683-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="7f683-105">若要連接至資料來源，您必須先在電腦上安裝適當的提供者。</span><span class="sxs-lookup"><span data-stu-id="7f683-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7f683-106">在這個頁面中選取資料庫時，會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="7f683-106">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="7f683-107">不過，如果在 [模擬資訊] 頁面中指定的使用者未具備從所選取資料庫讀取的權限，則匯入將不會成功。</span><span class="sxs-lookup"><span data-stu-id="7f683-107">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="7f683-108">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="7f683-108">UI element list</span></span>  
 <span data-ttu-id="7f683-109">**易記連接名稱**</span><span class="sxs-lookup"><span data-stu-id="7f683-109">**Friendly connection name**</span></span>  
 <span data-ttu-id="7f683-110">為此資料來源連接輸入唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="7f683-110">Type a unique name for this data source connection.</span></span> <span data-ttu-id="7f683-111">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="7f683-111">This is a required field.</span></span>  
  
 <span data-ttu-id="7f683-112">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="7f683-112">**Server name**</span></span>  
 <span data-ttu-id="7f683-113">輸入或選取要連接的伺服器執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="7f683-113">Type or select the name of the server instance to connect to.</span></span>  
  
 <span data-ttu-id="7f683-114">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="7f683-114">**User name**</span></span>  
 <span data-ttu-id="7f683-115">為資料庫連接指定使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="7f683-115">Specify a user name for the database connection.</span></span>  
  
 <span data-ttu-id="7f683-116">這個使用者名稱是在建構資料來源的連接字串時使用。</span><span class="sxs-lookup"><span data-stu-id="7f683-116">This user name is used when constructing the connection string for the data source.</span></span> <span data-ttu-id="7f683-117">這些認證也會在預覽和篩選 [資料表屬性] 視窗和 [匯入精靈] 中的資料時使用。</span><span class="sxs-lookup"><span data-stu-id="7f683-117">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="7f683-118">這些認證不會用來匯入或重新整理資料，而是會使用 [模擬資訊] 頁面上指定的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="7f683-118">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="7f683-119">**密碼**</span><span class="sxs-lookup"><span data-stu-id="7f683-119">**Password**</span></span>  
 <span data-ttu-id="7f683-120">為資料庫連接指定密碼。</span><span class="sxs-lookup"><span data-stu-id="7f683-120">Specify a password for the database connection.</span></span>  
  
 <span data-ttu-id="7f683-121">**儲存密碼**</span><span class="sxs-lookup"><span data-stu-id="7f683-121">**Save my password**</span></span>  
 <span data-ttu-id="7f683-122">指定是否要儲存您在 **[密碼]** 方塊中輸入的密碼。</span><span class="sxs-lookup"><span data-stu-id="7f683-122">Specify whether the password you have entered in the **Password** box is stored.</span></span>  
  
 <span data-ttu-id="7f683-123">**進階**</span><span class="sxs-lookup"><span data-stu-id="7f683-123">**Advanced**</span></span>  
 <span data-ttu-id="7f683-124">使用 **[設定進階屬性]** 對話方塊設定其他連接屬性。</span><span class="sxs-lookup"><span data-stu-id="7f683-124">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="7f683-125">如需詳細資訊，請參閱[設定進階屬性 &#40;SSAS&#41;](set-advanced-properties-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="7f683-125">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="7f683-126">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="7f683-126">**Test Connection**</span></span>  
 <span data-ttu-id="7f683-127">嘗試使用目前的設定建立與資料來源之間的連接。</span><span class="sxs-lookup"><span data-stu-id="7f683-127">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="7f683-128">顯示一則訊息，指出連接是否成功。</span><span class="sxs-lookup"><span data-stu-id="7f683-128">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
