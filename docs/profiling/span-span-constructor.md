---
title: 'span:: span – konstruktor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a813506e64242d1effdb9ed64d35c9ee5d31239
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949971"
---
# <a name="spanspan-constructor"></a>span::span – konstruktor

Inicializuje novou instanci `span` třídy.

## <a name="syntax"></a>Syntaxe

```cpp
span(
   const marker_series& _Series,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parametry

`_Series` Platný kontext řady značek

`_Format` Složený řetězec formátu, který obsahuje text vzájemně se smíšenými nulami nebo více formátovacími položkami, které odpovídají objektům v seznamu argumentů.

`_Importance` Úroveň důležitosti.

`_Category` Kategorií.

## <a name="requirements"></a>Požadavky

**Záhlaví:** *cvmarkersobj. h*

**Obor názvů:** Concurrency::d odeslání diagnostických

## <a name="see-also"></a>Viz také

- [span – třída](../profiling/span-class.md)