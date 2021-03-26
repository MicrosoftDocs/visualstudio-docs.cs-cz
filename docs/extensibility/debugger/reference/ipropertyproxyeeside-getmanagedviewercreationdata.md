---
description: Načte informace o prohlížeči pro tento typ vlastnosti, aby bylo možné vytvořit instanci tohoto prohlížeče.
title: 'IPropertyProxyEESide:: GetManagedViewerCreationData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc0ab85a3000db2090e9679b0ae065b9280f20cf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082501"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Načte informace o prohlížeči pro tento typ vlastnosti, aby bylo možné vytvořit instanci tohoto prohlížeče.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
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
mimo Vrátí název sestavení, který uchovává tento objekt.

`assemBytes`\
mimo Vrátí objekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) obsahující bajty sestavení tohoto objektu (Jedná se o hodnotu null, pokud nejsou k dispozici žádné bajty).

`assemPdb`\
mimo Vrátí `IEEDataStorage` objekt, který obsahuje informace o úložišti symbolů pro tento objekt (hodnota null, pokud není k dispozici žádné úložiště symbolů).

`className`\
mimo Vrátí název třídy obsahující tento objekt.

`alr`\
mimo Vrátí hodnotu z výčtu [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) , která označuje umístění sestavení.

`replacementOk`\
mimo Vrátí nenulovou `TRUE` hodnotu (), pokud hodnota tohoto objektu může být změněna; nula ( `FALSE` ), pokud je objekt určen jen pro čtení.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tuto metodu používá typ vizualizace k vytvoření instance spravovaného prohlížeče.

## <a name="see-also"></a>Viz také
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
