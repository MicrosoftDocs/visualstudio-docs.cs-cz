---
title: Glosář ladicího programu sady Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 19d82f006bb1c37981f60e1a0b2710588eb0053c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204780"
---
# <a name="visual-studio-debugger-glossary"></a>Slovníček pro Visual Studio Debugger
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Níže jsou uvedené výrazy používané v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] sadě SDK pro ladění.  
  
## <a name="terms"></a>Terminologie  
 vázaná zarážka  
 Abstrakce pro zarážku nastavenou v kódu. Existuje vztah 1:1 mezi vázanou zarážkou a instrukcí zarážky v datovém proudu kódu. Při uvolnění kódu mohou být navázány vázané zarážky.  
  
 kauzalita  
 Poskytuje možnost sledovat logické vlákno provádění napříč více fyzickými vlákny, procesy a počítači a pro rekonstrukci zásobníku volání daného logického vlákna v kterémkoli daném okamžiku v rámci tohoto vlákna.  
  
 kontext kódu  
 Poskytuje abstrakci pozice v kódu známého pro ladicí stroj. Pro většinu architektur běhu je kontext kódu adresa v datovém proudu instrukcí programu. Pro netradiční jazyky, ve kterých kód nemůže být reprezentován pokyny, kontext kódu může být reprezentován jiným způsobem.  
  
 cesta kódu  
 Představuje bod spuštění v kódu, kde je vytvořena větev, nebo je provedeno volání funkce. Trasování zásobníku je v podstatě seznam cest kódu volání funkcí.  
  
 ladicí stroj (DE)  
 Komponenta, která umožňuje ladění architektury run-time. Ladicí stroj funguje ve spojení s překladačem nebo operačním systémem a poskytuje služby ladění, jako je například řízení spouštění, zarážky a vyhodnocení výrazu.  
  
 kontext dokumentu  
 Poskytuje abstrakci pozice v dokumentu zdrojového souboru známého ladicímu modulu. Pro většinu jazyků je kontext dokumentu pozice ve zdrojovém souboru. Pro netradiční jazyky, pro které zdrojový soubor nemusí být text, může být kontext dokumentu reprezentován jiným způsobem. Viz také *pozice dokumentu*.  
  
 pozice dokumentu  
 Poskytuje abstrakci pozice ve zdrojovém souboru známém rozhraním IDE. Ve většině jazyků je umístěním dokumentu pozice ve zdrojovém souboru. V případě netradičních jazyků může být pozice dokumentu reprezentovaná jinými způsoby. Viz také *kontext dokumentu*.  
  
 Chyba zarážky  
 Abstrakce popisující chybu v nedokončené zarážce. Zarážka chyby může popsat chybu v umístění čeká na zarážce, výraz přidružený k nevyřízené zarážce nebo jiné informace, které brání nevyřízené zarážce ve vazbě na umístění kódu.  
  
 kontext vyhodnocení  
 Poskytuje abstrakci programovacího kontextu pro vyhodnocení výrazu. Kontext vyhodnocení je obvykle oborem. Při provádění vyhodnocení výrazu v kontextu výrazu poskytuje kontext výrazu pravidla oboru, která odpovídají jeho bodu vytváření. Například kontext výrazu vytvořený v bloku zásobníku poskytne kontext pro vyhodnocení místních proměnných, parametrů metod, členů třídy (Pokud je k dispozici) a globálních proměnných.  
  
 zachycená výjimka  
 Výjimka, která je zachycena ladicím strojem, i když není v aktuálním bloku zásobníku k dispozici žádný mechanismus zpracování výjimek.  
  
 JustMyCode  
 Koncept ladění pouze kódu, který patří uživateli a ignorování veškerého zprostředkujícího kódu, jako je například systémový kód, i v případě, že je zdrojový kód k dispozici pro tento systémový kód.  
  
 čeká na zarážku  
 Poskytuje abstrakci pro zarážky před, během a po načtení kódu a způsob, jak virtualizovat zarážky. Nevyřízená zarážka:  
  
- Obsahuje všechny informace potřebné k navázání zarážky na kód v jednom nebo více programech.  
  
- Může vytvořit vazby na více umístění kódu v jednom nebo více programech.  
  
- Nikdy se neváže ke kódu.  
  
  Pokaždé, když se načte kód, jsou zkontrolovány všechny probíhající zarážky v programu, aby se zobrazily, zda mohou vytvořit vazby. Čeká se na zarážku, která obsahuje všechny svázané zarážky, které váže.  
  
  zpracování  
  Fyzický proces Win32. Proces může obsahovat více programů. Viz také *program*.  
  
  program  
  Jeden obor názvů běžící v rámci určité architektury run-time. Viz také *proces*.  
  
  Správce ladění relace (SDM)  
  Spravuje libovolný počet ladicích modulů, které ladí libovolný počet programů ve více procesech na libovolném počtu počítačů. Na úrovni Basic je model SDM multiplexou ladicích modulů. SDM navíc poskytuje jednotný přehled o relaci ladění IDE.  
  
  rámec zásobníku  
  Představuje stav výpočtu pro konkrétní rámec a konkrétní úroveň volání vnořených funkcí.  
  
  vlákno  
  Zobecněný pojem spuštění instrukcí založeného na zásobníku, který běží aspoň v jednom programu.  
  
  zarážka upozornění  
  Abstrakce pro popis upozornění v nedokončené zarážce. Zarážka varování popisuje důvod, proč se nevyřízená zarážka ještě neváže k umístění kódu. To může být způsobeno tím, že kód ještě nebyl načten pro umístění popsané v nedokončené zarážce, nebo z jiného důvodu.  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřitelnost programu Visual Studio Debugger](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
