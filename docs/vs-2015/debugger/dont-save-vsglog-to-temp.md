---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 449c6c1ecdb0644b9b52b6ec12ce867dc34d66c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156105"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definuje podle jejich přítomnosti, zda je soubor protokolu grafiky uložen do složky dočasných souborů uživatele.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>Hodnota  
 Symbol preprocesoru, který podle jeho přítomnosti nebo absence určuje, zda je soubor protokolu grafiky uložen do adresáře dočasných souborů uživatele. Pokud je tento symbol definován, název souboru definovaný pomocí `VSG_DEFAULT_RUN_FILENAME` je relativní vzhledem k aktuálnímu adresáři zachycené aplikace nebo je absolutní cesta. v opačném případě je název souboru definovaného pomocí `VSG_DEFAULT_RUN_FILENAME` relativní vzhledem k adresáři dočasných souborů uživatele a nemůže být absolutní cesta.  
  
## <a name="remarks"></a>Poznámky  
 V závislosti na oprávněních uživatele nemusí být soubor protokolu grafiky možné uložit v libovolném umístění. Doporučujeme, abyste při ukládání grafických protokolů do adresáře dočasných souborů uživatele nebo na jiné známé místo, pokud si nejste jistí, jestli je možné do uživatele zapsat umístění, na které byste zvolili.  
  
 Chcete-li zabránit ukládání souboru protokolu grafiky do dočasného adresáře souborů, je nutné `DONT_SAVE_VSGLOG_TO_TEMP` před vložením definovat `vsgcapture.h` .  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak uložit soubor protokolu grafiky do absolutní cesty na hostitelském počítači.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>Viz také  
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)
