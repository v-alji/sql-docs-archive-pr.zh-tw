---
title: 新增 IP 位址對話方塊 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygrouplistener.addipaddress.f1
ms.assetid: 98c9ad3b-ff3c-4c1d-b344-59a72fca137c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5192e6414b34bee6de09d45a7284f25404235dc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592260"
---
# <a name="add-ip-address-dialog-box-sql-server-management-studio"></a><span data-ttu-id="ed438-102">[加入 IP 位址] 對話方塊 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="ed438-102">Add IP Address Dialog Box (SQL Server Management Studio)</span></span>
  <span data-ttu-id="ed438-103"> 此 F1 描述主題描述 [加入 IP 位址\]\*\*\** 對話方塊的選項。</span><span class="sxs-lookup"><span data-stu-id="ed438-103">This F1 help topic describes the options of the **Add IP Address** dialog box.</span></span> <span data-ttu-id="ed438-104">可從 **[新增可用性群組接聽程式]** 對話方塊以及 \*\*\*\* 或 **的** [指定複本] [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 頁面的 [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] [接聽程式] [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]索引標籤存取此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ed438-104">This dialog box accessed from the **New Availability Group Listener** dialog box and the **Listener** tab of the **Specify Replicas** page of the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] or the [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ed438-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="ed438-105">Prerequisites</span></span>  
 <span data-ttu-id="ed438-106">開始將子網路加入至可用性群組接聽程式之前，請務必知道每個子網路的 IP 位址，以及 IPv4 位址的子網路遮罩。</span><span class="sxs-lookup"><span data-stu-id="ed438-106">Before you begin to add subnets to an availability group listener, ensure that know the IP address for each subnet and, for an IPv4 address, the subnet mask.</span></span>  
  
##  <a name="add-ip-address-options"></a><a name="PageOptions"></a> <span data-ttu-id="ed438-107">加入 IP 位址選項</span><span class="sxs-lookup"><span data-stu-id="ed438-107">Add IP Address Options</span></span>  
 <span data-ttu-id="ed438-108">**子網路**</span><span class="sxs-lookup"><span data-stu-id="ed438-108">**Subnet**</span></span>  
 <span data-ttu-id="ed438-109">使用此下拉式清單，為您要加入至可用性群組接聽程式的子網路選取位址。</span><span class="sxs-lookup"><span data-stu-id="ed438-109">Use the drop list to select an address for the subnet that you are adding to the availability group listener.</span></span> <span data-ttu-id="ed438-110">根據預設，子網路擁有 IPv4 位址和 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="ed438-110">By default a subnet possesses both an IPv4 address and an IPv6 address.</span></span> <span data-ttu-id="ed438-111">第一次使用 **[加入 IP 位址]** 對話方塊時， **[子網路]** 下拉式清單會為裝載可用性群組之複本的每個子網路顯示這兩種子網路位址。</span><span class="sxs-lookup"><span data-stu-id="ed438-111">The first time you use the **Add IP Address** dialog,  the **Subnet** drop list displays both subnet addresses for each subnet that hosts a replica for the availability group.</span></span> <span data-ttu-id="ed438-112">若要將給定的子網路加入至接聽程式，請選取其中一個子網路位址。</span><span class="sxs-lookup"><span data-stu-id="ed438-112">To add a given subnet to the listener, select one of its subnet addresses.</span></span>  
  
 <span data-ttu-id="ed438-113">在完成 **[加入 IP 位址]** 對話方塊，並按一下 **[確定]** 將選定的子網路位址加入至接聽程式之後， **[子網路]** 下拉式清單會篩選出該子網路位址。</span><span class="sxs-lookup"><span data-stu-id="ed438-113">After you complete the **Add IP Address** dialog box and click **OK** to add a selected subnet address to the listener, the **Subnet** drop list filters out that subnet address.</span></span> <span data-ttu-id="ed438-114">所有未選定的子網路位址會保留在下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="ed438-114">All unselected subnet addresses remain on the drop list.</span></span> <span data-ttu-id="ed438-115">針對每個子網路，務必只將一個子網路位址加入至接聽程式，否則接聽程式建立會失敗。</span><span class="sxs-lookup"><span data-stu-id="ed438-115">Be sure that you add one and only one subnet address per subnet to the listener, or listener creation will fail.</span></span>  
  
 <span data-ttu-id="ed438-116">**位址**</span><span class="sxs-lookup"><span data-stu-id="ed438-116">**Addresses**</span></span>  
 <span data-ttu-id="ed438-117">使用此欄位，為選定的子網路位址輸入靜態 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="ed438-117">Use this field to enter a static IP address for the selected subnet address.</span></span> <span data-ttu-id="ed438-118">請連絡您的網路系統管理員以取得此靜態 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="ed438-118">Contact your network administrator for this IP address.</span></span> <span data-ttu-id="ed438-119">請務必為選定的子網路位址輸入有效位址，否則接聽程式建立會失敗。</span><span class="sxs-lookup"><span data-stu-id="ed438-119">Ensure that you enter a valid address for the selected subnet address, or listener creation will fail.</span></span>  
  
 <span data-ttu-id="ed438-120">**IPv4 位址**</span><span class="sxs-lookup"><span data-stu-id="ed438-120">**IPv4 Address**</span></span>  
 <span data-ttu-id="ed438-121">如果您選取了子網路的 IPv4 子網路位址，請在這裡輸入有效的 IPv4 靜態位址。</span><span class="sxs-lookup"><span data-stu-id="ed438-121">If you selected the IPv4 subnet address of a subnet, enter a valid IPv4 static address here.</span></span>  
  
 <span data-ttu-id="ed438-122">**子網路遮罩**</span><span class="sxs-lookup"><span data-stu-id="ed438-122">**Subnet Mask**</span></span>  
 <span data-ttu-id="ed438-123">對於 IPv4 位址，此唯讀欄位顯示選定之子網路的子網路遮罩。</span><span class="sxs-lookup"><span data-stu-id="ed438-123">For an IPv4 address, this read-only field displays the subnet mask of the selected subnet.</span></span>  
  
 <span data-ttu-id="ed438-124">**IPv6 位址**</span><span class="sxs-lookup"><span data-stu-id="ed438-124">**IPv6 Address**</span></span>  
 <span data-ttu-id="ed438-125">如果您選取了子網路的 IPv6 子網路位址，請在這裡輸入有效的 IPv6 靜態位址。</span><span class="sxs-lookup"><span data-stu-id="ed438-125">If you selected the IPv6 subnet address of a subnet, enter a valid IPv6 static address here.</span></span>  
  
 <span data-ttu-id="ed438-126">**確定**</span><span class="sxs-lookup"><span data-stu-id="ed438-126">**OK**</span></span>  
 <span data-ttu-id="ed438-127">按一下以加入所選位址的子網路，以及指定的靜態 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="ed438-127">Click to create add the subnet whose address you selected, along with the static IP address that you specified.</span></span> <span data-ttu-id="ed438-128">包含這些值的資料列就會加入至 **[新增可用性群組接聽程式]** 或 **[指定複本]** 對話方塊的子網路方格中。</span><span class="sxs-lookup"><span data-stu-id="ed438-128">A row containing these values will be added to the subnet grid of the **New Availability Group Listener** or **Specify Replicas** dialog box.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ed438-129">**[加入 IP 位址]** 對話方塊不會驗證 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="ed438-129">The **Add IP Address** dialog does not verify the IP address.</span></span> <span data-ttu-id="ed438-130">此對話方塊也不會阻止您為已加入至可用性群組接聽程式的子網路加入第二個子網路位址。</span><span class="sxs-lookup"><span data-stu-id="ed438-130">Also the dialog does not prevent you from adding the second subnet address for a subnet that you have already added to the availability group listener.</span></span>  
  
 <span data-ttu-id="ed438-131">**取消**</span><span class="sxs-lookup"><span data-stu-id="ed438-131">**Cancel**</span></span>  
 <span data-ttu-id="ed438-132">按一下以取消選取，並返回 [新增可用性群組接聽程式]\*\*\*\* 對話方塊或 [接聽程式]\*\*\*\* 索引標籤，而不加入任何子網路的靜態 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="ed438-132">Click to cancel your selections, and return to the **New Availability Group Listener** dialog box or **Listener** tab without adding a static IP address for any subnet.</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ed438-133">相關工作</span><span class="sxs-lookup"><span data-stu-id="ed438-133">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ed438-134">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ed438-134">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="ed438-135">使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="ed438-135">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   <span data-ttu-id="ed438-136">[使用 [將複本加入可用性群組中精靈] &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="ed438-136">[Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="ed438-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed438-137">See Also</span></span>  
 <span data-ttu-id="ed438-138">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ed438-138">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="ed438-139">[可用性群組接聽程式、用戶端連接性及應用程式容錯移轉 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="ed438-139">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="ed438-140">AlwaysOn 用戶端連接性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed438-140">AlwaysOn Client Connectivity (SQL Server)</span></span>](always-on-client-connectivity-sql-server.md)  
  
  
