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
ms.openlocfilehash: 36b48529f82a908ea765151561a71c58cd2c7bc5
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578417"
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