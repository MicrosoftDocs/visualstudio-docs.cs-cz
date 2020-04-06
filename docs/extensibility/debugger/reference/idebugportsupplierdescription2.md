---
title: IDebugPortSupplierDescription2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69853e34788a2f24afe183dfbb7070e48f14aa46
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724364"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Umožňuje ui zobrazit text uvnitř části **Informace o přenosu** v dialogovém okně Připojit k **procesu.** [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]

## <a name="syntax"></a>Syntaxe

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno dodavateli portů.

## <a name="methods"></a>Metody
 V následující tabulce jsou `IDebugPortSupplierDescription2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Načte metadata popisu a popisu pro dodavatele portu.|

## <a name="requirements"></a>Požadavky
 Záhlaví: Msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
