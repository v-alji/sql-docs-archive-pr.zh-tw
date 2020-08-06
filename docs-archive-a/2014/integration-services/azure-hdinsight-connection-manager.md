---
title: Azure HDInsight 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPHDICM.F1
- SQL11.DTS.DESIGNER.AFPHDICM.F1
ms.assetid: 850a978d-5dba-45b6-a10e-306aafbc353d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0eaf2f57fec50a58ad1b7e7578407fb6cf3fa0c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687131"
---
# <a name="azure-hdinsight-connection-manager"></a><span data-ttu-id="aa369-102">Azure HDInsight 連線管理員</span><span class="sxs-lookup"><span data-stu-id="aa369-102">Azure HDInsight Connection Manager</span></span>
<span data-ttu-id="aa369-103">**Azure HDInsight 連線管理員**可讓 SSIS 套件連線到 Azure HDInsight 叢集。</span><span class="sxs-lookup"><span data-stu-id="aa369-103">The **Azure HDInsight Connection Manager** enables an SSIS package to connect to an Azure HDInsight cluster.</span></span>

<span data-ttu-id="aa369-104">若要建立及設定 **Azure HDInsight 連線管理員**，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="aa369-104">To create and configure an **Azure HDInsight Connection Manager**, follow the steps below:</span></span>

1. <span data-ttu-id="aa369-105">在 [新增 SSIS 連線管理員]\*\*\*\* 對話方塊中，選取 [AzureHDInsight]\*\*\*\*，然後按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aa369-105">In the **Add SSIS Connection Manager** dialog box, select **AzureHDInsight**, and click **Add**.</span></span>
2. <span data-ttu-id="aa369-106">在 [Azure HDInsight Connection Manager Editor] (Azure HDInsight 連線管理員編輯器)\*\*\*\* 對話方塊中，指定 HDInsight 叢集要連線的**叢集 DNS 名稱** (前面不加上通訊協定)、**使用者名稱**和**密碼**。</span><span class="sxs-lookup"><span data-stu-id="aa369-106">In the **Azure HDInsight Connection Manager Editor** dialog box, specify the **Cluster DNS name** (without the protocol prefix), **Username**, and **Password** for the HDInsight cluster to connect to.</span></span>
3. <span data-ttu-id="aa369-107">按一下 **[確定]** ，關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="aa369-107">Click **OK** to close the dialog box.</span></span>
4. <span data-ttu-id="aa369-108">您可以在 [屬性] \*\*\*\* 視窗中看到您建立的連線管理員屬性。</span><span class="sxs-lookup"><span data-stu-id="aa369-108">You can see the properties of the connection manager you created in the **Properties** window.</span></span>
