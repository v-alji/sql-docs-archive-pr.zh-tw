---
title: 安裝 Microsoft Connector for 1.1 SAP BW |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ef96f38054f04e71de72bda0bbb12f8f003ef20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595186"
---
# <a name="installing-the-microsoft-connector-for-11-sap-bw"></a><span data-ttu-id="ac1fc-102">安裝 Microsoft Connector for 1.1 SAP BW</span><span class="sxs-lookup"><span data-stu-id="ac1fc-102">Installing the Microsoft Connector for 1.1 SAP BW</span></span>
  <span data-ttu-id="ac1fc-103">若要安裝 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW 及其檔，請從 SQL Server Feature Pack 網頁下載並執行 Windows installer 套件。</span><span class="sxs-lookup"><span data-stu-id="ac1fc-103">To install the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW and its documentation, download and run the Windows installer package from the SQL Server Feature Pack Web page.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ac1fc-104">Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。</span><span class="sxs-lookup"><span data-stu-id="ac1fc-104">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="ac1fc-105">如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="ac1fc-105">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ac1fc-106">擷取 SAP Netweaver BW 中的資料需要額外的 SAP 授權。</span><span class="sxs-lookup"><span data-stu-id="ac1fc-106">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="ac1fc-107">請洽詢 SAP 以確認這些需求。</span><span class="sxs-lookup"><span data-stu-id="ac1fc-107">Check with SAP to verify these requirements.</span></span>  
  
## <a name="required-sap-files"></a><span data-ttu-id="ac1fc-108">必要的 SAP 檔案</span><span class="sxs-lookup"><span data-stu-id="ac1fc-108">Required SAP Files</span></span>  
 <span data-ttu-id="ac1fc-109">若要使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 進行 SAP BW，您不需要在本機電腦上 (SAP GUI) 安裝 Sap 前端軟體。</span><span class="sxs-lookup"><span data-stu-id="ac1fc-109">To use the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW, you do not have to install the SAP Front End software (SAP GUI) on the local computer.</span></span>  
  
 <span data-ttu-id="ac1fc-110">不過，您必須將 SAP .NET Connector 檔案 librfc32.dll 複製到 Windows 資料夾的系統子資料夾中</span><span class="sxs-lookup"><span data-stu-id="ac1fc-110">However you must copy the SAP .NET connector file, librfc32.dll, into the system subfolder in the Windows folder.</span></span> <span data-ttu-id="ac1fc-111">(通常此資料夾的位置是 **C:\Windows\system32**)。</span><span class="sxs-lookup"><span data-stu-id="ac1fc-111">(Typically, this folder location is **C:\Windows\system32**.)</span></span>  
  
## <a name="considerations-for-64-bit-computers"></a><span data-ttu-id="ac1fc-112">64 位元電腦的考量</span><span class="sxs-lookup"><span data-stu-id="ac1fc-112">Considerations for 64-bit Computers</span></span>  
 <span data-ttu-id="ac1fc-113">[!INCLUDE[msCoName](../includes/msconame-md.md)]適用于 SAP BW 的連接器1.1 完全支援64位版本的 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows。</span><span class="sxs-lookup"><span data-stu-id="ac1fc-113">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW fully supports the 64-bit version of [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows.</span></span> <span data-ttu-id="ac1fc-114">在64位電腦上，SAP BW 的 [!INCLUDE[msCoName](../includes/msconame-md.md)] 連接器1.1 具有下列額外需求：</span><span class="sxs-lookup"><span data-stu-id="ac1fc-114">On a 64-bit computer, the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW has the following additional requirements:</span></span>  
  
-   <span data-ttu-id="ac1fc-115">若要在 64 位元 Windows 作業系統上以 64 位元模式執行封裝，請將 64 位元版本的 SAP GUI 檔案 librfc32.dll 複製到 Windows 資料夾的 **system32** 資料夾中</span><span class="sxs-lookup"><span data-stu-id="ac1fc-115">To run packages in 64-bit mode on any 64-bit Windows operating system, copy the 64-bit version of the SAP GUI file, librfc32.dll, into the **system32** folder of the Windows folder.</span></span> <span data-ttu-id="ac1fc-116">(通常此檔案的位置是 **C:\Windows\system32**)。</span><span class="sxs-lookup"><span data-stu-id="ac1fc-116">(Typically, this file location is **C:\Windows\system32**.)</span></span>  
  
-   <span data-ttu-id="ac1fc-117">若要在 64 位元 Windows 作業系統上以 32 位元模式執行封裝，請將 SAP GUI 檔案 librfc32.dll 複製到 Windows 資料夾的 **SysWow64** 資料夾中</span><span class="sxs-lookup"><span data-stu-id="ac1fc-117">To run packages in 32-bit mode on any 64-bit Windows operating system, copy the SAP GUI file, librfc32.dll, into the **SysWow64** folder of the Windows folder.</span></span> <span data-ttu-id="ac1fc-118">(通常此資料夾的位置是 **C:\Windows\SysWow64**)。</span><span class="sxs-lookup"><span data-stu-id="ac1fc-118">(Typically, this folder location is **C:\Windows\SysWow64**.)</span></span>  
  
  
