---
title: 連接到 Microsoft Access 資料庫 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connaccessdb.f1
ms.assetid: 9fa81839-dd8b-41d3-915e-c774a707ed53
author: minewiskan
ms.author: owend
ms.openlocfilehash: fbb180a754b6bc276d588997117eb84fd1a5a873
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593024"
---
# <a name="connect-to-a-microsoft-access-database-ssas"></a><span data-ttu-id="f25f5-102">連接到 Microsoft Access 資料庫 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="f25f5-102">Connect to a Microsoft Access Database (SSAS)</span></span>
  <span data-ttu-id="f25f5-103">[資料表匯入精靈]\*\*\*\* 的這個頁面可讓您指定連接到 Microsoft Access 資料庫的設定。</span><span class="sxs-lookup"><span data-stu-id="f25f5-103">This page of the **Table Import Wizard** enables you to specify settings to connect to a Microsoft Access database.</span></span> <span data-ttu-id="f25f5-104">若要從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]存取精靈，請按一下 **[模型]** 功能表上的 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="f25f5-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="f25f5-105">若要連接 Microsoft Access 資料庫，您必須先在電腦上安裝適當的 ACE 提供者。</span><span class="sxs-lookup"><span data-stu-id="f25f5-105">To connect to a Microsoft Access database, you must have the appropriate ACE provider installed on your computer.</span></span> <span data-ttu-id="f25f5-106">如需詳細資訊，請參閱[支援的資料來源 &#40;SSAS 表格式&#41;](tabular-models/data-sources-supported-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="f25f5-106">For more information, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f25f5-107">在這個頁面中選取檔案時，會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="f25f5-107">The credentials of the current user are used when selecting a file in this page.</span></span> <span data-ttu-id="f25f5-108">不過，如果在 [模擬資訊] 頁面中指定的使用者未具備從所選檔案讀取的權限，則匯入將不會成功。</span><span class="sxs-lookup"><span data-stu-id="f25f5-108">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected file.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="f25f5-109">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="f25f5-109">UI element list</span></span>  
 <span data-ttu-id="f25f5-110">**易記連接名稱**</span><span class="sxs-lookup"><span data-stu-id="f25f5-110">**Friendly connection name**</span></span>  
 <span data-ttu-id="f25f5-111">為此資料來源連接輸入唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="f25f5-111">Type a unique name for this data source connection.</span></span> <span data-ttu-id="f25f5-112">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="f25f5-112">This is a required field.</span></span>  
  
 <span data-ttu-id="f25f5-113">**資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="f25f5-113">**Database name**</span></span>  
 <span data-ttu-id="f25f5-114">為 Microsoft Access 資料庫檔案指定完整路徑。</span><span class="sxs-lookup"><span data-stu-id="f25f5-114">Specify the full path for a Microsoft Access database file.</span></span>  
  
 <span data-ttu-id="f25f5-115">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="f25f5-115">**Browse**</span></span>  
 <span data-ttu-id="f25f5-116">導覽至可取得 Microsoft Access 資料庫檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="f25f5-116">Navigate to a location where a Microsoft Access database file is available.</span></span>  
  
 <span data-ttu-id="f25f5-117">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="f25f5-117">**User name**</span></span>  
 <span data-ttu-id="f25f5-118">為資料庫連接指定使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="f25f5-118">Specify a user name for the database connection.</span></span>  
  
 <span data-ttu-id="f25f5-119">**密碼**</span><span class="sxs-lookup"><span data-stu-id="f25f5-119">**Password**</span></span>  
 <span data-ttu-id="f25f5-120">為資料庫連接指定密碼。</span><span class="sxs-lookup"><span data-stu-id="f25f5-120">Specify a password for the database connection.</span></span>  
  
 <span data-ttu-id="f25f5-121">**儲存密碼**</span><span class="sxs-lookup"><span data-stu-id="f25f5-121">**Save my password**</span></span>  
 <span data-ttu-id="f25f5-122">指定是否要儲存您在 **[密碼]** 方塊中輸入的密碼。</span><span class="sxs-lookup"><span data-stu-id="f25f5-122">Specify whether the password you have entered in the **Password** box is stored.</span></span>  
  
 <span data-ttu-id="f25f5-123">**進階**</span><span class="sxs-lookup"><span data-stu-id="f25f5-123">**Advanced**</span></span>  
 <span data-ttu-id="f25f5-124">使用 **[設定進階屬性]** 對話方塊設定其他連接屬性。</span><span class="sxs-lookup"><span data-stu-id="f25f5-124">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span>  
  
 <span data-ttu-id="f25f5-125">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="f25f5-125">**Test Connection**</span></span>  
 <span data-ttu-id="f25f5-126">嘗試使用目前的設定建立與資料來源之間的連接。</span><span class="sxs-lookup"><span data-stu-id="f25f5-126">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="f25f5-127">顯示一則訊息，指出連接是否成功。</span><span class="sxs-lookup"><span data-stu-id="f25f5-127">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
