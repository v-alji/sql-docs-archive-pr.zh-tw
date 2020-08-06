---
title: 資料表值物件屬性 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.designers.properties.TVO
ms.assetid: eaf06cbf-8242-4483-894f-80ae02a4840e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6f1c1e6414d0059dfd1d43bbbb40eabdfc9470b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704598"
---
# <a name="table-valued-object-properties-visual-database-tools"></a><span data-ttu-id="6aa16-102">資料表值物件屬性 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6aa16-102">Table-Valued Object Properties (Visual Database Tools)</span></span>
  <span data-ttu-id="6aa16-103">您在查詢和檢視表設計工具  中選取資料表值物件時，這些屬性就會出現在 [屬性] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="6aa16-103">These properties appear in the Properties window when you select a table-valued object in **Query and View Designer**.</span></span> <span data-ttu-id="6aa16-104">資料表值物件可以是檢視、同義字、衍生資料表，或是資料表值函數。</span><span class="sxs-lookup"><span data-stu-id="6aa16-104">The table-valued object could be a view, synonym, derived table, or table-valued function.</span></span> <span data-ttu-id="6aa16-105">除非另有說明，這些屬性在 [屬性]  視窗中都是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="6aa16-105">Unless otherwise noted, these properties are read-only in the **Properties** window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6aa16-106">此主題中的屬性，是依類別目錄的順序排列，而非依字母排列。</span><span class="sxs-lookup"><span data-stu-id="6aa16-106">The properties in this topic are ordered by category rather than alphabet.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6aa16-107">您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。</span><span class="sxs-lookup"><span data-stu-id="6aa16-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6aa16-108">若要變更您的設定，請在 [工具]  功能表上選擇 [匯入和匯出設定]  。</span><span class="sxs-lookup"><span data-stu-id="6aa16-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="6aa16-109">**識別類別目錄**</span><span class="sxs-lookup"><span data-stu-id="6aa16-109">**Identity Category**</span></span>  
 <span data-ttu-id="6aa16-110">展開以顯示 [名稱]  和 [TVO 類型]  屬性。</span><span class="sxs-lookup"><span data-stu-id="6aa16-110">Expands to show the **Name** and **TVO Type** properties.</span></span>  
  
 <span data-ttu-id="6aa16-111">**名稱**</span><span class="sxs-lookup"><span data-stu-id="6aa16-111">**Name**</span></span>  
 <span data-ttu-id="6aa16-112">顯示選取之資料表值物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="6aa16-112">Shows the name of the selected table-valued object.</span></span>  
  
 <span data-ttu-id="6aa16-113">**TVO 類型**</span><span class="sxs-lookup"><span data-stu-id="6aa16-113">**TVO Type**</span></span>  
 <span data-ttu-id="6aa16-114">顯示資料表值物件的類型。</span><span class="sxs-lookup"><span data-stu-id="6aa16-114">Shows which type of table-valued object.</span></span> <span data-ttu-id="6aa16-115">它可以是基底資料表、檢視、資料表值函數，或是衍生資料表。</span><span class="sxs-lookup"><span data-stu-id="6aa16-115">It can be either a base table, view, table-valued function, or a derived table.</span></span>  
  
 <span data-ttu-id="6aa16-116">**查詢設計工具類別**</span><span class="sxs-lookup"><span data-stu-id="6aa16-116">**Query DesignerCategory**</span></span>  
 <span data-ttu-id="6aa16-117">展開以顯示 [別名]  、[資料行清單]  、[全名]  和 [參數清單]  的屬性。</span><span class="sxs-lookup"><span data-stu-id="6aa16-117">Expands to show properties for **Alias**, **Column List**, **Full Name**, and **Parameter List**.</span></span>  
  
 <span data-ttu-id="6aa16-118">**別名**</span><span class="sxs-lookup"><span data-stu-id="6aa16-118">**Alias**</span></span>  
 <span data-ttu-id="6aa16-119">顯示選取之資料表值物件的別名。</span><span class="sxs-lookup"><span data-stu-id="6aa16-119">Shows the alias for the selected table-valued object.</span></span> <span data-ttu-id="6aa16-120">若要加入或變更別名，請將其鍵入欄位中。</span><span class="sxs-lookup"><span data-stu-id="6aa16-120">To add or change an alias, type it into the field.</span></span>  
  
 <span data-ttu-id="6aa16-121">**資料行清單**</span><span class="sxs-lookup"><span data-stu-id="6aa16-121">**Column List**</span></span>  
 <span data-ttu-id="6aa16-122">顯示選取之資料表值物件中所包含的資料行。</span><span class="sxs-lookup"><span data-stu-id="6aa16-122">Shows the columns included in the selected table-valued object.</span></span> <span data-ttu-id="6aa16-123">若要在不同視窗中查看它們，請按一下 [資料行清單]，然後按一下屬性右邊的省略符號 (...)。</span><span class="sxs-lookup"><span data-stu-id="6aa16-123">To see them in a separate window, click Column List and then click the ellipses (...) to the right of the property.</span></span>  
  
 <span data-ttu-id="6aa16-124">**全名**</span><span class="sxs-lookup"><span data-stu-id="6aa16-124">**Full Name**</span></span>  
 <span data-ttu-id="6aa16-125">顯示選取之資料表值物件的名稱，其中包含諸如物件的結構描述或資料來源的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="6aa16-125">Shows the name of the selected table-valued object, including additional information such as the schema or data source of the object.</span></span>  
  
 <span data-ttu-id="6aa16-126">**參數清單**</span><span class="sxs-lookup"><span data-stu-id="6aa16-126">**Parameter List**</span></span>  
 <span data-ttu-id="6aa16-127">顯示針對選取之資料表值函數所定義的參數。</span><span class="sxs-lookup"><span data-stu-id="6aa16-127">Shows the parameters defined for selected table-valued function.</span></span> <span data-ttu-id="6aa16-128">若要定義參數的值，請按一下 [參數清單]，然後按一下屬性右邊的省略符號 (...)。</span><span class="sxs-lookup"><span data-stu-id="6aa16-128">To define a value for the parameters, click Parameter List and then click the ellipses (...) to the right of the property.</span></span> <span data-ttu-id="6aa16-129">在 [函數參數] 對話方塊中，請鍵入值。</span><span class="sxs-lookup"><span data-stu-id="6aa16-129">In the Function Parameters dialog box, type in values.</span></span> <span data-ttu-id="6aa16-130">唯有選取資料表值函數時，才能使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="6aa16-130">This property is only available when a table-valued function is selected.</span></span>  
  
  
