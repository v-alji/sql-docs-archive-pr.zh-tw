---
title: 如果您打算啟用變更資料捕獲，請移除 cdc 架構 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- cdc schema
- change data capture
ms.assetid: 6a84aa25-0f31-4be3-b2dd-4f249b8254ae
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: abdb33fa3d1ff022a65ed569f19d48bcf4468501
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598147"
---
# <a name="remove-the-cdc-schema-if-you-plan-to-enable-change-data-capture"></a><span data-ttu-id="796c9-102">如果您計畫啟用異動資料擷取，請移除 cdc 結構描述</span><span class="sxs-lookup"><span data-stu-id="796c9-102">Remove the cdc schema if you plan to enable change data capture</span></span>
  <span data-ttu-id="796c9-103">資料庫已經包含 cdc 結構描述。</span><span class="sxs-lookup"><span data-stu-id="796c9-103">A database already contains a cdc schema.</span></span> <span data-ttu-id="796c9-104">如果您計畫在升級之後啟用異動資料擷取，就必須先卸除此 cdc 結構描述。</span><span class="sxs-lookup"><span data-stu-id="796c9-104">If you plan to enable change data capture after upgrade, you must first drop this cdc schema.</span></span> <span data-ttu-id="796c9-105">當您啟用異動資料擷取的資料庫時，[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 將會建立名為 cdc 的新結構描述。</span><span class="sxs-lookup"><span data-stu-id="796c9-105">When you enable a database for change data capture, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] will create a new schema named cdc.</span></span>  
  
  
