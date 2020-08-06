---
title: 網路屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- LingerTimeout property
- EnableNagleAlgorithm property
- MinPendingAcceptExCount property
- MaxPendingSendCount property
- EnableBinaryXML property
- MinPendingReceiveCount property
- MaxCompletedReceiveCount property
- DisableNonblockingMode property
- RequestSizeThreshold property
- CompressionLevel property
- ReceiveBufferSize property
- EnableCompression property
- ServerSendTimeout property
- IPV4Support property
- MaxPendingReceiveCount property
- MaxPendingAcceptExCount property
- IPV6Support property
- MaxAllowedRequestSize property
- ServerReceiveTimeout property
- EnableLingerOnClose property
- InitialConnectTimeout property
- SendBufferSize property
- ScatterReceiveMultiplier property
- network properties [Analysis Services]
ms.assetid: ef4251e2-abe5-4c5b-9868-7549782d0244
author: minewiskan
ms.author: owend
ms.openlocfilehash: 10ad5bbbcffdfc3d3c4fefe3111e4c4425919915
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595310"
---
# <a name="network-properties"></a><span data-ttu-id="8fbc0-102">網路屬性</span><span class="sxs-lookup"><span data-stu-id="8fbc0-102">Network Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="8fbc0-103">支援下表列出的伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-103">supports the server properties listed in the following tables.</span></span> <span data-ttu-id="8fbc0-104">如需有關其他伺服器屬性及如何設定伺服器屬性的詳細資訊，請參閱＜ [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="8fbc0-105">**適用於：** 多維度與表格式伺服器模式</span><span class="sxs-lookup"><span data-stu-id="8fbc0-105">**Applies to:** Multidimensional and Tabular server mode</span></span>  
  
## <a name="general"></a><span data-ttu-id="8fbc0-106">一般</span><span class="sxs-lookup"><span data-stu-id="8fbc0-106">General</span></span>  
 `ListenOnlyOnLocalConnections`  
 <span data-ttu-id="8fbc0-107">此為布林值屬性，識別是否僅在本機連接上接聽，例如 localhost。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-107">A Boolean property that identifies whether to listen only on local connections, for example localhost.</span></span>  
  
## <a name="listener"></a><span data-ttu-id="8fbc0-108">接聽程式</span><span class="sxs-lookup"><span data-stu-id="8fbc0-108">Listener</span></span>  
 `IPV4Support`  
 <span data-ttu-id="8fbc0-109">此為帶正負號的 32 位元整數屬性，定義 IPv4 通訊協定的支援。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-109">A signed 32-bit integer property that defines support for IPv4 protocol.</span></span> <span data-ttu-id="8fbc0-110">此屬性的值為下表列出的值之一：</span><span class="sxs-lookup"><span data-stu-id="8fbc0-110">This property has one of the values listed in the following table:</span></span>  
  
|<span data-ttu-id="8fbc0-111">值</span><span class="sxs-lookup"><span data-stu-id="8fbc0-111">Value</span></span>|<span data-ttu-id="8fbc0-112">描述</span><span class="sxs-lookup"><span data-stu-id="8fbc0-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8fbc0-113">*0*</span><span class="sxs-lookup"><span data-stu-id="8fbc0-113">*0*</span></span>|<span data-ttu-id="8fbc0-114">IPv4 已停用；用戶端無法連接。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-114">IPv4 disabled; clients can't connect.</span></span>|  
|<span data-ttu-id="8fbc0-115">*1*</span><span class="sxs-lookup"><span data-stu-id="8fbc0-115">*1*</span></span>|<span data-ttu-id="8fbc0-116">(預設值) 需要有 IPv4；如果伺服器無法接聽 IPv4 將無法啟動。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-116">(Default) IPv4 is required; server won't start if it cannot listen to IPv4.</span></span>|  
|<span data-ttu-id="8fbc0-117">*2*</span><span class="sxs-lookup"><span data-stu-id="8fbc0-117">*2*</span></span>|<span data-ttu-id="8fbc0-118">IPv4 是選擇性的；伺服器會嘗試接聽 IPv4，但即使無法接聽仍會啟動。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-118">IPv4 is optional; server tries to listen to IPv4 but starts even if unable to.</span></span>|  
  
 `IPV6Support`  
 <span data-ttu-id="8fbc0-119">此為帶正負號的 32 位元整數屬性，定義 IPv6 通訊協定的支援。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-119">A signed 32-bit integer property that defines support for IPv6 protocol.</span></span> <span data-ttu-id="8fbc0-120">此屬性的值為下表列出的值之一：</span><span class="sxs-lookup"><span data-stu-id="8fbc0-120">This property has one of the values listed in the following table:</span></span>  
  
