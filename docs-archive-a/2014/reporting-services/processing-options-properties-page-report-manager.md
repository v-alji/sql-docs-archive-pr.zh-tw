---
title: 處理選項屬性頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 28f07c70-7132-4d15-9505-4fdf31dc9cc0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ab43474869eb0b06eba33b4bd597907b7371ce09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585115"
---
# <a name="processing-options-properties-page-report-manager"></a><span data-ttu-id="1bdb0-102">處理選項屬性頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="1bdb0-102">Processing Options Properties Page (Report Manager)</span></span>
  <span data-ttu-id="1bdb0-103">使用 [處理選項] 屬性頁面可以設定目前選取之報表的報表執行屬性。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-103">Use the Processing Options properties page to set report execution properties for the currently selected report.</span></span> <span data-ttu-id="1bdb0-104">這些選項會決定何時進行報表的資料處理。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-104">These options determine when data processing for the report occurs.</span></span> <span data-ttu-id="1bdb0-105">您可以設定這些選項，以便在離峰時段擷取報表資料。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-105">You can set these options to retrieve report data during off-peak hours.</span></span> <span data-ttu-id="1bdb0-106">如果您的報表經常被存取，當多位使用者彼此會在短時間內存取相同的報表時，您就可以暫時快取副本，以避免等待時間。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-106">If you have a report that is accessed frequently, you can temporarily cache copies of it to eliminate wait time if multiple users are accessing the same report within minutes of each other.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1bdb0-107">並非所有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]版本都提供報表記錄、執行快照集和快取功能。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-107">The Report history, Execution snapshots and Caching features are not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1bdb0-108">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-108">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="1bdb0-109">導覽</span><span class="sxs-lookup"><span data-stu-id="1bdb0-109">Navigation</span></span>  
 <span data-ttu-id="1bdb0-110">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-processing-options-properties-page"></a><span data-ttu-id="1bdb0-111">若要開啟處理選項屬性頁面</span><span class="sxs-lookup"><span data-stu-id="1bdb0-111">To open the Processing Options properties page</span></span>  
  
1.  <span data-ttu-id="1bdb0-112">開啟報表管理員，然後找出您想要設定處理屬性的報表。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-112">Open Report Manager, and locate the report for which you want to set processing properties.</span></span>  
  
