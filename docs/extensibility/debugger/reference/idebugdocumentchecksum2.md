---
title: IDebugDocumentChecksum2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03cfb29cc54a2f0ab18bce3ec0761cfab62e20df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731900"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Představuje kontrolní součet pro ladicí dokument a umožňuje předávání kontrolního součtu mezi součástmi.

## <a name="syntax"></a>Syntaxe

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní může být implementováno libovolnou komponentou, která zveřejňuje rozhraní [IDebugDocumentContext2.](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Je však hlavně implementována ladicími moduly tak, aby kontrolní součet vložený do souboru symbolů (*.pdb) mohl být předán zpět do integrovaného systému ide a použit při hledání zdroje.

## <a name="methods"></a>Metody
 V následující tabulce jsou `IDebugDocumentChecksum2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Načte kontrolní součet dokumentu a identifikátor algoritmu s maximálním počtem bajtů, které mají být používány.|

## <a name="requirements"></a>Požadavky
 Záhlaví: Msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
