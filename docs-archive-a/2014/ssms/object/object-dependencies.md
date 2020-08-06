---
title: 物件相依性 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.common.objectdependencies.f1
ms.assetid: c63d1160-3f3d-45df-99be-6fe081125fb5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 13d1775f1e4e6885fe56a43ce40c4ac155c5b361
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708898"
---
# <a name="object-dependencies"></a><span data-ttu-id="05a94-102">物件相依性</span><span class="sxs-lookup"><span data-stu-id="05a94-102">Object Dependencies</span></span>
  <span data-ttu-id="05a94-103">某些資料庫物件與其他資料庫物件具有相依性。</span><span class="sxs-lookup"><span data-stu-id="05a94-103">Some database objects have dependencies upon other database objects.</span></span> <span data-ttu-id="05a94-104">例如，檢視和預存程序必須相依於特定資料表，這些資料表中包含檢視或程序所傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="05a94-104">For example, views and stored procedures depend upon the existence of tables that contain the data returned by the view or procedure.</span></span> <span data-ttu-id="05a94-105">目前物件的 **物件相依性 (一般頁面)** 列出必須存在，物件才能正常運作的資料庫物件，以及相依於所選物件的物件。</span><span class="sxs-lookup"><span data-stu-id="05a94-105">The **Object Dependencies (General Page)** for the current object lists both the database objects that must be present for the object to function properly and the objects that depend upon the selected object.</span></span> <span data-ttu-id="05a94-106">參考自身定義中之其他物件，並將定義儲存在系統目錄中的物件稱為 *參考實體*。</span><span class="sxs-lookup"><span data-stu-id="05a94-106">An object that references another object in its definition and that definition is stored in the system catalog is called a *referencing entity*.</span></span> <span data-ttu-id="05a94-107">受其他物件參考的物件稱為 *被參考的實體*。</span><span class="sxs-lookup"><span data-stu-id="05a94-107">An object that is referred to by another object is called a *referenced entity*.</span></span>  
  
 <span data-ttu-id="05a94-108">目前物件的 **物件相依性 (進階頁面)** 列出相依於此物件的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫物件及 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 物件。</span><span class="sxs-lookup"><span data-stu-id="05a94-108">The **Object Dependencies (Advanced Page)** for the current object lists the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database objects and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] objects that depend on the object.</span></span> <span data-ttu-id="05a94-109">這些物件可能會儲存在不同的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="05a94-109">The objects may be stored on different servers.</span></span>  
  
 <span data-ttu-id="05a94-110">在變更或刪除選取的物件之前，請使用此對話方塊來了解相依性。</span><span class="sxs-lookup"><span data-stu-id="05a94-110">Use this dialog box to understand the dependencies before changing or deleting the selected object.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="05a94-111">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="05a94-111">UI element list</span></span>  
 <span data-ttu-id="05a94-112">**相依于的物件**  _\<selected object>_</span><span class="sxs-lookup"><span data-stu-id="05a94-112">**Objects that depend on**  _\<selected object>_</span></span>  
 <span data-ttu-id="05a94-113">按一下此按鈕會顯示已進行相依性追蹤，並相依於所選取物件的物件清單。</span><span class="sxs-lookup"><span data-stu-id="05a94-113">Clicking this button displays a list of those objects that are dependency-tracked and that depend on the selected object.</span></span>  
  
 <span data-ttu-id="05a94-114">**物件** _\<selected object>_**相依于**    </span><span class="sxs-lookup"><span data-stu-id="05a94-114">**Objects on which**  _\<selected object>_  **depends**</span></span>  
 <span data-ttu-id="05a94-115">按一下此按鈕會顯示已進行相依性追蹤，所選取物件相依的物件清單。</span><span class="sxs-lookup"><span data-stu-id="05a94-115">Clicking this button displays a list of those objects that are dependency-tracked, on which the selected object depends.</span></span>  
  
 <span data-ttu-id="05a94-116">**Dependencies** (相依性)</span><span class="sxs-lookup"><span data-stu-id="05a94-116">**Dependencies**</span></span>  
 <span data-ttu-id="05a94-117">按一下**相依於** _\<selected object> 的物件_時，系統會以階層檢視顯示相依於所選物件的物件。</span><span class="sxs-lookup"><span data-stu-id="05a94-117">If **Objects that depend on** _\<selected object>_ is clicked, this displays an hierarchical view of objects that depend on the selected object.</span></span> <span data-ttu-id="05a94-118">按一下  _\<selected object>_ **所相依的物件**時，系統會以階層檢視顯示所選物件相依的物件。</span><span class="sxs-lookup"><span data-stu-id="05a94-118">If **Objects on which** _\<selected object>_ **depends** is clicked, this displays an hierarchical view of objects on which the selected object depends.</span></span>  
  
 <span data-ttu-id="05a94-119">**名稱**</span><span class="sxs-lookup"><span data-stu-id="05a94-119">**Name**</span></span>  
 <span data-ttu-id="05a94-120">顯示在上述 [相依性]  樹狀檢視中選取之物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="05a94-120">Displays the name of the object selected in the **Dependencies** tree view above.</span></span>  
  
 <span data-ttu-id="05a94-121">**型別**</span><span class="sxs-lookup"><span data-stu-id="05a94-121">**Type**</span></span>  
 <span data-ttu-id="05a94-122">顯示在上述 [相依性]  樹狀檢視中選取之物件的類型。</span><span class="sxs-lookup"><span data-stu-id="05a94-122">Displays the type of the object selected in the **Dependencies** tree view above.</span></span>  
  
 <span data-ttu-id="05a94-123">**上次同步處理時間**</span><span class="sxs-lookup"><span data-stu-id="05a94-123">**Last Sync Time**</span></span>  
 > [!NOTE]  
