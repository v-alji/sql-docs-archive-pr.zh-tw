---
title: Azure 訂用帳戶連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpsubscrconn.f1
- sql11.dts.designer.afpsubscrconn.f1
ms.assetid: e1225327-c308-4c50-8f44-c411f52ef378
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bff1286525983b32c2191f1f8864a0f2bef0e6b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596225"
---
# <a name="azure-subscription-connection-manager"></a><span data-ttu-id="d9a65-102">Azure 訂用帳戶連線管理員</span><span class="sxs-lookup"><span data-stu-id="d9a65-102">Azure Subscription Connection Manager</span></span>
  <span data-ttu-id="d9a65-103">Azure HDInsight 連線管理員可使用您指定的屬性值，即 Azure 訂用帳戶識別碼和管理憑證，讓 SSIS 封裝連線到 Azure 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="d9a65-103">The Azure HDInsight connection manager enables an SSIS package to connect to an Azure subscription by using the values you specify for the properties: Azure Subscription ID and Management Certificate.</span></span>

1.  <span data-ttu-id="d9a65-104">在上方顯示的 [加入 SSIS 連線管理員]\*\*\*\* 對話方塊中，選取 [Azure 訂用帳戶]\*\*\*\*，然後按一下 [加入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d9a65-104">In the **Add SSIS Connection Manager** dialog box shown above, you select **Azure Subscription**, and click **Add**.</span></span>  <span data-ttu-id="d9a65-105">[Azure Subscription Connection Manager Editor (Azure 訂用帳戶連線管理員編輯器)]\*\*\*\* 對話方塊應會隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d9a65-105">You should see the following **Azure Subscription Connection Manager Editor** dialog box.</span></span>

     <span data-ttu-id="d9a65-106">![SSIS-AzureSubscriptionManager](../media/ssis-azuresubscriptionmanager.png "SSIS-AzureSubscriptionManager")</span><span class="sxs-lookup"><span data-stu-id="d9a65-106">![SSIS-AzureSubscriptionManager](../media/ssis-azuresubscriptionmanager.png "SSIS-AzureSubscriptionManager")</span></span>

2.  <span data-ttu-id="d9a65-107">在 [Azure 訂用帳戶識別碼]\*\*\*\* 輸入可唯一識別 Azure 訂用帳戶的 Azure 訂用帳戶識別碼。</span><span class="sxs-lookup"><span data-stu-id="d9a65-107">Enter your Azure subscription ID, which uniquely identifies an Azure subscription, for the **Azure subscription ID**.</span></span>  <span data-ttu-id="d9a65-108">可以在 [設定]\*\*\*\* 頁面下的 [Azure 管理入口網站](https://manage.windowsazure.com)找到此值：</span><span class="sxs-lookup"><span data-stu-id="d9a65-108">The value can be found on the [Azure Management Portal](https://manage.windowsazure.com) under **Settings** page:</span></span>

     <span data-ttu-id="d9a65-109">![SSIS-AzureSettings-SubscriptionID](../media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")</span><span class="sxs-lookup"><span data-stu-id="d9a65-109">![SSIS-AzureSettings-SubscriptionID](../media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")</span></span>

3.  <span data-ttu-id="d9a65-110">從下拉式清單中選擇 [Management certificate store location (管理憑證存放區位置)]\*\*\*\* 和 [Management certificate store name (管理憑證存放區名稱)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d9a65-110">Choose **Management certificate store location** and **Management certificate store name** from the drop-down lists.</span></span>

4.  <span data-ttu-id="d9a65-111">輸入 [管理憑證指紋]\*\*\*\*，或按一下 [瀏覽...]\*\*\*\* 可從選取的存放區選擇憑證。</span><span class="sxs-lookup"><span data-stu-id="d9a65-111">Enter **Management certificate thumbprint** or click the **Browse...** to choose a certificate from the selected store.</span></span> <span data-ttu-id="d9a65-112">憑證必須上傳為訂用帳戶的管理憑證。</span><span class="sxs-lookup"><span data-stu-id="d9a65-112">The certificate must be uploaded as a management certificate for the subscription.</span></span> <span data-ttu-id="d9a65-113">若要這樣做，請按一下 Azure 入口網站下一個頁面上的 [上傳]\*\*\*\* (如需詳細資訊，請參閱此 [MSDN 文章](https://msdn.microsoft.com/library/azure/gg551722.aspx))。</span><span class="sxs-lookup"><span data-stu-id="d9a65-113">To do so, click **Upload** on the following page of the Azure Portal (see this [MSDN post](https://msdn.microsoft.com/library/azure/gg551722.aspx) for more detail).</span></span>

     <span data-ttu-id="d9a65-114">![SSIS-AzureSettings-ManagementCertificate](../media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")</span><span class="sxs-lookup"><span data-stu-id="d9a65-114">![SSIS-AzureSettings-ManagementCertificate](../media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")</span></span>

5.  <span data-ttu-id="d9a65-115">按一下 [**測試連接**] 來測試連接。</span><span class="sxs-lookup"><span data-stu-id="d9a65-115">Click **Test Connection** to test the connection.</span></span>

6.  <span data-ttu-id="d9a65-116">按一下 **[確定]** ，關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d9a65-116">Click **OK** to close the dialog box.</span></span>


