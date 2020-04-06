---
title: Glosář ladicího programu sady Visual Studio | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 954532311fe6b63fc288877a6d41722e6ea47581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713350"
---
# <a name="visual-studio-debugger-glossary"></a>Slovníček pro Visual Studio Debugger
Následují termíny používané [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] v ladicí sdk.

## <a name="terms"></a>Výrazy
 vázaná zarážka Abstrakce pro zarážku nastavenou v kódu. Existuje vztah 1:1 mezi vázanou zarážkou a instrunicí zarážky v datovém proudu kódu. Při uvolnění kódu vázané zarážky může zrušit vazbu.

 kauzalita Poskytuje možnost sledovat logické vlákno spuštění napříč více fyzickými vlákny, procesy a počítači a rekonstruovat zásobník volání tohoto logického vlákna v libovolném okamžiku v době životnosti daného vlákna.

 kontext kódu Poskytuje abstrakci pozice v kódu známém ladicímu modulu. Pro většinu architektur za běhu je kontext kódu adresou v instrukčním proudu programu. Pro netradiční jazyky, ve kterých kód nemusí být reprezentován pokyny, kontext kódu může být reprezentován jinými prostředky.

 cesta kódu Představuje bod spuštění v kódu, kde je přijata větev nebo volání funkce. Trasování zásobníku je v podstatě seznam cest kódu volání funkce.

 ladicí modul (DE) Součást, která umožňuje ladění architektury za běhu. Ladicí modul pracuje ve spojení s interpretem nebo operačním systémem a poskytuje ladicí služby, jako je řízení provádění, zarážky a vyhodnocení výrazu.

 kontext dokumentu Poskytuje abstrakci pozice ve zdrojovém souboru dokumentu známého ladicímu modulu. Pro většinu jazyků je kontext dokumentu umístěníve zdrojovém souboru. U netradičních jazyků, pro které zdrojový soubor nemusí být text, může být kontext dokumentu reprezentován jiným způsobem. Viz také *pozice dokumentu*.

 pozice dokumentu Poskytuje abstrakci pozice ve zdrojovém souboru známém ide. Pro většinu jazyků je pozice dokumentu pozice ve zdrojovém souboru. U netradičních jazyků může být pozice dokumentu reprezentována jinými způsoby. Viz také *kontext dokumentu*.

 Zarážka chyby Abstrakce pro popis chyby v čekající zarážky. Zarážka chyby může popisovat chybu v umístění čekající zarážky, výraz přidružený k čekající zarážky nebo jiné informace, které brání čekající zarážky z vazby na umístění kódu.

 kontext hodnocení Poskytuje abstrakci programovacího kontextu pro vyhodnocení výrazu. Kontext hodnocení je obvykle obor. Při vyhodnocení výrazu v kontextu výrazu kontext výrazu poskytuje pravidla oboru, které odpovídají jeho bodu vytvoření. Například kontext výrazu vytvořený v rámci zásobníku poskytne kontext pro vyhodnocení místních proměnných, parametrů metody, členů třídy (pokud je to možné) a globálních proměnných.

 zachycená výjimka Výjimka, která je zachycena ladicím strojem, i když v aktuálním rámci zásobníku není zaveden žádný mechanismus zpracování výjimek.

 JustMyCode Koncept ladění pouze kód, který patří uživateli a ignoruje všechny zprostředkující kód, jako je například systémový kód – i v případě, že zdrojový kód je k dispozici pro tento systémový kód.

 čekající zarážka Poskytuje abstrakci pro zarážky před, během a po načtení kódu a způsob virtualizace zarážek. Čekající zarážka:

- Obsahuje všechny informace potřebné k vytvoření zarážky s kódem v jednom nebo více programech.

- Může se vázat na více umístění kódu v jednom nebo více programech.

- Nikdy se neváže na kód.

  Při každém načtení kódu jsou kontrolovány všechny čekající zarážky v programu, aby se zjistilo, zda mohou být svázány. Čekající zarážka je prý obsahovat všechny vázané zarážky, které váže.

  proces fyzického win32. Proces může obsahovat více programů. Viz také *program*.

  Program Jeden obor názvů spuštěný uvnitř konkrétní architektury za běhu. Viz také *proces*.

  správce ladění relace (SDM) Spravuje libovolný počet ladicích strojů ladění libovolného počtu programů ve více procesech na libovolném počtu počítačů. Na základní úrovni je SDM multiplexerem ladicích motorů. Kromě toho SDM poskytuje jednotné zobrazení relace ladění rozhraní IDE.

  zásobníku představuje stav výpočtu na konkrétní snímek a konkrétní úroveň vnořené volání funkce.

  vlákno Generalizovaná představa spuštění instrukcí založených na zásobníku spuštěná alespoň v jednom programu.

  upozornění zarážka Abstrakce pro popis upozornění v čekající zarážky. Zarážka upozornění popisuje důvod, proč čekající zarážka ještě není vázána na umístění kódu. To může být, že kód nebyl načten ještě pro umístění popsané čekající zarážky nebo z nějakého jiného důvodu.

## <a name="see-also"></a>Viz také
- [Rozšiřitelnost programu Visual Studio Debugger](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
