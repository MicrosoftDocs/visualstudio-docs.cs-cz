---
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ca8a33626ad68dcac690ca288d4bc375679a4e3e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880772"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Představuje kontrolní součet pro dokument ladění a umožňuje předávání kontrolního součtu mezi komponentami.

## <a name="syntax"></a>Syntax

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní může být implementováno pomocí jakékoli komponenty, která zpřístupňuje rozhraní [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) . Je však v podstatě implementována moduly ladění, takže kontrolní součet vložený do souboru symbolů (*. pdb) lze předat zpět do rozhraní IDE a použít při hledání zdroje.

## <a name="methods"></a>Metody
 V následující tabulce jsou uvedeny metody `IDebugDocumentChecksum2` .

|Metoda|Popis|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Načte kontrolní součet dokumentu a identifikátor algoritmu s maximálním počtem bajtů, které se mají použít.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
