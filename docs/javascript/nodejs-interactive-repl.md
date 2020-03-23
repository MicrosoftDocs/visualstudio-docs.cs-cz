---
title: Použití souboru Node.js REPL
description: Visual Studio poskytuje podporu pro interakci s runtime Node.js
ms.date: 12/04/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: faed930c60869010f740cf0a1e118a40299ce782
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62840657"
---
# <a name="work-with-the-nodejs-interactive-window"></a>Práce s interaktivním oknem Node.js

Node.js Nástroje pro Visual Studio zahrnují interaktivní okno pro nainstalovaný runtime Node.js. Toto okno umožňuje zadat kód JavaScript a okamžitě zobrazit výsledky, stejně jako spustit příkazy npm pro interakci s aktuálním projektem. Interaktivní okno je také známé jako REPL (**R**ead /**E**valuate /**P**rint **L**oop).

## <a name="open-the-interactive-window"></a>Otevření interaktivního okna

Interaktivní okno můžete otevřít klepnutím pravým tlačítkem myši na uzel projektu Node.js v Průzkumníku řešení a výběrem **interaktivního okna Otevřít soubor Node.js**.

![Interaktivní okno Node.js v kontextové nabídce projektu](../javascript/media/interactivewindow-open-from-project.png)

Výchozí zkratkové klávesy pro otevření interaktivního okna Node.js jsou **[CTRL] + K, N**. Nebo můžete otevřít okno z panelu nástrojů výběrem **možnosti Zobrazit** > interaktivní okno aplikace**Windows** > **Node.js**.

## <a name="use-the-repl"></a>Použijte REPL

Po otevření můžete zadat příkazy.

![Interaktivní okno Node.js](../javascript/media/interactivewindow.png)

Interaktivní okno má několik vestavěných příkazů, které začínají tečkovou předponou, aby se odlišily od jakékoli deklarované funkce JavaScriptu. Podporovány jsou následující příkazy:

**.cls, .clear** Vymaže obsah okna editoru a ponechá historii a kontext spuštění beze změny.

**.help** Zobrazí nápovědu k zadanému příkazu nebo ke všem dostupným příkazům a vazbám klíčů, pokud není zadánžádný.

**.info** Zobrazuje informace o aktuálním použitém spustitelném souboru Node.js.

**.npm** Spustí příkaz npm. Pokud řešení obsahuje více než jeden projekt, `.npm [projectname] <npm arguments>`zadejte cílový projekt pomocí .

**.reset** Obnoví spuštění prostředí do počátečního stavu, zachovat historii.

**.uložit** Uloží aktuální relaci REPL do souboru.