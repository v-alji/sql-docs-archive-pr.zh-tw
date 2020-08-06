---
title: 儲存 (不允許) 對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.table.tablerecreatenosave.f1
ms.assetid: 7efda8e3-739f-4c97-a497-b8808a0acbea
author: stevestein
ms.author: sstein
ms.openlocfilehash: 19e5f848f20cf74feb3e802e931cbde3aa8d3dc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703694"
---
# <a name="save-not-permitted-dialog-box"></a><span data-ttu-id="31c38-102">儲存 (不允許) 對話方塊</span><span class="sxs-lookup"><span data-stu-id="31c38-102">Save (Not Permitted) Dialog Box</span></span>
  <span data-ttu-id="31c38-103">[儲存]  \(不允許) 對話方塊會警告您不允許儲存變更，因為您所做的變更需要卸除及重新建立所列出的資料表。</span><span class="sxs-lookup"><span data-stu-id="31c38-103">The **Save** (Not Permitted) dialog box warns you that saving changes is not permitted because the changes you have made require the listed tables to be dropped and re-created.</span></span>  
  
 <span data-ttu-id="31c38-104">下列動作可能需要重新建立資料表：</span><span class="sxs-lookup"><span data-stu-id="31c38-104">The following actions might require a table to be re-created:</span></span>  
  
-   <span data-ttu-id="31c38-105">將新的資料行加入資料表的中間</span><span class="sxs-lookup"><span data-stu-id="31c38-105">Adding a new column to the middle of the table</span></span>  
  
-   <span data-ttu-id="31c38-106">卸除資料行</span><span class="sxs-lookup"><span data-stu-id="31c38-106">Dropping a column</span></span>  
  
-   <span data-ttu-id="31c38-107">變更資料行的 Null 屬性</span><span class="sxs-lookup"><span data-stu-id="31c38-107">Changing column nullability</span></span>  
  
-   <span data-ttu-id="31c38-108">變更資料行的順序</span><span class="sxs-lookup"><span data-stu-id="31c38-108">Changing the order of the columns</span></span>  
  
-   <span data-ttu-id="31c38-109">變更資料行的資料類型</span><span class="sxs-lookup"><span data-stu-id="31c38-109">Changing the data type of a column</span></span>  
  
 <span data-ttu-id="31c38-110">若要變更這個選項，請在 [工具]  功能表上按一下 [選項]  ，展開 [設計工具]  ，然後按一下 [資料表和資料庫設計工具]  。</span><span class="sxs-lookup"><span data-stu-id="31c38-110">To change this option, on the **Tools** menu, click **Options**, expand **Designers**, and then click **Table and Database Designers**.</span></span> <span data-ttu-id="31c38-111">選取或清除 [防止儲存需要資料表重建的變更]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="31c38-111">Select or clear the **Prevent saving changes that require the table to be re-created** check box.</span></span>  
  
  
