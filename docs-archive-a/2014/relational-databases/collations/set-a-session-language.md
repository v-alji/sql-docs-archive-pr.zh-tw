---
title: 設定工作階段語言 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server], international considerations
- globalization [SQL Server], sessions
- time [SQL Server]
- sessions [SQL Server], languages
- international considerations [SQL Server], sessions
- dates [SQL Server], session languages
- global considerations [SQL Server], sessions
- client-side session language
- time [SQL Server], session languages
- messages [SQL Server], international considerations
- server-side session language
ms.assetid: de7f2c90-8f4f-4cfc-94cc-4933a7fd2bde
author: stevestein
ms.author: sstein
ms.openlocfilehash: da8d6adce66ac5b97e533b5afaefabda40e4b966
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606904"
---
# <a name="set-a-session-language"></a><span data-ttu-id="59589-102">設定工作階段語言</span><span class="sxs-lookup"><span data-stu-id="59589-102">Set a Session Language</span></span>
  <span data-ttu-id="59589-103">工作階段語言可根據語言和文化喜好設定，用來設定在伺服器顯示下列元素的方式：</span><span class="sxs-lookup"><span data-stu-id="59589-103">The session language can be used to set how the following elements are displayed on the server, based on language and cultural preference:</span></span>  
  
-   <span data-ttu-id="59589-104">錯誤訊息與其他系統訊息所使用的語言。</span><span class="sxs-lookup"><span data-stu-id="59589-104">The language that will be used for error and other system messages.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="59589-105">支援所有系統錯誤字串及訊息的多個複本，而支援語言即為所提供之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 語言版本的所有語言。</span><span class="sxs-lookup"><span data-stu-id="59589-105">supports having multiple copies of all system error strings and messages in all the languages in which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is available.</span></span> <span data-ttu-id="59589-106">您可以利用 [sys.messages](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) 目錄檢視來檢視這些訊息。</span><span class="sxs-lookup"><span data-stu-id="59589-106">These messages can be viewed in the [sys.messages](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) catalog view.</span></span> <span data-ttu-id="59589-107">在您安裝當地語系化版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]時，會將這些系統訊息翻譯成您所安裝的語言版本。</span><span class="sxs-lookup"><span data-stu-id="59589-107">When you install a localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], these system messages are translated for the language version that you install.</span></span> <span data-ttu-id="59589-108">依預設，您也會取得美國英文版的這些訊息。</span><span class="sxs-lookup"><span data-stu-id="59589-108">By default, you also obtain the U.S. English set of these messages.</span></span> <span data-ttu-id="59589-109">此外，您也可以使用 [sp_addmessage](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql)，新增以特定語言顯示的使用者自訂訊息。</span><span class="sxs-lookup"><span data-stu-id="59589-109">Additionally, you can add user-defined messages in a specific language by using [sp_addmessage](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql).</span></span>  
  
-   <span data-ttu-id="59589-110">日期和時間資料的格式。</span><span class="sxs-lookup"><span data-stu-id="59589-110">The format of date and time data.</span></span>  
  
-   <span data-ttu-id="59589-111">星期日期和月份的名稱，其中包括縮寫。</span><span class="sxs-lookup"><span data-stu-id="59589-111">The names of days and months, including abbreviations.</span></span>  
  
-   <span data-ttu-id="59589-112">星期的第一天。</span><span class="sxs-lookup"><span data-stu-id="59589-112">The first day of the week.</span></span>  
  
-   <span data-ttu-id="59589-113">貨幣資料。</span><span class="sxs-lookup"><span data-stu-id="59589-113">Currency data.</span></span>  
  
 <span data-ttu-id="59589-114">工作階段設定可以使用 33 種語言。</span><span class="sxs-lookup"><span data-stu-id="59589-114">There are 33 languages available for use as session settings.</span></span> <span data-ttu-id="59589-115">如需語言的清單，請參閱＜ [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql)＞。</span><span class="sxs-lookup"><span data-stu-id="59589-115">For a list of languages, see [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql).</span></span>  
  
## <a name="setting-the-session-language-from-the-server"></a><span data-ttu-id="59589-116">從伺服器設定工作階段語言</span><span class="sxs-lookup"><span data-stu-id="59589-116">Setting the Session Language from the Server</span></span>  
 <span data-ttu-id="59589-117">若要從伺服器端設定工作階段語言，請使用 [SET LANGUAGE](/sql/t-sql/statements/set-language-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="59589-117">To set the session language from the server side, use [SET LANGUAGE](/sql/t-sql/statements/set-language-transact-sql).</span></span>  
  
## <a name="setting-the-session-language-from-the-client"></a><span data-ttu-id="59589-118">從用戶端設定工作階段語言</span><span class="sxs-lookup"><span data-stu-id="59589-118">Setting the Session Language from the Client</span></span>  
 <span data-ttu-id="59589-119">您可以利用 OLE DB、ODBC 或 ADO.NET，在用戶端設定工作階段語言。</span><span class="sxs-lookup"><span data-stu-id="59589-119">The session language can be set on the client side by using OLE DB, ODBC or ADO.NET.</span></span> <span data-ttu-id="59589-120">如果是 OLE DB，請使用 SSPROP_INIT_CURRENTLANGUAGE 屬性。</span><span class="sxs-lookup"><span data-stu-id="59589-120">For OLE DB, use the SSPROP_INIT_CURRENTLANGUAGE property.</span></span> <span data-ttu-id="59589-121">如需詳細資訊，請參閱 [初始化和授權屬性](../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="59589-121">For more information, see [Initialization and Authorization Properties](../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).</span></span>  
  
 <span data-ttu-id="59589-122">如果是 ODBC，請使用 Language 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="59589-122">For ODBC, use the Language keyword.</span></span> <span data-ttu-id="59589-123">如需詳細資訊，請參閱 [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)。</span><span class="sxs-lookup"><span data-stu-id="59589-123">For more information, see [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md).</span></span>  
  
 <span data-ttu-id="59589-124">如果是 ADO.NET，請使用 **ConnectionString** 物件的 **Current Language** 參數。</span><span class="sxs-lookup"><span data-stu-id="59589-124">For ADO.NET, use the **Current Language** parameter of the **ConnectionString** object.</span></span> <span data-ttu-id="59589-125">如需詳細資訊，請參閱 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Access Components (MDAC) 軟體開發套件 (SDK) 文件集。</span><span class="sxs-lookup"><span data-stu-id="59589-125">For more information, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Access Components (MDAC) software development kit (SDK) documentation.</span></span>  
  
  
