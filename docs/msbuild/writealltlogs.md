---
title: WriteAllTLogs | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteAllTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7eadb30ee25b1182be5deb12feebd5ef280ebf4b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630675"
---
# <a name="writealltlogs"></a>WriteAllTLogs

Zapíše protokoly sledování pro všechna vlákna a kontexty.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parametry

[v]`intermediateDirectory`

 Adresář, do kterého chcete uložit protokol sledování.

[v]`tlogRootName`

 Kořenový název názvu souboru protokolu.

## <a name="return-value"></a>Návratová hodnota

 **HRESULT** s **succeeded** bit nastavit, pokud byl vytvořen kontext sledování.

## <a name="requirements"></a>Požadavky

 **Záhlaví:** *FileTracker.h*

## <a name="see-also"></a>Viz také

- [WriteContextTLogs](../msbuild/writecontexttlogs.md)