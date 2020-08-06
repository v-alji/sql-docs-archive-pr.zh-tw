---
title: SQL Server Management Studio 中的屬性頁 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- property pages [SQL Server Management Studio]
ms.assetid: 719282c3-e9cc-4e0e-9a83-7fb8b8b17f67
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3fae6a07fbaa2a259fcca5c3807094b31e0d52d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705850"
---
# <a name="property-pages-in-sql-server-management-studio"></a><span data-ttu-id="217d0-102">SQL Server Management Studio 中的屬性頁</span><span class="sxs-lookup"><span data-stu-id="217d0-102">Property Pages in SQL Server Management Studio</span></span>
  <span data-ttu-id="217d0-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中所有 [屬性頁] 對話方塊都會以共用格式來顯示展開和摺疊類別目錄的資訊。</span><span class="sxs-lookup"><span data-stu-id="217d0-103">Property page dialog boxes in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] all use a common format displaying information with expanding and collapsing categories.</span></span> <span data-ttu-id="217d0-104">顯示的欄位會隨著特定內容而不同。</span><span class="sxs-lookup"><span data-stu-id="217d0-104">The fields shown depend on the particular property.</span></span> <span data-ttu-id="217d0-105">以灰色顯示的屬性是唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="217d0-105">Properties shown in gray are read-only.</span></span> <span data-ttu-id="217d0-106">[分類] 和 [字母] 按鈕在每個屬性頁的頂端附近。</span><span class="sxs-lookup"><span data-stu-id="217d0-106">Categorized and Alphabetic buttons are near the top of each property page.</span></span>  
  
 <span data-ttu-id="217d0-107">下表說明 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 屬性頁對話方塊的一般元素。</span><span class="sxs-lookup"><span data-stu-id="217d0-107">The following table describes the common elements of [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] property page dialog boxes.</span></span>  
  
|<span data-ttu-id="217d0-108">元素</span><span class="sxs-lookup"><span data-stu-id="217d0-108">Element</span></span>|<span data-ttu-id="217d0-109">描述</span><span class="sxs-lookup"><span data-stu-id="217d0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="217d0-110">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="217d0-110">**Categorized**</span></span>|<span data-ttu-id="217d0-111">依類別目錄排序來列出所選物件的所有屬性和屬性值。</span><span class="sxs-lookup"><span data-stu-id="217d0-111">Lists all properties and property values for the selected object, sorted by category.</span></span> <span data-ttu-id="217d0-112">在類別目錄檢視中，您可以摺疊類別目錄來縮減可見屬性的數目。</span><span class="sxs-lookup"><span data-stu-id="217d0-112">In category view, you can collapse a category to reduce the number of visible properties.</span></span> <span data-ttu-id="217d0-113">當您展開或摺疊類別目錄時，類別目錄名稱左側會出現加號 (+) 或減號 (-)。</span><span class="sxs-lookup"><span data-stu-id="217d0-113">When you expand or collapse a category, you see a plus sign (+) or minus sign (-) to the left of the category name.</span></span> <span data-ttu-id="217d0-114">類別目錄依字母順序來排列。</span><span class="sxs-lookup"><span data-stu-id="217d0-114">Categories are listed alphabetically.</span></span>|  
|<span data-ttu-id="217d0-115">**字母順序**</span><span class="sxs-lookup"><span data-stu-id="217d0-115">**Alphabetic**</span></span>|<span data-ttu-id="217d0-116">依字母順序排序來列出所選物件的所有屬性和屬性值。</span><span class="sxs-lookup"><span data-stu-id="217d0-116">Lists all properties and property values for the selected object, sorted alphabetically.</span></span>|  
|<span data-ttu-id="217d0-117">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="217d0-117">Property name</span></span>|<span data-ttu-id="217d0-118">方格的第一個資料行列出屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="217d0-118">The first column in the grid lists the property names.</span></span>|  
|<span data-ttu-id="217d0-119">屬性</span><span class="sxs-lookup"><span data-stu-id="217d0-119">Properties</span></span>|<span data-ttu-id="217d0-120">方格的第二個資料行列出屬性值。</span><span class="sxs-lookup"><span data-stu-id="217d0-120">The second column in the grid lists the property values.</span></span>|  
|<span data-ttu-id="217d0-121">描述窗格</span><span class="sxs-lookup"><span data-stu-id="217d0-121">Description pane</span></span>|<span data-ttu-id="217d0-122">描述窗格在頁面底端，它會顯示屬性類型和屬性的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="217d0-122">The description pane appears at the bottom of the page and shows the property type and a short description of the property.</span></span> <span data-ttu-id="217d0-123">您可以使用快速鍵功能表上的 [描述]  命令，來關閉和開啟屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="217d0-123">You can turn the description of the property off and on using the **Description** command on the shortcut menu.</span></span>|  
  
  
