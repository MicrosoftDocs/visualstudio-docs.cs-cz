---
title: StartTrackingContextWithRoot | Microsoft Docs
description: Naučte se používat StartTrackingContextWithRoot MSBuild ke spuštění kontextu sledování pomocí souboru odezvy určujícího kořenovou značku.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ccca75a0fe525c4e1d9f421b2264070ebda9bdf3
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048131"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot

Spustí sledovací kontext pomocí souboru odezvy určujícího kořenovou značku.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>Parametry

pro `intermediateDirectory`

 Adresář, do kterého má být uložen protokol sledování.

pro `taskName`

 Identifikuje sledovací kontext. Tento název se používá k vytvoření názvu souboru protokolu.

pro `rootMarkerResponseFile`

 Cesta k souboru odpovědí, který obsahuje kořenovou značku. Kořenový název slouží k seskupení všech sledování kontextu.

## <a name="return-value"></a>Vrácená hodnota

 Hodnota **HRESULT** s **úspěšně** nastaveným bitem, pokud byl vytvořen sledovací kontext.

## <a name="requirements"></a>Požadavky

 **Záhlaví:** *stoper. h*

## <a name="see-also"></a>Viz také

- [StartTrackingContext](../msbuild/starttrackingcontext.md)