---
title: ISSCommandWithParameters::GetParameterProperties (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
author: rothja
ms.author: jroth
ms.openlocfilehash: 2160c93748375a4aa3bee3d530d441182204134a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594039"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a><span data-ttu-id="e80bc-102">ISSCommandWithParameters::GetParameterProperties (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="e80bc-102">ISSCommandWithParameters::GetParameterProperties (OLE DB)</span></span>
  <span data-ttu-id="e80bc-103">傳回 SSPARAMPROPS 屬性集結構的陣列，而且每個 UDT 或 XML 參數使用一個 SSPARAMPROPS 屬性集。</span><span class="sxs-lookup"><span data-stu-id="e80bc-103">Returns an array of SSPARAMPROPS property set structures, one SSPARAMPROPS property set for each UDT or XML parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e80bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="e80bc-104">Syntax</span></span>  
  
```  
  
HRESULT GetParameterProperties(  
DB_UPARAMS *pcParams,  
SSPARAMPROPS **prgParamProperties);  
```  
  
## <a name="arguments"></a><span data-ttu-id="e80bc-105">引數</span><span class="sxs-lookup"><span data-stu-id="e80bc-105">Arguments</span></span>  
 <span data-ttu-id="e80bc-106">*pcParams*[out][in]</span><span class="sxs-lookup"><span data-stu-id="e80bc-106">*pcParams*[out][in]</span></span>  
 <span data-ttu-id="e80bc-107">記憶體的指標，其中包含在 *prgParamProperties* 中傳回的 SSPARAMPROPS 結構數目。</span><span class="sxs-lookup"><span data-stu-id="e80bc-107">A pointer to memory that contains the number of SSPARAMPROPS structures returned in *prgParamProperties*.</span></span>  
  
 <span data-ttu-id="e80bc-108">*prgParamProperties*[out]</span><span class="sxs-lookup"><span data-stu-id="e80bc-108">*prgParamProperties*[out]</span></span>  
 <span data-ttu-id="e80bc-109">藉其傳回 SSPARAMPROPS 結構陣列的記憶體指標。</span><span class="sxs-lookup"><span data-stu-id="e80bc-109">A pointer to memory in which an array of SSPARAMPROPS structures is returned.</span></span> <span data-ttu-id="e80bc-110">提供者會為結構配置記憶體，並將位址傳回此記憶體;取用者不再需要結構時，會使用**IMalloc：： Free**釋放此記憶體。</span><span class="sxs-lookup"><span data-stu-id="e80bc-110">The provider allocates memory for the structures and returns the address to this memory; the consumer releases this memory with **IMalloc::Free** when it no longer needs the structures.</span></span> <span data-ttu-id="e80bc-111">在呼叫**IMalloc：： Free** for *prgParamProperties*之前，取用者也必須呼叫每個 DBPROP 結構的*vValue*屬性的**VariantClear** ，以便在 variant 包含參考型別 (例如 BSTR 的情況下，避免發生記憶體流失的情況。 ) 如果輸出上的*時 pcparams*為零，或是 DB_E_ERRORSOCCURRED 發生的錯誤，則提供者不會配置任何記憶體，並確保*prgParamProperties*在輸出上為 null 指標。</span><span class="sxs-lookup"><span data-stu-id="e80bc-111">Before calling **IMalloc::Free** for *prgParamProperties*, the consumer must also call **VariantClear** for the *vValue* property of each DBPROP structure in order to prevent a memory leak in cases where the variant contains a reference type (such as a BSTR.) If *pcParams* is zero on output or an error other than DB_E_ERRORSOCCURRED occurs, the provider does not allocate any memory and ensures that *prgParamProperties* is a null pointer on output.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="e80bc-112">傳回碼值</span><span class="sxs-lookup"><span data-stu-id="e80bc-112">Return Code Values</span></span>  
 <span data-ttu-id="e80bc-113">**GetParameterProperties**方法會傳回與 Core OLE DB **ICommandProperties：： GetProperties**方法相同的錯誤碼，不同之處在于無法引發 DB_S_ERRORSOCCURRED 和 DB_E_ERRORSOCCURED。</span><span class="sxs-lookup"><span data-stu-id="e80bc-113">The **GetParameterProperties** method returns the same error codes as the core OLE DB **ICommandProperties::GetProperties** method, except that DB_S_ERRORSOCCURRED and DB_E_ERRORSOCCURED cannot be raised.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e80bc-114">備註</span><span class="sxs-lookup"><span data-stu-id="e80bc-114">Remarks</span></span>  
 <span data-ttu-id="e80bc-115">**ISSCommandWithParameters：： GetParameterProperties**的行為一致，與**GetParameterInfo**有關。</span><span class="sxs-lookup"><span data-stu-id="e80bc-115">**ISSCommandWithParameters::GetParameterProperties** behaves consistently with respect to **GetParameterInfo**.</span></span> <span data-ttu-id="e80bc-116">如果尚未呼叫[ISSCommandWithParameters：： SetParameterProperties](isscommandwithparameters-setparameterproperties-ole-db.md)或**SetParameterInfo** ，或已使用 cParams 等於零的呼叫， **GetParameterInfo**會衍生參數資訊，並傳回這個。</span><span class="sxs-lookup"><span data-stu-id="e80bc-116">If [ISSCommandWithParameters::SetParameterProperties](isscommandwithparameters-setparameterproperties-ole-db.md) or **SetParameterInfo** have not been called or have been called with cParams equal to zero, **GetParameterInfo** derives parameter information and returns this.</span></span> <span data-ttu-id="e80bc-117">如果至少已針對一個參數呼叫**ISSCommandWithParameters：： SetParameterProperties**或**SetParameterInfo** ， **ISSCommandWithParameters：： GetParameterProperties**只會針對已呼叫**ISSCommandWithParameters：： SetParameterProperties**的參數傳回屬性。</span><span class="sxs-lookup"><span data-stu-id="e80bc-117">If **ISSCommandWithParameters::SetParameterProperties** or **SetParameterInfo** have been called for at least one parameter, **ISSCommandWithParameters::GetParameterProperties** returns properties only for those parameters for which **ISSCommandWithParameters::SetParameterProperties** has been called.</span></span> <span data-ttu-id="e80bc-118">如果在**ISSCommandWithParameters：： GetParameterProperties**或**GetParameterInfo**之後呼叫**ISSCommandWithParameters：： SetParameterProperties** ，則對**ISSCommandWithParameters：： GetParameterProperties**的後續呼叫會針對已呼叫**ISSCommandWithParameters：： SetParameterProperties**的參數傳回覆寫的值。</span><span class="sxs-lookup"><span data-stu-id="e80bc-118">If **ISSCommandWithParameters::SetParameterProperties** is called after **ISSCommandWithParameters::GetParameterProperties** or **GetParameterInfo**, subsequent calls to **ISSCommandWithParameters::GetParameterProperties** return the overridden values for those parameters for which **ISSCommandWithParameters::SetParameterProperties** has been called.</span></span>  
  
 <span data-ttu-id="e80bc-119">SSPARAMPROPS 結構定義如下：</span><span class="sxs-lookup"><span data-stu-id="e80bc-119">The SSPARAMPROPS structure is defined as follows:</span></span>  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|<span data-ttu-id="e80bc-120">成員</span><span class="sxs-lookup"><span data-stu-id="e80bc-120">Member</span></span>|<span data-ttu-id="e80bc-121">描述</span><span class="sxs-lookup"><span data-stu-id="e80bc-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e80bc-122">*iOrdinal*</span><span class="sxs-lookup"><span data-stu-id="e80bc-122">*iOrdinal*</span></span>|<span data-ttu-id="e80bc-123">所傳遞參數的序數。</span><span class="sxs-lookup"><span data-stu-id="e80bc-123">The ordinal of the passed parameter.</span></span>|  
|<span data-ttu-id="e80bc-124">*cPropertySets*</span><span class="sxs-lookup"><span data-stu-id="e80bc-124">*cPropertySets*</span></span>|<span data-ttu-id="e80bc-125">*rgPropertySets* 中的 DBPROPSET 結構數目。</span><span class="sxs-lookup"><span data-stu-id="e80bc-125">The number of DBPROPSET structures in *rgPropertySets*.</span></span>|  
|<span data-ttu-id="e80bc-126">*rgPropertySets*</span><span class="sxs-lookup"><span data-stu-id="e80bc-126">*rgPropertySets*</span></span>|<span data-ttu-id="e80bc-127">藉其傳回 DBPROPSET 結構陣列的記憶體指標。</span><span class="sxs-lookup"><span data-stu-id="e80bc-127">A pointer to memory in which to return an array of DBPROPSET structures.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e80bc-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e80bc-128">See Also</span></span>  
 [<span data-ttu-id="e80bc-129">ISSCommandWithParameters &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="e80bc-129">ISSCommandWithParameters &#40;OLE DB&#41;</span></span>](isscommandwithparameters-ole-db.md)  
  
  
