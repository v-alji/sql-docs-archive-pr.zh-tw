---
title: 連接到 Azure 儲存體 (還原) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restore.connectstorage.f1
ms.assetid: c0b7d7c8-b878-4b7f-8120-d0c6917b583f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dff9730d6592381b1c8e8a1cf7ee45ad7532a440
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606916"
---
# <a name="connect-to-azure-storage-restore"></a><span data-ttu-id="c5d9c-102">連線到 Azure 儲存體 (還原)</span><span class="sxs-lookup"><span data-stu-id="c5d9c-102">Connect to Azure Storage (Restore)</span></span>
  <span data-ttu-id="c5d9c-103">此對話方塊可讓您指定 Azure 儲存體帳戶資訊的連線，以擷取儲存在 Azure 儲存體帳戶中的檔案。</span><span class="sxs-lookup"><span data-stu-id="c5d9c-103">The dialog box allows you to specify the connection to Azure storage account information in order to retrieve the files storage in the Azure storage account.</span></span> <span data-ttu-id="c5d9c-104">指定必要資訊之後，按一下 [連接]  建立 Azure 儲存體的連線。</span><span class="sxs-lookup"><span data-stu-id="c5d9c-104">After specifying the required information, click **Connect** to establish the connection to Azure storage.</span></span>  
  
## <a name="azure-storage-account"></a><span data-ttu-id="c5d9c-105">Azure 儲存體帳戶</span><span class="sxs-lookup"><span data-stu-id="c5d9c-105">Azure Storage Account</span></span>  
 <span data-ttu-id="c5d9c-106">**儲存體帳戶**</span><span class="sxs-lookup"><span data-stu-id="c5d9c-106">**Storage account**</span></span>  
 <span data-ttu-id="c5d9c-107">選取、輸入或貼上您想要使用的 Azure 儲存體帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="c5d9c-107">Select, type or paste the name of the Azure storage account you want to use.</span></span> <span data-ttu-id="c5d9c-108">下拉式方塊會列出先前使用的帳戶。</span><span class="sxs-lookup"><span data-stu-id="c5d9c-108">The drop down box lists the accounts previously used.</span></span>  
  
 <span data-ttu-id="c5d9c-109">**帳戶金鑰**</span><span class="sxs-lookup"><span data-stu-id="c5d9c-109">**Account key**</span></span>  
 <span data-ttu-id="c5d9c-110">指定 Azure 儲存體帳戶存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="c5d9c-110">Specify the Azure storage account access key.</span></span>  
  
 <span data-ttu-id="c5d9c-111">[使用安全端點 (HTTPS)]  核取方塊</span><span class="sxs-lookup"><span data-stu-id="c5d9c-111">**Use secure endpoints (HTTPS)** check box</span></span>  
 <span data-ttu-id="c5d9c-112">選取此選項，以確保 Azure 儲存體的安全連線 (建議使用)。</span><span class="sxs-lookup"><span data-stu-id="c5d9c-112">Select this option to make a secure connection to Azure storage - recommended.</span></span>  
  
 <span data-ttu-id="c5d9c-113">[儲存帳戶金鑰]  核取方塊</span><span class="sxs-lookup"><span data-stu-id="c5d9c-113">**Save account key** check box</span></span>  
 <span data-ttu-id="c5d9c-114">如果您想要 SQL Server 記住此儲存體帳戶的存取金鑰，請選取此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c5d9c-114">Select this check box if you want SQL Server to remember the access key for this storage account.</span></span>  
  
### <a name="sql-credential"></a><span data-ttu-id="c5d9c-115">SQL 認證</span><span class="sxs-lookup"><span data-stu-id="c5d9c-115">SQL Credential</span></span>  
 <span data-ttu-id="c5d9c-116">**選取現有認證**</span><span class="sxs-lookup"><span data-stu-id="c5d9c-116">**Select an existing credential**</span></span>  
 <span data-ttu-id="c5d9c-117">選取符合儲存體帳戶和帳戶金鑰資訊的現有 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="c5d9c-117">Select an existing SQL Credential that matches the storage account and account key information.</span></span>  
  
 <span data-ttu-id="c5d9c-118">**建立新認證**</span><span class="sxs-lookup"><span data-stu-id="c5d9c-118">**Create a new Credential**</span></span>  
 <span data-ttu-id="c5d9c-119">選取此選項，以使用儲存體帳戶和帳戶金鑰資訊建立新認證。</span><span class="sxs-lookup"><span data-stu-id="c5d9c-119">Select this option to create a new credential using the storage account and account key information.</span></span> <span data-ttu-id="c5d9c-120">在 [認證名稱]  欄位中指定新認證的名稱。</span><span class="sxs-lookup"><span data-stu-id="c5d9c-120">Specify the name of the new credential in the **Credential Name** field.</span></span>  
  
  
