---
title: 指定 (SSAS) 的連接字串 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.speconnstring.f1
ms.assetid: 3f89b55b-2659-4e9f-a3ad-ab9a23b6942d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9333c239504a79184e08776acb3f1d845f06cc4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705478"
---
# <a name="specify-a-connection-string-ssas"></a><span data-ttu-id="7bc55-102">指定連接字串 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="7bc55-102">Specify a connection string (SSAS)</span></span>
  <span data-ttu-id="7bc55-103">**[資料表匯入精靈]** 的這個頁面可讓您指定連接字串以連接至 OLE DB 或 ODBC 資料來源。</span><span class="sxs-lookup"><span data-stu-id="7bc55-103">This page of the **Table Import Wizard** enables you to specify a connection string to connect to an OLE DB or ODBC data source.</span></span> <span data-ttu-id="7bc55-104">若要從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]存取精靈，請按一下 **[模型]** 功能表上的 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="7bc55-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="7bc55-105">若要連接至資料來源，您必須先在電腦上安裝適當的提供者。</span><span class="sxs-lookup"><span data-stu-id="7bc55-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span> <span data-ttu-id="7bc55-106">如需支援的資料來源和提供者的詳細資訊，請參閱 [支援的資料來源 &#40;SSAS 表格式&#41;](tabular-models/data-sources-supported-ssas-tabular.md)(支援的資料來源 (SSAS 表格式))。</span><span class="sxs-lookup"><span data-stu-id="7bc55-106">For more information about supported data sources and providers, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="7bc55-107">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="7bc55-107">UI element list</span></span>  
 <span data-ttu-id="7bc55-108">**此連接的易記名稱**</span><span class="sxs-lookup"><span data-stu-id="7bc55-108">**Friendly name for this connection**</span></span>  
 <span data-ttu-id="7bc55-109">為此資料來源連接輸入唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="7bc55-109">Type a unique name for this data source connection.</span></span> <span data-ttu-id="7bc55-110">這是必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="7bc55-110">This is a required field.</span></span>  
  
 <span data-ttu-id="7bc55-111">**連接字串**</span><span class="sxs-lookup"><span data-stu-id="7bc55-111">**Connection String**</span></span>  
 <span data-ttu-id="7bc55-112">輸入用來連接到 OLE DB 或 ODBC 資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="7bc55-112">Type a connection string to connect to an OLE DB or ODBC data source.</span></span>  
  
 <span data-ttu-id="7bc55-113">**建置**</span><span class="sxs-lookup"><span data-stu-id="7bc55-113">**Build**</span></span>  
 <span data-ttu-id="7bc55-114">使用 [資料連結屬性]\*\*\*\* 對話方塊，指定連接字串的屬性。</span><span class="sxs-lookup"><span data-stu-id="7bc55-114">Specify the properties for a connection string by using the **Data Link Properties** dialog box.</span></span> <span data-ttu-id="7bc55-115">如需詳細資訊，請參閱可從該對話方塊存取的 Microsoft 資料連結說明。</span><span class="sxs-lookup"><span data-stu-id="7bc55-115">For more information, see the Microsoft Data Link Help, which is available from that dialog box.</span></span>  
  
 <span data-ttu-id="7bc55-116">**測試連接**</span><span class="sxs-lookup"><span data-stu-id="7bc55-116">**Test Connection**</span></span>  
 <span data-ttu-id="7bc55-117">嘗試使用指定的連接字串，建立與資料來源之間的連接。</span><span class="sxs-lookup"><span data-stu-id="7bc55-117">Attempt to establish a connection to the data source using the specified connection string.</span></span> <span data-ttu-id="7bc55-118">顯示一則訊息，指出連接是否成功。</span><span class="sxs-lookup"><span data-stu-id="7bc55-118">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
