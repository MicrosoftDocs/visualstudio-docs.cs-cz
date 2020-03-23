---
title: WriteContextTLogs | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteContextTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf34ff63b00cf523ba9ef704f4417be4d5cdbf77
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630702"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs

Zapíše soubory protokolů pro aktuální kontext.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
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

- [WriteAllTLogs](../msbuild/writealltlogs.md)