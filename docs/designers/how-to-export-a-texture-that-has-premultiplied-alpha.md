---
title: 'Postupy: Export textury s přednásobeným alfa'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84017bef80f42bd1848833b957abd88297d1e12d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72635487"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Postupy: Export textury s přednásobeným alfa

Kanál obsahu obrazu může generovat předem vynásobené alfa textury ze zdrojového obrazu. Ty mohou být jednodušší a robustnější než textury, které neobsahují předem vynásobené alfa.

Tento dokument ukazuje tyto činnosti:

- Konfigurace zdrojového obrazu, který má být zpracován kanálem obsahu obrázku.

- Konfigurace kanálu obsahu obrázků pro generování předem vynásobené alfa.

## <a name="premultiplied-alpha"></a>Předem vynásobená alfa
Předem vynásobená alfa nabízí několik výhod oproti konvenční, nepřednásobité alfa, protože lépe reprezentuje skutečnou interakci světla s fyzikálními materiály oddělením barevného příspěvku texelu (barvu, kterou přidává scény) z jeho průsvitnosti (množství podkladové barvy, které umožňuje projít). Některé z výhod použití předem vynásobené alfa jsou:

- Prolnutí s předem vynásobenou alfa je asociativní operace; výsledek prolnutí více průsvitných textur je stejný, bez ohledu na pořadí, ve kterém jsou textury prolnuty.

- Vzhledem k asociativní povaze prolnutí s předem vynásobenou alfa je zjednodušeno víceprůchodové vykreslování průsvitných objektů.

- Použitím předem vynásobeného alfa lze dosáhnout jak čistého aditivního prolnutí (nastavením alfa na nulu), tak lineárně interpolovaným prolnutím současně. Například v částicovém systému se aditivní směs ohnivých částic může stát průsvitnou kouřovou částicí, která se mísí pomocí lineární interpolace. Bez předem vynásobené alfa, budete muset čerpat částice ohně odděleně od kouřových částic a upravit stav vykreslení mezi voláním kreslení.

- Textury, které používají předem vynásobenou alfa komprimovanou s vyšší kvalitou než ty, které nevykazují vybledlé hrany – nebo "efekt aureoly", které mohou být výsledkem, když prolnete textury, které nepoužívají předem vynásobenou alfa.

#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Vytvoření textury, která používá předem vynásobenou alfa verzi

1. Začněte se základní texturou. Načtěte existující obrazový soubor nebo jej vytvořte podle popisu v [části Postup: Vytvoření základní textury](../designers/how-to-create-a-basic-texture.md).

2. Nakonfigurujte soubor textury tak, aby byl zpracován kanálem obsahu obrázků. V **Průzkumníku řešení**otevřete místní nabídku pro soubor textury a pak zvolte **Vlastnosti**. Na stránce **Configuration Properties** > **General** nastavte vlastnost **Typ položky** na Kanál obsahu **obrázku**. Ujistěte se, že **content** vlastnost je nastavena na **Ano** a **vyloučit z sestavení** je nastavena na **ne**, a pak zvolte **použít** tlačítko. Zobrazí se stránka vlastností vlastností konfigurace **kanálu obsahu obrázku.**

3. Nakonfigurujte kanál obsahu bitových obrázků tak, aby generoval předem vynásobenou alfa. Na stránce**Obecné** rozložení**obsahu** >  **obrazu vlastností** > konfigurace nastavte vlastnost **Převést na předem vynásobený alfa formát** na **Hodnotu Ano (/generatepremultipliedalpha).**

4. Zvolte tlačítko **OK.**

   Při vytváření projektu převede kanál obsahu obrázků zdrojový obraz z pracovního formátu do zadaný výstupního formátu – to zahrnuje převod obrazu na předem vynásobený alfa formát – a výsledek se zkopíruje do výstupu projektu. Adresář.