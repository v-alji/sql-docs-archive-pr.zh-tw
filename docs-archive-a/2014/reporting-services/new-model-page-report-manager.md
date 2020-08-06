---
title: 新的模型頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 27d5bf66-b0e7-489e-a830-ffe2ec8e5350
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ed591108585b494ebb4498c1a0ab3e782693a45b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598239"
---
# <a name="new-model-page-report-manager"></a><span data-ttu-id="75f37-102">新增模型頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="75f37-102">New Model Page (Report Manager)</span></span>
  <span data-ttu-id="75f37-103">您可以使用這個頁面，從共用資料來源產生預設報表模型。</span><span class="sxs-lookup"><span data-stu-id="75f37-103">Use this page to generate a default report model from a shared data source.</span></span> <span data-ttu-id="75f37-104">您只能從 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多維度資料來源、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 關聯式資料來源和 Oracle 關聯式資料來源產生報表模型。</span><span class="sxs-lookup"><span data-stu-id="75f37-104">You can only generate report models from [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] multidimensional data sources, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] relational data sources, and Oracle relational data sources.</span></span>  
  
 <span data-ttu-id="75f37-105">您在報表管理員中產生的模型是以共用資料來源的結構描述為基礎。</span><span class="sxs-lookup"><span data-stu-id="75f37-105">Models that you generate in Report Manager are based on the schema of the shared data source.</span></span> <span data-ttu-id="75f37-106">系統會針對資料來源中的所有資料表和資料行建立實體、資料夾和欄位。</span><span class="sxs-lookup"><span data-stu-id="75f37-106">Entities, folders, and fields are created for all tables and columns in the data source.</span></span> <span data-ttu-id="75f37-107">您無法排除這些項目，也無法設定決定模型產生方式的選項。</span><span class="sxs-lookup"><span data-stu-id="75f37-107">You cannot exclude items, nor can you set options that determine how the model is generated.</span></span> <span data-ttu-id="75f37-108">如果您想要自訂或修改模型，就必須改用模型設計師。</span><span class="sxs-lookup"><span data-stu-id="75f37-108">If you want to customize or refine a model, you must use Model Designer instead.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="75f37-109">導覽</span><span class="sxs-lookup"><span data-stu-id="75f37-109">Navigation</span></span>  
 <span data-ttu-id="75f37-110">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="75f37-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-model-page"></a><span data-ttu-id="75f37-111">若要開啟新增模型頁面</span><span class="sxs-lookup"><span data-stu-id="75f37-111">To open the New Model page</span></span>  
  
1.  <span data-ttu-id="75f37-112">開啟報表管理員，然後找出您想要從中產生模型的共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="75f37-112">Open Report Manager, and locate the shared data source from which you want to generate a model.</span></span>  
  
2.  <span data-ttu-id="75f37-113">將滑鼠停留在該資料來源上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="75f37-113">Hover over the data source, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="75f37-114">在下拉式功能表中，執行下列其中一項步驟：</span><span class="sxs-lookup"><span data-stu-id="75f37-114">In the drop-down menu, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="75f37-115">按一下 **[產生報表模型]** 開啟 [新增模型] 頁面。</span><span class="sxs-lookup"><span data-stu-id="75f37-115">Click **Generate Report Model** to open the New Model page.</span></span>  
  
    -   <span data-ttu-id="75f37-116">按一下 **[管理]** 開啟報表的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="75f37-116">Click **Manage** to open the General properties page for the report.</span></span> <span data-ttu-id="75f37-117">然後，按一下 **[產生報表模型]** 開啟 [新增模型] 頁面。</span><span class="sxs-lookup"><span data-stu-id="75f37-117">Then click **Generate Model** to open the New Model page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="75f37-118">選項。</span><span class="sxs-lookup"><span data-stu-id="75f37-118">Options</span></span>  
 <span data-ttu-id="75f37-119">**名稱**</span><span class="sxs-lookup"><span data-stu-id="75f37-119">**Name**</span></span>  
 <span data-ttu-id="75f37-120">指定模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="75f37-120">Specifies the name of the model.</span></span> <span data-ttu-id="75f37-121">名稱必須至少包含一個英數字元。</span><span class="sxs-lookup"><span data-stu-id="75f37-121">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="75f37-122">它也可以包含空格和某些符號。</span><span class="sxs-lookup"><span data-stu-id="75f37-122">It can also include spaces and some symbols.</span></span> <span data-ttu-id="75f37-123">指定名稱時，請勿使用下列字元：</span><span class="sxs-lookup"><span data-stu-id="75f37-123">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="75f37-124">; ?</span><span class="sxs-lookup"><span data-stu-id="75f37-124">; ?</span></span> <span data-ttu-id="75f37-125">： \@ & = +，$/\* \< > |" /</span><span class="sxs-lookup"><span data-stu-id="75f37-125">: \@ & = + , $ / \* \< > | " /</span></span>  
  
 <span data-ttu-id="75f37-126">**說明**</span><span class="sxs-lookup"><span data-stu-id="75f37-126">**Description**</span></span>  
 <span data-ttu-id="75f37-127">顯示模型的描述。</span><span class="sxs-lookup"><span data-stu-id="75f37-127">Shows a description of the model.</span></span> <span data-ttu-id="75f37-128">透過報表管理員檢視這個項目的使用者會在瀏覽資料夾階層時看到此描述。</span><span class="sxs-lookup"><span data-stu-id="75f37-128">Users who view this item through Report Manager see this description when browsing the folder hierarchy.</span></span>  
  
 <span data-ttu-id="75f37-129">**變更位置**</span><span class="sxs-lookup"><span data-stu-id="75f37-129">**Change Location**</span></span>  
 <span data-ttu-id="75f37-130">顯示新模型的資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="75f37-130">Shows the folder location for the new model.</span></span> <span data-ttu-id="75f37-131">您可以按一下 **[變更位置]** 按鈕以選取不同的位置。</span><span class="sxs-lookup"><span data-stu-id="75f37-131">You can click the **Change Location** button to select a different location.</span></span>  
  
  
