---
title: 選取維度資料表與索引鍵 (緩時變維度精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.selecttableandkeys.f1
ms.assetid: 01e0495f-de35-4607-ba19-0539e801e8fd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 671c66a8a5d5f1f4f5201fd8c9ecc144540d8b68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710761"
---
# <a name="select-a-dimension-table-and-keys-slowly-changing-dimension-wizard"></a><span data-ttu-id="698e6-102">選取維度資料表與索引鍵 (緩時變維度精靈)</span><span class="sxs-lookup"><span data-stu-id="698e6-102">Select a Dimension Table and Keys (Slowly Changing Dimension Wizard)</span></span>
  <span data-ttu-id="698e6-103">使用 **[選取維度資料表與索引鍵]** 頁面，即可選取要載入的維度資料表。</span><span class="sxs-lookup"><span data-stu-id="698e6-103">Use the **Select a Dimension Table and Keys** page to select a dimension table to load.</span></span> <span data-ttu-id="698e6-104">將資料流程的資料行對應至即將載入的資料行。</span><span class="sxs-lookup"><span data-stu-id="698e6-104">Map columns from the data flow to the columns that will be loaded.</span></span>  
  
 <span data-ttu-id="698e6-105">若要深入了解這個精靈，請參閱＜ [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="698e6-105">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="698e6-106">選項。</span><span class="sxs-lookup"><span data-stu-id="698e6-106">Options</span></span>  
 <span data-ttu-id="698e6-107">**[ODBC 目的地編輯器]**</span><span class="sxs-lookup"><span data-stu-id="698e6-107">**Connection manager**</span></span>  
 <span data-ttu-id="698e6-108">從清單中選取現有的 OLE DB 連線管理員，或按一下 [新增]  建立 OLE DB 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="698e6-108">Select an existing OLE DB connection manager from the list, or click **New** to create an OLE DB connection manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="698e6-109">[緩時變維度精靈] 只支援 OLE DB 連線管理員，所以只支援與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的連線。</span><span class="sxs-lookup"><span data-stu-id="698e6-109">The Slowly Changing Dimension Wizard only supports OLE DB connection managers, and only supports connections to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="698e6-110">**新增**</span><span class="sxs-lookup"><span data-stu-id="698e6-110">**New**</span></span>  
 <span data-ttu-id="698e6-111">使用 [設定 OLE DB 連線管理員]  對話方塊，以選取現有的連線管理員，或按一下 [新增]  建立新的 OLE DB 連線。</span><span class="sxs-lookup"><span data-stu-id="698e6-111">Use the **Configure OLE DB Connection Manager** dialog box to select an existing connection manager, or click **New** to create a new OLE DB connection.</span></span>  
  
 <span data-ttu-id="698e6-112">**[資料表或檢視表]**</span><span class="sxs-lookup"><span data-stu-id="698e6-112">**Table or View**</span></span>  
 <span data-ttu-id="698e6-113">從清單中選取資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="698e6-113">Select a table or view from the list.</span></span>  
  
 <span data-ttu-id="698e6-114">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="698e6-114">**Input Columns**</span></span>  
 <span data-ttu-id="698e6-115">從輸入資料行的清單中選取您要指定對應的資料行。</span><span class="sxs-lookup"><span data-stu-id="698e6-115">Select from the list of input columns for which you may specify mapping.</span></span>  
  
 <span data-ttu-id="698e6-116">**維度資料行**</span><span class="sxs-lookup"><span data-stu-id="698e6-116">**Dimension Columns**</span></span>  
 <span data-ttu-id="698e6-117">檢視所有可用的維度資料行。</span><span class="sxs-lookup"><span data-stu-id="698e6-117">View all available dimension columns.</span></span>  
  
 <span data-ttu-id="698e6-118">**索引鍵類型**</span><span class="sxs-lookup"><span data-stu-id="698e6-118">**Key Type**</span></span>  
 <span data-ttu-id="698e6-119">選取其中一個維度資料行作為商務索引鍵。</span><span class="sxs-lookup"><span data-stu-id="698e6-119">Select one of the dimension columns to be the business key.</span></span> <span data-ttu-id="698e6-120">您必須要有一個商務索引鍵。</span><span class="sxs-lookup"><span data-stu-id="698e6-120">You must have one business key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="698e6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="698e6-121">See Also</span></span>  
 [<span data-ttu-id="698e6-122">使用緩時變維度精靈來設定輸出</span><span class="sxs-lookup"><span data-stu-id="698e6-122">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
