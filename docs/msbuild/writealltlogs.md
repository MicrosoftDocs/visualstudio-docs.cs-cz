---
title: WriteAllTLogs | Microsoft Docs
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
ms.openlocfilehash: 7c64f0079a03b730fb700cfbc6320c5dffa05d7a
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579512"
---
# <a name="writealltlogs"></a>WriteAllTLogs
Zapisuje protokoly sledování pro všechna vlákna a kontexty.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parametry
[in] `intermediateDirectory`

 Adresář, do kterého má být uložen protokol sledování.

[in] `tlogRootName`

 Název kořenového souboru protokolu

## <a name="return-value"></a>Návratová hodnota
 Hodnota **HRESULT** s **úspěšně** nastaveným bitem, pokud byl vytvořen sledovací kontext.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *stoper. h*

## <a name="see-also"></a>Viz také
- [WriteContextTLogs](../msbuild/writecontexttlogs.md)