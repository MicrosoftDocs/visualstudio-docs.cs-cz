---
title: Mapy kódu jsou pomalé
description: Zjistěte, jak zlepšit výkon map kódu a jak můžete minimalizovat čas potřebný k dokončení vykreslování.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5a279a04b1bd76933df335bc0b2527ab4b2418f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389641"
---
# <a name="improve-performance-for-code-maps"></a>Vylepšení výkonu pro mapy kódu

Při prvním vygenerování mapy se Visual Studio všechny závislosti, které najde. Tento proces může nějakou dobu trvat, zejména u velkých řešení, ale zlepšuje pozdější výkon. Pokud se váš kód změní, Visual Studio znovu indexuje pouze aktualizovaný kód. Pokud chcete minimalizovat dobu, po které mapa dokončí vykreslování, zvažte následující návrhy:

- Namapovat jenom závislosti, které vás zajímají.

- Před vygenerování mapy pro celé řešení zmenšete rozsah řešení.

- Automatické sestavení pro řešení vypnete tak, že na **panelu** nástrojů mapy kódu vyberete Přeskočit sestavení.

- Automatické přidávání nadřazených položek vypnete tak, že na panelu nástrojů mapy kódu vyberete **Zahrnout** nadřazené prvky.

   ![Přeskočení tlačítek Sestavení a Zahrnutí rodičů](../modeling/media/codemapsfilterskipbuildicons.png)

- Upravte soubor mapy kódu přímo a odeberte uzly a odkazy, které nepotřebujete. Změna mapy nemá vliv na podkladový kód. Viz [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Vytvoření map nebo přidání položek do mapy  z Průzkumník řešení, když je  vlastnost Kopírovat do výstupního adresáře položky projektu nastavená na **Hodnotu Kopírovat vždy,** může to trvat déle. Pokud chcete zvýšit výkon, změňte tuto vlastnost na **Kopírovat, pokud je novější** nebo `PreserveNewest` . Viz [Přírůstková sestavení.](../msbuild/incremental-builds.md)

Dokončená mapa zobrazuje závislosti pouze pro úspěšně sestavený kód. Pokud u některých komponent dojde k chybám sestavení, zobrazí se tyto chyby na mapě. Před rozhodováním o architektuře na základě mapy se ujistěte, že se komponenta skutečně sestaví a má na ní závislosti.
