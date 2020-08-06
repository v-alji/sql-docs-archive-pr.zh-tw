---
title: 為 FILESTREAM 存取設定防火牆 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- Windows Firewall [Database Engine], FILESTREAM
- FILESTREAM [SQL Server], Windows Firewall
ms.assetid: fc52007f-c26f-4f8e-b9d8-55a7978f4d56
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8b787403fefdd336dd82bf7ccb93cdf21fe5a90d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599026"
---
# <a name="configure-a-firewall-for-filestream-access"></a><span data-ttu-id="677df-102">為 FILESTREAM 存取設定防火牆</span><span class="sxs-lookup"><span data-stu-id="677df-102">Configure a Firewall for FILESTREAM Access</span></span>
  <span data-ttu-id="677df-103">若要在受防火牆保護的環境中使用 FILESTREAM，用戶端和伺服器都必須能夠將 DNS 名稱解析為包含 FILESTREAM 檔案的伺服器。</span><span class="sxs-lookup"><span data-stu-id="677df-103">To use FILESTREAM in a firewall-protected environment, both the client and server must be able to resolve DNS names to the server that contains the FILESTREAM files.</span></span> <span data-ttu-id="677df-104">FILESTREAM 要求 Windows 檔案共用通訊埠 139 和 445 必須要開啟。</span><span class="sxs-lookup"><span data-stu-id="677df-104">FILESTREAM requires the Windows file-sharing ports 139 and 445 to be open.</span></span>  
  
### <a name="to-open-the-windows-file-sharing-ports-on-a-computer-that-is-running-windows-7"></a><span data-ttu-id="677df-105">在執行 Windows 7 的電腦上開啟 Windows 檔案共用通訊埠</span><span class="sxs-lookup"><span data-stu-id="677df-105">To open the Windows file-sharing ports on a computer that is running Windows 7</span></span>  
  
1.  <span data-ttu-id="677df-106">在 [控制台] 中，開啟 [Windows 防火牆]。</span><span class="sxs-lookup"><span data-stu-id="677df-106">In Control Panel, open **Windows Firewall**.</span></span>  
  
2.  <span data-ttu-id="677df-107">在左窗格中，按一下 [進階設定]。</span><span class="sxs-lookup"><span data-stu-id="677df-107">In the left pane, click **Advanced settings**.</span></span> <span data-ttu-id="677df-108">如果系統提示您輸入系統管理員密碼或確認，請輸入密碼或提供確認。</span><span class="sxs-lookup"><span data-stu-id="677df-108">If you're prompted for an administrator password or confirmation, type the password or provide confirmation.</span></span>  
  
3.  <span data-ttu-id="677df-109">在 [具有進階安全性的 Windows 防火牆] 對話方塊的左窗格中，按一下 [輸入規則]，然後按一下右窗格中的 [新增規則]。</span><span class="sxs-lookup"><span data-stu-id="677df-109">In the **Windows Firewall with Advanced Security** dialog box, in the left pane, click **Inbound Rules**, and then, in the right pane, click **New Rule**.</span></span>  
  
4.  <span data-ttu-id="677df-110">遵循 [新增輸入規則精靈] 中的指示以加入 TCP 通訊埠 139。</span><span class="sxs-lookup"><span data-stu-id="677df-110">Follow the instructions in the New Inbound Rule wizard to add TCP port 139.</span></span>  
  
5.  <span data-ttu-id="677df-111">重複上一個步驟以加入 TCP 通訊埠 445。</span><span class="sxs-lookup"><span data-stu-id="677df-111">Repeat the previous step to add TCP port 445.</span></span>  
  
6.  <span data-ttu-id="677df-112">關閉 [具有進階安全性的 Windows 防火牆] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="677df-112">Close the **Windows Firewall with Advanced Security** dialog box.</span></span>  
  
  
