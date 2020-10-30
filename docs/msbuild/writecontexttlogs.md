---
title: WriteContextTLogs | Microsoft Docs
description: Naučte se syntaxi, požadavky a návratovou hodnotu pro WriteContextTLogs, která zapisuje soubory protokolu pro aktuální kontext.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 622cbebdb4073dfd9b4237e9dfbcb8bbf4a506de
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047381"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs

Zapisuje soubory protokolů pro aktuální kontext.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parametry

pro `intermediateDirectory`

 Adresář, do kterého má být uložen protokol sledování.

pro `tlogRootName`

 Název kořenového souboru protokolu

## <a name="return-value"></a>Vrácená hodnota

 Hodnota **HRESULT** s **úspěšně** nastaveným bitem, pokud byl vytvořen sledovací kontext.

## <a name="requirements"></a>Požadavky

 **Záhlaví:** *stoper. h*

## <a name="see-also"></a>Viz také

- [WriteAllTLogs](../msbuild/writealltlogs.md)