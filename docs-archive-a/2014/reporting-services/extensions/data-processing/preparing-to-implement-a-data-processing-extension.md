---
title: 準備實作資料處理延伸模組 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- interfaces [Reporting Services]
- data processing extensions [Reporting Services], implementing
ms.assetid: 698817e4-33da-4eb5-9407-4103e1c35247
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3588aea825233631cb4ad7752919ad88bb4dbf5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708942"
---
# <a name="preparing-to-implement-a-data-processing-extension"></a><span data-ttu-id="faf33-102">準備實作資料處理延伸模組</span><span class="sxs-lookup"><span data-stu-id="faf33-102">Preparing to Implement a Data Processing Extension</span></span>
  <span data-ttu-id="faf33-103">在您實作 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組之前，應該定義要實作的介面。</span><span class="sxs-lookup"><span data-stu-id="faf33-103">Before you implement your [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension, you should define the interfaces to implement.</span></span> <span data-ttu-id="faf33-104">您可能會想要提供整組介面的延伸模組特定實作，或者您可能會直接將實作的集點放在子集上，例如 <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> 與 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> 介面，其中用戶端主要會與作為 **DataReader** 物件的結果集互動，而且將使用 [!INCLUDE[ssRS](../../../includes/ssrs.md)] 資料處理延伸模組作為結果集與資料來源之間的橋樑。</span><span class="sxs-lookup"><span data-stu-id="faf33-104">You may want to provide extension-specific implementations of the entire set of interfaces, or you may simply want to focus your implementation on a subset, such as the <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> and <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> interfaces in which clients would interact primarily with a result set as a **DataReader** object and would use your [!INCLUDE[ssRS](../../../includes/ssrs.md)] data processing extension as a bridge between the result set and your data source.</span></span>  
  
 <span data-ttu-id="faf33-105">您可以使用兩種方法之一來實作資料處理延伸模組：</span><span class="sxs-lookup"><span data-stu-id="faf33-105">You can implement data processing extensions in one of two ways:</span></span>  
  
-   <span data-ttu-id="faf33-106">您的資料處理延伸模組類別可以實作 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 資料提供者介面，並選擇性地擴充 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 提供的資料處理延伸模組介面。</span><span class="sxs-lookup"><span data-stu-id="faf33-106">Your data processing extension classes can implement the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data provider interfaces and optionally the extended data processing extension interfaces provided by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="faf33-107">您的資料處理延伸模組類別可以實作 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 提供的資料處理延伸模組介面，並選擇性地擴充資料處理延伸模組介面。</span><span class="sxs-lookup"><span data-stu-id="faf33-107">Your data processing extension classes can implement the data processing extension interfaces provided by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] and optionally the extended data processing extension interfaces.</span></span>  
  
 <span data-ttu-id="faf33-108">如果您的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組不支援特定的屬性或方法，請將屬性或方法實作成無作業。</span><span class="sxs-lookup"><span data-stu-id="faf33-108">If your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension will not support a particular property or method, implement the property or method as no-operation.</span></span> <span data-ttu-id="faf33-109">如果用戶端預期特定的行為，會擲回 **NotSupportedException** 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="faf33-109">If a client expects a particular behavior, throw a **NotSupportedException** exception.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="faf33-110">屬性或方法的無作業實作，只適用於您選擇實作的那些介面之屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="faf33-110">A no-operation implementation of a property or method only applies to the properties and methods of those interfaces that you choose to implement.</span></span> <span data-ttu-id="faf33-111">您選擇不實作的選擇性介面應該從資料處理延伸模組組件中排除。</span><span class="sxs-lookup"><span data-stu-id="faf33-111">Optional interfaces that you choose not to implement should be left out of your data processing extension assembly.</span></span> <span data-ttu-id="faf33-112">如需有關介面是必要或選擇性的詳細資訊，請參閱本節稍後的資料表。</span><span class="sxs-lookup"><span data-stu-id="faf33-112">For more information about whether an interface is required or optional, see the table later in this section.</span></span>  
  
