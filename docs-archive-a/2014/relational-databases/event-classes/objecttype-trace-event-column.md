---
title: ObjectType 追蹤事件資料行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Object Type column values
- events [SQL Server], Object Type column values
- event classes [SQL Server], Object Type column values
- Object Type column values [SQL Server]
ms.assetid: 42f85c50-34c9-49ca-955f-af9595e2707f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f90661e5ebedc91505989c3d80dcec78436ce86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593407"
---
# <a name="objecttype-trace-event-column"></a><span data-ttu-id="936d1-102">ObjectType 追蹤事件資料行</span><span class="sxs-lookup"><span data-stu-id="936d1-102">ObjectType Trace Event Column</span></span>
  <span data-ttu-id="936d1-103">Object Type 追蹤事件資料行會用於各種追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="936d1-103">The Object Type trace event column is used in a variety of trace events.</span></span> <span data-ttu-id="936d1-104">此主題描述此資料行和其相關聯定義的可能值。</span><span class="sxs-lookup"><span data-stu-id="936d1-104">This topic describes the possible values of this column and their associated definitions.</span></span>  
  
## <a name="object-type-column-values"></a><span data-ttu-id="936d1-105">Object Type 資料行值</span><span class="sxs-lookup"><span data-stu-id="936d1-105">Object Type Column Values</span></span>  
  
