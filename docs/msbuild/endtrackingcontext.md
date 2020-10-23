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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da1ef921106732a7787f68a979bc88f3ac012b6d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436668"
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