## <a name="required-extension-functionality"></a><span data-ttu-id="faf33-113">必要的擴充功能</span><span class="sxs-lookup"><span data-stu-id="faf33-113">Required Extension Functionality</span></span>  
 <span data-ttu-id="faf33-114">每個 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組必須提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="faf33-114">Each [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension must provide the following functionality:</span></span>  
  
-   <span data-ttu-id="faf33-115">開啟資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="faf33-115">Open a connection to a data source.</span></span>  
  
-   <span data-ttu-id="faf33-116">分析查詢並傳回結果集的欄位名稱清單。</span><span class="sxs-lookup"><span data-stu-id="faf33-116">Analyze a query and return a list of field names for the result set.</span></span>  
  
-   <span data-ttu-id="faf33-117">針對資料來源執行查詢並傳回資料列集。</span><span class="sxs-lookup"><span data-stu-id="faf33-117">Execute a query against the data source and return a row set.</span></span>  
  
-   <span data-ttu-id="faf33-118">將單一值參數傳遞至查詢。</span><span class="sxs-lookup"><span data-stu-id="faf33-118">Pass single-valued parameters to the query.</span></span>  
  
-   <span data-ttu-id="faf33-119">反覆運算資料列集中的資料列並擷取資料。</span><span class="sxs-lookup"><span data-stu-id="faf33-119">Iterate through rows in the row set and retrieve data.</span></span>  
  
 <span data-ttu-id="faf33-120">每個資料處理延伸模組都可加以擴充以包括下列功能：</span><span class="sxs-lookup"><span data-stu-id="faf33-120">Each data processing extension can be extended to include the following functionality:</span></span>  
  
-   <span data-ttu-id="faf33-121">分析查詢並傳回查詢所使用的參數名稱清單。</span><span class="sxs-lookup"><span data-stu-id="faf33-121">Analyze a query and return a list of parameter names used in the query.</span></span>  
  
-   <span data-ttu-id="faf33-122">分析查詢並傳回群組查詢所依據的欄位清單。</span><span class="sxs-lookup"><span data-stu-id="faf33-122">Analyze a query and return the list of fields by which the query is grouped.</span></span>  
  
-   <span data-ttu-id="faf33-123">分析查詢並傳回排序查詢所依據的欄位清單。</span><span class="sxs-lookup"><span data-stu-id="faf33-123">Analyze a query and return the list of fields by which the query is sorted.</span></span>  
  
-   <span data-ttu-id="faf33-124">提供使用者名稱與密碼以連接與連接字串無關的資料來源。</span><span class="sxs-lookup"><span data-stu-id="faf33-124">Provide a user name and password to connect to the data source that is independent of the connection string.</span></span>  
  
-   <span data-ttu-id="faf33-125">反覆運算資料列集中的資料列，並擷取有關資料值的輔助中繼資料。</span><span class="sxs-lookup"><span data-stu-id="faf33-125">Iterate through rows in the row set and retrieve auxiliary metadata about the data values.</span></span>  
  
-   <span data-ttu-id="faf33-126">在伺服器彙總資料。</span><span class="sxs-lookup"><span data-stu-id="faf33-126">Aggregate data at the server.</span></span>  
  
## <a name="available-extension-interfaces"></a><span data-ttu-id="faf33-127">可用的延伸模組介面</span><span class="sxs-lookup"><span data-stu-id="faf33-127">Available Extension Interfaces</span></span>  
 <span data-ttu-id="faf33-128">下表描述可用的介面，以及實作是否為必要或為選擇性。</span><span class="sxs-lookup"><span data-stu-id="faf33-128">The following table describes the available interfaces and whether implementation is required or optional.</span></span>  
  
|<span data-ttu-id="faf33-129">介面</span><span class="sxs-lookup"><span data-stu-id="faf33-129">Interface</span></span>|<span data-ttu-id="faf33-130">描述</span><span class="sxs-lookup"><span data-stu-id="faf33-130">Description</span></span>|<span data-ttu-id="faf33-131">實作</span><span class="sxs-lookup"><span data-stu-id="faf33-131">Implementation</span></span>|  
|---------------|-----------------|--------------------|  
|<span data-ttu-id="faf33-132">IDbConnection</span><span class="sxs-lookup"><span data-stu-id="faf33-132">IDbConnection</span></span>|<span data-ttu-id="faf33-133">代表資料來源的唯一工作階段。</span><span class="sxs-lookup"><span data-stu-id="faf33-133">Represents a unique session with a data source.</span></span> <span data-ttu-id="faf33-134">在用戶端/伺服器資料庫系統的情況下，此工作階段可能相當於伺服器的網路連接。</span><span class="sxs-lookup"><span data-stu-id="faf33-134">In the case of a client/server database system, the session may be equivalent to a network connection to the server.</span></span>|<span data-ttu-id="faf33-135">必要</span><span class="sxs-lookup"><span data-stu-id="faf33-135">Required</span></span>|  
|<span data-ttu-id="faf33-136">IDbConnectionExtension</span><span class="sxs-lookup"><span data-stu-id="faf33-136">IDbConnectionExtension</span></span>|<span data-ttu-id="faf33-137">代表有關安全性與驗證之 [!INCLUDE[ssRS](../../../includes/ssrs.md)] 資料處理延伸模組所實作的其他連接屬性。</span><span class="sxs-lookup"><span data-stu-id="faf33-137">Represents additional connection properties that can be implemented by [!INCLUDE[ssRS](../../../includes/ssrs.md)] data processing extensions regarding security and authentication.</span></span>|<span data-ttu-id="faf33-138">選用</span><span class="sxs-lookup"><span data-stu-id="faf33-138">Optional</span></span>|  
|<span data-ttu-id="faf33-139">IDbTransaction</span><span class="sxs-lookup"><span data-stu-id="faf33-139">IDbTransaction</span></span>|<span data-ttu-id="faf33-140">表示本機交易。</span><span class="sxs-lookup"><span data-stu-id="faf33-140">Represents a local transaction.</span></span>|<span data-ttu-id="faf33-141">必要</span><span class="sxs-lookup"><span data-stu-id="faf33-141">Required</span></span>|  
|<span data-ttu-id="faf33-142">IDbTransactionExtension</span><span class="sxs-lookup"><span data-stu-id="faf33-142">IDbTransactionExtension</span></span>|<span data-ttu-id="faf33-143">代表可由 [!INCLUDE[ssRS](../../../includes/ssrs.md)] 資料處理延伸模組所實作的其他交易屬性。</span><span class="sxs-lookup"><span data-stu-id="faf33-143">Represents additional transaction properties that can be implemented by [!INCLUDE[ssRS](../../../includes/ssrs.md)] data processing extensions.</span></span>|<span data-ttu-id="faf33-144">選用</span><span class="sxs-lookup"><span data-stu-id="faf33-144">Optional</span></span>|  
|<span data-ttu-id="faf33-145">IDbCommand</span><span class="sxs-lookup"><span data-stu-id="faf33-145">IDbCommand</span></span>|<span data-ttu-id="faf33-146">代表當連接到資料來源時所使用的查詢或命令。</span><span class="sxs-lookup"><span data-stu-id="faf33-146">Represents a query or command that is used when connected to a data source.</span></span>|<span data-ttu-id="faf33-147">必要</span><span class="sxs-lookup"><span data-stu-id="faf33-147">Required</span></span>|  
|<span data-ttu-id="faf33-148">IDbCommandAnalysis</span><span class="sxs-lookup"><span data-stu-id="faf33-148">IDbCommandAnalysis</span></span>|<span data-ttu-id="faf33-149">代表分析查詢和傳回用於查詢的參數名稱清單的其他命令資訊。</span><span class="sxs-lookup"><span data-stu-id="faf33-149">Represents additional command information for analyzing a query and returning a list of parameter names used in the query.</span></span>|<span data-ttu-id="faf33-150">選用</span><span class="sxs-lookup"><span data-stu-id="faf33-150">Optional</span></span>|  
|<span data-ttu-id="faf33-151">IDataParameter</span><span class="sxs-lookup"><span data-stu-id="faf33-151">IDataParameter</span></span>|<span data-ttu-id="faf33-152">代表傳遞到命令或查詢的參數或名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="faf33-152">Represents a parameter or name/value pair that is passed to a command or query.</span></span>|<span data-ttu-id="faf33-153">必要</span><span class="sxs-lookup"><span data-stu-id="faf33-153">Required</span></span>|  
|<span data-ttu-id="faf33-154">IDataParameterCollection</span><span class="sxs-lookup"><span data-stu-id="faf33-154">IDataParameterCollection</span></span>|<span data-ttu-id="faf33-155">代表所有與命令或查詢相關的參數集合。</span><span class="sxs-lookup"><span data-stu-id="faf33-155">Represents a collection of all parameters relevant to a command or query.</span></span>|<span data-ttu-id="faf33-156">必要</span><span class="sxs-lookup"><span data-stu-id="faf33-156">Required</span></span>|  
|<span data-ttu-id="faf33-157">IDataReader</span><span class="sxs-lookup"><span data-stu-id="faf33-157">IDataReader</span></span>|<span data-ttu-id="faf33-158">提供一種方法，可順向且唯讀地讀取來自資料來源的資料流。</span><span class="sxs-lookup"><span data-stu-id="faf33-158">Provides a method of reading a forward-only, read-only stream of data from your data source.</span></span>|<span data-ttu-id="faf33-159">必要</span><span class="sxs-lookup"><span data-stu-id="faf33-159">Required</span></span>|  
|<span data-ttu-id="faf33-160">IDataReaderExtension</span><span class="sxs-lookup"><span data-stu-id="faf33-160">IDataReaderExtension</span></span>|<span data-ttu-id="faf33-161">提供方法來讀取一或多個藉由在資料來源處執行命令所取得的順向資料流之結果集。</span><span class="sxs-lookup"><span data-stu-id="faf33-161">Provides a method of reading one or more forward-only streams of result sets, obtained by executing a command at a data source.</span></span> <span data-ttu-id="faf33-162">這個介面會提供其他支援的欄位彙總。</span><span class="sxs-lookup"><span data-stu-id="faf33-162">This interface provides additional support for field aggregates.</span></span>|<span data-ttu-id="faf33-163">選用</span><span class="sxs-lookup"><span data-stu-id="faf33-163">Optional</span></span>|  
|<span data-ttu-id="faf33-164">IExtension</span><span class="sxs-lookup"><span data-stu-id="faf33-164">IExtension</span></span>|<span data-ttu-id="faf33-165">提供 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組的基底類別。</span><span class="sxs-lookup"><span data-stu-id="faf33-165">Provides the base class for a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension.</span></span> <span data-ttu-id="faf33-166">另外也可讓實作者包括當地語系化的延伸模組名稱，並將組態設定從組態檔傳遞到延伸模組。</span><span class="sxs-lookup"><span data-stu-id="faf33-166">Also enables an implementer to include a localized name for the extension and to pass configuration settings from the configuration file to the extension.</span></span>|<span data-ttu-id="faf33-167">必要</span><span class="sxs-lookup"><span data-stu-id="faf33-167">Required</span></span>|  
  
 <span data-ttu-id="faf33-168">資料處理延伸模組介面會盡可能與 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 資料提供者介面、方法及屬性的子集相同。</span><span class="sxs-lookup"><span data-stu-id="faf33-168">The data processing extension interfaces are identical to a subset of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data provider interfaces, methods, and properties whenever possible.</span></span> <span data-ttu-id="faf33-169">如需有關實作完整 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 資料提供者的詳細資訊，請參閱＜[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 軟體開發套件 (SDK) 文件集中的＜實作 .NET Framework 資料提供者＞。</span><span class="sxs-lookup"><span data-stu-id="faf33-169">For more information about implementing a full [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data provider, see "Implementing a .NET Framework Data Provider" in your [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Software Development Kit (SDK) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf33-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="faf33-170">See Also</span></span>  
 <span data-ttu-id="faf33-171">[Reporting Services 延伸模組](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="faf33-171">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="faf33-172">[實作資料處理延伸模組](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="faf33-172">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="faf33-173">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="faf33-173">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
