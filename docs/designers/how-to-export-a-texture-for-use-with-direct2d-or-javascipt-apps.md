---
title: Export textury pro aplikace Direct2D a JavaScript
description: Kanál obsahu obrázku generuje textury kompatibilní s interním vykreslením Direct2D pro použití v aplikacích Direct2D a aplikacích UWP vytvořených pomocí JavaScriptu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 502dcaec9aeb8fdb2f4b7a72b801f19d2d08dbc4
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134391"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascript-apps"></a>Postupy: Export textury pro použití s aplikacemi Direct2D nebo JavaScript

Kanál obsahu obrázku může generovat textury, které jsou kompatibilní s Direct2D's interními vydanými konvencemi vykreslování. Textury tohoto druhu jsou vhodné pro použití v aplikacích, které používají Direct2D, a v aplikacích pro UWP vytvořených pomocí JavaScriptu.

Tento dokument znázorňuje tyto aktivity:

- Konfigurace zdrojového obrázku, který má být zpracován kanálem obsahu obrázku.

- Konfigurace kanálu obsahu obrázku tak, aby generovala texturu, kterou můžete použít v aplikaci Direct2D nebo JavaScript.

  - Vygenerujte soubor *. dds* komprimovaný blokem.

  - Generuje předem vynásobený alfa.

  - Zakáže generování mipmap.

## <a name="rendering-conventions-in-direct2d"></a>Konvence vykreslování v Direct2D

Textury používané v kontextu Direct2D musí splňovat tyto konvence interního vykreslování Direct2D:

- Direct2D implementuje transparentnost a průsvitnost pomocí předem vynásobené alfa. Textury používané s Direct2D musí obsahovat předem vynásobené alfa, a to i v případě, že textura nepoužívá transparentnost nebo průsvitnost. Další informace o předem vynásobeném alfa naleznete v tématu [How to: Export textury, která má předem vynásobený alfa](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).

- Textura musí být zadána ve formátu *. dds* pomocí jednoho z těchto formátů komprese bloku:

  - BC1_UNORM komprese

  - BC2_UNORM komprese

  - BC3_UNORM komprese

- Mipmapy se nepodporují.

### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Vytvoření textury, která je kompatibilní s Direct2Dmi konvencemi vykreslování

1. Začněte základní texturou. Načtěte existující bitovou kopii nebo vytvořte novou, jak je popsáno v tématu [How to: Create a Basic Texture](../designers/how-to-create-a-basic-texture.md). Chcete-li podporovat blokovou kompresi ve formátu *. dds* , určete texturu, která má šířku a výšku, které jsou násobky čtyř velikosti, například 100x100, 128 × 128 nebo 256x192. Vzhledem k tomu, že mipmapping není podporován, textura nemusí být čtvercová a nemusí být mocninou velikosti dvou.

2. Nakonfigurujte soubor textury tak, aby byl zpracován kanálem obsahu obrázku. V **Průzkumník řešení** otevřete místní nabídku pro soubor textury, který jste právě vytvořili, a pak zvolte **vlastnosti** . Na stránce **Vlastnosti konfigurace**  >  **Obecné** nastavte vlastnost **typ položky** na **kanál obsahu obrázku** . Ujistěte se, že vlastnost **Content** je nastavena na **hodnotu Ano** a možnost **vyloučit ze sestavení** je nastavena na hodnotu **ne** , a poté klikněte na tlačítko **použít** . Zobrazí se stránka vlastností konfigurace **kanálu obsahu obrázku** .

3. Nastavte formát výstupu na jeden z formátů komprimovaných blokem. Na stránce **Vlastnosti konfigurace**  >  **Obrázek kanálu obsahu obrázek**  >  **General** nastavte vlastnost **compress** na hodnotu **BC3_UNORM Compression (/Compress: BC3_UNORM)** . V závislosti na vašich požadavcích můžete zvolit libovolný z dalších formátů BC1, BC2 nebo BC3. Direct2D v současné době nepodporuje textury BC4, BC5, BC6 nebo BC7. Další informace o různých formátech BC naleznete v tématu [Block Compression (Direct3D 10)](/windows/desktop/direct3d10/d3d10-graphics-programming-guide-resources-block-compression).

   > [!NOTE]
   > Formát komprese, který je určen, určuje formát souboru, který je vytvořen kanálem obsahu obrázku. To se liší od vlastnosti **Formát** zdrojového obrázku v editoru obrázků, který určuje formát zdrojového souboru bitové kopie, který je uložen na disku – to znamená *pracovní formát* . Obvykle nechcete mít komprimovaný pracovní formát.

4. Nakonfigurujte kanál obsahu obrázku tak, aby vytvořil výstup, který používá předem vynásobený alfa. Na stránce **Vlastnosti konfigurace**  >  **Obrázek nastavení kanálu obsahu obrázek**  >  **General** nastavte vlastnost **převést na předem vynásobené alfa formát** na **Ano (/generatepremultipliedalpha)** .

5. Nakonfigurujte kanál obsahu obrázku tak, aby negeneroval mipmapy. Na stránce **Vlastnosti konfigurace**  >  **Obrázek nastavení kanálu obsahu**  >  **General** nastavte vlastnost **Generovat MIPS** na hodnotu **ne** .

6. Klikněte na tlačítko **OK** .

   Při sestavování projektu kanál obsahu obrazu převede zdrojový obraz z pracovního formátu na výstupní formát, který jste zadali – převod zahrnuje generaci předem vynásobené alfa – a výsledek je zkopírován do výstupního adresáře projektu.
