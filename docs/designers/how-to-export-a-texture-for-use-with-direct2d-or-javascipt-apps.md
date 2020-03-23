---
title: Export textury pro aplikace Direct2D a JavaScript
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d163aafa8b00ce1d59b1fc7b597ab5ca535a1ee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72635515"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascript-apps"></a>Postup: Export textury pro použití s aplikacemi Direct2D nebo JavaScript

Kanál obsahu obrázků může generovat textury, které jsou kompatibilní s interními konvencemi vykreslování rozhraní Direct2D. Textury tohoto druhu jsou vhodné pro použití v aplikacích, které používají Direct2D, a v aplikacích UPW vytvořených pomocí JavaScriptu.

Tento dokument ukazuje tyto činnosti:

- Konfigurace zdrojového obrazu, který má být zpracován kanálem obsahu obrázku.

- Konfigurace kanálu obsahu obrázků pro generování textury, kterou můžete použít v aplikaci Direct2D nebo JavaScript.

  - Vygenerujte blokkomprimovaný soubor *DDS.*

  - Generovat předem vynásobenou alfa.

  - Zakažte generování mipmap.

## <a name="rendering-conventions-in-direct2d"></a>Vykreslování konvencí v Direct2D

Textury, které se používají v kontextu Direct2D musí odpovídat tyto Direct2D vnitřní vykreslování konvence:

- Direct2D implementuje průhlednost a průsvitnost pomocí předem vynásobené alfa. Textury používané s Rozhraním Direct2D musí obsahovat předem vynásobenou alfa, i když textura nepoužívá průhlednost nebo průsvitnost. Další informace o předem vynásobené alfa, naleznete v [tématu Jak: Export textury, která má předem vynásobenou alfa](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).

- Textura musí být dodána ve formátu *.dds* pomocí jednoho z těchto formátů komprese bloků:

  - BC1_UNORM komprese

  - BC2_UNORM komprese

  - BC3_UNORM komprese

- Mipmapy nejsou podporovány.

### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Vytvoření textury, která je kompatibilní s konvencemi vykreslování Direct2D

1. Začněte se základní texturou. Načtěte existující obrázek nebo vytvořte nový obrázek, jak je popsáno v [části Postup: Vytvoření základní textury](../designers/how-to-create-a-basic-texture.md). Chcete-li podporovat kompresi bloků ve formátu *.dds,* zadejte texturu, která má šířku a výšku, které jsou násobky čtyř velikostí, například 100x100, 128x128 nebo 256x192. Vzhledem k tomu, že mipmapping není podporován, textura nemusí být čtvercová a nemusí mít velikost dvou mocnin.

2. Nakonfigurujte soubor textury tak, aby byl zpracován kanálem obsahu obrázků. V **Průzkumníku řešení**otevřete místní nabídku právě vytvořeného souboru textury a pak zvolte **Vlastnosti**. Na stránce **Configuration Properties** > **General** nastavte vlastnost **Typ položky** na Kanál obsahu **obrázku**. Ujistěte se, že **content** vlastnost je nastavena na **Ano** a **vyloučit z sestavení** je nastavena na **ne**, a pak zvolte **použít** tlačítko. Zobrazí se stránka vlastností vlastností konfigurace **kanálu obsahu obrázku.**

3. Nastavte výstupní formát na jeden z blokových komprimovaných formátů. Na stránce**Obecné** pole**Obsahu** > obrazu **vlastností** > konfigurace nastavte vlastnost **Compress** na **BC3_UNORM kompresi (/compress:BC3_UNORM).** V závislosti na vašich požadavcích můžete zvolit libovolný z ostatních formátů BC1, BC2 nebo BC3. Direct2D v současné době nepodporuje textury BC4, BC5, BC6 nebo BC7. Další informace o různých formátech BC naleznete v [tématu Bloková komprese (Direct3D 10)](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-resources-block-compression).

   > [!NOTE]
   > Zadaný formát komprese určuje formát souboru vytvořeného kanálem obsahu obrázků. To se liší od vlastnosti **Format** zdrojového obrazu v Editoru obrázků, která určuje formát zdrojového obrazového souboru uloženého na disku – *tj.* Obvykle nechcete pracovní formát, který je komprimovaný.

4. Nakonfigurujte kanál obsahu bitové kopie tak, aby vytvářel výstup, který používá předem vynásobenou alfa. Na stránce**Obecné** rozložení**obsahu** >  **obrazu vlastností** > konfigurace nastavte vlastnost **Převést na předem vynásobený alfa formát** na **Hodnotu Ano (/generatepremultipliedalpha).**

5. Nakonfigurujte kanál obsahu obrázku tak, aby negeneroval mipmapy. Na stránce**Obecné** pole**Obsahu** > obrazu **vlastností** > konfigurace nastavte vlastnost **Generate Mips** na **ne**.

6. Zvolte tlačítko **OK.**

   Při vytváření projektu převede kanál obsahu obrázků zdrojový obraz z pracovního formátu do zadaný výstupního formátu – převod zahrnuje generování předem vynásobené alfa – a výsledek se zkopíruje do výstupního adresáře projektu.
