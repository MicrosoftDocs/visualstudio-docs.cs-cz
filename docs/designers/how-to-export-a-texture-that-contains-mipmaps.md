---
title: 'Postupy: Export textury obsahující mipmapy'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b46a353606fc90aa89abf68d1e901675b4880b4c
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768928"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Postupy: Export textury obsahující mipmapy

Kanál obsahu obrázku může vygenerovat mipmapy ze zdrojového obrázku jako součást fáze sestavení vašeho projektu. Aby bylo možné dosáhnout určitých účinků, někdy je nutné zadat obsah obrázku pro každou úroveň MIP ručně. Pokud nepotřebujete určit obsah obrázku v každé úrovni MIP ručně, generování mipmapy při sestavení zajistí, aby se mipmap obsah nikdy nesynchronizoval. Také eliminuje náklady na výkon při generování mipmapy v době běhu.

Tento článek popisuje:

- Konfigurace zdrojového obrázku, který má být zpracován kanálem obsahu obrázku.

- Konfigurace kanálu obsahu obrázku tak, aby generoval mipmapy.

## <a name="export-mipmaps"></a>Exportovat mipmapy

Mipmapping poskytuje pro texturované plochy v 3D hře nebo aplikaci automatickou úroveň podrobností na obrazovce. Zlepšuje výkon při vykreslování hry nebo aplikace pomocí předběžného zpracování ukázkových verzí textury. Verze předběžného zpracování vzorků znamená, že celá textura nemusí být pokaždé vzorkování pokaždé, když je vzorkovaná.

### <a name="to-export-a-texture-that-has-mipmaps"></a>Export textury, která má mipmapy

1. Začněte základní texturou. Načtěte existující soubor obrázku nebo ho vytvořte tak, jak je popsáno v tématu [Postupy: Vytvoření základní textury](../designers/how-to-create-a-basic-texture.md). Pro podporu mipmapy určete texturu, která má šířku a výšku, které mají stejnou mocninu dvou velikostí, například 64 × 64, 256x256 nebo 512x512.

2. Nakonfigurujte soubor textury, který jste právě vytvořili, aby byl zpracován kanálem obsahu obrázku. V **Průzkumník řešení**otevřete místní nabídku pro soubor textury, který jste vytvořili, a pak zvolte **vlastnosti**. Na stránce **Vlastnosti konfigurace**  >  **Obecné** nastavte vlastnost **typ položky** na **kanál obsahu obrázku**. Ujistěte se, že vlastnost **Content** je nastavená na **hodnotu Ano** a **vyloučit z buildu** je nastavená na **ne**. Vyberte **Použít**.

   Zobrazí se stránka vlastností konfigurace **kanálu obsahu obrázku** .

3. Nakonfigurujte kanál obsahu obrázku tak, aby generoval mipmapy. Na stránce **Vlastnosti konfigurace**  >  **Obrázek nastavení kanálu obsahu obrázek**  >  **General** nastavte vlastnost **Generovat MIPS** na **Ano (/generatemips)**.

4. Vyberte **OK**.

Při sestavování projektu kanál obsahu obrazu převede zdrojový obraz z pracovního formátu na výstupní formát, který jste zadali, včetně úrovní MIP. Výsledek je zkopírován do výstupního adresáře projektu.
