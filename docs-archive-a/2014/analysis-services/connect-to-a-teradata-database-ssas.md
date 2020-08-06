---
title: " (SSAS) 連接到 Teradata 資料庫 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connterradb.f1
ms.assetid: 875ad4a3-a2b3-4b68-8c1c-6507e9f25b4d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 047eed5f8625059750a67c51735c7c0d61d17853
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593012"
---
# <a name="connect-to-a-teradata-database-ssas"></a><span data-ttu-id="da5bf-102">連接至 Teradata 資料庫 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="da5bf-102">Connect to a Teradata Database (SSAS)</span></span>
  <span data-ttu-id="da5bf-103">**[資料表匯入精靈]** 的這個頁面可讓您指定連接到 Teradata 資料庫的設定。</span><span class="sxs-lookup"><span data-stu-id="da5bf-103">This page of the **Table Import Wizard** enables you to specify settings to connect to a Teradata database.</span></span> <span data-ttu-id="da5bf-104">若要從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]存取精靈，請按一下 **[模型]** 功能表上的 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="da5bf-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="da5bf-105">若要連接至資料來源，您必須先在電腦上安裝適當的提供者。</span><span class="sxs-lookup"><span data-stu-id="da5bf-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="da5bf-106">在這個頁面中選取資料庫時，會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="da5bf-106">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="da5bf-107">不過，如果在 [模擬資訊] 頁面中指定的使用者未具備從所選取資料庫讀取的權限，則匯入將不會成功。</span><span class="sxs-lookup"><span data-stu-id="da5bf-107">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="da5bf-108">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="da5bf-108">UI element list</span></span>  
 <span data-ttu-id="da5bf-109">**易記連接名稱**</span><span class="sxs-lookup"><span data-stu-id="da5bf-109">**Friendly connection name**</span></span>  
 <span data-ttu-id="da5bf-110">為此資料來源連接輸入唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="da5bf-110">Type a unique name for this data source connection.</span></span> <span data-ttu-id="da5bf-111">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="da5bf-111">This is a required field.</span></span>  
  
 <span data-ttu-id="da5bf-112">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="da5bf-112">**Server name**</span></span>  
 <span data-ttu-id="da5bf-113">輸入或選取要連接的伺服器執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="da5bf-113">Type or select the name of the server instance to connect to.</span></span>  
  
 <span data-ttu-id="da5bf-114">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="da5bf-114">**User name**</span></span>  
 <span data-ttu-id="da5bf-115">為資料庫連接指定使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="da5bf-115">Specify a user name for the database connection.</span></span>  
  
 <span data-ttu-id="da5bf-116">這個使用者名稱是在建構資料來源的連接字串時使用。</span><span class="sxs-lookup"><span data-stu-id="da5bf-116">This user name is used when constructing the connection string for the data source.</span></span> <span data-ttu-id="da5bf-117">這些認證也會在預覽和篩選 [資料表屬性] 視窗和 [匯入精靈] 中的資料時使用。</span><span class="sxs-lookup"><span data-stu-id="da5bf-117">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="da5bf-118">這些認證不會用來匯入或重新整理資料，而是會使用 [模擬資訊] 頁面上指定的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="da5bf-118">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation information page are used instead.</span></span>  
  
 <span data-ttu-id="da5bf-119">**密碼**</span><span class="sxs-lookup"><span data-stu-id="da5bf-119">**Password**</span></span>  
 <span data-ttu-id="da5bf-120">為資料庫連接指定密碼。</span><span class="sxs-lookup"><span data-stu-id="da5bf-120">Specify a password for the database connection.</span></span>  
  
 <span data-ttu-id="da5bf-121">**儲存密碼**</span><span class="sxs-lookup"><span data-stu-id="da5bf-121">**Save my password**</span></span>  
 <span data-ttu-id="da5bf-122">指定是否應該儲存您在 [密碼]\*\*\*\* 方塊中輸入的密碼。</span><span class="sxs-lookup"><span data-stu-id="da5bf-122">Specify whether the password you have entered in the **Password** box should be stored.</span></span>  
  
 <span data-ttu-id="da5bf-123">**進階**</span><span class="sxs-lookup"><span data-stu-id="da5bf-123">**Advanced**</span></span>  
 <span data-ttu-id="da5bf-124">使用 **[設定進階屬性]** 對話方塊設定其他連接屬性。</span><span class="sxs-lookup"><span data-stu-id="da5bf-124">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="da5bf-125">如需詳細資訊，請參閱[設定進階屬性 &#40;SSAS&#41;](set-advanced-properties-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="da5bf-125">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="da5bf-126">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="da5bf-126">**Test Connection**</span></span>  
 <span data-ttu-id="da5bf-127">嘗試使用目前的設定建立與資料來源之間的連接。</span><span class="sxs-lookup"><span data-stu-id="da5bf-127">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="da5bf-128">顯示一則訊息，指出連接是否成功。</span><span class="sxs-lookup"><span data-stu-id="da5bf-128">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
