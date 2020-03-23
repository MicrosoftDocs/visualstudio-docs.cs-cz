---
title: 'Postupy: Vytvoření základní textury'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 916be87824a86e96d6fcb791cf8181d70e1e8104
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589449"
---
# <a name="how-to-create-a-basic-texture"></a>Postupy: Vytvoření základní textury

Tento článek ukazuje, jak pomocí editoru obrázků vytvořit základní texturu, včetně následujících aktivit:

- Nastavení velikosti textury

- Nastavení barev popředí a pozadí

- Použití alfa kanálu (průhlednost)

- Použití nástrojů **Výplň** **a Elipsa**

- Nastavení vlastností nástroje

## <a name="create-a-basic-texture"></a>Vytvoření základní textury

Pomocí Editoru obrázků můžete vytvářet a upravovat obrázky a textury pro vaši hru nebo aplikaci.

Následující kroky ukazují, jak vytvořit texturu, která představuje cíl "bullseye". Po dokončení by měla textura vypadat jako na následujícím obrázku. Aby bylo lepší zobrazení průhlednosti textury, editor obrázků byl nakonfigurován tak, aby k jeho zobrazení používal zelený šachovný vzor.

!["Bullseye" cíl s průhledností zobrazenou zeleně](../designers/media/digit-bullseye-texture-in-editor.png)

Než začnete, ujistěte se, že se zobrazí okno **Vlastnosti.** Okno **Vlastnosti** slouží k nastavení velikosti obrazu, změně vlastností nástroje a určení barev při práci.

### <a name="create-a-bullseye-target-texture"></a>Vytvoření textury cíle "bullseye"

1. Vytvořte texturu, se kterou chcete pracovat. Informace o přidání textury do projektu naleznete v [Editoru obrázků](../designers/image-editor.md#get-started).

2. Nastavte velikost obrazu na 512 x 512 pixelů. V okně **Vlastnosti** nastavte hodnoty vlastností **Šířka** a **Výška** na `512`.

3. Na panelu nástrojů Editor obrázků zvolte nástroj **výplň.** Okno **Vlastnosti** nyní zobrazuje vlastnosti nástroje **výplň** spolu s vlastnostmi obrazu.

4. Nastavte barvu popředí na zcela průhlednou černou. V okně **Vlastnosti** vyberte ve skupině **vlastností Barvy** **popředí**. Nastavte hodnoty vlastností **R**, **G**, **B**a **A** `0`vedle výběru barev na .

5. Na panelu nástrojů Editor obrázků zvolte nástroj **výplň** a stiskněte a podržte klávesu **Shift** a zvolte libovolný bod v obraze. Použití klávesy **Shift** způsobí, že alfa hodnota barvy výplně nahradí barvu v obraze; v opačném případě se hodnota alfa použije k prolnutí barvy výplně spolu s barvou v obraze.

    > [!IMPORTANT]
    > Tento krok spolu s výběrem barev v předchozím kroku zajišťuje, že základní obraz je připraven pro cílovou texturu "bullseye", kterou nakreslíte. Když je obraz vyplněn průhlednou černou – a protože ohraničení cíle je černé – nebudou kolem cíle žádné artefakty aliasingu.

6. Na panelu nástrojů Editor obrázků zvolte nástroj **elipsa.**

7. Nastavte barvu popředí na zcela neprůhlednou černou. Nastavte hodnoty vlastností **R**, **G** `0` a **B** na hodnotu `255`a hodnotu **Vlastnosti A** na .

8. Nastavte barvu pozadí na zcela neprůhlednou bílou. V okně **Vlastnosti** vyberte ve skupině vlastností **Barvy** **možnost Pozadí**. Nastavte hodnoty vlastností **R**, **G**, `255` **B**a **A** na .

9. Nastavte šířku obrysu elipsy. V okně **Vlastnosti** nastavte ve skupině vlastností **Vzhled** hodnotu **width** vlastnosti na `8`.

10. Ujistěte se, že je povoleno vyhlazení. V okně **Vlastnosti** se ve skupině vlastností **Vzhled** ujistěte, že je nastavena vlastnost **Anti-alias.**

11. Pomocí nástroje **Elipsa** nakreslete kružnici od souřadnice `(3, 3)` obrazových bodů k souřadnici `(508, 508)`obrazových bodů . Chcete-li kruh nakreslit snadněji, můžete při kreslení stisknout a podržet klávesu **Shift.**

    > [!NOTE]
    > Souřadnice obrazových bodů aktuálního umístění ukazatele se zobrazí na stavovém řádku sady Visual Studio.

12. Změňte barvu pozadí. Nastavte **R** R `44`na `165`, **G** až, `255` **B** až `211`, a **A** až .

13. Nakreslete `(64, 64)` další `(448, 448)`kružnici od souřadnice obrazových bodů k souřadnici obrazových bodů .

14. Změňte barvu pozadí zpět na zcela neprůhlednou bílou. Sada **R**, **G,** **B**a **A** až `255`.

15. Nakreslete `(128, 128)` další `(384, 384)`kružnici od souřadnice obrazových bodů k souřadnici obrazových bodů .

16. Změňte barvu pozadí. Nastavte **R** R `255`na , `64` **G** a **B** na , a **A** až `255`.

17. Nakreslete `(192, 192)` další `(320, 320)`kružnici od souřadnice obrazových bodů k souřadnici obrazových bodů .

Cílová textura "bullseye" je kompletní. Zde je konečný obrázek, zobrazený s průhledností.

![Kompletní "bullseye" cíl textury](../designers/media/gfx_image_demo_bullseye.png)

Jako další krok můžete generovat úrovně MIP pro tuto texturu. Další informace naleznete v [tématu How to: Create and modify MIP levels](../designers/how-to-create-and-modify-mip-levels.md).

## <a name="see-also"></a>Viz také

- [Editor obrázků](../designers/image-editor.md)
