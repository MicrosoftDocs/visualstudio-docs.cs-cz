---
description: Vytvoří enumerátor pro rozhraní implementované touto třídou.
title: 'IDebugClassField:: EnumInterfacesImplemented | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f90bf6efc3a34e4f6b9f60ef5bdadb0640f495b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164315"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Vytvoří enumerátor pro rozhraní implementované touto třídou.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumInterfacesImplemented( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumInterfacesImplemented(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
mimo Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam implementovaných rozhraní. Vrací hodnotu null, pokud nejsou k dispozici žádná rozhraní.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK nebo vrátí S_FALSE, pokud pro tuto třídu nejsou implementována žádná rozhraní. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Každý prvek výčtu je objekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) popisující rozhraní. Všimněte si, že nespravovaný [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] kód nepoužívá rozhraní jako diskrétní entitu, takže tato metoda vždy vrátí hodnotu null pro nespravovaný [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] kód.

## <a name="see-also"></a>Viz také
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
