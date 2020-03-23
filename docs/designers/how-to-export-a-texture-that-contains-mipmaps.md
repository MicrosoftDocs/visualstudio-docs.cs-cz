---
title: 'Postupy: Export textury obsahující mipmapy'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71d570e6dc7544911ebe2bb279aafb3a07620cbc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589406"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Postup: Export textury, která obsahuje mipmapy

Kanál obsahu obrázků může generovat mipmapy ze zdrojového obrazu jako součást fáze sestavení projektu. Chcete-li dosáhnout určitých efektů, někdy musíte zadat obsah obrazu každé úrovně MIP ručně. Pokud nepotřebujete zadat obsah obrazu každé úrovně MIP ručně, generování mipmap v době sestavení zajišťuje, že obsah mipmap nikdy nebude mimo synchronizaci. Také eliminuje náklady na výkon generování mipmap za běhu.

Tento článek se zabývá:

- Konfigurace zdrojového obrazu, který má být zpracován kanálem obsahu obrázku.

- Konfigurace kanálu obsahu obrázků pro generování mipmap.

## <a name="export-mipmaps"></a>Exportovat mipmapy

Mipmapping poskytuje automatické nastavení prostoru obrazovky Úroveň detailů pro texturované povrchy ve 3D hře nebo aplikaci. Zvyšuje výkon vykreslování hry nebo aplikace tím, že předem napočítává verze textury s ukázkami. Pre-computing down-sampled verze znamená, že celá textura nemusí být down-sampled pokaždé, když je vzorkován.

### <a name="to-export-a-texture-that-has-mipmaps"></a>Export textury s mipmapami

1. Začněte se základní texturou. Načtěte existující obrazový soubor nebo jej vytvořte podle popisu v [části Postup: Vytvoření základní textury](../designers/how-to-create-a-basic-texture.md). Chcete-li podporovat mipmaps, zadejte texturu, která má šířku a výšku, které jsou oba stejné mocniny ve velikosti, například 64x64, 256x256 nebo 512x512.

2. Nakonfigurujte právě vytvořený soubor textury tak, aby byl zpracován kanálem obsahu obrázků. V **Průzkumníku řešení**otevřete místní nabídku vytvořeného souboru textury a pak zvolte **Vlastnosti**. Na stránce **Configuration Properties** > **General** nastavte vlastnost **Typ položky** na Kanál obsahu **obrázku**. Ujistěte se, že **content** vlastnost je nastavena na **Ano** a **vyloučit z sestavení** je nastavena na **ne**. Vyberte **Použít**.

   Zobrazí se stránka vlastností vlastností konfigurace **kanálu obsahu obrázku.**

3. Nakonfigurujte kanál obsahu obrázků tak, aby generoval mipmapy. Na stránce**Obecné** pole**Obsahu** > obrazu **vlastností** > konfigurace nastavte vlastnost **Generate Mips** na **ano (/generatemips).**

4. Vyberte **OK**.

Při vytváření projektu převede kanál obsahu obrázků zdrojový obraz z pracovního formátu do zadaný výstupního formátu, včetně úrovní MIP. Výsledek je zkopírován do výstupního adresáře projektu.
