---
title: 從命令提示字元安裝 Upgrade Advisor |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- command prompt [Upgrade Advisor]
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: a6841cc2-ca13-4b1c-9343-9e4d54312c3a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b0c5193f0b235b6d37170992d9d7ca9568b1f675
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688446"
---
# <a name="installing-upgrade-advisor-from-the-command-prompt"></a><span data-ttu-id="3e308-102">從命令提示字元安裝 Upgrade Advisor</span><span class="sxs-lookup"><span data-stu-id="3e308-102">Installing Upgrade Advisor from the Command Prompt</span></span>
  <span data-ttu-id="3e308-103">您可以使用安裝精靈或命令提示字元來安裝 Upgrade Advisor。</span><span class="sxs-lookup"><span data-stu-id="3e308-103">You can install Upgrade Advisor either by using the Setup Wizard or from the command prompt.</span></span> <span data-ttu-id="3e308-104">藉由使用命令提示字元，可執行自主式且自動化的安裝。</span><span class="sxs-lookup"><span data-stu-id="3e308-104">By using the command prompt you can perform unattended and automated installations.</span></span>  
  
## <a name="installation-syntax"></a><span data-ttu-id="3e308-105">安裝語法</span><span class="sxs-lookup"><span data-stu-id="3e308-105">Installation Syntax</span></span>  
 <span data-ttu-id="3e308-106">從命令提示字元安裝 Upgrade Advisor 的基本語法如下：</span><span class="sxs-lookup"><span data-stu-id="3e308-106">The basic syntax for installing Upgrade Advisor from the command prompt is as follows:</span></span>  
  
 `SQLUA.msi [options]`  
  
 <span data-ttu-id="3e308-107">下表顯示最常用的選項。</span><span class="sxs-lookup"><span data-stu-id="3e308-107">The following table shows the most common options.</span></span>  
  
|<span data-ttu-id="3e308-108">引數</span><span class="sxs-lookup"><span data-stu-id="3e308-108">Argument</span></span>|<span data-ttu-id="3e308-109">描述</span><span class="sxs-lookup"><span data-stu-id="3e308-109">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="3e308-110">/q [n&#124;b&#124;r&#124;f]</span><span class="sxs-lookup"><span data-stu-id="3e308-110">/q[n&#124;b&#124;r&#124;f]</span></span>|<span data-ttu-id="3e308-111">設定使用者介面 (UI) 層級：</span><span class="sxs-lookup"><span data-stu-id="3e308-111">Sets user interface (UI) level:</span></span><br /><br /> <span data-ttu-id="3e308-112">n = 沒有 UI</span><span class="sxs-lookup"><span data-stu-id="3e308-112">n = no UI</span></span><br /><br /> <span data-ttu-id="3e308-113">b = 基本 UI (只有進度，沒有提示)</span><span class="sxs-lookup"><span data-stu-id="3e308-113">b = basic UI (progress only, no prompts)</span></span><br /><br /> <span data-ttu-id="3e308-114">r = 縮減 UI (在安裝結尾顯示對話方塊)</span><span class="sxs-lookup"><span data-stu-id="3e308-114">r = reduced UI (dialog box at the end of installation)</span></span><br /><br /> <span data-ttu-id="3e308-115">f = 完整 UI</span><span class="sxs-lookup"><span data-stu-id="3e308-115">f = full UI</span></span>|  
|<span data-ttu-id="3e308-116">/L</span><span class="sxs-lookup"><span data-stu-id="3e308-116">/L</span></span>|<span data-ttu-id="3e308-117">指定記錄檔選項。</span><span class="sxs-lookup"><span data-stu-id="3e308-117">Specifies log file options.</span></span> <span data-ttu-id="3e308-118">若要將所有訊息記錄到*log_file_name*，請使用 **-L \* v**_log_file_name_。</span><span class="sxs-lookup"><span data-stu-id="3e308-118">To log all messages to *log_file_name*, use **-L\*v**_log_file_name_.</span></span> <span data-ttu-id="3e308-119">若只要記錄錯誤訊息，請使用 `-Le` *log_file_name*。</span><span class="sxs-lookup"><span data-stu-id="3e308-119">To log error messages only, use `-Le`*log_file_name*.</span></span>|  
|<span data-ttu-id="3e308-120">ADDLOCAL = ALL&#124; REMOVE = ALL&#124;重新安裝 = 全部</span><span class="sxs-lookup"><span data-stu-id="3e308-120">ADDLOCAL=ALL&#124; REMOVE=ALL&#124;REINSTALL=ALL</span></span>|<span data-ttu-id="3e308-121">指定要安裝 (ADDLOCAL)、移除 (REMOVE) 或重新安裝 (REINSTALL) Upgrade Advisor。</span><span class="sxs-lookup"><span data-stu-id="3e308-121">Specifies to install (ADDLOCAL), remove (REMOVE), or reinstall (REINSTALL) Upgrade Advisor.</span></span>|  
|<span data-ttu-id="3e308-122">UAINSTALLDIR=path</span><span class="sxs-lookup"><span data-stu-id="3e308-122">UAINSTALLDIR=path</span></span>|<span data-ttu-id="3e308-123">將 Upgrade Advisor 安裝至 path 指定的位置。</span><span class="sxs-lookup"><span data-stu-id="3e308-123">Installs Upgrade Advisor to the location specified by path.</span></span>|  
  
## <a name="installation-examples"></a><span data-ttu-id="3e308-124">安裝範例</span><span class="sxs-lookup"><span data-stu-id="3e308-124">Installation Examples</span></span>  
 <span data-ttu-id="3e308-125">下列範例將示範如何使用命令提示字元來安裝 Upgrade Advisor：</span><span class="sxs-lookup"><span data-stu-id="3e308-125">The following example shows how to install Upgrade Advisor by using the command prompt:</span></span>  
  
```  
SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 <span data-ttu-id="3e308-126">當您執行此命令時，也可以使用 Msiexec 程式：</span><span class="sxs-lookup"><span data-stu-id="3e308-126">You can also use the Msiexec program when you run this command:</span></span>  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 <span data-ttu-id="3e308-127">如果您必須使用其他安裝選項，這樣做就很有用。</span><span class="sxs-lookup"><span data-stu-id="3e308-127">This can be helpful if you have to use additional installation options.</span></span>  
  
## <a name="removal-examples"></a><span data-ttu-id="3e308-128">移除範例</span><span class="sxs-lookup"><span data-stu-id="3e308-128">Removal Examples</span></span>  
 <span data-ttu-id="3e308-129">下列範例將示範如何使用命令提示字元來移除 Upgrade Advisor：</span><span class="sxs-lookup"><span data-stu-id="3e308-129">The following example shows how to remove Upgrade Advisor by using the command prompt:</span></span>  
  
```  
SQLUA.msi /qn REMOVE=ALL  
```  
  
 <span data-ttu-id="3e308-130">當您執行此命令時，也可以使用 Msiexec 程式：</span><span class="sxs-lookup"><span data-stu-id="3e308-130">You can also use the Msiexec program when you run this command:</span></span>  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn REMOVE=ALL  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e308-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e308-131">See Also</span></span>  
 <span data-ttu-id="3e308-132">[安裝 Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="3e308-132">[Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="3e308-133">升級建議程式必要條件</span><span class="sxs-lookup"><span data-stu-id="3e308-133">Upgrade Advisor Prerequisites</span></span>](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
