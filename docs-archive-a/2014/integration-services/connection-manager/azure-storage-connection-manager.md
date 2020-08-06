---
title: Azure 儲存體連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpstorageconn.f1
- sql11.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 47580d8d1d961df9fbcbed0bd7164f1c54792b86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596230"
---
# <a name="azure-storage-connection-manager"></a><span data-ttu-id="2f6b4-102">Azure 儲存體連線管理員</span><span class="sxs-lookup"><span data-stu-id="2f6b4-102">Azure Storage Connection Manager</span></span>
  <span data-ttu-id="2f6b4-103">Azure 儲存體連線管理員可讓 SSIS 封裝使用您指定的屬性值連接到 Azure 儲存體帳戶︰儲存體帳戶名稱和帳戶金鑰。</span><span class="sxs-lookup"><span data-stu-id="2f6b4-103">The Azure Storage connection manager enables an SSIS package to connect to an Azure Storage account by using the values you specify for the properties: Storage Account Name and Account Key.</span></span>  
  
1.  <span data-ttu-id="2f6b4-104">在 [加入 SSIS 連線管理員]\*\*\*\* 對話方塊中，選取 [AzureStorage]\*\*\*\*，然後按一下 [加入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f6b4-104">In the **Add SSIS Connection Manager** dialog box, select **AzureStorage**, and click **Add**.</span></span>  
  
2.  <span data-ttu-id="2f6b4-105">在 [Azure 儲存體連線管理員編輯器] 對話方塊中，選擇 [使用 Azure 帳戶]\*\*\*\* 透過網際網路連接至 Azure 儲存體服務，或選擇 [使用本機開發人員帳戶]\*\*\*\* 連接至 Azure 儲存體模擬器裝載的本機服務。</span><span class="sxs-lookup"><span data-stu-id="2f6b4-105">In the Azure Storage Connection Manager Editor dialog box, choose **Use Azure account** to connect to an Azure Storage Service via internet or choose **Use local developer account** to connect to the local service hosted by the Azure Storage Emulator.</span></span>  
  
3.  <span data-ttu-id="2f6b4-106">如已選取 [使用 Azure 帳戶]\*\*\*\* 選項，請執行下列動作︰</span><span class="sxs-lookup"><span data-stu-id="2f6b4-106">If you selected **Use Azure account** option, do the following:</span></span>  
  
    1.  <span data-ttu-id="2f6b4-107">指定 [儲存體帳戶名稱]\*\*\*\* 和 [帳戶金鑰]\*\*\*\* 欄位的值。</span><span class="sxs-lookup"><span data-stu-id="2f6b4-107">Specify values for the **Storage account name** and **Account key** field.</span></span> <span data-ttu-id="2f6b4-108">這些值會儲存為 SSIS 封裝中的機密資料。</span><span class="sxs-lookup"><span data-stu-id="2f6b4-108">These values will be stored as sensitive data in SSIS package.</span></span>  
  
    2.  <span data-ttu-id="2f6b4-109">如果您想要使用 HTTPS 而非 HTTP連接到 Azure 儲存體服務，請選取 [使用 HTTPS]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f6b4-109">Select **Use HTTPS** if you want to use HTTPS instead of HTTP to connect to the Azure Storage Service.</span></span>  
  
4.  <span data-ttu-id="2f6b4-110">按一下 **[確定]** ，關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2f6b4-110">Click **OK** to close the dialog box.</span></span>  
  
5.  <span data-ttu-id="2f6b4-111">您可以在 [屬性] \*\*\*\* 視窗中看到您建立的連線管理員屬性。</span><span class="sxs-lookup"><span data-stu-id="2f6b4-111">You can see the properties of the connection manager you created in the **Properties** window.</span></span>  
  
  
