---
title: 刪除物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.deleteobjects.f1
helpviewer_keywords:
- Delete Objects dialog box
ms.assetid: 49541441-179c-40d3-ba0c-01bcae545984
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7b20d1eee3e48c5531b6b788e125b943f7606d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584264"
---
# <a name="delete-objects"></a><span data-ttu-id="67541-102">刪除物件</span><span class="sxs-lookup"><span data-stu-id="67541-102">Delete Objects</span></span>
  <span data-ttu-id="67541-103">使用此對話方塊來刪除資料庫或資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="67541-103">Use this dialog box to delete a database or database object.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="67541-104">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="67541-104">UI element list</span></span>  
 <span data-ttu-id="67541-105">**要刪除的物件**</span><span class="sxs-lookup"><span data-stu-id="67541-105">**Object to be deleted**</span></span>  
 <span data-ttu-id="67541-106">顯示將要刪除之物件的名稱、類型、擁有者和狀態，以及有關執行期間發生錯誤的任何訊息。</span><span class="sxs-lookup"><span data-stu-id="67541-106">Displays the names, types, owners, and status of the objects that are about to be deleted, as well as any messages about errors during execution.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67541-107">在資料庫上執行 [刪除]  相當於在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中發出 DROP DATABASE。</span><span class="sxs-lookup"><span data-stu-id="67541-107">Running **Delete** on a database is equivalent to issuing DROP DATABASE in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="67541-108">**顯示相依性**</span><span class="sxs-lookup"><span data-stu-id="67541-108">**Show Dependencies**</span></span>  
 <span data-ttu-id="67541-109">按一下即可同時顯示相依於目前所選取物件的物件，以及目前物件相依的物件 (向上和向下相依性)。</span><span class="sxs-lookup"><span data-stu-id="67541-109">Click to display both the objects that are dependent on the currently selected object and objects that the current object is dependent on (upward and downward dependency).</span></span> <span data-ttu-id="67541-110">[顯示相依性]  對話方塊中所顯示的資訊是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="67541-110">The information displayed in the **Show Dependencies** dialog box is read-only.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67541-111">[顯示相依性]  按鈕並不會出現在所有類型的資料庫物件上。</span><span class="sxs-lookup"><span data-stu-id="67541-111">The **Show Dependencies** button does not appear for all types of database objects.</span></span> <span data-ttu-id="67541-112">若要檢視相依性，但[顯示相依性]  按鈕無法使用時，請以滑鼠右鍵按一下物件總管中的物件，然後按一下 [檢視相依性]  。</span><span class="sxs-lookup"><span data-stu-id="67541-112">To view dependencies when the **Show Dependencies** button is not available, right-click the object in Object Explorer, and then click **View Dependencies**.</span></span>  
  
 <span data-ttu-id="67541-113">**刪除資料庫的備份與還原記錄資訊**</span><span class="sxs-lookup"><span data-stu-id="67541-113">**Delete backup and restore history information for databases**</span></span>  
 <span data-ttu-id="67541-114">只出現於資料庫已刪除時，此核取方塊會導致主旨資料庫的備份與還原記錄從 **msdb** 資料庫中刪除。</span><span class="sxs-lookup"><span data-stu-id="67541-114">Only appears when a database is deleted, this check box causes the backup and restore history for the subject database to be deleted from the **msdb** database.</span></span>  
  
 <span data-ttu-id="67541-115">**關閉現有的連接**</span><span class="sxs-lookup"><span data-stu-id="67541-115">**Close existing connections**</span></span>  
 <span data-ttu-id="67541-116">只出現於資料庫已刪除時，此核取方塊會結束主旨資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="67541-116">Only appears when a database is deleted, this check box terminates connections to the subject database.</span></span>  
  
  
