---
title: EndTrackingContext | Microsoft Docs
description: Seznamte se s syntaxí, návratovou hodnotou a požadavky na použití nástroje MSBuild EndTrackingContext k ukončení aktuálního sledovacího kontextu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90f4c8c4a83a496dba537e74dddfde4ae3f2f21a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877223"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

Ukončí aktuální sledovací kontext.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Vrácená hodnota

Hodnota **HRESULT** s **úspěšně** nastaveným bitem, pokud byl kontext sledování ukončen.

## <a name="requirements"></a>Požadavky

**Záhlaví:** *stoper. h*

## <a name="see-also"></a>Viz také

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
