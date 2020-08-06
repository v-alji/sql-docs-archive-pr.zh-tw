---
title: 安裝類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 0420c555-7a3b-42b9-8651-0b4f5bcb0008
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: bab1b6c912dce64d1269fd79348a2b0b85f7f670
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688453"
---
# <a name="installation-type"></a><span data-ttu-id="56eb7-102">安裝類型</span><span class="sxs-lookup"><span data-stu-id="56eb7-102">Installation Type</span></span>
  <span data-ttu-id="56eb7-103">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝精靈的 [安裝類型] 頁面，即可指定要安裝新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體，或是將功能加入至現有的執行個體。</span><span class="sxs-lookup"><span data-stu-id="56eb7-103">Use the Installation Type page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to specify whether to install a new instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or add features to an existing instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="56eb7-104">選項</span><span class="sxs-lookup"><span data-stu-id="56eb7-104">Options</span></span>  
 <span data-ttu-id="56eb7-105">選取指定您選擇的選項按鈕：</span><span class="sxs-lookup"><span data-stu-id="56eb7-105">Select the radio button that specifies your choice:</span></span>  
  
-   <span data-ttu-id="56eb7-106">執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的新安裝</span><span class="sxs-lookup"><span data-stu-id="56eb7-106">Perform a new installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="56eb7-107">將功能加入到現有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體</span><span class="sxs-lookup"><span data-stu-id="56eb7-107">Add features to an existing instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
     <span data-ttu-id="56eb7-108">如果您選取將功能加入至現有執行個體的選項，請使用下拉式清單來選取要更新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="56eb7-108">If you select the option to add features to an existing instance, use the drop-down list to select the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to update.</span></span>  
  
 <span data-ttu-id="56eb7-109">您只能將 SysPrep 支援的功能（ [!INCLUDE[ssDE](../../includes/ssde-md.md)] 和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ）加入至備妥的映射 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="56eb7-109">You can only add the SysPrep supported features-[!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-to a prepared image of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="56eb7-110">當備妥的執行個體完成之後，您就可以加入其他 SysPrep 不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="56eb7-110">Other features that are not supported by SysPrep can be added after the prepared instance is completed.</span></span>  
  
 <span data-ttu-id="56eb7-111">**注意** ：在容錯移轉叢集執行個體安裝完成之後，您就無法將功能加入至其中。</span><span class="sxs-lookup"><span data-stu-id="56eb7-111">**Note** You cannot add features to a failover cluster instance after it is installed.</span></span> <span data-ttu-id="56eb7-112">若要將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能加入至現有的容錯移轉叢集，您必須執行新的安裝來安裝個別的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="56eb7-112">To add [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features to an existing failover cluster, you must perform a new installation to install a separate instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
  
