---
title: 變更容錯移轉叢集執行個體的 IP 位址 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- modifying IP addresses
- failover clustering [SQL Server], IP addresses
- IP addresses [SQL Server]
- clusters [SQL Server], IP addresses
ms.assetid: b685f400-cbfe-4c5d-a070-227a1123dae4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 45d3ef0b70282efd870e4a076663719c2549deaa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595575"
---
# <a name="change-the-ip-address-of-a-failover-cluster-instance"></a><span data-ttu-id="4c4fe-102">變更容錯移轉叢集執行個體的 IP 位址</span><span class="sxs-lookup"><span data-stu-id="4c4fe-102">Change the IP Address of a Failover Cluster Instance</span></span>
  <span data-ttu-id="4c4fe-103">此主題描述如何使用容錯移轉叢集管理員嵌入式管理單元，在 AlwaysOn 容錯移轉叢集執行個體 (FCI) 中變更 IP 位址資源。</span><span class="sxs-lookup"><span data-stu-id="4c4fe-103">This topic describes how to change the IP address resource in an AlwaysOn Failover Cluster Instance (FCI) by using the Failover Cluster Manager snap-in.</span></span> <span data-ttu-id="4c4fe-104">容錯移轉叢集管理員嵌入式管理單元是 Windows Server 容錯移轉叢集 (WSFC) 服務的叢集管理應用程式。</span><span class="sxs-lookup"><span data-stu-id="4c4fe-104">The Failover Cluster Manager snap-in is the cluster management application for the Windows Server Failover Clustering (WSFC) service.</span></span>  
  
-   <span data-ttu-id="4c4fe-105">**開始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="4c4fe-105">**Before you begin:**  [Security](#Security)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4c4fe-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="4c4fe-106">Before You Begin</span></span>  
 <span data-ttu-id="4c4fe-107">在開始之前，請先檢閱下列《 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 線上叢書》主題︰ [安裝容錯移轉叢集之前](../install/before-installing-failover-clustering.md)。</span><span class="sxs-lookup"><span data-stu-id="4c4fe-107">Before you begin, review the following [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online topic: [Before Installing Failover Clustering](../install/before-installing-failover-clustering.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4c4fe-108">Security</span><span class="sxs-lookup"><span data-stu-id="4c4fe-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4c4fe-109">權限</span><span class="sxs-lookup"><span data-stu-id="4c4fe-109">Permissions</span></span>  
 <span data-ttu-id="4c4fe-110">若要維護或更新 FCI，您必須是本機系統管理員，並且具有能在 FCI 的所有節點上以服務登入的權限。</span><span class="sxs-lookup"><span data-stu-id="4c4fe-110">To maintain or update an FCI, you must be a local administrator with permission to logon as a service on all nodes of the FCI.</span></span>  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> <span data-ttu-id="4c4fe-111">使用容錯移轉叢集管理員嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="4c4fe-111">Using the Failover Cluster Manager Snap-in</span></span>  
 <span data-ttu-id="4c4fe-112">**若要使用 FCI 變更 IP 位址資源**</span><span class="sxs-lookup"><span data-stu-id="4c4fe-112">**To change the IP address resource for an FCI**</span></span>  
  
1.  <span data-ttu-id="4c4fe-113">開啟 [容錯移轉叢集管理員] 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="4c4fe-113">Open the Failover Cluster Manager snap-in.</span></span>  
  
2.  <span data-ttu-id="4c4fe-114">展開 **[服務和應用程式]** 節點，在左窗格中按一下 [FCI]。</span><span class="sxs-lookup"><span data-stu-id="4c4fe-114">Expand the **Services and applications** node, in the left pane and click on the FCI.</span></span>  
  
3.  <span data-ttu-id="4c4fe-115">在右窗格的 [伺服器名稱]\*\*\*\* 類別下，以滑鼠右鍵按一下 [SQL Server 執行個體]，並選取 [屬性]\*\*\*\* 選項開啟 [屬性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4c4fe-115">On the right pane, under the **Server Name** category, right-click the SQL Server Instance, and select **Properties** option to open the **Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="4c4fe-116">在 **[一般]** 索引標籤上，變更 IP 位址資源。</span><span class="sxs-lookup"><span data-stu-id="4c4fe-116">On the **General** tab, change the IP address resource.</span></span>  
  
5.  <span data-ttu-id="4c4fe-117">按一下 **[確定]** ，關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4c4fe-117">Click **OK** to close the dialog box.</span></span>  
  
6.  <span data-ttu-id="4c4fe-118">在右窗格中，以滑鼠右鍵按一下 [SQL IP 位址1(容錯移轉叢集執行個體名稱)]，然後選取 [離線工作]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c4fe-118">In the right-hand pane, right-click the SQL IP Address1(failover cluster instance name) and select **Take Offline**.</span></span> <span data-ttu-id="4c4fe-119">您會發現 SQL IP 位址1(容錯移轉叢集執行個體名稱)、SQL 網路名稱(容錯移轉叢集執行個體名稱) 及 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的狀態，會從 [線上] 變更為 [離線暫止]，再變成 [離線]。</span><span class="sxs-lookup"><span data-stu-id="4c4fe-119">You will see the SQL IP Address1(failover cluster instance name), SQL Network Name(failover cluster instance name), and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] status change from Online to Offline Pending, and then to Offline.</span></span>  
  
7.  <span data-ttu-id="4c4fe-120">在右窗格中，以滑鼠右鍵按一下 [[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]]，然後選取 [線上工作]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c4fe-120">In the right-hand pane, right-click [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and then select **Bring Online**.</span></span> <span data-ttu-id="4c4fe-121">您會發現 SQL IP 位址1(容錯移轉叢集執行個體名稱)、SQL 網路名稱(容錯移轉叢集執行個體名稱) 與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的狀態，會從 [離線] 變更為 [線上暫止]，再變成 [線上]。</span><span class="sxs-lookup"><span data-stu-id="4c4fe-121">You will see the SQL IP Address1(failover cluster instance name), SQL Network Name(failover cluster instance name), and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] status change from Offline to Online Pending, and then to Online.</span></span>  
  
8.  <span data-ttu-id="4c4fe-122">關閉 [容錯移轉叢集管理員] 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="4c4fe-122">Close the Failover Cluster Manager snap-in.</span></span>  
  
  
