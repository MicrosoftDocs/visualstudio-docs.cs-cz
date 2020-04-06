---
title: iPropertyProxyeeside::GetmanagedViewerCreationData | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e72922b348c8744f10037e199e93f735ff4be8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714961"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Načte informace o prohlížeči pro tento typ vlastnosti, aby mohl vytvořit konkretizovat tento prohlížeč.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
   out string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     className,
   out enum_ASSEMBLYLOCRESOLUTION alr,
   out int                        replacementOk
);
```

## <a name="parameters"></a>Parametry
`assemName`\
[out] Vrátí název sestavení, které drží tento objekt.

`assemBytes`\
[out] Vrátí objekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) obsahující bajty sestavení tohoto objektu (toto je hodnota null, pokud nejsou k dispozici žádné bajty).

`assemPdb`\
[out] Vrátí `IEEDataStorage` objekt obsahující informace o úložišti symbolů pro tento objekt (toto je hodnota null, pokud není k dispozici žádné úložiště symbolů).

`className`\
[out] Vrátí název třídy obsahující tento objekt.

`alr`\
[out] Vrátí hodnotu z výčtu [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) označující umístění sestavení.

`replacementOk`\
[out] Vrátí nenulovou hodnotu (`TRUE`), pokud lze hodnotu tohoto objektu změnit; zero`FALSE`( ), pokud je objekt jen pro čtení.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda se používá typ vizualizéry k vytvoření instance spravovaného prohlížeče.

## <a name="see-also"></a>Viz také
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
