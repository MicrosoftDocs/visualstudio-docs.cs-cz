---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40f3c3c22de6b4b0ebdbdf2dfc953f4cb1c9b5e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736082"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Definuje podle jejich přítomnosti, zda je soubor protokolu grafiky uložen do složky dočasných souborů uživatele.

## <a name="syntax"></a>Syntaxe

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>Hodnota
 Symbol preprocesoru, který podle jeho přítomnosti nebo absence určuje, zda je soubor protokolu grafiky uložen do adresáře dočasných souborů uživatele. Pokud je tento symbol definován, je název souboru definovaný `VSG_DEFAULT_RUN_FILENAME` relativní vzhledem k aktuálnímu adresáři zachycené aplikace nebo je absolutní cesta. v opačném případě je název souboru definovaný `VSG_DEFAULT_RUN_FILENAME` relativní vzhledem k adresáři dočasných souborů uživatele a nemůže být absolutní cesta.

## <a name="remarks"></a>Poznámky
 V závislosti na oprávněních uživatele nemusí být soubor protokolu grafiky možné uložit v libovolném umístění. Doporučujeme, abyste při ukládání grafických protokolů do adresáře dočasných souborů uživatele nebo na jiné známé místo, pokud si nejste jistí, jestli je možné do uživatele zapsat umístění, na které byste zvolili.

 Chcete-li zabránit ukládání souboru protokolu grafiky do složky dočasných souborů, je nutné před zahrnutím `vsgcapture.h` definovat `DONT_SAVE_VSGLOG_TO_TEMP`.

## <a name="example"></a>Příklad
 Tento příklad ukazuje, jak uložit soubor protokolu grafiky do absolutní cesty na hostitelském počítači.

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h
#define DONT_SAVE_VSGLOG_TO_TEMP
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Viz také:
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
