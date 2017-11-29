---
title: "ICorDebugStackWalk::GetFrame 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.GetFrame Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bef8cfc13727913e9311b5ce847190fe5544dc18
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="716df-102">ICorDebugStackWalk::GetFrame 方法</span><span class="sxs-lookup"><span data-stu-id="716df-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="716df-103">获取当前帧中[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)对象。</span><span class="sxs-lookup"><span data-stu-id="716df-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="716df-104">语法</span><span class="sxs-lookup"><span data-stu-id="716df-104">Syntax</span></span>  
  
```  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="716df-105">参数</span><span class="sxs-lookup"><span data-stu-id="716df-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="716df-106">[in]指向表示当前帧堆栈中的创建的框架对象的地址的指针。</span><span class="sxs-lookup"><span data-stu-id="716df-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="716df-107">返回值</span><span class="sxs-lookup"><span data-stu-id="716df-107">Return Value</span></span>  
 <span data-ttu-id="716df-108">此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。</span><span class="sxs-lookup"><span data-stu-id="716df-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="716df-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="716df-109">HRESULT</span></span>|<span data-ttu-id="716df-110">描述</span><span class="sxs-lookup"><span data-stu-id="716df-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="716df-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="716df-111">S_OK</span></span>|<span data-ttu-id="716df-112">运行时成功地返回当前帧。</span><span class="sxs-lookup"><span data-stu-id="716df-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="716df-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="716df-113">E_FAIL</span></span>|<span data-ttu-id="716df-114">不返回当前帧。</span><span class="sxs-lookup"><span data-stu-id="716df-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="716df-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="716df-115">S_FALSE</span></span>|<span data-ttu-id="716df-116">当前帧是本机的堆栈帧。</span><span class="sxs-lookup"><span data-stu-id="716df-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="716df-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="716df-117">E_INVALIDARG</span></span>|<span data-ttu-id="716df-118">`pFrame` 为 null。</span><span class="sxs-lookup"><span data-stu-id="716df-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="716df-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="716df-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="716df-120">帧指针是已在堆栈; 末尾因此，可以不访问任何其他帧。</span><span class="sxs-lookup"><span data-stu-id="716df-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="716df-121">异常</span><span class="sxs-lookup"><span data-stu-id="716df-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="716df-122">备注</span><span class="sxs-lookup"><span data-stu-id="716df-122">Remarks</span></span>  
 <span data-ttu-id="716df-123">`ICorDebugStackWalk`返回仅实际堆栈帧。</span><span class="sxs-lookup"><span data-stu-id="716df-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="716df-124">使用[icordebugthread3:: Getactiveinternalframes](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)方法以返回内部帧。</span><span class="sxs-lookup"><span data-stu-id="716df-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="716df-125">（内部帧是推送到堆栈由运行时存储临时数据的数据结构。）</span><span class="sxs-lookup"><span data-stu-id="716df-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="716df-126">要求</span><span class="sxs-lookup"><span data-stu-id="716df-126">Requirements</span></span>  
 <span data-ttu-id="716df-127">**平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="716df-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="716df-128">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="716df-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="716df-129">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="716df-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="716df-130">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="716df-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="716df-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="716df-131">See Also</span></span>  
 [<span data-ttu-id="716df-132">ICorDebugStackWalk 接口</span><span class="sxs-lookup"><span data-stu-id="716df-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [<span data-ttu-id="716df-133">调试接口</span><span class="sxs-lookup"><span data-stu-id="716df-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="716df-134">调试</span><span class="sxs-lookup"><span data-stu-id="716df-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)