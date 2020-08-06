---
title: SQLXML 4.0 的指導方針和限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, about SQLXML
ms.assetid: fe433d30-90a1-421e-85c6-af13294dc18d
author: rothja
ms.author: jroth
ms.openlocfilehash: e020cbf0ac32e4c878b0b74b67e7c9c679d5d178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584359"
---
# <a name="guidelines-and-limitations-of-sqlxml-40"></a><span data-ttu-id="d3b0d-102">SQLXML 4.0 的指導方針和限制</span><span class="sxs-lookup"><span data-stu-id="d3b0d-102">Guidelines and Limitations of SQLXML 4.0</span></span>
  <span data-ttu-id="d3b0d-103">當您使用 SQLXML 4.0 時，請記住以下事項：</span><span class="sxs-lookup"><span data-stu-id="d3b0d-103">Remember the following when working with SQLXML 4.0:</span></span>  
  
-   <span data-ttu-id="d3b0d-104">當做查詢結果傳回的 XML 不會針對產生此 XML 的對應結構描述進行驗證。</span><span class="sxs-lookup"><span data-stu-id="d3b0d-104">XML returned as a query result is not validated against the mapping schema that generated the XML.</span></span>  
  
-   <span data-ttu-id="d3b0d-105">SQLXML 4.0 同時包含與版本無關以及與版本相關的 PROGID。</span><span class="sxs-lookup"><span data-stu-id="d3b0d-105">SQLXML 4.0 includes version-independent and version-dependent PROGIDs.</span></span> <span data-ttu-id="d3b0d-106">建議您所有的實際執行應用程式都應該使用與版本相關的 PROGID。</span><span class="sxs-lookup"><span data-stu-id="d3b0d-106">It is recommended that all production applications use version-dependent PROGIDs.</span></span> <span data-ttu-id="d3b0d-107">這一點特別重要，因為 SQLXML 4.0 並非完全具有回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="d3b0d-107">This is especially important because SQLXML 4.0 is not fully backward compatible.</span></span> <span data-ttu-id="d3b0d-108">當您安裝更新的版本時，使用與版本相關的 PROGID 會防止您的實際執行可能發生的失敗。</span><span class="sxs-lookup"><span data-stu-id="d3b0d-108">Using version dependent PROGIDs protects from possible production failures when you install newer releases.</span></span> <span data-ttu-id="d3b0d-109">在不同的版本之間，程式行為可能會因為各種原因而失敗，例如錯誤修正、可能的設計變更等等。</span><span class="sxs-lookup"><span data-stu-id="d3b0d-109">From release to release, program behavior may change for a variety of reasons, such as bug fixes, possible design changes, and so on.</span></span> <span data-ttu-id="d3b0d-110">當您安裝更新的版本時，使用與版本相關的 PROGID 會防止發生非預期的失敗。</span><span class="sxs-lookup"><span data-stu-id="d3b0d-110">Using version-dependent PROGIDs protects from unexpected failure when you install newer releases.</span></span> <span data-ttu-id="d3b0d-111">如果在您安裝更新的版本時使用與版本相關的 PROGID，您的應用程式將會繼續運作，而不會發生失敗。</span><span class="sxs-lookup"><span data-stu-id="d3b0d-111">With version-dependent PROGIDs, when you install a newer release, your application will continue to work without failure.</span></span> <span data-ttu-id="d3b0d-112">如果您決定變更與之前版本相關的 PROGID，並在較新的版本中使用與最近版本相關的 PROGID，您必須先測試應用程式，然後才能實際執行它。</span><span class="sxs-lookup"><span data-stu-id="d3b0d-112">If you decide to change the previous version-dependent PROGIDs and use the recent version-dependent PROGIDs in a newer release, you must test your application before putting it into production.</span></span> <span data-ttu-id="d3b0d-113">例如，使用與版本無關之 PROGID 的應用程式可能會在以下案例中發生失敗：</span><span class="sxs-lookup"><span data-stu-id="d3b0d-113">For example, applications using version-independent PROGIDs may fail in the following scenario:</span></span>  
  
     <span data-ttu-id="d3b0d-114">您正在執行使用 SQLXML 4.0 以及與版本無關之 PROGID 的應用程式，而且您決定安裝某個其他軟體程式。</span><span class="sxs-lookup"><span data-stu-id="d3b0d-114">You are running an application that uses SQLXML 4.0 and version-independent PROGIDs, and you decide to install some other software program.</span></span> <span data-ttu-id="d3b0d-115">此程式可能會安裝舊版的 SQLXML。</span><span class="sxs-lookup"><span data-stu-id="d3b0d-115">This program might install an earlier version of SQLXML.</span></span> <span data-ttu-id="d3b0d-116">您的應用程式可能會失敗，因為應用程式內與版本無關的 PROGIDS 現在指向舊版的 SQLXML，它不一定擁有您的應用程式所使用的 SQLXML 功能。</span><span class="sxs-lookup"><span data-stu-id="d3b0d-116">Your application may fail because the version-independent PROGIDS in your application now point to the earlier version of SQLXML, which may or may not have the SQLXML feature that your application is using.</span></span>  
  
-   <span data-ttu-id="d3b0d-117">如果您因為任何原因而不想使用 SQLXMLOLEDB 提供者，而想要使用 SQLXML 提供者的功能，請將**Sqlxml Version**屬性設定為 "sqlxml. 4.0"。</span><span class="sxs-lookup"><span data-stu-id="d3b0d-117">If for any reason you don't want to use the SQLXMLOLEDB provider, and instead want to use the SQLOLEDB provider for SQLXML features, set the **SQLXML Version** property to "SQLXML.4.0".</span></span>  
  
  
