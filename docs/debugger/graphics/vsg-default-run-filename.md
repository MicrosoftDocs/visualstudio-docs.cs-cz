---
description: Definuje výchozí název souboru protokolu grafiky.
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5f6bd07e54fc90bcc99f7462cc087ba01866727c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160477"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
Definuje výchozí název souboru protokolu grafiky.

## <a name="syntax"></a>Syntaxe

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>Parametry
 `filename` Název souboru, který je ve výchozím nastavení k souboru protokolu grafiky při zachycení informací grafiky prostřednictvím kódu programu.

## <a name="value"></a>Hodnota
 Řetězcový literál, který představuje název souboru protokolu grafiky. Ve výchozím nastavení je to L "default. vsglog".

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>Poznámky
 Pokud je definován symbol preprocesoru `DONT_SAVE_VSGLOG_TO_TEMP` , je název souboru relativní vzhledem k aktuálnímu adresáři zachycené aplikace nebo je absolutní cesta. v opačném případě je relativní vzhledem k adresáři dočasných souborů uživatele a nemůže být absolutní cesta.

 Chcete-li změnit definovaný název souboru, je nutné jej před vložením `vsgcapture.h` do programu předefinovat.

## <a name="example"></a>Příklad
 Tento příklad ukazuje, jak změnit výchozí název souboru digitalizačního souboru:

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Viz také
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
