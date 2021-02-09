---
title: 'Postupy: Export textury s přednásobeným alfa'
description: Přečtěte si, jak kanál obsahu v obraze generuje předem vynásobené alfa textury ze zdrojové image, kterou je možné zjednodušit a využít a robustnější.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 56e8d198e55b521b761f8f3a7b54f6c2c0ee2c33
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930929"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Postupy: Export textury s přednásobeným alfa

Kanál obsahu obrázku může ve zdrojové imagi generovat předem vynásobené alfa textury. Ty mohou být jednodušší použít a robustnější než textury, které neobsahují předem vynásobené alfa.

Tento dokument znázorňuje tyto aktivity:

- Konfigurace zdrojového obrázku, který má být zpracován kanálem obsahu obrázku.

- Konfigurace kanálu obsahu obrázku tak, aby generovala předem vynásobený kanál alfa.

## <a name="premultiplied-alpha"></a>Předem vynásobený alfa
Předem vynásobený alfa nabízí několik výhod oproti konvenčnímu nenásobenému alfa, protože lépe představuje skutečnou interakci světla s fyzickými materiály oddělením příspěvku barvy Texel (barvy, kterou přidá do scény) z průsvitnost (množství základní barvy, kterou umožňuje prostřednictvím). Některé výhody použití předem vynásobené alfa jsou:

- Smíchání s předem vynásobeným alfa je asociativní operace; Výsledek prolnutí více průsvitných textur je stejný, bez ohledu na pořadí, ve kterém jsou textury smíchány.

- Z důvodu asociativního charakteru prolnutí s předem vynásobeným alfa se zjednodušené vykreslování průsvitných objektů zjednodušuje.

- Pomocí předem vynásobené hodnoty alfa je možné dosáhnout souběžně čistě doplňkového míchání (nastavením hodnoty Alpha na nulu) a lineárně interpolované prolnutí. Například v systému částic se mohou doplňkové směsné částice požáru stát průsvitnými částicemi kouře, které jsou smíchány pomocí lineární interpolace. Bez předem vynásobené alfa by bylo nutné vykreslit částice požáru odděleně od kouřových částic a změnit stav vykreslování mezi voláními vykreslování.

- Textury, které používají předem vynásobené alfa kompresi s vyšší kvalitou než ty, které nejsou, a neprojevují debarvované hrany nebo "halo efekt", které mohou být výsledkem prolnutí textur, které nepoužívají předem vynásobené alfa.

#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Vytvoření textury, která používá předem vynásobené alfa

1. Začněte základní texturou. Načtěte existující soubor obrázku nebo ho vytvořte tak, jak je popsáno v tématu [Postupy: Vytvoření základní textury](../designers/how-to-create-a-basic-texture.md).

2. Nakonfigurujte soubor textury tak, aby byl zpracován kanálem obsahu obrázku. V **Průzkumník řešení** otevřete místní nabídku pro soubor textury a zvolte možnost **vlastnosti**. Na stránce **Vlastnosti konfigurace**  >  **Obecné** nastavte vlastnost **typ položky** na **kanál obsahu obrázku**. Ujistěte se, že vlastnost **Content** je nastavena na **hodnotu Ano** a možnost **vyloučit ze sestavení** je nastavena na hodnotu **ne**, a poté klikněte na tlačítko **použít** . Zobrazí se stránka vlastností konfigurace **kanálu obsahu obrázku** .

3. Nakonfigurujte kanál obsahu obrázku tak, aby generoval předem vynásobený alfa. Na stránce **Vlastnosti konfigurace**  >  **Obrázek nastavení kanálu obsahu obrázek**  >   nastavte vlastnost **převést na předem vynásobené alfa formát** na **Ano (/generatepremultipliedalpha)**.

4. Klikněte na tlačítko **OK** .

   Při sestavování projektu kanál obsahu obrazu převede zdrojový obraz z pracovního formátu na výstupní formát, který jste zadali – to zahrnuje převod obrázku na předem vynásobený formát alfa – a výsledek je zkopírován do výstupního adresáře projektu.