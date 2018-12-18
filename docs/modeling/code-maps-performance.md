---
title: Mapy kódu jsou pomalé
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 2dece1e63fffdba67678422ad9241babc63b7abd
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34267696"
---
# <a name="improve-performance-for-code-maps"></a>Zlepšení výkonu pro map kódu

Při generování mapu poprvé, Visual Studio indexuje všechny závislosti, které nalezne. Tento proces může určitou dobu trvat, zejména u velkých řešení, ale novější zlepšuje. Pokud se váš kód změní, Visual Studio reindexes pouze aktualizovaný kód. Chcete-li minimalizovat čas potřebný pro mapu ukončíte vykreslování, zvažte následující návrhy:

- [Mapovat jenom závislosti, které vás zajímají.](#create-a-code-map-to-see-specific-dependencies)

- Před generováním mapy pro celé řešení snížit rozsah řešení.

- Vypnout automatické sestavení řešení výběrem **přeskočit sestavení** na panelu nástrojů map kódu.

- Vypnout automatické přidání nadřazených položek výběrem **zahrnují nadřazené položky** na panelu nástrojů map kódu.

   ![Přeskočit sestavení a zahrnují nadřazených prvků tlačítek](../modeling/media/codemapsfilterskipbuildicons.png)

- Upravte soubor mapy kódu přímo pro odebrání uzlů a odkazy, které nepotřebujete. Změna mapy neovlivní kódu. V tématu [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Může trvat delší dobu k vytvoření mapy nebo přidání položky do mapy z **Průzkumníku řešení** při položka projektu **kopírovat do výstupního adresáře** je nastavena na **kopie vždy**. Chcete-li zvýšit výkon, změňte tuto vlastnost, aby **kopírovat, pokud je novější** nebo `PreserveNewest`. V tématu [přírůstkové sestavení](../msbuild/incremental-builds.md).

Dokončené mapa znázorňuje závislosti pouze pro úspěšně integrovaný kód. Pokud dojde k chybám sestavení pro určité součásti, zobrazí se tyto chyby na mapě. Ujistěte se, že komponentu ve skutečnosti sestavení a před provedením architektury rozhodnutí, která na základě mapy má závislosti na.