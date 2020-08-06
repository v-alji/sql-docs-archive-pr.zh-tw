---
title: Azure Resource Manager 連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPARMCM.F1
- SQL11.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: a2380258-0418-4a8c-a731-5071a44ddf1e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1dce4def11f14072295dbf3cde9d5ab77304fe74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596878"
---
# <a name="azure-resource-manager-connection-manager"></a><span data-ttu-id="8abf1-102">Azure Resource Manager 連線管理員</span><span class="sxs-lookup"><span data-stu-id="8abf1-102">Azure Resource Manager Connection Manager</span></span>
<span data-ttu-id="8abf1-103">**Azure Resource Manager 連線管理員** 可讓 SSIS 套件使用[服務主體](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)來管理 Azure 資源。</span><span class="sxs-lookup"><span data-stu-id="8abf1-103">The **Azure Resource Manager Connection Manager** enables an SSIS package to manage Azure resources using a [service principal](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).</span></span>

<span data-ttu-id="8abf1-104">若要建立及設定 **Azure Resource Manager 連線管理員**，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="8abf1-104">To create and configure an **Azure Resource Manager Connection Manager**, follow the steps below:</span></span>

1. <span data-ttu-id="8abf1-105">在 [新增 SSIS 連線管理員]\*\*\*\* 對話方塊中，選取 [AzureResourceManager]\*\*\*\*，然後按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8abf1-105">In the **Add SSIS Connection Manager** dialog box, select **AzureResourceManager**, and click **Add**.</span></span>
2. <span data-ttu-id="8abf1-106">在 [Azure Resource Manager Connection Manager Editor] (Azure Resource Manager 連線管理員編輯器)\*\*\*\* 對話方塊中，指定**應用程式識別碼**、**應用程式金鑰**和**租用戶識別碼**服務主體。</span><span class="sxs-lookup"><span data-stu-id="8abf1-106">In the **Azure Resource Manager Connection Manager Editor** dialog box, specify the **Application ID**, **Application Key**, and **Tenant ID** for the service principal.</span></span> <span data-ttu-id="8abf1-107">如需這些屬性的詳細資訊，請參閱[這篇](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)文章。</span><span class="sxs-lookup"><span data-stu-id="8abf1-107">For details about these properties, please refer to [this](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) article.</span></span>
3. <span data-ttu-id="8abf1-108">按一下 **[確定]** ，關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8abf1-108">Click **OK** to close the dialog box.</span></span>
4. <span data-ttu-id="8abf1-109">您可以在 [屬性] \*\*\*\* 視窗中看到您建立的連線管理員屬性。</span><span class="sxs-lookup"><span data-stu-id="8abf1-109">You can see the properties of the connection manager you created in the **Properties** window.</span></span>