|<span data-ttu-id="936d1-106">值</span><span class="sxs-lookup"><span data-stu-id="936d1-106">Value</span></span>|<span data-ttu-id="936d1-107">定義</span><span class="sxs-lookup"><span data-stu-id="936d1-107">Definition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="936d1-108">8259</span><span class="sxs-lookup"><span data-stu-id="936d1-108">8259</span></span>|<span data-ttu-id="936d1-109">檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="936d1-109">Check Constraint</span></span>|  
|<span data-ttu-id="936d1-110">8260</span><span class="sxs-lookup"><span data-stu-id="936d1-110">8260</span></span>|<span data-ttu-id="936d1-111">預設 (條件約束或獨立)</span><span class="sxs-lookup"><span data-stu-id="936d1-111">Default (constraint or standalone)</span></span>|  
|<span data-ttu-id="936d1-112">8262</span><span class="sxs-lookup"><span data-stu-id="936d1-112">8262</span></span>|<span data-ttu-id="936d1-113">外部索引鍵條件約束</span><span class="sxs-lookup"><span data-stu-id="936d1-113">Foreign-key Constraint</span></span>|  
|<span data-ttu-id="936d1-114">8272</span><span class="sxs-lookup"><span data-stu-id="936d1-114">8272</span></span>|<span data-ttu-id="936d1-115">預存程序</span><span class="sxs-lookup"><span data-stu-id="936d1-115">Stored Procedure</span></span>|  
|<span data-ttu-id="936d1-116">8274</span><span class="sxs-lookup"><span data-stu-id="936d1-116">8274</span></span>|<span data-ttu-id="936d1-117">規則</span><span class="sxs-lookup"><span data-stu-id="936d1-117">Rule</span></span>|  
|<span data-ttu-id="936d1-118">8275</span><span class="sxs-lookup"><span data-stu-id="936d1-118">8275</span></span>|<span data-ttu-id="936d1-119">系統資料表</span><span class="sxs-lookup"><span data-stu-id="936d1-119">System Table</span></span>|  
|<span data-ttu-id="936d1-120">8276</span><span class="sxs-lookup"><span data-stu-id="936d1-120">8276</span></span>|<span data-ttu-id="936d1-121">伺服器的觸發程序</span><span class="sxs-lookup"><span data-stu-id="936d1-121">Trigger on Server</span></span>|  
|<span data-ttu-id="936d1-122">8277</span><span class="sxs-lookup"><span data-stu-id="936d1-122">8277</span></span>|<span data-ttu-id="936d1-123">(使用者定義的) 資料表</span><span class="sxs-lookup"><span data-stu-id="936d1-123">(User-defined) Table</span></span>|  
|<span data-ttu-id="936d1-124">8278</span><span class="sxs-lookup"><span data-stu-id="936d1-124">8278</span></span>|<span data-ttu-id="936d1-125">檢視</span><span class="sxs-lookup"><span data-stu-id="936d1-125">View</span></span>|  
|<span data-ttu-id="936d1-126">8280</span><span class="sxs-lookup"><span data-stu-id="936d1-126">8280</span></span>|<span data-ttu-id="936d1-127">擴充預存程序</span><span class="sxs-lookup"><span data-stu-id="936d1-127">Extended Stored Procedure</span></span>|  
|<span data-ttu-id="936d1-128">16724</span><span class="sxs-lookup"><span data-stu-id="936d1-128">16724</span></span>|<span data-ttu-id="936d1-129">CLR 觸發程序</span><span class="sxs-lookup"><span data-stu-id="936d1-129">CLR Trigger</span></span>|  
|<span data-ttu-id="936d1-130">16964</span><span class="sxs-lookup"><span data-stu-id="936d1-130">16964</span></span>|<span data-ttu-id="936d1-131">資料庫</span><span class="sxs-lookup"><span data-stu-id="936d1-131">Database</span></span>|  
|<span data-ttu-id="936d1-132">16975</span><span class="sxs-lookup"><span data-stu-id="936d1-132">16975</span></span>|<span data-ttu-id="936d1-133">Object</span><span class="sxs-lookup"><span data-stu-id="936d1-133">Object</span></span>|  
|<span data-ttu-id="936d1-134">17222</span><span class="sxs-lookup"><span data-stu-id="936d1-134">17222</span></span>|<span data-ttu-id="936d1-135">全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="936d1-135">FullText Catalog</span></span>|  
|<span data-ttu-id="936d1-136">17232</span><span class="sxs-lookup"><span data-stu-id="936d1-136">17232</span></span>|<span data-ttu-id="936d1-137">CLR 預存程序</span><span class="sxs-lookup"><span data-stu-id="936d1-137">CLR Stored Procedure</span></span>|  
|<span data-ttu-id="936d1-138">17235</span><span class="sxs-lookup"><span data-stu-id="936d1-138">17235</span></span>|<span data-ttu-id="936d1-139">結構描述</span><span class="sxs-lookup"><span data-stu-id="936d1-139">Schema</span></span>|  
|<span data-ttu-id="936d1-140">17475</span><span class="sxs-lookup"><span data-stu-id="936d1-140">17475</span></span>|<span data-ttu-id="936d1-141">認證</span><span class="sxs-lookup"><span data-stu-id="936d1-141">Credential</span></span>|  
|<span data-ttu-id="936d1-142">17491</span><span class="sxs-lookup"><span data-stu-id="936d1-142">17491</span></span>|<span data-ttu-id="936d1-143">DDL 事件</span><span class="sxs-lookup"><span data-stu-id="936d1-143">DDL Event</span></span>|  
|<span data-ttu-id="936d1-144">17741</span><span class="sxs-lookup"><span data-stu-id="936d1-144">17741</span></span>|<span data-ttu-id="936d1-145">Management 事件</span><span class="sxs-lookup"><span data-stu-id="936d1-145">Management Event</span></span>|  
|<span data-ttu-id="936d1-146">17747</span><span class="sxs-lookup"><span data-stu-id="936d1-146">17747</span></span>|<span data-ttu-id="936d1-147">Security 事件</span><span class="sxs-lookup"><span data-stu-id="936d1-147">Security Event</span></span>|  
|<span data-ttu-id="936d1-148">17749</span><span class="sxs-lookup"><span data-stu-id="936d1-148">17749</span></span>|<span data-ttu-id="936d1-149">User 事件</span><span class="sxs-lookup"><span data-stu-id="936d1-149">User Event</span></span>|  
|<span data-ttu-id="936d1-150">17985</span><span class="sxs-lookup"><span data-stu-id="936d1-150">17985</span></span>|<span data-ttu-id="936d1-151">CLR 彙總函式</span><span class="sxs-lookup"><span data-stu-id="936d1-151">CLR Aggregate Function</span></span>|  
|<span data-ttu-id="936d1-152">17993</span><span class="sxs-lookup"><span data-stu-id="936d1-152">17993</span></span>|<span data-ttu-id="936d1-153">內嵌資料表值 SQL 函數</span><span class="sxs-lookup"><span data-stu-id="936d1-153">Inline Table-valued SQL Function</span></span>|  
|<span data-ttu-id="936d1-154">18000</span><span class="sxs-lookup"><span data-stu-id="936d1-154">18000</span></span>|<span data-ttu-id="936d1-155">資料分割函數</span><span class="sxs-lookup"><span data-stu-id="936d1-155">Partition Function</span></span>|  
|<span data-ttu-id="936d1-156">18002</span><span class="sxs-lookup"><span data-stu-id="936d1-156">18002</span></span>|<span data-ttu-id="936d1-157">複寫篩選程序</span><span class="sxs-lookup"><span data-stu-id="936d1-157">Replication Filter Procedure</span></span>|  
|<span data-ttu-id="936d1-158">18004</span><span class="sxs-lookup"><span data-stu-id="936d1-158">18004</span></span>|<span data-ttu-id="936d1-159">資料表值 SQL 函數</span><span class="sxs-lookup"><span data-stu-id="936d1-159">Table-valued SQL Function</span></span>|  
|<span data-ttu-id="936d1-160">18259</span><span class="sxs-lookup"><span data-stu-id="936d1-160">18259</span></span>|<span data-ttu-id="936d1-161">伺服器角色</span><span class="sxs-lookup"><span data-stu-id="936d1-161">Server Role</span></span>|  
|<span data-ttu-id="936d1-162">18263</span><span class="sxs-lookup"><span data-stu-id="936d1-162">18263</span></span>|[!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="936d1-163">Windows 群組</span><span class="sxs-lookup"><span data-stu-id="936d1-163">Windows Group</span></span>|  
|<span data-ttu-id="936d1-164">19265</span><span class="sxs-lookup"><span data-stu-id="936d1-164">19265</span></span>|<span data-ttu-id="936d1-165">非對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="936d1-165">Asymmetric Key</span></span>|  
|<span data-ttu-id="936d1-166">19277</span><span class="sxs-lookup"><span data-stu-id="936d1-166">19277</span></span>|<span data-ttu-id="936d1-167">主要金鑰</span><span class="sxs-lookup"><span data-stu-id="936d1-167">Master Key</span></span>|  
|<span data-ttu-id="936d1-168">19280</span><span class="sxs-lookup"><span data-stu-id="936d1-168">19280</span></span>|<span data-ttu-id="936d1-169">主索引鍵</span><span class="sxs-lookup"><span data-stu-id="936d1-169">Primary Key</span></span>|  
|<span data-ttu-id="936d1-170">19283</span><span class="sxs-lookup"><span data-stu-id="936d1-170">19283</span></span>|<span data-ttu-id="936d1-171">ObfusKey</span><span class="sxs-lookup"><span data-stu-id="936d1-171">ObfusKey</span></span>|  
|<span data-ttu-id="936d1-172">19521</span><span class="sxs-lookup"><span data-stu-id="936d1-172">19521</span></span>|<span data-ttu-id="936d1-173">非對稱金鑰登入</span><span class="sxs-lookup"><span data-stu-id="936d1-173">Asymmetric Key Login</span></span>|  
|<span data-ttu-id="936d1-174">19523</span><span class="sxs-lookup"><span data-stu-id="936d1-174">19523</span></span>|<span data-ttu-id="936d1-175">憑證登入</span><span class="sxs-lookup"><span data-stu-id="936d1-175">Certificate Login</span></span>|  
|<span data-ttu-id="936d1-176">19538</span><span class="sxs-lookup"><span data-stu-id="936d1-176">19538</span></span>|<span data-ttu-id="936d1-177">角色</span><span class="sxs-lookup"><span data-stu-id="936d1-177">Role</span></span>|  
|<span data-ttu-id="936d1-178">19539</span><span class="sxs-lookup"><span data-stu-id="936d1-178">19539</span></span>|<span data-ttu-id="936d1-179">SQL 登入</span><span class="sxs-lookup"><span data-stu-id="936d1-179">SQL Login</span></span>|  
|<span data-ttu-id="936d1-180">19543</span><span class="sxs-lookup"><span data-stu-id="936d1-180">19543</span></span>|<span data-ttu-id="936d1-181">Windows 登入</span><span class="sxs-lookup"><span data-stu-id="936d1-181">Windows Login</span></span>|  
|<span data-ttu-id="936d1-182">20034</span><span class="sxs-lookup"><span data-stu-id="936d1-182">20034</span></span>|<span data-ttu-id="936d1-183">遠端服務繫結</span><span class="sxs-lookup"><span data-stu-id="936d1-183">Remote Service Binding</span></span>|  
|<span data-ttu-id="936d1-184">20036</span><span class="sxs-lookup"><span data-stu-id="936d1-184">20036</span></span>|<span data-ttu-id="936d1-185">資料庫的事件通知</span><span class="sxs-lookup"><span data-stu-id="936d1-185">Event Notification on Database</span></span>|  
|<span data-ttu-id="936d1-186">20037</span><span class="sxs-lookup"><span data-stu-id="936d1-186">20037</span></span>|<span data-ttu-id="936d1-187">事件通知</span><span class="sxs-lookup"><span data-stu-id="936d1-187">Event Notification</span></span>|  
|<span data-ttu-id="936d1-188">20038</span><span class="sxs-lookup"><span data-stu-id="936d1-188">20038</span></span>|<span data-ttu-id="936d1-189">純量 SQL 函數</span><span class="sxs-lookup"><span data-stu-id="936d1-189">Scalar SQL Function</span></span>|  
|<span data-ttu-id="936d1-190">20047</span><span class="sxs-lookup"><span data-stu-id="936d1-190">20047</span></span>|<span data-ttu-id="936d1-191">物件的事件通知</span><span class="sxs-lookup"><span data-stu-id="936d1-191">Event Notification on Object</span></span>|  
|<span data-ttu-id="936d1-192">20051</span><span class="sxs-lookup"><span data-stu-id="936d1-192">20051</span></span>|<span data-ttu-id="936d1-193">同義字</span><span class="sxs-lookup"><span data-stu-id="936d1-193">Synonym</span></span>|  
|<span data-ttu-id="936d1-194">20307</span><span class="sxs-lookup"><span data-stu-id="936d1-194">20307</span></span>|<span data-ttu-id="936d1-195">順序</span><span class="sxs-lookup"><span data-stu-id="936d1-195">Sequence</span></span>|  
|<span data-ttu-id="936d1-196">20549</span><span class="sxs-lookup"><span data-stu-id="936d1-196">20549</span></span>|<span data-ttu-id="936d1-197">端點</span><span class="sxs-lookup"><span data-stu-id="936d1-197">End Point</span></span>|  
|<span data-ttu-id="936d1-198">20801</span><span class="sxs-lookup"><span data-stu-id="936d1-198">20801</span></span>|<span data-ttu-id="936d1-199">可以快取的特定查詢</span><span class="sxs-lookup"><span data-stu-id="936d1-199">Adhoc Queries which may be cached</span></span>|  
|<span data-ttu-id="936d1-200">20816</span><span class="sxs-lookup"><span data-stu-id="936d1-200">20816</span></span>|<span data-ttu-id="936d1-201">可以快取的準備查詢</span><span class="sxs-lookup"><span data-stu-id="936d1-201">Prepared Queries which may be cached</span></span>|  
|<span data-ttu-id="936d1-202">20819</span><span class="sxs-lookup"><span data-stu-id="936d1-202">20819</span></span>|<span data-ttu-id="936d1-203">Service Broker 服務佇列</span><span class="sxs-lookup"><span data-stu-id="936d1-203">Service Broker Service Queue</span></span>|  
|<span data-ttu-id="936d1-204">20821</span><span class="sxs-lookup"><span data-stu-id="936d1-204">20821</span></span>|<span data-ttu-id="936d1-205">唯一的條件約束</span><span class="sxs-lookup"><span data-stu-id="936d1-205">Unique Constraint</span></span>|  
|<span data-ttu-id="936d1-206">21057</span><span class="sxs-lookup"><span data-stu-id="936d1-206">21057</span></span>|<span data-ttu-id="936d1-207">應用程式角色</span><span class="sxs-lookup"><span data-stu-id="936d1-207">Application Role</span></span>|  
|<span data-ttu-id="936d1-208">21059</span><span class="sxs-lookup"><span data-stu-id="936d1-208">21059</span></span>|<span data-ttu-id="936d1-209">憑證</span><span class="sxs-lookup"><span data-stu-id="936d1-209">Certificate</span></span>|  
|<span data-ttu-id="936d1-210">21075</span><span class="sxs-lookup"><span data-stu-id="936d1-210">21075</span></span>|<span data-ttu-id="936d1-211">伺服器</span><span class="sxs-lookup"><span data-stu-id="936d1-211">Server</span></span>|  
|<span data-ttu-id="936d1-212">21076</span><span class="sxs-lookup"><span data-stu-id="936d1-212">21076</span></span>|<span data-ttu-id="936d1-213">Transact-SQL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="936d1-213">Transact-SQL Trigger</span></span>|  
|<span data-ttu-id="936d1-214">21313</span><span class="sxs-lookup"><span data-stu-id="936d1-214">21313</span></span>|<span data-ttu-id="936d1-215">組件</span><span class="sxs-lookup"><span data-stu-id="936d1-215">Assembly</span></span>|  
|<span data-ttu-id="936d1-216">21318</span><span class="sxs-lookup"><span data-stu-id="936d1-216">21318</span></span>|<span data-ttu-id="936d1-217">CLR 純量函數</span><span class="sxs-lookup"><span data-stu-id="936d1-217">CLR Scalar Function</span></span>|  
|<span data-ttu-id="936d1-218">21321</span><span class="sxs-lookup"><span data-stu-id="936d1-218">21321</span></span>|<span data-ttu-id="936d1-219">內嵌純量 SQL 函數</span><span class="sxs-lookup"><span data-stu-id="936d1-219">Inline scalar SQL Function</span></span>|  
|<span data-ttu-id="936d1-220">21328</span><span class="sxs-lookup"><span data-stu-id="936d1-220">21328</span></span>|<span data-ttu-id="936d1-221">資料分割配置</span><span class="sxs-lookup"><span data-stu-id="936d1-221">Partition Scheme</span></span>|  
|<span data-ttu-id="936d1-222">21333</span><span class="sxs-lookup"><span data-stu-id="936d1-222">21333</span></span>|<span data-ttu-id="936d1-223">User</span><span class="sxs-lookup"><span data-stu-id="936d1-223">User</span></span>|  
|<span data-ttu-id="936d1-224">21571</span><span class="sxs-lookup"><span data-stu-id="936d1-224">21571</span></span>|<span data-ttu-id="936d1-225">Service Broker 服務合約</span><span class="sxs-lookup"><span data-stu-id="936d1-225">Service Broker Service Contract</span></span>|  
|<span data-ttu-id="936d1-226">21572</span><span class="sxs-lookup"><span data-stu-id="936d1-226">21572</span></span>|<span data-ttu-id="936d1-227">資料庫的觸發程序</span><span class="sxs-lookup"><span data-stu-id="936d1-227">Trigger on Database</span></span>|  
|<span data-ttu-id="936d1-228">21574</span><span class="sxs-lookup"><span data-stu-id="936d1-228">21574</span></span>|<span data-ttu-id="936d1-229">CLR 資料表值函式</span><span class="sxs-lookup"><span data-stu-id="936d1-229">CLR Table-valued Function</span></span>|  
|<span data-ttu-id="936d1-230">21577</span><span class="sxs-lookup"><span data-stu-id="936d1-230">21577</span></span>|<span data-ttu-id="936d1-231">內部資料表 (例如，XML 節點資料表、佇列資料表。)</span><span class="sxs-lookup"><span data-stu-id="936d1-231">Internal Table (For example, XML Node Table, Queue Table.)</span></span>|  
|<span data-ttu-id="936d1-232">21581</span><span class="sxs-lookup"><span data-stu-id="936d1-232">21581</span></span>|<span data-ttu-id="936d1-233">Service Broker 訊息類型</span><span class="sxs-lookup"><span data-stu-id="936d1-233">Service Broker Message Type</span></span>|  
|<span data-ttu-id="936d1-234">21586</span><span class="sxs-lookup"><span data-stu-id="936d1-234">21586</span></span>|<span data-ttu-id="936d1-235">Service Broker 路由</span><span class="sxs-lookup"><span data-stu-id="936d1-235">Service Broker Route</span></span>|  
|<span data-ttu-id="936d1-236">21587</span><span class="sxs-lookup"><span data-stu-id="936d1-236">21587</span></span>|<span data-ttu-id="936d1-237">統計資料</span><span class="sxs-lookup"><span data-stu-id="936d1-237">Statistics</span></span>|  
|<span data-ttu-id="936d1-238">21825</span><span class="sxs-lookup"><span data-stu-id="936d1-238">21825</span></span><br /><br /> <span data-ttu-id="936d1-239">21827</span><span class="sxs-lookup"><span data-stu-id="936d1-239">21827</span></span><br /><br /> <span data-ttu-id="936d1-240">21831</span><span class="sxs-lookup"><span data-stu-id="936d1-240">21831</span></span><br /><br /> <span data-ttu-id="936d1-241">21843</span><span class="sxs-lookup"><span data-stu-id="936d1-241">21843</span></span><br /><br /> <span data-ttu-id="936d1-242">21847</span><span class="sxs-lookup"><span data-stu-id="936d1-242">21847</span></span>|<span data-ttu-id="936d1-243">User</span><span class="sxs-lookup"><span data-stu-id="936d1-243">User</span></span>|  
|<span data-ttu-id="936d1-244">22099</span><span class="sxs-lookup"><span data-stu-id="936d1-244">22099</span></span>|<span data-ttu-id="936d1-245">Service Broker 服務</span><span class="sxs-lookup"><span data-stu-id="936d1-245">Service Broker Service</span></span>|  
|<span data-ttu-id="936d1-246">22601</span><span class="sxs-lookup"><span data-stu-id="936d1-246">22601</span></span>|<span data-ttu-id="936d1-247">索引</span><span class="sxs-lookup"><span data-stu-id="936d1-247">Index</span></span>|  
|<span data-ttu-id="936d1-248">22604</span><span class="sxs-lookup"><span data-stu-id="936d1-248">22604</span></span>|<span data-ttu-id="936d1-249">憑證登入</span><span class="sxs-lookup"><span data-stu-id="936d1-249">Certificate Login</span></span>|  
|<span data-ttu-id="936d1-250">22611</span><span class="sxs-lookup"><span data-stu-id="936d1-250">22611</span></span>|<span data-ttu-id="936d1-251">XMLSchema</span><span class="sxs-lookup"><span data-stu-id="936d1-251">XMLSchema</span></span>|  
|<span data-ttu-id="936d1-252">22868</span><span class="sxs-lookup"><span data-stu-id="936d1-252">22868</span></span>|<span data-ttu-id="936d1-253">類型</span><span class="sxs-lookup"><span data-stu-id="936d1-253">Type</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="936d1-254">另請參閱</span><span class="sxs-lookup"><span data-stu-id="936d1-254">See Also</span></span>  
 [<span data-ttu-id="936d1-255">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="936d1-255">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
