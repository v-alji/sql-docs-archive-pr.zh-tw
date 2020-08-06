---
title: 在套件中使用註解 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- self-documenting packages
- adding annotations
- annotations [Integration Services]
ms.assetid: 48c8ed9a-b10d-490c-9ba7-4b77aa44e3dd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 27c7df6afd894ea9730027da1d54786ed8397fad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607449"
---
# <a name="use-annotations-in-packages"></a><span data-ttu-id="a9b94-102">使用封裝中的註解</span><span class="sxs-lookup"><span data-stu-id="a9b94-102">Use Annotations in Packages</span></span>
  <span data-ttu-id="a9b94-103">[!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師會提供註解，可用於使封裝自我記錄並易於了解及維護。</span><span class="sxs-lookup"><span data-stu-id="a9b94-103">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer provides annotations, which you can use to make packages self-documenting and easier to understand and maintain.</span></span> <span data-ttu-id="a9b94-104">您可以將註解加入「 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師」的控制流程、資料流程及事件處理常式設計介面。</span><span class="sxs-lookup"><span data-stu-id="a9b94-104">You can add annotations to the control flow, data flow, and event handler design surfaces of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="a9b94-105">註解 (Annotation) 可以包含任何類型的文字，而且它們可用於將標籤、註解 (Comment) 及其他描述性資訊加入至封裝。</span><span class="sxs-lookup"><span data-stu-id="a9b94-105">The annotations can contain any type of text, and they are useful for adding labels, comments, and other descriptive information to a package.</span></span> <span data-ttu-id="a9b94-106">註解只是設計階段功能。</span><span class="sxs-lookup"><span data-stu-id="a9b94-106">Annotations are a design-time feature only.</span></span> <span data-ttu-id="a9b94-107">例如，註解不寫入記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="a9b94-107">For example, they are not written to logs.</span></span>  
  
 <span data-ttu-id="a9b94-108">當您按 ENTER 鍵時，文字會折行。</span><span class="sxs-lookup"><span data-stu-id="a9b94-108">When you press ENTER, the text wraps to the next line.</span></span> <span data-ttu-id="a9b94-109">註解方塊會自動在您加入其他文字行時放大。</span><span class="sxs-lookup"><span data-stu-id="a9b94-109">The annotation box automatically increases in size as you add additional lines of text.</span></span> <span data-ttu-id="a9b94-110">封裝註解會以純文字格式保存在封裝檔案的 CDATA 區段中。</span><span class="sxs-lookup"><span data-stu-id="a9b94-110">Package annotations are persisted as clear text in the CDATA section of the package file.</span></span>  
  
 <span data-ttu-id="a9b94-111">如需對封裝檔案格式所做變更的詳細資訊，請參閱 [SSIS 封裝格式](../../2014/integration-services/ssis-package-format.md)。</span><span class="sxs-lookup"><span data-stu-id="a9b94-111">For more information about changes to the format of the package file, see [SSIS Package Format](../../2014/integration-services/ssis-package-format.md).</span></span>  
  
 <span data-ttu-id="a9b94-112">當您儲存封裝時，「 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師」會在封裝中儲存註解。</span><span class="sxs-lookup"><span data-stu-id="a9b94-112">When you save the package, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer saves the annotations in the package.</span></span>  
  
### <a name="to-add-an-annotation-to-a-package"></a><span data-ttu-id="a9b94-113">將註解加入封裝</span><span class="sxs-lookup"><span data-stu-id="a9b94-113">To add an annotation to a package</span></span>  
  
-   [<span data-ttu-id="a9b94-114">將註解加入封裝</span><span class="sxs-lookup"><span data-stu-id="a9b94-114">Add an Annotation to a Package</span></span>](../../2014/integration-services/add-an-annotation-to-a-package.md)  
  
  
