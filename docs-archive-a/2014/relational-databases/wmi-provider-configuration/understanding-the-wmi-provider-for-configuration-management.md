---
title: 瞭解設定管理的 WMI 提供者 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management, operations supported
ms.assetid: 92323972-7943-4208-bbf4-050774fb6027
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0f4f38265093fdb0c27d6bd49ff64ba4b572111e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584306"
---
# <a name="understanding-the-wmi-provider-for-configuration-management"></a><span data-ttu-id="ea44f-102">了解用於組態管理的 WMI 提供者</span><span class="sxs-lookup"><span data-stu-id="ea44f-102">Understanding the WMI Provider for Configuration Management</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="ea44f-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]提供設定管理的 WMI 提供者。</span><span class="sxs-lookup"><span data-stu-id="ea44f-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides the WMI Provider for Configuration Management.</span></span> <span data-ttu-id="ea44f-104">這可讓您使用 Windows Management Instrumentation (WMI) 管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端與伺服器的網路設定，以及伺服器別名。</span><span class="sxs-lookup"><span data-stu-id="ea44f-104">This lets you use Windows Management Instrumentation (WMI) to manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client and server network settings, and server aliases.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="ea44f-105">服務、網路設定和別名是由電腦的 root\Microsoft\SqlServer\ComputerManagement*nn*命名空間中的 WMI 物件所代表。</span><span class="sxs-lookup"><span data-stu-id="ea44f-105">services, network settings, and aliases are represented by WMI objects in the root\Microsoft\SqlServer\ComputerManagement*nn* namespace of the computer.</span></span> <span data-ttu-id="ea44f-106">在指定的電腦上建立與 WMI 提供者的連接之後，可以使用 WQL 或指令碼語言查詢服務、網路設定與別名。</span><span class="sxs-lookup"><span data-stu-id="ea44f-106">After a connection is established with the WMI provider on the specified computer, the services, network settings, and aliases can be queried using WQL or a scripting language.</span></span>  
  
 <span data-ttu-id="ea44f-107">WMI 提供者是執行個體提供者。</span><span class="sxs-lookup"><span data-stu-id="ea44f-107">The WMI Provider is an instance provider.</span></span> <span data-ttu-id="ea44f-108">它會提供[WMI 類別](../wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md)的實例，並支援下列非同步作業。</span><span class="sxs-lookup"><span data-stu-id="ea44f-108">It supplies instances of the [WMI Classes](../wmi-provider-configuration-classes/wmi-provider-for-configuration-management-classes.md) and supports the following asynchronous operations.</span></span>  
  
 <span data-ttu-id="ea44f-109">執行個體擷取</span><span class="sxs-lookup"><span data-stu-id="ea44f-109">Instance retrieval</span></span>  
 <span data-ttu-id="ea44f-110">擷取特定類別類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea44f-110">Retrieval of a particular class type instance.</span></span>  
  
 <span data-ttu-id="ea44f-111">列舉型別</span><span class="sxs-lookup"><span data-stu-id="ea44f-111">Enumeration</span></span>  
 <span data-ttu-id="ea44f-112">列舉類別類型的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea44f-112">Enumeration of all instances of a class type.</span></span>  
  
 <span data-ttu-id="ea44f-113">修改</span><span class="sxs-lookup"><span data-stu-id="ea44f-113">Modification</span></span>  
 <span data-ttu-id="ea44f-114">修改類別類型的特定執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea44f-114">Modification of a particular instance of a class type.</span></span>  
  
 <span data-ttu-id="ea44f-115">類別所擁有的方法允許修改其屬性。</span><span class="sxs-lookup"><span data-stu-id="ea44f-115">Classes have methods that allow the modification of their properties.</span></span>  
  
 <span data-ttu-id="ea44f-116">刪除</span><span class="sxs-lookup"><span data-stu-id="ea44f-116">Deletion</span></span>  
 <span data-ttu-id="ea44f-117">移除類別類型的特定執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea44f-117">Removing a particular instance of a class type.</span></span>  
  
 <span data-ttu-id="ea44f-118">查詢處理</span><span class="sxs-lookup"><span data-stu-id="ea44f-118">Query processing</span></span>  
 <span data-ttu-id="ea44f-119">根據篩選器列舉類別類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea44f-119">Enumeration of instances of a class type based on a filter.</span></span>  
  
 <span data-ttu-id="ea44f-120">如需使用 WMI 提供者進行設定管理的管理應用程式範例，請參閱搭配[Wmi 提供者使用 WQL 和指令碼語言來進行設定管理](using-wql-and-scripting-languages-with-the-wmi-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="ea44f-120">For examples of management application using the WMI Provider for Configuration Management, see [Using WQL and Scripting Languages with the WMI Provider for Configuration Management](using-wql-and-scripting-languages-with-the-wmi-provider.md).</span></span>  
  
 <span data-ttu-id="ea44f-121">如需有關使用 WMI 提供者進行程式設計管理應用程式的詳細資訊，請參閱 .NET Framework SDK 中的 WMI 檔 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ea44f-121">For more information about programming management applications using the WMI Provider, see the WMI documentation in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework SDK.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea44f-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea44f-122">See Also</span></span>  
 <span data-ttu-id="ea44f-123">[使用 WMI 提供者進行設定管理](working-with-the-wmi-provider-for-configuration-management.md) </span><span class="sxs-lookup"><span data-stu-id="ea44f-123">[Working with the WMI Provider for Configuration Management](working-with-the-wmi-provider-for-configuration-management.md) </span></span>  
 [<span data-ttu-id="ea44f-124">搭配組態管理的 WMI 提供者使用 WQL 與指令碼語言</span><span class="sxs-lookup"><span data-stu-id="ea44f-124">Using WQL and Scripting Languages with the WMI Provider for Configuration Management</span></span>](using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
