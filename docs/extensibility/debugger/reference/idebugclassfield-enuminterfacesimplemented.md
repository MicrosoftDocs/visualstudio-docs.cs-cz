---
title: IDebugClassField::EnumInterfacesImplemented | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91d9cac6b695ba2a0d34da776fa79ba62ba2e015
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734484"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Vytvoří čítač pro rozhraní implementované touto třídou.

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
[out] Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam implementovaných rozhraní. Vrátí hodnotu null, pokud neexistují žádná rozhraní.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK nebo vrátí S_FALSE pokud v této třídě nejsou implementována žádná rozhraní. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Každý prvek výčtu je [Objekt IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) popisující rozhraní. Všimněte si, že nespravovaný [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] kód nepoužívá rozhraní jako samostatnou entitu, takže tato metoda vždy vrátí hodnotu null pro nespravovaný [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] kód.

## <a name="see-also"></a>Viz také
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
