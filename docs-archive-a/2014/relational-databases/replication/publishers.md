---
title: 發行者 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configuredistributionwizard.enablepublishers.f1
ms.assetid: 116cd6a5-32ac-4273-81a2-d184408e0f07
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 879fa3cc2ecadf56914928c6ae83600f513f6ddb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584382"
---
# <a name="publishers"></a><span data-ttu-id="8b7a4-102">發行者</span><span class="sxs-lookup"><span data-stu-id="8b7a4-102">Publishers</span></span>
  <span data-ttu-id="8b7a4-103">您可以提供權限讓其他發行者使用此散發者。</span><span class="sxs-lookup"><span data-stu-id="8b7a4-103">You can give permission for other Publishers to use this Distributor.</span></span> <span data-ttu-id="8b7a4-104">請注意，讓發行者可以使用這個伺服器作為它的遠端散發者，並不會使該伺服器成為發行者。</span><span class="sxs-lookup"><span data-stu-id="8b7a4-104">Be aware that enabling a Publisher to use this server as its remote Distributor does not make that server a Publisher.</span></span> <span data-ttu-id="8b7a4-105">您必須連接到發行者，設定其發行，並選擇此伺服器為散發者。</span><span class="sxs-lookup"><span data-stu-id="8b7a4-105">You must connect to the Publisher, configure it for publishing, and choose this server as the Distributor.</span></span> <span data-ttu-id="8b7a4-106">您可以透過新增發行集精靈來設定發行者和選擇散發者。</span><span class="sxs-lookup"><span data-stu-id="8b7a4-106">You can configure the Publisher and choose a Distributor through the New Publication Wizard.</span></span>  
  
 <span data-ttu-id="8b7a4-107">您選取作為發行者的伺服器，將使用此精靈的 **[散發資料庫]** 頁面上指定的散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="8b7a4-107">The servers you select as Publishers will use the distribution database specified on the **Distribution Database** page of this wizard.</span></span> <span data-ttu-id="8b7a4-108">如果您要使用不同的散發資料庫，此時請不要啟用發行者。</span><span class="sxs-lookup"><span data-stu-id="8b7a4-108">If you want to use a different distribution database, do not enable the Publisher at this time.</span></span> <span data-ttu-id="8b7a4-109">在完成設定散發精靈之後，請改用 **[散發者屬性]** 對話方塊來加入發行者。</span><span class="sxs-lookup"><span data-stu-id="8b7a4-109">Instead, use the **Distributor Properties** dialog box to add Publishers after you complete the Configure Distribution Wizard.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8b7a4-110">選項。</span><span class="sxs-lookup"><span data-stu-id="8b7a4-110">Options</span></span>  
 <span data-ttu-id="8b7a4-111">**發行者**</span><span class="sxs-lookup"><span data-stu-id="8b7a4-111">**Publishers**</span></span>  
 <span data-ttu-id="8b7a4-112">選取可使用這個散發者的伺服器。</span><span class="sxs-lookup"><span data-stu-id="8b7a4-112">Select the servers that are allowed to use this Distributor.</span></span> <span data-ttu-id="8b7a4-113">按一下發行者旁的屬性按鈕 ( **...** )，即可檢視並設定其他屬性。</span><span class="sxs-lookup"><span data-stu-id="8b7a4-113">Click the properties button (**...**) next to a Publisher to view and set additional properties.</span></span>  
  
 <span data-ttu-id="8b7a4-114">**加入**</span><span class="sxs-lookup"><span data-stu-id="8b7a4-114">**Add**</span></span>  
 <span data-ttu-id="8b7a4-115">如果未列出您要允許的伺服器，請按一下 [加入]  ，將 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 發行者或 Oracle 發行者加入可用發行者的清單中。</span><span class="sxs-lookup"><span data-stu-id="8b7a4-115">If the server you want to allow is not listed, click **Add** to add a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher or Oracle Publisher to the list of available Publishers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b7a4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b7a4-116">See Also</span></span>  
 <span data-ttu-id="8b7a4-117">[[設定散發]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="8b7a4-117">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="8b7a4-118">[設定發行和散發](configure-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="8b7a4-118">[Configure Publishing and Distribution](configure-publishing-and-distribution.md) </span></span>  
 <span data-ttu-id="8b7a4-119">[檢視及修改散發者和發行者屬性](view-and-modify-distributor-and-publisher-properties.md) </span><span class="sxs-lookup"><span data-stu-id="8b7a4-119">[View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md) </span></span>  
 [<span data-ttu-id="8b7a4-120">建立發行集</span><span class="sxs-lookup"><span data-stu-id="8b7a4-120">Create a Publication</span></span>](publish/create-a-publication.md)  
  
  
