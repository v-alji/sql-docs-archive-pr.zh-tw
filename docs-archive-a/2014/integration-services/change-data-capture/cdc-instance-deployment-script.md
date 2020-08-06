---
title: CDC 執行個體部署指令碼 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8fa82822-ac99-48ef-a18d-f4f3a77105b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6deea884168c2329e312eeaa2be16c28a955cca3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708558"
---
# <a name="cdc-instance-deployment-script"></a><span data-ttu-id="332e1-102">CDC 執行個體部署指令碼</span><span class="sxs-lookup"><span data-stu-id="332e1-102">CDC Instance Deployment Script</span></span>
  <span data-ttu-id="332e1-103">顯示 CDC 執行個體部署指令碼的 [CDC 執行個體部署指令碼] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="332e1-103">The CDC Instance Deployment Script dialog box that displays the CDC instance deployment script.</span></span> <span data-ttu-id="332e1-104">此指令碼可用來重新建立 CDC 資料庫，並將其所有成品放在另一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上。</span><span class="sxs-lookup"><span data-stu-id="332e1-104">This script can be used to re-create the CDC database with all of its artifacts on a different [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="332e1-105">在完成部署指令碼之後，您應該確定以下事項：</span><span class="sxs-lookup"><span data-stu-id="332e1-105">At the completion of the deployment script, you should make sure of the following:</span></span>  
  
-   <span data-ttu-id="332e1-106">部署指令碼假設已針對 Oracle CDC 準備好目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，其方式是使用 Oracle CDC 服務組態主控台，或是使用程式所建立的 **[準備指令碼]** 。</span><span class="sxs-lookup"><span data-stu-id="332e1-106">The deployment script assumes that the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance was prepared for Oracle CDC, by using the Oracle CDC Service Configuration Console or by using **prepare script** that program creates.</span></span>  
  
-   <span data-ttu-id="332e1-107">用來啟用 CDC 之資料庫的部分指令碼必須由 `sysadmin`執行。</span><span class="sxs-lookup"><span data-stu-id="332e1-107">The part of the script that is used to enable the database for CDC needs to be run by a `sysadmin`.</span></span>  
  
-   <span data-ttu-id="332e1-108">此指令碼不會保留 Oracle 記錄採礦密碼。</span><span class="sxs-lookup"><span data-stu-id="332e1-108">The script does not preserve the Oracle log-mining password.</span></span> <span data-ttu-id="332e1-109">在執行指令碼及啟動 Oracle CDC 服務之後，需要手動設定這個選項。</span><span class="sxs-lookup"><span data-stu-id="332e1-109">This needs to be set manually after the script is run and the Oracle CDC Service is started.</span></span>  
  
 <span data-ttu-id="332e1-110">在 **[CDC 執行個體部署指令碼]** 對話方塊中選取以下選項。</span><span class="sxs-lookup"><span data-stu-id="332e1-110">Select the following options in the **CDC Instance Deployment Script** dialog box.</span></span>  
  
 <span data-ttu-id="332e1-111">**另存新檔**</span><span class="sxs-lookup"><span data-stu-id="332e1-111">**Save As**</span></span>  
 <span data-ttu-id="332e1-112">將指令碼以文字檔格式儲存在您想要儲存的任何位置。</span><span class="sxs-lookup"><span data-stu-id="332e1-112">Saves the script in a text file that you can save in any location you want.</span></span> <span data-ttu-id="332e1-113">您可以將包含指令碼的檔案複製到其他任何伺服器上，並在該處執行。</span><span class="sxs-lookup"><span data-stu-id="332e1-113">You can copy the file with the script to any other server to run it there.</span></span>  
  
 <span data-ttu-id="332e1-114">**複製**</span><span class="sxs-lookup"><span data-stu-id="332e1-114">**Copy**</span></span>  
 <span data-ttu-id="332e1-115">將指令碼複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="332e1-115">Copies the script to the clipboard.</span></span> <span data-ttu-id="332e1-116">然後您可以將指令碼貼到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或任何文字編輯器中，於日後執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="332e1-116">You can then paste the script into the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or any text editor to run the scripts later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="332e1-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="332e1-117">See Also</span></span>  
 [<span data-ttu-id="332e1-118">準備 SQL Server 以使用 CDC</span><span class="sxs-lookup"><span data-stu-id="332e1-118">Prepare SQL Server for CDC</span></span>](prepare-sql-server-for-cdc.md)  
  
  