|<span data-ttu-id="8fbc0-121">值</span><span class="sxs-lookup"><span data-stu-id="8fbc0-121">Value</span></span>|<span data-ttu-id="8fbc0-122">描述</span><span class="sxs-lookup"><span data-stu-id="8fbc0-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8fbc0-123">*0*</span><span class="sxs-lookup"><span data-stu-id="8fbc0-123">*0*</span></span>|<span data-ttu-id="8fbc0-124">IPv6 已停用；用戶端無法連接。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-124">IPv6 disabled; clients can't connect.</span></span>|  
|<span data-ttu-id="8fbc0-125">*1*</span><span class="sxs-lookup"><span data-stu-id="8fbc0-125">*1*</span></span>|<span data-ttu-id="8fbc0-126">(預設值) 需要有 IPv6；如果伺服器無法接聽 IPv6 將無法啟動。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-126">(Default) IPv6 is required; server won't start if it cannot listen to IPv6.</span></span>|  
|<span data-ttu-id="8fbc0-127">*2*</span><span class="sxs-lookup"><span data-stu-id="8fbc0-127">*2*</span></span>|<span data-ttu-id="8fbc0-128">IPv6 是選擇性的；伺服器會嘗試接聽 IPv6，但即使無法接聽仍會啟動。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-128">IPv6 is optional; server tries to listen to IPv6 but starts even if unable to.</span></span>|  
  
 `MaxAllowedRequestSize`  
 <span data-ttu-id="8fbc0-129">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-129">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `RequestSizeThreshold`  
 <span data-ttu-id="8fbc0-130">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-130">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ServerReceiveTimeout`  
 <span data-ttu-id="8fbc0-131">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-131">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ServerSendTimeout`  
 <span data-ttu-id="8fbc0-132">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-132">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="requests"></a><span data-ttu-id="8fbc0-133">Requests</span><span class="sxs-lookup"><span data-stu-id="8fbc0-133">Requests</span></span>  
 `EnableBinaryXML`  
 <span data-ttu-id="8fbc0-134">此為布林值屬性，指定伺服器是否會辨識要求的二進位 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-134">A Boolean property that specifies whether the server will recognize requests binary xml format.</span></span>  
  
 `EnableCompression`  
 <span data-ttu-id="8fbc0-135">此為布林值屬性，指定是否針對要求啟用壓縮。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-135">A Boolean property that specifies whether compression is enabled for requests.</span></span>  
  
## <a name="responses"></a><span data-ttu-id="8fbc0-136">回應</span><span class="sxs-lookup"><span data-stu-id="8fbc0-136">Responses</span></span>  
 `CompressionLevel`  
 <span data-ttu-id="8fbc0-137">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-137">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `EnableBinaryXML`  
 <span data-ttu-id="8fbc0-138">此為布林值屬性，指定伺服器是否啟用二進位 XML 回應。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-138">A Boolean property that specifies whether the server is enabled for binary xml responses.</span></span>  
  
 `EnableCompression`  
 <span data-ttu-id="8fbc0-139">此為布林值屬性，指定是否針對用戶端要求的回應啟用壓縮。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-139">A Boolean property that specifies whether compression is enabled for responses to client requests.</span></span>  
  
## <a name="tcp"></a><span data-ttu-id="8fbc0-140">TCP</span><span class="sxs-lookup"><span data-stu-id="8fbc0-140">TCP</span></span>  
 `InitialConnectTimeout`  
 <span data-ttu-id="8fbc0-141">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-141">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxCompletedReceiveCount`  
 <span data-ttu-id="8fbc0-142">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-142">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxPendingAcceptExCount`  
 <span data-ttu-id="8fbc0-143">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-143">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxPendingReceiveCount`  
 <span data-ttu-id="8fbc0-144">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-144">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxPendingSendCount`  
 <span data-ttu-id="8fbc0-145">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-145">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MinPendingAcceptExCount`  
 <span data-ttu-id="8fbc0-146">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-146">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MinPendingReceiveCount`  
 <span data-ttu-id="8fbc0-147">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-147">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ScatterReceiveMultiplier`  
 <span data-ttu-id="8fbc0-148">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-148">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ DisableNonblockingMode`  
 <span data-ttu-id="8fbc0-149">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-149">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ EnableLingerOnClose`  
 <span data-ttu-id="8fbc0-150">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-150">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\EnableNagleAlgorithm`  
 <span data-ttu-id="8fbc0-151">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-151">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ LingerTimeout`  
 <span data-ttu-id="8fbc0-152">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-152">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ ReceiveBufferSize`  
 <span data-ttu-id="8fbc0-153">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-153">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ SendBufferSize`  
 <span data-ttu-id="8fbc0-154">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="8fbc0-154">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fbc0-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fbc0-155">See Also</span></span>  
 <span data-ttu-id="8fbc0-156">[在 Analysis Services 中設定伺服器屬性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="8fbc0-156">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="8fbc0-157">判斷 Analysis Services 執行個體的伺服器模式</span><span class="sxs-lookup"><span data-stu-id="8fbc0-157">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