>  <span data-ttu-id="05a94-124">只有 [進階]  頁面會提供此選項。</span><span class="sxs-lookup"><span data-stu-id="05a94-124">This option is available only on the **Advanced** page.</span></span>  
  
 <span data-ttu-id="05a94-125">指定上次更新相依性資訊的時間和日期。</span><span class="sxs-lookup"><span data-stu-id="05a94-125">Specifies the time and date when the dependency information was last updated.</span></span>  
  
 <span data-ttu-id="05a94-126">**相依性類型**</span><span class="sxs-lookup"><span data-stu-id="05a94-126">**Dependency type**</span></span>  
 > [!NOTE]  
>  <span data-ttu-id="05a94-127">只有 [一般]  頁面會提供此選項。</span><span class="sxs-lookup"><span data-stu-id="05a94-127">This option is available only on the **General** page.</span></span>  
  
 <span data-ttu-id="05a94-128">顯示兩個物件之間的相依性類型。</span><span class="sxs-lookup"><span data-stu-id="05a94-128">Displays the type of dependency between two objects.</span></span> <span data-ttu-id="05a94-129">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="05a94-129">Can be one of the following:</span></span>  
  
-   <span data-ttu-id="05a94-130">結構描述繫結的相依性</span><span class="sxs-lookup"><span data-stu-id="05a94-130">Schema-bound dependency</span></span>  
  
     <span data-ttu-id="05a94-131">是兩個物件間的關聯性，只要參考物件存在，就可以防止受參考的物件遭到卸除或修改。</span><span class="sxs-lookup"><span data-stu-id="05a94-131">Is a relationship between two objects that prevents the referenced object from being dropped or modified as long as the referencing object exists.</span></span> <span data-ttu-id="05a94-132">使用 WITH SCHEMABINDING 子句建立檢視或使用者自訂函數時，或資料表透過 CHECK 或 DEFAULT 條件約束，或在計算資料行的定義中參考其他物件時，就會建立結構描述繫結的相依性。</span><span class="sxs-lookup"><span data-stu-id="05a94-132">A schema-bound dependency is created when a view or user-defined function is created by using the WITH SCHEMABINDING clause, or when a table references another object through a CHECK or DEFAULT constraint or in the definition of a computed column.</span></span>  
  
-   <span data-ttu-id="05a94-133">非結構描述繫結的相依性</span><span class="sxs-lookup"><span data-stu-id="05a94-133">Non-schema-bound dependency</span></span>  
  
     <span data-ttu-id="05a94-134">是兩個物件間的關聯性，無法防止受參考的物件遭到卸除或修改。</span><span class="sxs-lookup"><span data-stu-id="05a94-134">Is a relationship between two objects that does not prevent the referenced object from being dropped or modified.</span></span>  
  
-   <span data-ttu-id="05a94-135">無法使用或未解析的實體</span><span class="sxs-lookup"><span data-stu-id="05a94-135">Not available or Unresolved Entity</span></span>  
  
     <span data-ttu-id="05a94-136">表示無法判定相依性類型。</span><span class="sxs-lookup"><span data-stu-id="05a94-136">Indicates the dependency type cannot be determined.</span></span> <span data-ttu-id="05a94-137">只有在選取的物件位於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 前之 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]的執行個體上時，才會發生這個狀況。</span><span class="sxs-lookup"><span data-stu-id="05a94-137">This occurs only when the selected object is on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
  
