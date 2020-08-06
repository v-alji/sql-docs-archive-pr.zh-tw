---
title: 第 2 課： 在容器上建立原則並產生共用存取簽章 (SAS) 金鑰 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 41674d9d-8132-4bff-be4d-85a861419f3d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab209f08d53b25a4791ef675e6fb6b78cab115f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707529"
---
# <a name="lesson-2-create-a-policy-on-container-and-generate-a-shared-access-signature-sas-key"></a><span data-ttu-id="67d57-103">第 2 課：</span><span class="sxs-lookup"><span data-stu-id="67d57-103">Lesson 2.</span></span> <span data-ttu-id="67d57-104">在容器上建立原則並產生共用存取簽章 (SAS) 金鑰</span><span class="sxs-lookup"><span data-stu-id="67d57-104">Create a policy on container and generate a Shared Access Signature (SAS) key</span></span>
  <span data-ttu-id="67d57-105">在這一課，您將學習如何在 Blob 容器上建立原則以及產生 SAS 金鑰。</span><span class="sxs-lookup"><span data-stu-id="67d57-105">In this lesson, you will learn how to create a policy on the Blob container and also generate a SAS key.</span></span>  
  
 <span data-ttu-id="67d57-106">預存的存取原則可對伺服器端的共用存取簽章提供一層額外的控制。</span><span class="sxs-lookup"><span data-stu-id="67d57-106">A stored access policy provides an additional level of control over shared access signatures on the server side.</span></span> <span data-ttu-id="67d57-107">共用存取簽章是一個 URI，會將有限的存取權限授與容器、Blob、佇列和資料表。</span><span class="sxs-lookup"><span data-stu-id="67d57-107">A shared access signature is a URI that grants restricted access rights to containers, blobs, queues, and tables.</span></span> <span data-ttu-id="67d57-108">使用這項新的增強功能時，您需要在容器上建立具有讀取、寫入和列出權限的原則。</span><span class="sxs-lookup"><span data-stu-id="67d57-108">When using this new enhancement, you need to create a policy on a container with read, write, and list rights.</span></span>  
  
 <span data-ttu-id="67d57-109">您可以使用下列其中一種方法建立原則和共用存取簽章：</span><span class="sxs-lookup"><span data-stu-id="67d57-109">You can create a policy and a shared access signature by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="67d57-110">Azure REST API 作業：[建立容器](https://msdn.microsoft.com/library/azure/dd179468.aspx)、[設定容器 Acl](https://msdn.microsoft.com/library/azure/dd179391.aspx)和[取得容器 acl](https://msdn.microsoft.com/library/azure/dd179469.aspx)。</span><span class="sxs-lookup"><span data-stu-id="67d57-110">Azure REST API operations: [Create Container](https://msdn.microsoft.com/library/azure/dd179468.aspx), [Set Container ACL](https://msdn.microsoft.com/library/azure/dd179391.aspx), and [Get Container ACL](https://msdn.microsoft.com/library/azure/dd179469.aspx).</span></span>  
  
-   <span data-ttu-id="67d57-111">Azure SDK 中的[CloudBlobContainer Cloudblobcontainer.getsharedaccesssignature 方法](https://docs.microsoft.com/dotnet/api/microsoft.azure.storage.blob.cloudblobcontainer.getsharedaccesssignature)。</span><span class="sxs-lookup"><span data-stu-id="67d57-111">[CloudBlobContainer.GetSharedAccessSignature Method](https://docs.microsoft.com/dotnet/api/microsoft.azure.storage.blob.cloudblobcontainer.getsharedaccesssignature) in the Azure SDK.</span></span>  
  
    ```  
  
       string signature = blob.GetSharedAccessSignature(new SharedAccessPolicy()   
        {   
            // Specify the expiration time for the signature.   
            SharedAccessExpiryTime = DateTime.Now.Years(1),   
            // Specify the permissions granted by the signature.    
            Permissions = SharedAccessPermissions.Write | SharedAccessPermissions.Read   
        });  
  
    ```  
  
-   <span data-ttu-id="67d57-112">協力廠商的 Azure explorer 工具，例如[Azure 儲存體總管](https://azurestorageexplorer.codeplex.com/)。</span><span class="sxs-lookup"><span data-stu-id="67d57-112">A third-party Azure explorer tool, such as [Azure Storage Explorer](https://azurestorageexplorer.codeplex.com/).</span></span>  
  
 <span data-ttu-id="67d57-113">**下一課：**</span><span class="sxs-lookup"><span data-stu-id="67d57-113">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="67d57-114">第 3 課：建立 SQL Server 認證</span><span class="sxs-lookup"><span data-stu-id="67d57-114">Lesson 3: Create a SQL Server Credential</span></span>](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
