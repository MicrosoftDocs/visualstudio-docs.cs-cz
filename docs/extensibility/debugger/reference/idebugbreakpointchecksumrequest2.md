---
title: IDebugBreakpointChecksumRequest2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 632c3611f6c03a47a7d46e985eb6aa2685864a7f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735123"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Představuje kontrolní součet dokumentu pro požadavek na zarážku.

## <a name="syntax"></a>Syntaxe

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Implementována [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ladicí balíček a spotřebované ladicí motory.

## <a name="methods"></a>Metody
 V následující tabulce jsou `IDebugBreakpointChecksumRequest2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Načte kontrolní součet dokumentu pro požadavek na zarážky vzhledem k jedinečnému identifikátoru algoritmu kontrolního součtu, který má být používán.|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Určuje, zda je kontrolní součet pro tento dokument povolen.|

## <a name="requirements"></a>Požadavky
 Záhlaví: Msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
