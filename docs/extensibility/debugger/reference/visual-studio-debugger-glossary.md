---
title: Glosář ladicího programu sady Visual Studio | Microsoft Docs
description: Tento článek vysvětluje několik podmínek používaných v sadě Visual Studio Debugging SDK, jako je například vázaná zarážka, příčina a kontext kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1871a395e87177c89f8af2bfce640a63c2cba324
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070684"
---
# <a name="visual-studio-debugger-glossary"></a>Slovníček pro Visual Studio Debugger
Níže jsou uvedené výrazy používané v [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] sadě SDK pro ladění.

## <a name="terms"></a>Terminologie
 vázaná zarážka zarážku abstrakce pro sadu zarážek v kódu. Existuje vztah 1:1 mezi vázanou zarážkou a instrukcí zarážky v datovém proudu kódu. Při uvolnění kódu mohou být navázány vázané zarážky.

 k dispozici je možnost sledovat logické vlákno provádění napříč různými fyzickými vlákny, procesy a počítači a rekonstruovat zásobník volání tohoto logického vlákna v jakémkoli daném okamžiku v době životnosti tohoto vlákna.

 kontext kódu poskytuje abstrakci pozice v kódu známého pro ladicí stroj. Pro většinu architektur běhu je kontext kódu adresa v datovém proudu instrukcí programu. Pro netradiční jazyky, ve kterých kód nemůže být reprezentován pokyny, kontext kódu může být reprezentován jiným způsobem.

 cesta kódu představuje bod spuštění v kódu, kde je vytvořena větev, nebo je provedeno volání funkce. Trasování zásobníku je v podstatě seznam cest kódu volání funkcí.

 ladicí stroj (DE) součást, která umožňuje ladění architektury run-time. Ladicí stroj funguje ve spojení s překladačem nebo operačním systémem a poskytuje služby ladění, jako je například řízení spouštění, zarážky a vyhodnocení výrazu.

 kontext dokumentu poskytuje abstrakci pozice v dokumentu zdrojového souboru známého ladicímu modulu. Pro většinu jazyků je kontext dokumentu pozice ve zdrojovém souboru. Pro netradiční jazyky, pro které zdrojový soubor nemusí být text, může být kontext dokumentu reprezentován jiným způsobem. Viz také *pozice dokumentu*.

 pozice dokumentu poskytuje abstrakci pozice ve zdrojovém souboru známém rozhraním IDE. Ve většině jazyků je umístěním dokumentu pozice ve zdrojovém souboru. V případě netradičních jazyků může být pozice dokumentu reprezentovaná jinými způsoby. Viz také *kontext dokumentu*.

 Chyba zarážky abstrakce pro popis chyby v nevyřízené zarážce. Zarážka chyby může popsat chybu v umístění čeká na zarážce, výraz přidružený k nevyřízené zarážce nebo jiné informace, které brání nevyřízené zarážce ve vazbě na umístění kódu.

 kontext vyhodnocení poskytuje abstrakci programovacího kontextu pro vyhodnocení výrazu. Kontext vyhodnocení je obvykle oborem. Při provádění vyhodnocení výrazu v kontextu výrazu poskytuje kontext výrazu pravidla oboru, která odpovídají jeho bodu vytváření. Například kontext výrazu vytvořený v bloku zásobníku poskytne kontext pro vyhodnocení místních proměnných, parametrů metod, členů třídy (Pokud je k dispozici) a globálních proměnných.

 zachycená výjimka výjimka, která je zachycena ladicím modulem, i když není v aktuálním bloku zásobníku k dispozici žádný mechanismus zpracování výjimek.

 JustMyCode koncept ladění pouze kódu, který patří uživateli a ignorování všech zprostředkujících kódů, jako je například systémový kód, a to i v případě, že je zdrojový kód k dispozici pro tento systémový kód.

 nevyřízená zarážka poskytuje abstrakci pro zarážky před, během a po načtení kódu a způsob, jak virtualizovat zarážky. Nevyřízená zarážka:

- Obsahuje všechny informace potřebné k navázání zarážky na kód v jednom nebo více programech.

- Může vytvořit vazby na více umístění kódu v jednom nebo více programech.

- Nikdy se neváže ke kódu.

  Pokaždé, když se načte kód, jsou zkontrolovány všechny probíhající zarážky v programu, aby se zobrazily, zda mohou vytvořit vazby. Čeká se na zarážku, která obsahuje všechny svázané zarážky, které váže.

  zpracování fyzického procesu Win32. Proces může obsahovat více programů. Viz také *program*.

  Programujte jeden obor názvů běžící v rámci určité architektury run-time. Viz také *proces*.

  Správce ladění relací (SDM) spravuje libovolný počet ladicích modulů, které ladí libovolný počet programů ve více procesech na libovolném počtu počítačů. Na úrovni Basic je model SDM multiplexou ladicích modulů. SDM navíc poskytuje jednotný přehled o relaci ladění IDE.

  rámec zásobníku představuje stav výpočtu na konkrétním snímku a konkrétní úroveň volání vnořených funkcí.

  vláknem zobecněný pojem spuštění instrukcí založeného na zásobníku, který běží aspoň v jednom programu.

  Upozornění zarážky abstrakce pro popis upozornění v nedokončené zarážce. Zarážka varování popisuje důvod, proč se nevyřízená zarážka ještě neváže k umístění kódu. To může být způsobeno tím, že kód ještě nebyl načten pro umístění popsané v nedokončené zarážce, nebo z jiného důvodu.

## <a name="see-also"></a>Viz také
- [Rozšiřitelnost programu Visual Studio Debugger](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
