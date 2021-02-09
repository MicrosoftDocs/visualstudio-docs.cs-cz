---
title: 'IDiaPropertyStorage:: Enum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8972fa93ebae30fc64839324106d068e27577434
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864647"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
Získá enumerátor pro vlastnosti v rámci této sady.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Enum ( 
   IEnumSTATPROPSTG** ppenum
);
```

#### <a name="parameters"></a>Parametry
 `ppenum`

mimo Vrátí `IEnumSTATPROPSTG` objekt (v oboru názvů Microsoft. VisualStudio. OLE. Interop) představující výčet vlastností.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)