---
title: Představení nástroje Spy + + | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++
ms.assetid: 733b514b-63a9-402d-89aa-4f0416766655
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d04b2e9e04e1f2b952baadbdf0cca32cc3b301b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731821"
---
# <a name="introducing-spy"></a>Představení nástroje Spy++
Spy + + umožňuje provádět následující úlohy:

- Zobrazení grafického stromu vztahů mezi systémovými objekty. Mezi ně patří [procesy](../debugger/processes-view.md), [vlákna](../debugger/threads-view.md)a [okna](../debugger/windows-view.md).

- Vyhledat zadaná [okna](../debugger/how-to-search-for-a-window-in-windows-view.md), [vlákna](../debugger/how-to-search-for-a-thread-in-threads-view.md), [procesy](../debugger/how-to-search-for-a-process-in-processes-view.md)nebo [zprávy](../debugger/how-to-search-for-a-message-in-messages-view.md).

- Zobrazí vlastnosti vybraných [oken](../debugger/how-to-display-window-properties.md), [vláken](../debugger/how-to-display-thread-properties.md), [procesů](../debugger/how-to-display-process-properties.md)nebo [zpráv](../debugger/how-to-display-message-properties.md).

- Výběr okna, vlákna, procesu nebo zprávy přímo v zobrazení.

- Pomocí [Nástroje pro hledání](../debugger/how-to-use-the-finder-tool.md) vyberte okno umístění ukazatele myši.

- [Možnost nastavit zprávu](../debugger/how-to-open-messages-view-from-find-window.md) pomocí složitých parametrů výběru protokolu zpráv.

  Nástroj Spy + + obsahuje panel nástrojů a hypertextové odkazy, které vám pomůžou pracovat rychleji. Nabízí **také příkaz k aktualizaci aktivního** zobrazení, **Nástroj hledání oken** , který zjednodušuje Spying, a dialogové okno **písmo** pro přizpůsobení zobrazení oken. Kromě toho umožňuje Spy + + ukládat a obnovovat předvolby uživatele.

  V různých oknech Spy + + můžete kliknout pravým tlačítkem myši a zobrazit místní nabídku často používaných příkazů. Příkazy, které jsou zobrazeny, závisí na umístění ukazatele. Pokud například kliknete pravým tlačítkem myši na položku v zobrazení okna a vybrané okno je viditelné, pak po kliknutí na tlačítko **Zvýraznit** v místní nabídce dojde k tomu, že se ohraničení vybraného okna nastaví na hodnotu, aby bylo možné snadněji najít.

> [!NOTE]
> Existují dva další nástroje, které se podobají Spy + +: PView, které zobrazují podrobnosti o procesech a vláknech a DDESPY. EXE, který umožňuje monitorovat zprávy DDE (DDE).

## <a name="64-bit-operating-systems"></a>64 – bitové operační systémy
 K dispozici jsou dvě verze nástroje Spy + +. První verze s názvem Spy + + (Spyxx. exe) je navržena tak, aby zobrazovala zprávy odesílané do okna, které běží v procesu 32. Například Visual Studio běží v procesu 32. Proto můžete pomocí nástroje Spy + + zobrazovat zprávy odesílané do **Průzkumník řešení**. Vzhledem k tomu, že výchozí konfigurace pro většinu sestavení v aplikaci Visual Studio je spuštěna v procesu 32, je tato první verze nástroje Spy + + ta, která je k dispozici v nabídce **nástroje** v aplikaci Visual Studio, pokud [jsou požadované součásti nainstalovány](../debugger/how-to-start-spy-increment.md).

 Druhá verze s názvem Spy + + (64-bit) (spyxx_amd64. exe) je navržena tak, aby zobrazovala zprávy odeslané do okna, které běží v procesu 64. Například v 64ém operačním systému Poznámkový blok běží v procesu 64. Proto můžete pomocí nástroje Spy + + (64-bit) zobrazit zprávy odesílané do programu Poznámkový blok. Spy + + (64-bit) se obvykle nachází v

 .. \\*instalační složky sady Visual Studio*\Common7\Tools\spyxx_amd64.exe.

 Z příkazového řádku můžete spustit jednu z verzí nástroje Spy + + přímo.

> [!NOTE]
> I když název souboru Spy + + (64-bit) obsahuje "AMD", běží v jakémkoli operačním systému Windows x64.

## <a name="see-also"></a>Viz také:
- [Postupy: Spuštění nástroje Spy++](../debugger/how-to-start-spy-increment.md)
- [Použití nástroje Spy++](../debugger/using-spy-increment.md)
- [Zobrazení nástroje Spy++](../debugger/spy-increment-views.md)
- [Referenční dokumentace nástroje Spy++](../debugger/spy-increment-reference.md)