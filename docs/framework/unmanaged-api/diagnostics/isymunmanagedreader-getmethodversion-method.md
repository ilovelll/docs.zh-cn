---
title: "ISymUnmanagedReader::GetMethodVersion 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodVersion
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5b57407cb12e4315b6a144d157a201f857614d9f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="e2f4f-102">ISymUnmanagedReader::GetMethodVersion 方法</span><span class="sxs-lookup"><span data-stu-id="e2f4f-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="e2f4f-103">获取的方法版本。</span><span class="sxs-lookup"><span data-stu-id="e2f4f-103">Gets the method version.</span></span> <span data-ttu-id="e2f4f-104">方法版本从 1 开始，并会递增每次重新编译该方法。</span><span class="sxs-lookup"><span data-stu-id="e2f4f-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="e2f4f-105">重新编译可发生方法而无需更改。</span><span class="sxs-lookup"><span data-stu-id="e2f4f-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2f4f-106">语法</span><span class="sxs-lookup"><span data-stu-id="e2f4f-106">Syntax</span></span>  
  
```  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2f4f-107">参数</span><span class="sxs-lookup"><span data-stu-id="e2f4f-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="e2f4f-108">[in]要为其获取版本方法。</span><span class="sxs-lookup"><span data-stu-id="e2f4f-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="e2f4f-109">[out]指向接收方法版本的变量的指针。</span><span class="sxs-lookup"><span data-stu-id="e2f4f-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2f4f-110">返回值</span><span class="sxs-lookup"><span data-stu-id="e2f4f-110">Return Value</span></span>  
 <span data-ttu-id="e2f4f-111">如果该方法成功; 则为 S_OK否则为 E_FAIL 或某些其他错误代码。</span><span class="sxs-lookup"><span data-stu-id="e2f4f-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2f4f-112">要求</span><span class="sxs-lookup"><span data-stu-id="e2f4f-112">Requirements</span></span>  
 <span data-ttu-id="e2f4f-113">**标头：** CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e2f4f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f4f-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2f4f-114">See Also</span></span>  
 [<span data-ttu-id="e2f4f-115">ISymUnmanagedReader 接口</span><span class="sxs-lookup"><span data-stu-id="e2f4f-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)