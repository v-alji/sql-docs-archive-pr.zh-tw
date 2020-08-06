---
title: ISSCommandWithParameters::SetParameterProperties (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
author: rothja
ms.author: jroth
ms.openlocfilehash: 4bf8e5cde9885a5d9b55d84c6384b76aecf50b8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687837"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a><span data-ttu-id="56b8b-102">ISSCommandWithParameters::SetParameterProperties (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="56b8b-102">ISSCommandWithParameters::SetParameterProperties (OLE DB)</span></span>
  <span data-ttu-id="56b8b-103">依照序數根據每個參數來設定參數的屬性，或指定 SSPARAMPROPS 結構的陣列來設定大量參數屬性。</span><span class="sxs-lookup"><span data-stu-id="56b8b-103">Sets the parameter properties on a per parameter basis by ordinal, or sets bulk parameter properties by specifying an array of SSPARAMPROPS structures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56b8b-104">語法</span><span class="sxs-lookup"><span data-stu-id="56b8b-104">Syntax</span></span>  
  
```  
  
HRESULT SetParameterProperties(  
DB_UPARAMS cParams,   
SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a><span data-ttu-id="56b8b-105">引數</span><span class="sxs-lookup"><span data-stu-id="56b8b-105">Arguments</span></span>  
 <span data-ttu-id="56b8b-106">*cParams*[in]</span><span class="sxs-lookup"><span data-stu-id="56b8b-106">*cParams*[in]</span></span>  
 <span data-ttu-id="56b8b-107">*rgParamProperties* 陣列中 SSPARAMPROPS 結構的數目。</span><span class="sxs-lookup"><span data-stu-id="56b8b-107">The number of SSPARAMPROPS structures in the *rgParamProperties* array.</span></span> <span data-ttu-id="56b8b-108">如果此數位為零， `ISSCommandWithParameters::SetParameterProperties` 將會刪除命令中所有參數可能已指定的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="56b8b-108">If this number is zero, `ISSCommandWithParameters::SetParameterProperties` will delete all properties that might have been specified for any parameters in the command.</span></span>  
  
 <span data-ttu-id="56b8b-109">*rgParamProperties*[in]</span><span class="sxs-lookup"><span data-stu-id="56b8b-109">*rgParamProperties*[in]</span></span>  
 <span data-ttu-id="56b8b-110">要設定的 SSPARAMPROPS 結構的陣列。</span><span class="sxs-lookup"><span data-stu-id="56b8b-110">An array of SSPARAMPROPS structures to be set.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="56b8b-111">傳回碼值</span><span class="sxs-lookup"><span data-stu-id="56b8b-111">Return Code Values</span></span>  
 <span data-ttu-id="56b8b-112">方法會傳回與 `ISSCommandWithParameters::SetParameterProperties` core OLE DB **ICommandProperties：： SetProperties**方法相同的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="56b8b-112">The `ISSCommandWithParameters::SetParameterProperties` method returns the same error codes as the core OLE DB **ICommandProperties::SetProperties** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56b8b-113">備註</span><span class="sxs-lookup"><span data-stu-id="56b8b-113">Remarks</span></span>  
 <span data-ttu-id="56b8b-114">使用此方法來設定參數屬性時，會依序數，或在 `ISSCommandWithParameters::SetParameterProperties` 從屬性陣列建立 SSPARAMPROPS 之後，以單一呼叫的方式來進行。</span><span class="sxs-lookup"><span data-stu-id="56b8b-114">Setting parameter properties with this method is allowed on a per parameter basis by ordinal, or with a single `ISSCommandWithParameters::SetParameterProperties` call once the SSPARAMPROPS has been built from the property array.</span></span>  
  
 <span data-ttu-id="56b8b-115">呼叫方法之前，必須先呼叫**SetParameterInfo**方法 `ISSCommandWithParameters::SetParameterProperties` 。</span><span class="sxs-lookup"><span data-stu-id="56b8b-115">The **SetParameterInfo** method must be called before calling the `ISSCommandWithParameters::SetParameterProperties` method.</span></span> <span data-ttu-id="56b8b-116">呼叫 `SetParameterProperties(0, NULL)` 會清除所有指定的參數屬性，呼叫 `SetParameterInfo(0,NULL,NULL)` 則會清除所有的參數資訊，包括任何可能與參數相關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="56b8b-116">Calling `SetParameterProperties(0, NULL)` clears all specified parameter properties, while calling `SetParameterInfo(0,NULL,NULL)` clears all the parameter info including any properties that might be associated with a parameter.</span></span>  
  
 <span data-ttu-id="56b8b-117">呼叫 `ISSCommandWithParameters::SetParameterProperties` 以指定不屬於類型 DBTYPE_XML 或 DBTYPE_UDT 的參數屬性會傳回 DB_E_ERRORSOCCURRED 或 DB_S_ERRORSOCCURRED，並將該參數包含在 SSPARAMPROPS 中所有標示出 dbprop 的*dwStatus*欄位標記為 DBPROPSTATUS_NOTSET。</span><span class="sxs-lookup"><span data-stu-id="56b8b-117">Calling `ISSCommandWithParameters::SetParameterProperties` to specify properties for a parameter which is not of type DBTYPE_XML or DBTYPE_UDT returns DB_E_ERRORSOCCURRED or DB_S_ERRORSOCCURRED and marks the *dwStatus* field of all DBPROPs contained in SSPARAMPROPS for that parameter with DBPROPSTATUS_NOTSET.</span></span> <span data-ttu-id="56b8b-118">系統會周遊 SSPARAMPROPS 中包含的每個 DBPROPSET 的 DBPROP 陣列，以偵測 DB_E_ERRORSOCCURRED 或 DB_S_ERRORSOCCURRED 所參考的是哪一個參數。</span><span class="sxs-lookup"><span data-stu-id="56b8b-118">The DBPROP array of each DBPROPSET contained in SSPARAMPROPS should be traversed to detect which parameter the DB_E_ERRORSOCCURRED or DB_S_ERRORSOCCURRED refers to.</span></span>  
  
 <span data-ttu-id="56b8b-119">如果 `ISSCommandWithParameters::SetParameterProperties` 呼叫以指定尚未使用**SetParameterInfo**設定參數資訊的參數屬性，則提供者會傳回 E_UNEXPECTED，並顯示下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="56b8b-119">If `ISSCommandWithParameters::SetParameterProperties` is called to specify the properties of parameters whose parameter info have not been set yet with **SetParameterInfo**, the provider returns E_UNEXPECTED with the following error message:</span></span>  
  
 <span data-ttu-id="56b8b-120">必須先針對指定的參數呼叫 SetParameterInfo 方法，然後才能呼叫 SetParameterProperties 方法。</span><span class="sxs-lookup"><span data-stu-id="56b8b-120">SetParameterProperties method cannot be called for the specified parameters without first calling SetParameterInfo method.</span></span> <span data-ttu-id="56b8b-121">而在設定參數屬性之前，也必須先設定參數資訊。</span><span class="sxs-lookup"><span data-stu-id="56b8b-121">The parameter information must be set before setting the parameter properties.</span></span>  
  
 <span data-ttu-id="56b8b-122">如果呼叫 `ISSCommandWithParameters::SetParameterProperties` 包含已設定參數資訊的某些參數，而且尚未設定參數資訊的某些參數，則 SSPARAMPROPS 屬性集之 DBPROPSET 中的 dwStatus 屬性將會傳回 DBSTATUS_NOTSET。</span><span class="sxs-lookup"><span data-stu-id="56b8b-122">If the call to `ISSCommandWithParameters::SetParameterProperties` contains some parameters where the parameter info has been set, and some parameters where the parameter info has not been set, the dwStatus properties in the DBPROPSET of the SSPARAMPROPS property set will return with DBSTATUS_NOTSET.</span></span>  
  
 <span data-ttu-id="56b8b-123">SSPARAMPROPS 結構定義如下：</span><span class="sxs-lookup"><span data-stu-id="56b8b-123">The SSPARAMPROPS structure is defined as follows:</span></span>  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 <span data-ttu-id="56b8b-124">從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 開始，資料庫引擎的改進功能就允許 ISSCommandWithParameters::SetParameterProperties 針對預期的結果取得更精確的描述。</span><span class="sxs-lookup"><span data-stu-id="56b8b-124">Improvements in the database engine starting with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] allow ISSCommandWithParameters::SetParameterProperties to obtain more accurate descriptions of the expected results.</span></span> <span data-ttu-id="56b8b-125">這些更精確的結果可能會與舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中 ISSCommandWithParameters::SetParameterProperties 所傳回的值不同。</span><span class="sxs-lookup"><span data-stu-id="56b8b-125">These more accurate results may differ from the values returned by ISSCommandWithParameters::SetParameterProperties in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="56b8b-126">如需詳細資訊，請參閱[中繼資料探索](../native-client/features/metadata-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="56b8b-126">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
|<span data-ttu-id="56b8b-127">成員</span><span class="sxs-lookup"><span data-stu-id="56b8b-127">Member</span></span>|<span data-ttu-id="56b8b-128">描述</span><span class="sxs-lookup"><span data-stu-id="56b8b-128">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="56b8b-129">*iOrdinal*</span><span class="sxs-lookup"><span data-stu-id="56b8b-129">*iOrdinal*</span></span>|<span data-ttu-id="56b8b-130">所傳遞參數的序數。</span><span class="sxs-lookup"><span data-stu-id="56b8b-130">The ordinal of the passed parameter.</span></span>|  
|<span data-ttu-id="56b8b-131">*cPropertySets*</span><span class="sxs-lookup"><span data-stu-id="56b8b-131">*cPropertySets*</span></span>|<span data-ttu-id="56b8b-132">*rgPropertySets* 中的 DBPROPSET 結構數目。</span><span class="sxs-lookup"><span data-stu-id="56b8b-132">The number of DBPROPSET structures in *rgPropertySets*.</span></span>|  
|<span data-ttu-id="56b8b-133">*rgPropertySets*</span><span class="sxs-lookup"><span data-stu-id="56b8b-133">*rgPropertySets*</span></span>|<span data-ttu-id="56b8b-134">藉其傳回 DBPROPSET 結構陣列的記憶體指標。</span><span class="sxs-lookup"><span data-stu-id="56b8b-134">A pointer to memory in which to return an array of DBPROPSET structures.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56b8b-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56b8b-135">See Also</span></span>  
 [<span data-ttu-id="56b8b-136">ISSCommandWithParameters &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="56b8b-136">ISSCommandWithParameters &#40;OLE DB&#41;</span></span>](isscommandwithparameters-ole-db.md)  
  
  
