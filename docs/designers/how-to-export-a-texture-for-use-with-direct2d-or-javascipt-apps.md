---
title: 'Postupy: Export textury pro použití s rozhraním Direct2D nebo aplikacemi JavaScript'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c748e8b380da906ca9fb8fc8588efa6ffcc44980
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826366"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps"></a>Postupy: Export textury pro použití s rozhraním Direct2D nebo aplikacemi

Kanál s obsahem obrazu může generovat textury, které jsou kompatibilní s Direct2D interní konvencí vykreslování. Textury tohoto druhu jsou vhodné pro použití v aplikacích, které používají rozhraní Direct2D a v aplikacích pro UPW vytvořené pomocí jazyka JavaScript.

Tento dokument vysvětluje tyto činnosti:

-   Konfigurace zdrojového obrazu pro zpracování obsahu kanálu obrázku.

-   Konfigurace obsahu kanálu obrázku ke generování textur, který vám pomůže v aplikaci Direct2D nebo JavaScript.

    -   Generovat komprimovanými *.dds* souboru.

    -   Generoval vynásobený kanál alfa.

    -   Zakážete generování mipmap.

## <a name="rendering-conventions-in-direct2d"></a>Vykreslování konvence v Direct2D

Textury, které se používají v souvislosti s Direct2D musí splňovat tyto vnitřní konvence Direct2D vykreslování:

-   Direct2D implementuje průhlednost a průsvitnost pomocí předem vynásobené hodnoty alfa. Textury použité v rámci Direct2D musí obsahovat předem vynásobenou hodnotu alpha, i když textury nepoužívají průhlednost nebo průsvitnost. Další informace o přednásobeném kanálu alfa naleznete v tématu [postupy: Export textury s Přednásobeným alfa](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).

-   Textura musí být zadána *.dds* formátu pomocí jedné z těchto formátů komprese bloku:

    -   Komprese BC1_UNORM

    -   BC2_UNORM komprese

    -   BC3_UNORM komprese

-   Mipmapy nejsou podporovány.

### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Vytvoření textury, který je kompatibilní s konvencemi vykreslování Direct2D

1. Začněte základní texturou. Načtěte stávající obrazový nebo vytvořte novou, jak je popsáno v [postupy: vytvoření základní textury](../designers/how-to-create-a-basic-texture.md). Pro podporu blokové komprese ve *.dds* formátování, určete texturu, která má šířku a výšku, které jsou násobky čtyř, velikost, například 100 x 100, 128 x 128 nebo 256 x 192. Protože není podporován mipmapping, textura nemá být čtvercová a nemá být mocninou čísla 2 velikosti.

2. Nakonfigurujte soubor textury tak, aby byl zpracován kanálem obsahu obrázku. V **Průzkumníka řešení**, otevřete místní nabídku pro soubor textury, který jste právě vytvořili a klikněte na tlačítko **vlastnosti**. Na **vlastnosti konfigurace** > **Obecné** nastavte **typ položky** vlastnost **kanál obsahu obrazu**. Ujistěte se, že **obsahu** je nastavena na **Ano** a **vyloučit ze sestavení** je nastavena na **ne**a klikněte na tlačítko  **Použít** tlačítko. **Kanál obsahu obrazu** se zobrazí stránka pro konfiguraci vlastností.

3. Nastavte formátu výstupu do jednoho z formátů komprimovanými. Na **vlastnosti konfigurace** > **kanál obsahu obrazu** > **Obecné** nastavte **komprimovat**vlastnost **BC3_UNORM komprese (/ komprese: BC3_UNORM)**. Může zvolit některý z jiných formátů BC1, BC2 nebo BC3 formátů, v závislosti na vašich požadavcích. Direct2D nepodporuje aktuálně textury BC4, BC5, BC6 nebo BC7 textury. Další informace o různých formátech BC naleznete v tématu [blokovat komprese (Direct3D 10)](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-resources-block-compression).

   > [!NOTE]
   > Formát komprese, který je určen Určuje formát souboru, který je vytvořen kanál obsahu obrázku. To se liší od **formátu** vlastnost zdrojového obrázku v editoru obrázků, což určuje formát zdrojového souboru bitové kopie uloženého na disku – to znamená, *pracovního formátu*. Obvykle nechcete komprimovaný pracovní formát.

4. Nakonfigurujte kanál obsahu obrázku vytvořit výstup, který používá předem vynásobené hodnoty alfa. Na **vlastnosti konfigurace** > **kanál obsahu obrazu** > **Obecné** nastavte **převést na Formát přednásobené alfa** vlastnost **Ano (/ generatepremultipliedalpha)**.

5. Nakonfigurujte kanál obsahu obrázku tak, aby negeneroval mipmapy. Na **vlastnosti konfigurace** > **kanál obsahu obrazu** > **Obecné** nastavte **generovat Mips** vlastnost **ne**.

6. Zvolte **OK** tlačítko.

   Při sestavování projektu kanál obsahu obrazu převede zdrojový obraz z pracovního formátu na výstupní formát, který jste zadali – převod zahrnuje generování předem vynásobených hodnot alfa – a výsledek je zkopírován do výstupního adresáře projektu.