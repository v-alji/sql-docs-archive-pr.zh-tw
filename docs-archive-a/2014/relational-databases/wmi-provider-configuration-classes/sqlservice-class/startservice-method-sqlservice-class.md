---
title: StartService 方法 (SqlService 類別) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- StartService Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- StartService method
ms.assetid: 83dfb6bd-dbd5-45d8-aad2-a11926317f91
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4d91646da2ac2c9f636655ff6c65808ba115e28f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702549"
---
# <a name="startservice-method-sqlservice-class"></a><span data-ttu-id="899bc-102">StartService 方法 (SqlService 類別)</span><span class="sxs-lookup"><span data-stu-id="899bc-102">StartService Method (SqlService Class)</span></span>
  <span data-ttu-id="899bc-103">嘗試將此服務置於它的啟動狀態。</span><span class="sxs-lookup"><span data-stu-id="899bc-103">Attempts to place the service into its started state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="899bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="899bc-104">Syntax</span></span>  
  
```  
  
object  
.StartService()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="899bc-105">組件</span><span class="sxs-lookup"><span data-stu-id="899bc-105">Parts</span></span>  
 <span data-ttu-id="899bc-106">*object*</span><span class="sxs-lookup"><span data-stu-id="899bc-106">*object*</span></span>  
 <span data-ttu-id="899bc-107">表示此服務的 [SqlService 類別](sqlservice-class.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="899bc-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="899bc-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="899bc-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="899bc-109">指定下列其中一個啟動狀態的 uint32 值。</span><span class="sxs-lookup"><span data-stu-id="899bc-109">A uint32 value that specifies one of the following startup states.</span></span>  
  
 <span data-ttu-id="899bc-110">0</span><span class="sxs-lookup"><span data-stu-id="899bc-110">0</span></span>  
 <span data-ttu-id="899bc-111">成功。</span><span class="sxs-lookup"><span data-stu-id="899bc-111">Success.</span></span> <span data-ttu-id="899bc-112">要求已被接受。</span><span class="sxs-lookup"><span data-stu-id="899bc-112">The request was accepted.</span></span>  
  
 <span data-ttu-id="899bc-113">1</span><span class="sxs-lookup"><span data-stu-id="899bc-113">1</span></span>  
 <span data-ttu-id="899bc-114">不支援。</span><span class="sxs-lookup"><span data-stu-id="899bc-114">Not Supported.</span></span> <span data-ttu-id="899bc-115">不支援此要求。</span><span class="sxs-lookup"><span data-stu-id="899bc-115">The request is not supported.</span></span>  
  
 <span data-ttu-id="899bc-116">2</span><span class="sxs-lookup"><span data-stu-id="899bc-116">2</span></span>  
 <span data-ttu-id="899bc-117">拒絕存取。</span><span class="sxs-lookup"><span data-stu-id="899bc-117">Access Denied.</span></span> <span data-ttu-id="899bc-118">使用者沒有適當的存取權限。</span><span class="sxs-lookup"><span data-stu-id="899bc-118">The user did not have appropriate access.</span></span>  
  
 <span data-ttu-id="899bc-119">3</span><span class="sxs-lookup"><span data-stu-id="899bc-119">3</span></span>  
 <span data-ttu-id="899bc-120">相依的服務正在執行中。</span><span class="sxs-lookup"><span data-stu-id="899bc-120">Dependent Services Running.</span></span> <span data-ttu-id="899bc-121">無法停止此服務，因為與它相依的其他服務正在執行中。</span><span class="sxs-lookup"><span data-stu-id="899bc-121">The service cannot be stopped because other services that are running are dependent on it.</span></span>  
  
 <span data-ttu-id="899bc-122">4</span><span class="sxs-lookup"><span data-stu-id="899bc-122">4</span></span>  
 <span data-ttu-id="899bc-123">服務控制無效。</span><span class="sxs-lookup"><span data-stu-id="899bc-123">Invalid Service Control.</span></span> <span data-ttu-id="899bc-124">要求的控制碼無效，或是服務不接受此控制碼。</span><span class="sxs-lookup"><span data-stu-id="899bc-124">The requested control code is not valid, or it is unacceptable to the service.</span></span>  
  
 <span data-ttu-id="899bc-125">5</span><span class="sxs-lookup"><span data-stu-id="899bc-125">5</span></span>  
 <span data-ttu-id="899bc-126">服務無法接受控制。</span><span class="sxs-lookup"><span data-stu-id="899bc-126">Service Cannot Accept Control.</span></span> <span data-ttu-id="899bc-127">服務 (Win32_BaseService:State) 的狀態等於 0、1 或 2，因此無法將要求的控制碼傳送至服務。</span><span class="sxs-lookup"><span data-stu-id="899bc-127">The requested control code cannot be sent to the service because the state of the service (Win32_BaseService:State) is equal to 0, 1, or 2.</span></span>  
  
 <span data-ttu-id="899bc-128">6</span><span class="sxs-lookup"><span data-stu-id="899bc-128">6</span></span>  
 <span data-ttu-id="899bc-129">服務不在使用中。</span><span class="sxs-lookup"><span data-stu-id="899bc-129">Service Not Active.</span></span> <span data-ttu-id="899bc-130">尚未啟動服務。</span><span class="sxs-lookup"><span data-stu-id="899bc-130">The service has not been started.</span></span>  
  
 <span data-ttu-id="899bc-131">7</span><span class="sxs-lookup"><span data-stu-id="899bc-131">7</span></span>  
 <span data-ttu-id="899bc-132">服務要求逾時。</span><span class="sxs-lookup"><span data-stu-id="899bc-132">Service Request Timeout.</span></span> <span data-ttu-id="899bc-133">服務並未及時回應啟動要求。</span><span class="sxs-lookup"><span data-stu-id="899bc-133">The service did not respond to the start request in a timely fashion.</span></span>  
  
 <span data-ttu-id="899bc-134">8</span><span class="sxs-lookup"><span data-stu-id="899bc-134">8</span></span>  
 <span data-ttu-id="899bc-135">未知的失敗。</span><span class="sxs-lookup"><span data-stu-id="899bc-135">Unknown Failure.</span></span> <span data-ttu-id="899bc-136">啟動服務時發生未知的失敗。</span><span class="sxs-lookup"><span data-stu-id="899bc-136">An unknown failure occurred when starting the service.</span></span>  
  
 <span data-ttu-id="899bc-137">9</span><span class="sxs-lookup"><span data-stu-id="899bc-137">9</span></span>  
 <span data-ttu-id="899bc-138">找不到路徑。</span><span class="sxs-lookup"><span data-stu-id="899bc-138">Path Not Found.</span></span> <span data-ttu-id="899bc-139">找不到通往服務可執行檔的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="899bc-139">The directory path to the service executable was not found.</span></span>  
  
 <span data-ttu-id="899bc-140">10</span><span class="sxs-lookup"><span data-stu-id="899bc-140">10</span></span>  
 <span data-ttu-id="899bc-141">服務已經在執行中。</span><span class="sxs-lookup"><span data-stu-id="899bc-141">Service Already Running.</span></span> <span data-ttu-id="899bc-142">服務已在執行中。</span><span class="sxs-lookup"><span data-stu-id="899bc-142">The service is already running.</span></span>  
  
 <span data-ttu-id="899bc-143">11</span><span class="sxs-lookup"><span data-stu-id="899bc-143">11</span></span>  
 <span data-ttu-id="899bc-144">服務資料庫已鎖定。</span><span class="sxs-lookup"><span data-stu-id="899bc-144">Service Database Locked.</span></span> <span data-ttu-id="899bc-145">要加入新服務的資料庫已被鎖定。</span><span class="sxs-lookup"><span data-stu-id="899bc-145">The database to add a new service is locked.</span></span>  
  
 <span data-ttu-id="899bc-146">12</span><span class="sxs-lookup"><span data-stu-id="899bc-146">12</span></span>  
 <span data-ttu-id="899bc-147">服務相依性已刪除。</span><span class="sxs-lookup"><span data-stu-id="899bc-147">Service Dependency Deleted.</span></span> <span data-ttu-id="899bc-148">已經從系統中移除這個服務所依賴的相依性。</span><span class="sxs-lookup"><span data-stu-id="899bc-148">A dependency on which this service relies has been removed from the system.</span></span>  
  
 <span data-ttu-id="899bc-149">13</span><span class="sxs-lookup"><span data-stu-id="899bc-149">13</span></span>  
 <span data-ttu-id="899bc-150">服務相依性失敗。</span><span class="sxs-lookup"><span data-stu-id="899bc-150">Service Dependency Failure.</span></span> <span data-ttu-id="899bc-151">服務在相依的服務中找不到所需的服務。</span><span class="sxs-lookup"><span data-stu-id="899bc-151">The service failed to find the service needed from a dependent service.</span></span>  
  
 <span data-ttu-id="899bc-152">14</span><span class="sxs-lookup"><span data-stu-id="899bc-152">14</span></span>  
 <span data-ttu-id="899bc-153">服務已停用。</span><span class="sxs-lookup"><span data-stu-id="899bc-153">Service Disabled.</span></span> <span data-ttu-id="899bc-154">已經從系統中停用服務。</span><span class="sxs-lookup"><span data-stu-id="899bc-154">The service has been disabled from the system.</span></span>  
  
 <span data-ttu-id="899bc-155">15</span><span class="sxs-lookup"><span data-stu-id="899bc-155">15</span></span>  
 <span data-ttu-id="899bc-156">服務登入失敗。</span><span class="sxs-lookup"><span data-stu-id="899bc-156">Service Logon Failed.</span></span> <span data-ttu-id="899bc-157">此服務未通過驗證，無法在系統上執行。</span><span class="sxs-lookup"><span data-stu-id="899bc-157">The service does not have the correct authentication to run on the system.</span></span>  
  
 <span data-ttu-id="899bc-158">16</span><span class="sxs-lookup"><span data-stu-id="899bc-158">16</span></span>  
 <span data-ttu-id="899bc-159">服務已標示為要刪除。</span><span class="sxs-lookup"><span data-stu-id="899bc-159">Service Marked For Deletion.</span></span> <span data-ttu-id="899bc-160">正在從系統中移除此服務。</span><span class="sxs-lookup"><span data-stu-id="899bc-160">The service is being removed from the system.</span></span>  
  
 <span data-ttu-id="899bc-161">17</span><span class="sxs-lookup"><span data-stu-id="899bc-161">17</span></span>  
 <span data-ttu-id="899bc-162">服務沒有執行緒。</span><span class="sxs-lookup"><span data-stu-id="899bc-162">Service No Thread.</span></span> <span data-ttu-id="899bc-163">服務沒有執行緒。</span><span class="sxs-lookup"><span data-stu-id="899bc-163">There is no execution thread for the service.</span></span>  
  
 <span data-ttu-id="899bc-164">18</span><span class="sxs-lookup"><span data-stu-id="899bc-164">18</span></span>  
 <span data-ttu-id="899bc-165">狀態循環相依性。</span><span class="sxs-lookup"><span data-stu-id="899bc-165">Status Circular Dependency.</span></span> <span data-ttu-id="899bc-166">啟動服務時有循環的相依性。</span><span class="sxs-lookup"><span data-stu-id="899bc-166">There are circular dependencies when starting the service.</span></span>  
  
 <span data-ttu-id="899bc-167">19</span><span class="sxs-lookup"><span data-stu-id="899bc-167">19</span></span>  
 <span data-ttu-id="899bc-168">狀態重複名稱。</span><span class="sxs-lookup"><span data-stu-id="899bc-168">Status Duplicate Name.</span></span> <span data-ttu-id="899bc-169">有一個服務在相同名稱下執行。</span><span class="sxs-lookup"><span data-stu-id="899bc-169">There is a service running under the same name.</span></span>  
  
 <span data-ttu-id="899bc-170">20</span><span class="sxs-lookup"><span data-stu-id="899bc-170">20</span></span>  
 <span data-ttu-id="899bc-171">狀態名稱無效。</span><span class="sxs-lookup"><span data-stu-id="899bc-171">Status Invalid Name.</span></span> <span data-ttu-id="899bc-172">服務名稱中有無效的字元。</span><span class="sxs-lookup"><span data-stu-id="899bc-172">There are characters that are not valid in the name of the service.</span></span>  
  
 <span data-ttu-id="899bc-173">21</span><span class="sxs-lookup"><span data-stu-id="899bc-173">21</span></span>  
 <span data-ttu-id="899bc-174">狀態參數無效。</span><span class="sxs-lookup"><span data-stu-id="899bc-174">Status Invalid Parameter.</span></span> <span data-ttu-id="899bc-175">已經將無效的參數傳遞給服務。</span><span class="sxs-lookup"><span data-stu-id="899bc-175">Parameters that are not valid have been passed to the service.</span></span>  
  
 <span data-ttu-id="899bc-176">22</span><span class="sxs-lookup"><span data-stu-id="899bc-176">22</span></span>  
 <span data-ttu-id="899bc-177">狀態服務帳戶無效。</span><span class="sxs-lookup"><span data-stu-id="899bc-177">Status Invalid Service Account.</span></span> <span data-ttu-id="899bc-178">執行此服務所使用的帳戶無效，或是它缺少執行此服務的權限。</span><span class="sxs-lookup"><span data-stu-id="899bc-178">The account which this service is to run under is not valid, or it lacks the permissions to run the service.</span></span>  
  
 <span data-ttu-id="899bc-179">23</span><span class="sxs-lookup"><span data-stu-id="899bc-179">23</span></span>  
 <span data-ttu-id="899bc-180">狀態服務存在。</span><span class="sxs-lookup"><span data-stu-id="899bc-180">Status Service Exists.</span></span> <span data-ttu-id="899bc-181">服務存在於系統可使用之服務的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="899bc-181">The service exists in the database of services available from the system.</span></span>  
  
 <span data-ttu-id="899bc-182">24</span><span class="sxs-lookup"><span data-stu-id="899bc-182">24</span></span>  
 <span data-ttu-id="899bc-183">服務已經暫停。</span><span class="sxs-lookup"><span data-stu-id="899bc-183">Service Already Paused.</span></span> <span data-ttu-id="899bc-184">服務目前在系統中暫停。</span><span class="sxs-lookup"><span data-stu-id="899bc-184">The service is currently paused in the system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="899bc-185">備註</span><span class="sxs-lookup"><span data-stu-id="899bc-185">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="899bc-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="899bc-186">See Also</span></span>  
 <span data-ttu-id="899bc-187">[啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="899bc-187">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
