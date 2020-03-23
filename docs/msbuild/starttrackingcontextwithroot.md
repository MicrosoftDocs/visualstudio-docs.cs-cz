---
title: StartTrackingContextWithRoot | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContextWithRoot
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68d585361b9797bf1df9c8b0b31f8a089e9de025
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632092"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot

Spustí kontext sledování pomocí souboru odpovědí určujícího kořenovou značku.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>Parametry

[v]`intermediateDirectory`

 Adresář, do kterého chcete uložit protokol sledování.

[v]`taskName`

 Identifikuje kontext sledování. Tento název slouží k vytvoření názvu souboru protokolu.

[v]`rootMarkerResponseFile`

 Název cesty souboru odpovědí obsahující kořenovou značku. Kořenový název se používá k seskupení všech sledování pro kontext dohromady.

## <a name="return-value"></a>Návratová hodnota

 **HRESULT** s **succeeded** bit nastavit, pokud byl vytvořen kontext sledování.

## <a name="requirements"></a>Požadavky

 **Záhlaví:** *FileTracker.h*

## <a name="see-also"></a>Viz také

- [StartTrackingContext](../msbuild/starttrackingcontext.md)