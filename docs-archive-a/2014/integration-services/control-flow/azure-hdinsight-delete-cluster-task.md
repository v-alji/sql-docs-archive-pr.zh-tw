---
title: Azure HDInsight 刪除叢集工作 | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpdelcltask.f1
- sql11.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
author: chugugrace
ms.author: chugu
ms.openlocfilehash: db0a15aaea37c6d18c1d3c2136e0fd0c94eb7506
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599135"
---
# <a name="azure-hdinsight-delete-cluster-task"></a><span data-ttu-id="52cd0-102">Azure HDInsight 刪除叢集工作</span><span class="sxs-lookup"><span data-stu-id="52cd0-102">Azure HDInsight Delete Cluster Task</span></span>
<span data-ttu-id="52cd0-103">**Azure HDInsight 刪除叢集工作**可讓 SSIS 套件刪除指定之 Azure 訂用帳戶和資源群組中的 Azure HDInsight 叢集。</span><span class="sxs-lookup"><span data-stu-id="52cd0-103">The **Azure HDInsight Delete Cluster Task** enables an SSIS package to delete an Azure HDInsight cluster in the specified Azure subscription and resource group.</span></span>
  
> [!NOTE]
> <span data-ttu-id="52cd0-104">刪除 HDInsight 叢集可能需要 10~20 分鐘。</span><span class="sxs-lookup"><span data-stu-id="52cd0-104">Deleting an HDInsight cluster may take 10~20 minutes.</span></span>  
  
<span data-ttu-id="52cd0-105">若要加入 **Azure HDInsight 刪除叢集工作**，請將其拖放至 SSIS 設計工具，並按兩下或在其上按一下滑鼠右鍵，然後按一下 [編輯] \*\*\*\* ，即可看到以下 [Azure HDInsight 刪除叢集工作編輯器] \*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="52cd0-105">To add an **Azure HDInsight Delete Cluster Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure HDInsight Delete Cluster Task Editor** dialog box.</span></span>  
  
<span data-ttu-id="52cd0-106">下表提供此對話方塊中欄位的描述。</span><span class="sxs-lookup"><span data-stu-id="52cd0-106">The following table provides a description for the fields in the dialog box.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="52cd0-107">**欄位**</span><span class="sxs-lookup"><span data-stu-id="52cd0-107">**Field**</span></span>|<span data-ttu-id="52cd0-108">**說明**</span><span class="sxs-lookup"><span data-stu-id="52cd0-108">**Description**</span></span>|  
|<span data-ttu-id="52cd0-109">AzureResourceManagerConnection</span><span class="sxs-lookup"><span data-stu-id="52cd0-109">AzureResourceManagerConnection</span></span>|<span data-ttu-id="52cd0-110">選取現有的 Azure Resource Manager 連線管理員或建立新的連線管理員，以用來刪除 HDInsight 叢集。</span><span class="sxs-lookup"><span data-stu-id="52cd0-110">Select an existing Azure Resource Manager Connection Manager or create a new one that will be used to delete the HDInsight cluster.</span></span>|
|<span data-ttu-id="52cd0-111">SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="52cd0-111">SubscriptionId</span></span>|<span data-ttu-id="52cd0-112">指定 HDInsight 叢集所在的訂用帳戶 ID。</span><span class="sxs-lookup"><span data-stu-id="52cd0-112">Specify the ID of the subscription the HDInsight cluster is in.</span></span>|
|<span data-ttu-id="52cd0-113">ResourceGroup</span><span class="sxs-lookup"><span data-stu-id="52cd0-113">ResourceGroup</span></span>|<span data-ttu-id="52cd0-114">指定 HDInsight 叢集所在的 Azure 資源群組。</span><span class="sxs-lookup"><span data-stu-id="52cd0-114">Specify the Azure resource group the HDInsight cluster is in.</span></span>|
|<span data-ttu-id="52cd0-115">ClusterName</span><span class="sxs-lookup"><span data-stu-id="52cd0-115">ClusterName</span></span>|<span data-ttu-id="52cd0-116">指定要刪除之叢集的名稱。</span><span class="sxs-lookup"><span data-stu-id="52cd0-116">Specify the name of the cluster to be deleted.</span></span>|  
|<span data-ttu-id="52cd0-117">FailIfNotExists</span><span class="sxs-lookup"><span data-stu-id="52cd0-117">FailIfNotExists</span></span>|<span data-ttu-id="52cd0-118">指定若叢集不存在則工作是否會失敗。</span><span class="sxs-lookup"><span data-stu-id="52cd0-118">Specify whether the task should fail if the cluster does not exist.</span></span>|
