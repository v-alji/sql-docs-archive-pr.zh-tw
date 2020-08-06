---
title: 建立認證 - 向 Azure 儲存體驗證 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backuptourl.createcred.f1
ms.assetid: 0622619d-27c5-4ff0-83e5-cde31648c27a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: afdbf2647c79e07cf3f190ec6710eeb6b7718f6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707625"
---
# <a name="create-credential---authenticate-to-azure-storage"></a><span data-ttu-id="4a334-102">建立認證 - 向 Azure 儲存體驗證</span><span class="sxs-lookup"><span data-stu-id="4a334-102">Create Credential - Authenticate to Azure Storage</span></span>
  <span data-ttu-id="4a334-103">使用 [備份至 URL - 建立認證]  對話方塊建立新的 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="4a334-103">Use the **Backup to URL - Create Credential** dialog box to create a new SQL Credential.</span></span>  
  
 <span data-ttu-id="4a334-104">使用此對話方塊建立認證時，您必須提供新增至本機憑證存放區的 Azure 管理憑證或下載到電腦上的發行設定檔，以驗證訂用帳戶和儲存體帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="4a334-104">When using this dialog box to create a credential, you must provide an Azure Management Certificate added to the local certificate store or a publishing profile downloaded to your computer to validate the subscription and the storage account information.</span></span>  
  
 <span data-ttu-id="4a334-105">**SQL 認證**</span><span class="sxs-lookup"><span data-stu-id="4a334-105">**SQL Credential**</span></span>  
 <span data-ttu-id="4a334-106">指定您要建立之 SQL 認證的名稱。</span><span class="sxs-lookup"><span data-stu-id="4a334-106">Specify the name of the SQL Credential you want to create.</span></span>  
  
## <a name="azure-credentials"></a><span data-ttu-id="4a334-107">Azure 認證</span><span class="sxs-lookup"><span data-stu-id="4a334-107">Azure Credentials</span></span>  
 <span data-ttu-id="4a334-108">**管理憑證**</span><span class="sxs-lookup"><span data-stu-id="4a334-108">**Management Certificate**</span></span>  
 <span data-ttu-id="4a334-109">使用這個選項可從本機憑證存放區指定憑證，該憑證符合來自 Azure 的管理憑證。</span><span class="sxs-lookup"><span data-stu-id="4a334-109">Use this option to specify a certificate from the local certificate store that matches the management certificate from Azure.</span></span> <span data-ttu-id="4a334-110">如需 Azure 管理憑證的詳細資訊，請參閱[建立及上傳 Azure 的管理憑證](https://go.microsoft.com/fwlink/?LinkId=320781)。</span><span class="sxs-lookup"><span data-stu-id="4a334-110">For more information on Azure management certificate, see [Create and Upload a Management Certificate for Azure](https://go.microsoft.com/fwlink/?LinkId=320781).</span></span>  
  
 <span data-ttu-id="4a334-111">**訂用帳戶**</span><span class="sxs-lookup"><span data-stu-id="4a334-111">**Subscription**</span></span>  
 <span data-ttu-id="4a334-112">選取、輸入或貼上符合本機憑證存放區之管理憑證的 Azure 訂用帳戶識別碼。</span><span class="sxs-lookup"><span data-stu-id="4a334-112">Select, type, or paste your Azure subscription ID that matches the management certificate from the local certificate store.</span></span>  
  
 <span data-ttu-id="4a334-113">**發行設定檔**</span><span class="sxs-lookup"><span data-stu-id="4a334-113">**Publishing Profile**</span></span>  
 <span data-ttu-id="4a334-114">如果您擁有下載到電腦上的發行設定檔，請使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="4a334-114">Use this option if you have a publishing profile downloaded to your computer.</span></span> <span data-ttu-id="4a334-115">如果您使用這個選項，則會自動填入訂閱識別碼和憑證。</span><span class="sxs-lookup"><span data-stu-id="4a334-115">If you use this option, the subscription ID, and the certificate are auto populated.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="4a334-116">SQL Server 目前支援發行設定檔 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="4a334-116">SQL Server currently supports publishing profile version 2.0.</span></span> <span data-ttu-id="4a334-117">若要下載發行設定檔的支援版本，請參閱＜ [下載發行設定檔 2.0](https://go.microsoft.com/fwlink/?LinkId=396421)＞。</span><span class="sxs-lookup"><span data-stu-id="4a334-117">To download the supported version of the publishing profile, see [Download Publishing Profile 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).</span></span>  
  
## <a name="storage-account"></a><span data-ttu-id="4a334-118">儲存體帳戶</span><span class="sxs-lookup"><span data-stu-id="4a334-118">Storage Account</span></span>  
 <span data-ttu-id="4a334-119">選取您想要用來儲存備份檔案的儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="4a334-119">Select the storage account you want to use to store the backup files on.</span></span>  
  
  
