---
title: StartTrackingContext | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50f62704897d68b0e323b948b8f4ed7e96a10c9a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632105"
---
# <a name="starttrackingcontext"></a>StartTrackingContext

Spusťte kontext sledování.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);
```

#### <a name="parameters"></a>Parametry

[v]`intermediateDirectory`

 Adresář, do kterého chcete uložit protokol sledování.

[v]`taskName`

 Identifikuje kontext sledování. Tento název slouží k vytvoření názvu souboru protokolu.

## <a name="return-value"></a>Návratová hodnota

 **HRESULT** s **succeeded** bit nastavit, pokud byl vytvořen kontext sledování.

## <a name="requirements"></a>Požadavky

 **Záhlaví:** *FileTracker.h*
