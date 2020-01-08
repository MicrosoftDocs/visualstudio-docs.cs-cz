---
title: StartTrackingContext | Microsoft Docs
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
ms.openlocfilehash: 4b84753974eeecb8dca85035d50635d0bee47645
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595043"
---
# <a name="starttrackingcontext"></a>StartTrackingContext
Spusťte sledovací kontext.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);
```

#### <a name="parameters"></a>Parametry
[in] `intermediateDirectory`

 Adresář, do kterého má být uložen protokol sledování.

[in] `taskName`

 Identifikuje sledovací kontext. Tento název se používá k vytvoření názvu souboru protokolu.

## <a name="return-value"></a>Návratová hodnota
 Hodnota **HRESULT** s **úspěšně** nastaveným bitem, pokud byl vytvořen sledovací kontext.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *stoper. h*
