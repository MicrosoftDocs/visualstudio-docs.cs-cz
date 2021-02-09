---
title: Mapy kódu jsou pomalé
description: Zjistěte, jak zlepšit výkon mapy kódu a jak můžete minimalizovat dobu potřebnou k dokončení vykreslování.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c37f07d309551ae0f8aa0062b7847722f33671be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861683"
---
# <a name="improve-performance-for-code-maps"></a>Zlepšení výkonu pro mapy kódu

Při prvním generování mapy aplikace Visual Studio indexuje všechny závislosti, které najde. Tento proces může určitou dobu trvat, zejména u velkých řešení, ale vylepšuje vyšší výkon. Pokud se váš kód změní, Visual Studio přeindexuje pouze aktualizovaný kód. Chcete-li minimalizovat čas potřebný k dokončení vykreslování mapy, vezměte v úvahu následující návrhy:

- Namapujte pouze závislosti, které vás zajímají.

- Než vygenerujete mapu pro celé řešení, snižte Rozsah řešení.

- Vypněte automatické sestavení pro řešení výběrem možnosti **Přeskočit sestavení** na panelu nástrojů mapa kódu.

- Vypnutí automatického přidávání nadřazených položek výběrem možnosti **Zahrnout nadřazené** položky na panelu nástrojů mapa kódu.

   ![Přeskočit sestavení a zahrnout nadřízených tlačítek](../modeling/media/codemapsfilterskipbuildicons.png)

- Upravte soubor s mapou kódu přímo pro odebrání uzlů a propojení, které nepotřebujete. Změna mapy nemá vliv na podkladový kód. Další informace najdete v tématu [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Vytváření map nebo přidávání položek na mapu z **Průzkumník řešení** může trvat déle, pokud je vlastnost **Kopírovat do výstupního adresáře** položky projektu nastavena na hodnotu **vždy kopírovat**. Chcete-li zvýšit výkon, změňte tuto vlastnost na **Kopírovat, pokud je novější** nebo `PreserveNewest` . Viz [přírůstková sestavení](../msbuild/incremental-builds.md).

Dokončená mapa znázorňuje závislosti pouze pro úspěšně sestavený kód. Pokud dojde k chybám sestavení u některých součástí, zobrazí se na mapě tyto chyby. Ujistěte se, že součást skutečně sestaví a má závislosti, než na základě mapy provedete rozhodování o architektuře.
