---
title: SQL Server 中的地區語言版本 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 20b99363-0490-4aa3-9a3d-262f827d81e8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 646ffaed1e4b709c2c26030379f0a7f223f221e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688438"
---
# <a name="local-language-versions-in-sql-server"></a><span data-ttu-id="9d9ce-102">SQL Server 中的地區語言版本</span><span class="sxs-lookup"><span data-stu-id="9d9ce-102">Local Language Versions in SQL Server</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9d9ce-103">支援 Windows 作業系統所支援的所有語言。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-103">supports all languages that are supported by Windows operating systems.</span></span>  
  
## <a name="cross-language-support"></a><span data-ttu-id="9d9ce-104">跨語言支援</span><span class="sxs-lookup"><span data-stu-id="9d9ce-104">Cross-Language Support</span></span>  
  
-   <span data-ttu-id="9d9ce-105">所有當地語系化版本的作業系統都支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的英文版。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-105">The English-language version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is supported on all localized versions of operating systems.</span></span>  
  
-   <span data-ttu-id="9d9ce-106">透過使用 Windows 多語系使用者介面 (MUI) 套件設定，便可在支援的作業系統對應語言版本或英文版的當地語系化作業系統上支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的當地語系化版本。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-106">Localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are supported on localized operating systems with the corresponding language or on English-language versions of supported operating systems by using the Windows Multilingual User Interface Pack (MUI) settings.</span></span> <span data-ttu-id="9d9ce-107">如需詳細資訊，請參閱 [Configure Operating System to Support Localized Versions](../../../2014/sql-server/install/local-language-versions-in-sql-server.md#BK_ConfigureOS)。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-107">For more information, see [Configure Operating System to Support Localized Versions](../../../2014/sql-server/install/local-language-versions-in-sql-server.md#BK_ConfigureOS).</span></span>  
  
-   <span data-ttu-id="9d9ce-108">當地語系化版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 只能升級到相同語言的當地語系化版本，不能升級到英文版。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-108">Localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can only be upgraded to localized versions of the same language, and cannot be upgraded to the English-language version.</span></span>  
  
-   <span data-ttu-id="9d9ce-109">當地語系化版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 也可以與英文版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體並存安裝。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-109">Localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can also be installed side by side with English-language instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="configure-operating-system-to-support-localized-versions"></a><a name="BK_ConfigureOS"></a> <span data-ttu-id="9d9ce-110">Configure Operating System to Support Localized Versions</span><span class="sxs-lookup"><span data-stu-id="9d9ce-110">Configure Operating System to Support Localized Versions</span></span>  
 <span data-ttu-id="9d9ce-111">透過使用 Windows 多語系使用者介面 (MUI) 套件設定， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的當地語系化版本可在支援的作業系統英文版上受到支援。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-111">Localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are supported on English-language versions of supported operating systems through the use of Windows Multilingual User Interface Pack (MUI) settings.</span></span>  
  
 <span data-ttu-id="9d9ce-112">不過，在以非英文 MUI 設定執行英文版作業系統的伺服器上安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的當地語系化版本之前，您必須確認某些作業系統設定。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-112">However, you must verify certain operating system settings before installing a localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a server that is running an English-language operating system with a non-English MUI setting.</span></span> <span data-ttu-id="9d9ce-113">您需要確認下列作業系統設定是否符合要安裝的當地語系化之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的語言：</span><span class="sxs-lookup"><span data-stu-id="9d9ce-113">You need to verify that the following operating system settings match the language of the localized [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to be installed:</span></span>  
  
-   <span data-ttu-id="9d9ce-114">作業系統使用者介面設定</span><span class="sxs-lookup"><span data-stu-id="9d9ce-114">The operating system user interface setting</span></span>  
  
-   <span data-ttu-id="9d9ce-115">作業系統使用者地區設定</span><span class="sxs-lookup"><span data-stu-id="9d9ce-115">The operating system user locale setting</span></span>  
  
-   <span data-ttu-id="9d9ce-116">系統地區設定</span><span class="sxs-lookup"><span data-stu-id="9d9ce-116">The system locale setting</span></span>  
  
 <span data-ttu-id="9d9ce-117">如果設定不符合當地語系化之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的語言，請使用下列程序，正確設定這些作業系統設定。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-117">If the settings do not match the language of the localized [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to be installed, then use the following procedures to correctly set these operating system settings.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="9d9ce-118">不支援在相同電腦上安裝不同語言版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-118">Installations of different language versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances on the same computer are not supported.</span></span>  
  
#### <a name="to-change-the-operating-system-user-interface-setting"></a><span data-ttu-id="9d9ce-119">若要變更作業系統使用者介面設定</span><span class="sxs-lookup"><span data-stu-id="9d9ce-119">To change the operating system user interface setting</span></span>  
  
1.  <span data-ttu-id="9d9ce-120">如果尚未安裝，請安裝符合當地語系化版本之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的作業系統 MUI。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-120">If not already installed, install the operating system MUI that matches your localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="9d9ce-121">在 [控制台] 中，開啟 **[地區及語言選項]** 。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-121">In Control Panel, open **Regional and Language Options**.</span></span>  
  
3.  <span data-ttu-id="9d9ce-122">在 **[語言]** 索引標籤上，針對 **[用於功能表和對話方塊的語言]** ，從清單中選取一值。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-122">On the **Languages** tab, for **Language used in menus and dialogs**, select a value from the list.</span></span>  
  
     <span data-ttu-id="9d9ce-123">這項設定將影響 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的使用者介面語言，因此它必須符合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的當地語系化版本。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-123">This setting will affect the user interface language of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], so it must match your localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="9d9ce-124">按一下 **[套用]** 來確認變更，並按一下 **[確定]** 來關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-124">Click **Apply** to confirm the change, and **OK** to close the window.</span></span>  
  
#### <a name="to-change-the-operating-system-user-locale-setting"></a><span data-ttu-id="9d9ce-125">若要變更作業系統使用者地區設定</span><span class="sxs-lookup"><span data-stu-id="9d9ce-125">To change the operating system user locale setting</span></span>  
  
1.  <span data-ttu-id="9d9ce-126">如果尚未安裝，請安裝符合當地語系化版本之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的作業系統 MUI。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-126">If not already installed, install the operating system MUI that matches your localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="9d9ce-127">在 [控制台] 中，開啟 **[地區及語言選項]** 。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-127">In Control Panel, open **Regional and Language Options**.</span></span>  
  
3.  <span data-ttu-id="9d9ce-128">在 **[地區選項]** 索引標籤上，針對 **[選擇一個項目來符合它的喜好設定]** ，從清單中選取一值。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-128">On the **Regional Options** tab, for **Select an item to match its preferences**, select a value from the list.</span></span>  
  
     <span data-ttu-id="9d9ce-129">這項設定會影響特定文化專用的資料格式。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-129">This setting will affect culture-specific data formatting.</span></span>  
  
4.  <span data-ttu-id="9d9ce-130">按一下 **[套用]** 來確認變更，並按一下 **[確定]** 來關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-130">Click **Apply** to confirm the change, and **OK** to close the window.</span></span>  
  
#### <a name="to-change-the-system-locale-setting"></a><span data-ttu-id="9d9ce-131">若要變更系統地區設定</span><span class="sxs-lookup"><span data-stu-id="9d9ce-131">To change the system locale setting</span></span>  
  
1.  <span data-ttu-id="9d9ce-132">如果尚未安裝，請安裝符合當地語系化版本之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的作業系統 MUI。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-132">If not already installed, install the operating system MUI that matches your localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="9d9ce-133">在 [控制台] 中，開啟 **[地區及語言選項]** 。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-133">In Control Panel, open **Regional and Language Options**.</span></span>  
  
3.  <span data-ttu-id="9d9ce-134">在 [進階]  索引標籤上，針對 [選擇一個符合於您要使用的非 Unicode 程式語言版本的語言]  ，從清單中選取一值。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-134">On the **Advanced** tab, for **Select a language to match the language version of the non-Unicode programs you want to use**, select a value from the list.</span></span>  
  
     <span data-ttu-id="9d9ce-135">這項設定可讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝選擇最佳預設定序。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-135">This setting will allow [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to choose the best default collation for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span>  
  
4.  <span data-ttu-id="9d9ce-136">按一下 **[套用]** 來確認變更，並按一下 **[確定]** 來關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="9d9ce-136">Click **Apply** to confirm the change, and **OK** to close the window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d9ce-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d9ce-137">See Also</span></span>  
 <span data-ttu-id="9d9ce-138">[安裝 SQL Server 2014 的硬體和軟體需求](hardware-and-software-requirements-for-installing-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9d9ce-138">[Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) </span></span>  
 [<span data-ttu-id="9d9ce-139">安裝 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="9d9ce-139">Install SQL Server 2014</span></span>](../../database-engine/install-windows/install-sql-server.md)  
  
  
