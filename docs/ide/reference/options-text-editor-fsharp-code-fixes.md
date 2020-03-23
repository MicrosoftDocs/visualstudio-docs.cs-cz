---
title: Možnosti, Textový editor, F#, Opravy kódu
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a5c736be59c257d98085831971d6b7b9dc2a0ef3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72666269"
---
# <a name="options-text-editor--f--code-fixes"></a>Možnosti: Textový editor > F# > opravy kódu

Na stránce Možnosti oprav kódu můžete určit nastavení, která mohou pomoci identifikovat chyby kódu a nabídnout řešení. Chcete-li získat přístup k této stránce možností, zvolte**Možnosti** **nástrojů** > a pak zvolte Opravy**kódu** **Text Editor** > **F#** > .

## <a name="code-fixes"></a>Opravy kódu

- **Zjednodušení názvů (odebrání zbytečných kvalifikátorů)**

  Pokud je toto políčko zaškrtnuto, plně kvalifikované názvy jsou zjednodušeny, pokud kvalifikace nejsou nutné, například pro člena často používaného oboru názvů.

- **Vždy umístěte otevřené výkazy na nejvyšší úroveň**

  Pokud je toto políčko `open` zaškrtnuto a zadáte příkaz do kódu, je umístěn na nejvyšší úrovni.

- **Odebrání nepoužívaných otevřených příkazů**

  Pokud je toto políčko zaškrtnuto, `open` dokumenty jsou analyzovány pro nepoužívané příkazy a `open` zobrazí se žárovka rychlé [akce](../quick-actions.md) s akcí k odebrání všech nepoužitých příkazů.

- **Analýza a navržení oprav nepoužívaných hodnot**

  Pokud je toto políčko zaškrtnuto, nástroj rozpozná hodnotu, která není v kódu používána. Pokud pak najedete na nepoužitou hodnotu, doporučí způsoby, ve kterých můžete použít hodnotu.

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
- [Nalezení změn kódu a další historie pomocí CodeLensu](../../ide/find-code-changes-and-other-history-with-codelens.md)
