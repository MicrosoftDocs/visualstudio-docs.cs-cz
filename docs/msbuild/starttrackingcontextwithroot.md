---
title: StartTrackingContextWithRoot | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632092"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot

Spustí sledovací kontext pomocí souboru odezvy určujícího kořenovou značku.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>Parametry

[in] `intermediateDirectory`

 Adresář, do kterého má být uložen protokol sledování.

[in] `taskName`

 Identifikuje sledovací kontext. Tento název se používá k vytvoření názvu souboru protokolu.

[in] `rootMarkerResponseFile`

 Cesta k souboru odpovědí, který obsahuje kořenovou značku. Kořenový název slouží k seskupení všech sledování kontextu.

## <a name="return-value"></a>Návratová hodnota

 Hodnota **HRESULT** s **úspěšně** nastaveným bitem, pokud byl vytvořen sledovací kontext.

## <a name="requirements"></a>Požadavky

 **Záhlaví:** *stoper. h*

## <a name="see-also"></a>Viz také

- [StartTrackingContext](../msbuild/starttrackingcontext.md)