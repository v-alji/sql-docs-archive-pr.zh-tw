---
title: 資料庫屬性 (變更追蹤頁面) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.changetracking.f1
ms.assetid: 9b929640-bc62-449b-9b06-b5a77b8cf372
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4107f81ef4cdf19df60d4a70d8e79007f2c9270c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702969"
---
# <a name="database-properties-changetracking-page"></a><span data-ttu-id="5e1d8-102">資料庫屬性 (變更追蹤頁面)</span><span class="sxs-lookup"><span data-stu-id="5e1d8-102">Database Properties (ChangeTracking Page)</span></span>
  <span data-ttu-id="5e1d8-103">使用此分頁檢視或修改選取之資料庫的變更追蹤設定。</span><span class="sxs-lookup"><span data-stu-id="5e1d8-103">Use this page to view or modify change tracking settings for the selected database.</span></span> <span data-ttu-id="5e1d8-104">如需此頁面可用之選項的詳細資訊，請參閱[啟用和停用變更追蹤 &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5e1d8-104">For more information about the options available on this page, see [Enable and Disable Change Tracking &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5e1d8-105">選項。</span><span class="sxs-lookup"><span data-stu-id="5e1d8-105">Options</span></span>  
 <span data-ttu-id="5e1d8-106">**變更追蹤**</span><span class="sxs-lookup"><span data-stu-id="5e1d8-106">**Change Tracking**</span></span>  
 <span data-ttu-id="5e1d8-107">使用此選項啟用或停用資料庫變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="5e1d8-107">Use to enable or disable change tracking for the database.</span></span>  
  
 <span data-ttu-id="5e1d8-108">若要啟用變更追蹤，必須先擁有修改資料庫的權限。</span><span class="sxs-lookup"><span data-stu-id="5e1d8-108">To enable change tracking, you must have permission to modify the database.</span></span>  
  
 <span data-ttu-id="5e1d8-109">將值設為 [True] 以設定資料庫選項，允許在個別資料表中啟用變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="5e1d8-109">Setting the value to **True** sets a database option that allows change tracking to be enabled on individual tables.</span></span>  
  
 <span data-ttu-id="5e1d8-110">您也可以使用 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql)設定變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="5e1d8-110">You can also configure change tracking by using [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
 <span data-ttu-id="5e1d8-111">**保留週期**</span><span class="sxs-lookup"><span data-stu-id="5e1d8-111">**Retention Period**</span></span>  
 <span data-ttu-id="5e1d8-112">指定在資料庫中保存變更追蹤資訊的最小週期。</span><span class="sxs-lookup"><span data-stu-id="5e1d8-112">Specifies the minimum period for keeping change track information in the database.</span></span> <span data-ttu-id="5e1d8-113">只有當 [自動清除]\*\*\*\* 值為 [True]\*\*\*\* 時，才會移除資料。</span><span class="sxs-lookup"><span data-stu-id="5e1d8-113">Data is removed only if the **Auto Clean-Up**value is **True**.</span></span>  
  
 <span data-ttu-id="5e1d8-114">預設值為 2。</span><span class="sxs-lookup"><span data-stu-id="5e1d8-114">The default value is 2.</span></span>  
  
 <span data-ttu-id="5e1d8-115">**保留週期單位**</span><span class="sxs-lookup"><span data-stu-id="5e1d8-115">**Retention Period Units**</span></span>  
 <span data-ttu-id="5e1d8-116">指定「保留週期」值的單位。</span><span class="sxs-lookup"><span data-stu-id="5e1d8-116">Specifies the units for the Retention Period value.</span></span> <span data-ttu-id="5e1d8-117">您可以選取 [日]、[小時] 或 [分鐘]。</span><span class="sxs-lookup"><span data-stu-id="5e1d8-117">You can select **Days**, **Hours**, or **Minutes**.</span></span> <span data-ttu-id="5e1d8-118">預設值為 [日]。</span><span class="sxs-lookup"><span data-stu-id="5e1d8-118">The default value is **Days**.</span></span>  
  
 <span data-ttu-id="5e1d8-119">最小保留週期是 1 分鐘。</span><span class="sxs-lookup"><span data-stu-id="5e1d8-119">The minimum retention period is 1 minute.</span></span> <span data-ttu-id="5e1d8-120">沒有最大保留週期。</span><span class="sxs-lookup"><span data-stu-id="5e1d8-120">There is no maximum retention period.</span></span>  
  
 <span data-ttu-id="5e1d8-121">**自動清除**</span><span class="sxs-lookup"><span data-stu-id="5e1d8-121">**Auto Clean-Up**</span></span>  
 <span data-ttu-id="5e1d8-122">指出在經過了指定的保留週期後，是否要自動清除變更追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="5e1d8-122">Indicates whether change tracking information is automatically removed after the specified retention period.</span></span>  
  
 <span data-ttu-id="5e1d8-123">如啟用 [自動清除]，會將所有先前自訂的保留週期重設為預設保留週期：2 日。</span><span class="sxs-lookup"><span data-stu-id="5e1d8-123">Enabling **Auto Clean-Up** resets any previous custom retention period to the default retention period of 2 days.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e1d8-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e1d8-124">See Also</span></span>  
 <span data-ttu-id="5e1d8-125">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5e1d8-125">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="5e1d8-126">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5e1d8-126">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
