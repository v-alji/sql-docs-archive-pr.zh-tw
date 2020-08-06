---
title: 第2課：依排程評估最佳作法原則 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 37ffad63-d6db-4609-8deb-786200659554
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a454e38ec2f07bf9867183a3894ac4ea001a942e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593725"
---
# <a name="lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis"></a><span data-ttu-id="10c85-102">第 2 課：根據排程評估最佳做法原則</span><span class="sxs-lookup"><span data-stu-id="10c85-102">Lesson 2: Evaluate Best Practices Policies on a Scheduled Basis</span></span>
  <span data-ttu-id="10c85-103">您可以針對 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的一個或多個執行個體，設定最佳作法原則的排程評估。</span><span class="sxs-lookup"><span data-stu-id="10c85-103">You can configure scheduled evaluations of best practices policies on one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="10c85-104">若要設定最佳做法原則根據排程執行，您必須將原則匯入至目標執行個體。</span><span class="sxs-lookup"><span data-stu-id="10c85-104">To configure best practices policies to run on a scheduled basis, you must import the policies into the target instance.</span></span>  
  
 <span data-ttu-id="10c85-105">若要將排程的原則部署至多個伺服器，您可以將原則匯入至一個執行個體、設定每個原則的排程、將排程的原則匯出至資料夾，然後透過已註冊的伺服器，將排程的原則部署至目標執行個體。</span><span class="sxs-lookup"><span data-stu-id="10c85-105">To deploy scheduled policies to multiple servers, you can import the policies to one instance, configure the schedules for each policy, export the scheduled policies to a folder, and then deploy the scheduled policies to target instances through Registered Servers.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="10c85-106">目標執行個體必須執行 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="10c85-106">The target instances must be running [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] or a later version.</span></span> <span data-ttu-id="10c85-107">若要進行自動化作業，原則必須儲存在本機的執行個體中，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 版本不支援此執行個體。</span><span class="sxs-lookup"><span data-stu-id="10c85-107">Automation requires the policies to be stored locally on the instance, which is not supported by versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that are earlier than [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="10c85-108">在這一課，您將進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="10c85-108">In this lesson, you will do the following:</span></span>  
  
-   <span data-ttu-id="10c85-109">將最佳做法原則匯入至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="10c85-109">Import the best practices policies into an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="10c85-110">設定原則根據排程執行。</span><span class="sxs-lookup"><span data-stu-id="10c85-110">Configure the policies to run on a schedule.</span></span>  
  
-   <span data-ttu-id="10c85-111">將排程的最佳做法原則透過已註冊的伺服器，部署至多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="10c85-111">Deploy the scheduled best practices policies to multiple instances through Registered Servers.</span></span>  
  
 <span data-ttu-id="10c85-112">這個課程包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="10c85-112">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="10c85-113">將原則匯入至單一執行個體</span><span class="sxs-lookup"><span data-stu-id="10c85-113">Import the Policies to a Single Instance</span></span>](../../2014/tutorials/import-the-policies-to-a-single-instance.md)  
  
-   [<span data-ttu-id="10c85-114">排程原則</span><span class="sxs-lookup"><span data-stu-id="10c85-114">Schedule the Policies</span></span>](../../2014/tutorials/schedule-the-policies.md)  
  
-   [<span data-ttu-id="10c85-115">將已排程的原則部署至多個執行個體</span><span class="sxs-lookup"><span data-stu-id="10c85-115">Deploy Scheduled Policies to Multiple Instances</span></span>](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
## <a name="see-also"></a><span data-ttu-id="10c85-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10c85-116">See Also</span></span>  
 [<span data-ttu-id="10c85-117">使用中央管理伺服器管理多部伺服器</span><span class="sxs-lookup"><span data-stu-id="10c85-117">Administer Multiple Servers Using Central Management Servers</span></span>](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