2.  <span data-ttu-id="1bdb0-113">將滑鼠停留在該報表上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-113">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="1bdb0-114">在下拉式功能表中，按一下 **[管理]**。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-114">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="1bdb0-115">這樣就會開啟該報表的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-115">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="1bdb0-116">選取 **[處理選項]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-116">Select the **Processing Options** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1bdb0-117">選項</span><span class="sxs-lookup"><span data-stu-id="1bdb0-117">Options</span></span>  
 <span data-ttu-id="1bdb0-118">**永遠以最新的資料執行此報表**</span><span class="sxs-lookup"><span data-stu-id="1bdb0-118">**Always run this report with the most recent data**</span></span>  
 <span data-ttu-id="1bdb0-119">如果您要在使用者選取報表時擷取報表資料，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-119">Use this option when you want to retrieve report data when the user selects the report.</span></span> <span data-ttu-id="1bdb0-120">當使用者選取報表時，如果報表有快取副本，則傳回給使用者，否則會執行資料擷取和轉譯。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-120">If a cached copy of the report is available, it is returned to the user; otherwise, data retrieval and rendering occurs when a user selects the report.</span></span>  
  
 <span data-ttu-id="1bdb0-121">選取 **[不要快取此報表的暫存副本]** 就會永遠以最新的資料來執行報表。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-121">Select **Do not cache temporary copies of this report** to always run the report with the most recent data.</span></span> <span data-ttu-id="1bdb0-122">開啟報表的每一位使用者都會觸發對資料來源的查詢，這些資料來源包含報表中使用的資料。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-122">Each user who opens the report triggers a query against the data source that contains data used in the report.</span></span>  
  
 <span data-ttu-id="1bdb0-123">選取 \*\*\*\*，即可在使用者首先開啟報表時，將報表的暫存副本放入快取中。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-123">Select **Cache a temporary copy of the report**to place a temporary copy of the report in a cache when a user first opens the report.</span></span> <span data-ttu-id="1bdb0-124">在快取期間內執行此報表的後續使用者都會收到快取的報表副本。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-124">Subsequent users who run the report within the caching period receive the cached copy of the report.</span></span> <span data-ttu-id="1bdb0-125">快取通常會改善效能，因為報表是從快取傳回，而非再次處理。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-125">Caching usually improves performance because the report is returned from the cache instead of being processed again.</span></span>  
  
 <span data-ttu-id="1bdb0-126">快取的報表最後一定會過期。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-126">Cached reports must eventually expire.</span></span> <span data-ttu-id="1bdb0-127">請指定要儲存快取之報表副本的分鐘數。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-127">Specify the number of minutes to save the cached copy of the report.</span></span> <span data-ttu-id="1bdb0-128">一旦暫存副本過期，系統就不會再從快取中傳回報表。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-128">As soon as a temporary copy expires, it is no longer returned from cache.</span></span> <span data-ttu-id="1bdb0-129">使用者下次開啟報表時，報表伺服器會重新處理報表，並將重新整理過的報表副本存到快取中。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-129">The next time a user opens the report, the report server processes the report again and places a copy of the refreshed report back in the cache.</span></span>  
  
 <span data-ttu-id="1bdb0-130">您也可以使用排程使快取報表過期，以頻率來取代分鐘數。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-130">You can also use a schedule to expire a cached report using a frequency other than minutes.</span></span> <span data-ttu-id="1bdb0-131">例如，若要使快取報表在某日結束時過期，可以選取晚上某個特定時間，使副本在超過該時間之後過期。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-131">For example, to expire a cached report at the end of the day, you can pick a specific hour at night after which the copy expires.</span></span>  
  
 <span data-ttu-id="1bdb0-132">**從執行快照集轉譯此報表**</span><span class="sxs-lookup"><span data-stu-id="1bdb0-132">**Render this report from a report execution snapshot**</span></span>  
 <span data-ttu-id="1bdb0-133">使用此選項即可在排程的時間內將已經儲存的報表當做快照集擷取。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-133">Use this option to retrieve a report that has been stored as a snapshot at a time that you schedule.</span></span> <span data-ttu-id="1bdb0-134">當您選擇此選項時，可以將資料處理排程為於離峰時段進行。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-134">When you choose this option, you can schedule data processing to occur during off-peak hours.</span></span> <span data-ttu-id="1bdb0-135">不同於使用者開啟報表時才會建立的快取副本，快照集會定期建立而且後續會按照排程重新整理。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-135">Unlike cached copies that are created when a user opens the report, a snapshot is created and subsequently refreshed on a schedule.</span></span> <span data-ttu-id="1bdb0-136">快照集不會過期；它們可一直執行服務，直到被較新的版本取代為止。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-136">Snapshots do not expire; they remain in service until they are replaced by newer versions.</span></span>  
  
 <span data-ttu-id="1bdb0-137">由報表執行設定的結果所產生的快照集，與報表記錄快照集具有相同特性。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-137">Snapshots that are generated as a result of report execution settings have the same characteristics as report history snapshots.</span></span> <span data-ttu-id="1bdb0-138">其差異在於只能有一個報表執行快照集，但潛在地具有許多報表記錄快照集。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-138">The difference is that there is only one report execution snapshot and potentially many report history snapshots.</span></span> <span data-ttu-id="1bdb0-139">報表記錄快照集可從報表的 [記錄] 頁面存取，其中儲存不同的時間點存在之報表的許多執行個體。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-139">Report history snapshots are accessed from the History page of the report, which stores many instances of a report as it existed at different points in time.</span></span> <span data-ttu-id="1bdb0-140">相對地，使用者從資料夾存取報表執行快照集的方法，與存取使用中報表的方法相同。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-140">In contrast, users access report execution snapshots from folders the same way that they access live reports.</span></span> <span data-ttu-id="1bdb0-141">對於報表執行快照集，沒有視覺提示可對使用者指出此報表是快照集。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-141">In the case of report execution snapshots, no visual cue exists to indicate to users that the report is a snapshot.</span></span>  
  
 <span data-ttu-id="1bdb0-142">若要在您按一下 [套用] 時建立報表快照集，請選取 **[當您在此頁面上按一下 [套用] 按鈕時，會建立報表快照集]** 的相關選項。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-142">Select the related option of **Create a report snapshot when you click Apply on this page** to create a report snapshot when you click Apply.</span></span> <span data-ttu-id="1bdb0-143">這樣就會立即產生報表快照集，使其在排程的起始時間之前就可供使用。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-143">This generates the report snapshot right away to make it available before the scheduled start time.</span></span>  
  
 <span data-ttu-id="1bdb0-144">**報表執行逾時**</span><span class="sxs-lookup"><span data-stu-id="1bdb0-144">**Report Execution Timeout**</span></span>  
 <span data-ttu-id="1bdb0-145">指定在特定秒數之後報表處理是否逾時。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-145">Specify whether report processing times out after a certain number of seconds.</span></span> <span data-ttu-id="1bdb0-146">如果選擇預設值，此報表會使用 [站台設定] 頁面中指定的逾時設定。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-146">If you choose the default setting, the timeout setting that is specified in the Site Settings page is used for this report.</span></span>  
  
 <span data-ttu-id="1bdb0-147">此值會套用至報表伺服器上的報表處理。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-147">This value applies to report processing on a report server.</span></span> <span data-ttu-id="1bdb0-148">它不會針對提供報表資料之資料庫伺服器上的資料處理設定逾時。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-148">It does not set a timeout for data processing on the database server that provides the data for your report.</span></span> <span data-ttu-id="1bdb0-149">不過，您所指定的值必須足以完成資料處理和報表處理。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-149">However, the value that you specify must be enough to complete both data processing and report processing.</span></span> <span data-ttu-id="1bdb0-150">報表處理的計數在選取報表時會開始，並在開啟報表時結束。</span><span class="sxs-lookup"><span data-stu-id="1bdb0-150">The count for report processing begins when the report is selected and ends when the report opens.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bdb0-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bdb0-151">See Also</span></span>  
 <span data-ttu-id="1bdb0-152">[設定報表處理屬性](report-server/set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="1bdb0-152">[Set Report Processing Properties](report-server/set-report-processing-properties.md) </span></span>  
 <span data-ttu-id="1bdb0-153">[快取多個報表 &#40;SSRS&#41;](report-server/caching-reports-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1bdb0-153">[Caching Reports &#40;SSRS&#41;](report-server/caching-reports-ssrs.md) </span></span>  
 <span data-ttu-id="1bdb0-154">[建立、修改和刪除共用排程](subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="1bdb0-154">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="1bdb0-155">報表管理員 F1 說明</span><span class="sxs-lookup"><span data-stu-id="1bdb0-155">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
