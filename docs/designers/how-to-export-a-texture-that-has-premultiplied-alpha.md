---
title: 'Postupy: Export textury s přednásobeným alfa'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c39d7ae466f48bed8bd6fe4c53662c0c8b3c801e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855518"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Postupy: Export textury s přednásobeným alfa

Kanál s obsahem obrazu může generovat vynásobené alfa textury ze zdrojového obrazu. To může být jednodušší použít a robustnější než textury, které neobsahují předem vynásobené hodnoty alfa.

Tento dokument vysvětluje tyto činnosti:

-   Konfigurace zdrojového obrazu pro zpracování obsahu kanálu obrázku.

-   Konfigurace obsahu kanálu obrázku ke generování předem vynásobených hodnot alfa.

## <a name="premultiplied-alpha"></a>Předem vynásobený prvek alfa
 Předem vynásobený prvek alfa nabízí několik výhod oproti konvenčním, předem alfa, protože lépe představuje skutečných interakci světla s fyzickými materiály oddělením podílu barvy texelu (barvy, který přidá do scény) z jeho průsvitnosti (podíl základní barvy, která umožní průnik částka). Některé výhody použití předem vynásobených hodnot alfa jsou:

-   Prolnutí s předem vynásobených hodnot alfa je asociativní operace; Výsledek prolnutí více průhledných textur je stejný, bez ohledu na pořadí, ve kterém jsou textury prolnuty.

-   Vzhledem k asociativnímu charakteru prolnutí s předem vynásobených hodnot alfa je vícenásobné vykreslení s více průchody průsvitných objektů zjednodušeno.

-   Pomocí předem vynásobené hodnoty alfa čiré aditivní prolnutí (podle nastavení alfa nula) i lineárně interpolované prolnutí lze dosáhnout současně. Například v systému částic směsi částic ohně přeměnit na průsvitné částice kouře, které jsou prolnuty pomocí lineární interpolace. Bez předem vynásobené hodnoty alfa je třeba nakreslit částice ohně odděleně od kouřových částic a měnit stav vykreslení mezi voláními výkresu.

-   Textury, které používají předem vynásobenou hodnotu alpha mají vyšší kvalitu než ty, které ji nemají komprese a nevykazují zabarvené hrany – nebo "halo efekt", který může být výsledkem prolnutí textur, které nepoužívají vynásobenou hodnotu alpha.

#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Vytvoření textury, která používá předem vynásobené hodnoty alfa

1. Začněte základní texturou. Načtěte stávající obrazový soubor nebo jej vytvořte podle pokynů v [postupy: vytvoření základní textury](../designers/how-to-create-a-basic-texture.md).

2. Nakonfigurujte soubor textury tak, aby byl zpracován kanálem obsahu obrázku. V **Průzkumníka řešení**, otevřete místní nabídku pro soubor textury a klikněte na tlačítko **vlastnosti**. Na **vlastnosti konfigurace** > **Obecné** nastavte **typ položky** vlastnost **kanál obsahu obrazu**. Ujistěte se, že **obsahu** je nastavena na **Ano** a **vyloučit ze sestavení** je nastavena na **ne**a klikněte na tlačítko  **Použít** tlačítko. **Kanál obsahu obrazu** se zobrazí stránka pro konfiguraci vlastností.

3. Nakonfigurujte kanál obsahu obrázku ke generování předem vynásobených hodnot alfa. Na **vlastnosti konfigurace** > **kanál obsahu obrazu** > **Obecné** nastavte **převést na Formát přednásobené alfa** vlastnost **Ano (/ generatepremultipliedalpha)**.

4. Zvolte **OK** tlačítko.

   Při sestavování projektu kanál obsahu obrazu převede zdrojový obraz z pracovního formátu na výstupní formát, který jste zadali – patří sem převod obrázku na předem vynásobený formát alfa – a výsledek je zkopírován do výstupu projektu adresář.