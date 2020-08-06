---
title: 執行 Data Quality Client 應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.browseforservers.f1
- sql12.dqs.connecttoserver.f1
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 45372ce22fd1b18f0ec13f7a7fd76a369b78dfd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709970"
---
# <a name="run-the-data-quality-client-application"></a><span data-ttu-id="0b91a-102">執行 Data Quality Client 應用程式</span><span class="sxs-lookup"><span data-stu-id="0b91a-102">Run the Data Quality Client Application</span></span>
  <span data-ttu-id="0b91a-103">您可以執行 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)]，然後登入 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]，藉以使用 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] (DQS)。</span><span class="sxs-lookup"><span data-stu-id="0b91a-103">You can use [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) by running [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and logging on to a [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0b91a-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="0b91a-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="0b91a-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="0b91a-105">Prerequisites</span></span>  
 <span data-ttu-id="0b91a-106">您必須執行 DQSInstaller.exe 檔案，才可以完成 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 的安裝。</span><span class="sxs-lookup"><span data-stu-id="0b91a-106">You must have completed the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] installation by running the DQSInstaller.exe file.</span></span> <span data-ttu-id="0b91a-107">如需詳細資訊，請參閱 [執行 DQSInstaller.exe 完成 Data Quality Server 安裝](install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)。</span><span class="sxs-lookup"><span data-stu-id="0b91a-107">For more information, see [Run DQSInstaller.exe to Complete Data Quality Server Installation](install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0b91a-108">Security</span><span class="sxs-lookup"><span data-stu-id="0b91a-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0b91a-109">權限</span><span class="sxs-lookup"><span data-stu-id="0b91a-109">Permissions</span></span>  
 <span data-ttu-id="0b91a-110">您必須擁有授與 DQS_MAIN 資料庫的其中一個 DQS 角色 (dqs_adminstrator、dqs_kb_editor 或 dqs_kb_operator)，才能登入 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0b91a-110">You must have one of the three DQS roles (dqs_adminstrator, dqs_kb_editor, or dqs_kb_operator) granted on the DQS_MAIN database to be able to log on to [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
##  <a name="run-data-quality-client"></a><a name="Run"></a><span data-ttu-id="0b91a-111">執行 Data Quality Client</span><span class="sxs-lookup"><span data-stu-id="0b91a-111">Run Data Quality Client</span></span>  
 <span data-ttu-id="0b91a-112">若要在已安裝 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 的電腦上執行此用戶端，請依照以下方式繼續進行：</span><span class="sxs-lookup"><span data-stu-id="0b91a-112">To run [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] on the computer where you have installed it, proceed as follows:</span></span>  
  
1.  <span data-ttu-id="0b91a-113">按一下 [開始]\*\*\*\*，並指向 [所有程式]\*\*\*\*，然後依序按一下 [[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]]\*\*\*\*、[Data Quality Services]\*\*\*\* 及 [Data Quality Client]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0b91a-113">Click **Start**, point to **All Programs**, click **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**, click **Data Quality Services**, and then click **Data Quality Client**.</span></span>  
  
2.  <span data-ttu-id="0b91a-114">在 [連線至伺服器] 對話方塊中：</span><span class="sxs-lookup"><span data-stu-id="0b91a-114">In the **Connect to Server** dialog box:</span></span>  
  
    1.  <span data-ttu-id="0b91a-115">指定您想要讓 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 應用程式連接的目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="0b91a-115">Specify the server that you want to connect the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application to.</span></span> <span data-ttu-id="0b91a-116">若要連接到本機電腦上的 **，請選取** [(LOCAL)] [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0b91a-116">Select **(LOCAL)** to connect to [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] on the local computer.</span></span> <span data-ttu-id="0b91a-117">您也可以按一下向下箭號，然後選取 **\<Browse network for more servers>** 以連接到不同的伺服器 (或依名稱) 連接到本機伺服器。</span><span class="sxs-lookup"><span data-stu-id="0b91a-117">You can also click the down arrow and select **\<Browse network for more servers>** to connect to a different server (or to connect to the local server by name).</span></span> <span data-ttu-id="0b91a-118">此時會顯示 **[瀏覽伺服器]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0b91a-118">The **Browse for Servers** dialog box will be displayed.</span></span> <span data-ttu-id="0b91a-119">您可以在 **[本機伺服器]** 索引標籤或 **[網路伺服器]** 索引標籤中選取伺服器。</span><span class="sxs-lookup"><span data-stu-id="0b91a-119">You can select a server in the **Local Servers** tab or in the **Network Servers** tab.</span></span>  
  
    2.  <span data-ttu-id="0b91a-120">如果您想要加密 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 與 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 之間的資料傳輸，請按一下 [選項]\*\*\*\*，然後選取 [加密連接]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0b91a-120">If you want to encrypt data transfer between [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] and [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], click **Options**, and then select the **Encrypt Connection** check box.</span></span>  
  
3.  <span data-ttu-id="0b91a-121">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="0b91a-121">Click **Connect**.</span></span>  
  
 <span data-ttu-id="0b91a-122">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 首頁畫面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0b91a-122">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen appears.</span></span> <span data-ttu-id="0b91a-123">如需詳細資訊，請參閱 [Data Quality Client 首頁畫面](../../2014/data-quality-services/data-quality-client-home-screen.md)。</span><span class="sxs-lookup"><span data-stu-id="0b91a-123">For more information, see [Data Quality Client Home Screen](../../2014/data-quality-services/data-quality-client-home-screen.md).</span></span>  
  
  
