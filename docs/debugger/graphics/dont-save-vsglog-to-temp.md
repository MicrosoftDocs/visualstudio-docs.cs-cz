---
description: Definuje přítomnost, zda je soubor protokolu grafiky uložen do adresáře dočasných souborů uživatele.
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bbf7fa453f36c861d632fc17e46e003e568008db
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232684"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Definuje přítomnost, zda je soubor protokolu grafiky uložen do adresáře dočasných souborů uživatele.

## <a name="syntax"></a>Syntax

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>Hodnota
 Symbol preprocesoru, který jeho přítomností nebo absencí určuje, zda je soubor protokolu grafiky uložen do adresáře dočasných souborů uživatele. Pokud je tento symbol definovaný, je název souboru definovaný pomocí relativní vzhledem k aktuálnímu adresáři zachycené aplikace nebo je absolutní cestou. V opačném případě je název souboru definovaný pomocí relativní vzhledem k adresáři dočasných souborů uživatele a nemůže být absolutní `VSG_DEFAULT_RUN_FILENAME` `VSG_DEFAULT_RUN_FILENAME` cestou.

## <a name="remarks"></a>Poznámky
 V závislosti na oprávněních uživatele nemusí být možné uložit soubor grafického protokolu na libovolném místě. Doporučujeme, abyste raději ukládali grafické protokoly do adresáře dočasných souborů uživatele nebo do jiného známého vhodného umístění, pokud si nejste jistí, jestli uživatel může umístění, do něj které zvolíte, zapsat.

 Pokud chcete zabránit uložení souboru protokolu grafiky do adresáře dočasných souborů, musíte před `DONT_SAVE_VSGLOG_TO_TEMP` zahrnutím souboru definovat `vsgcapture.h` .

## <a name="example"></a>Příklad
 Tento příklad ukazuje, jak uložit soubor protokolu grafiky na absolutní cestu na hostitelském počítači.

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h
#define DONT_SAVE_VSGLOG_TO_TEMP
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Viz také
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
