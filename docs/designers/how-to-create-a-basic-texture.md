---
title: 'Postupy: Vytvoření základní textury'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4bd1d34ef2dc31935038bb1be30d548c58208fd
ms.sourcegitcommit: 25fc9605ba673afb51a24ce587cf4304b06aa577
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2018
ms.locfileid: "47028985"
---
# <a name="how-to-create-a-basic-texture"></a>Postupy: vytvoření základní textury

Tento článek ukazuje, jak použít Editor obrázků pro vytvoření základní textury, včetně následující činnosti:

- Nastavení velikosti pole textury

- Nastavení barvy popředí a pozadí

- Prostřednictvím alfa kanálu (transparentnost)

- Použití **vyplnit** a **Elipsa** nástroje

- Nastavení vlastnosti nástroje

## <a name="create-a-basic-texture"></a>Vytvoření základní textury

Můžete použít Editor obrázků pro vytvoření a úprava obrazů a textur pro vaše hry nebo aplikace.

Následující kroky ukazují, jak vytvořit texturu, která představuje cíl "terč". Až skončíte, by měla textura vypadat jako na následujícím obrázku. K předvedení lépe průhlednosti v textuře, Editor obrázků má nakonfigurovaná pro použití vzoru zelené, šachovnicová mřížka zobrazíte.

![Cíl "Terč" s zobrazené zeleně transparentnosti](../designers/media/digit-bullseye-texture-in-editor.png)

Než začnete, ujistěte se, že **vlastnosti** se zobrazí okno. Můžete použít **vlastnosti** okna nastavte velikost obrázku, změňte vlastnosti nástroje a zadat barvy při práci.

### <a name="create-a-bullseye-target-texture"></a>Vytvoření textury cíl "terč"

1. Vytvořte textur, se kterým chcete pracovat. Informace o tom, jak přidat do projektu texturu naleznete v tématu [Editor obrázků](../designers/image-editor.md#get-started).

2. Nastavte velikost obrázku na 512 x 512 pixelů. V **vlastnosti** okno, nastavte hodnoty **šířka** a **výška** vlastností `512`.

3. Na panelu nástrojů editoru obrázků **vyplnit** nástroj. **Vlastnosti** okno nyní zobrazuje vlastnosti **vyplnit** spolu s vlastností bitové kopie.

4. Nastavte barvu popředí na zcela průhledný černý. V **vlastnosti** okno v **barvy** skupiny vlastností, vyberte **popředí**. Nastavte hodnoty **R**, **G**, **B**, a **A** vlastnosti vedle výběr barvy tento výběr `0`.

5. Na panelu nástrojů editoru obrázků **vyplnit** nástroj a potom stiskněte a podržte **Shift** klíče a zvolit libovolný bod v bitové kopii. Použití **Shift** klíč způsobí, že alfa hodnota barvy výplně nahradit barvu v obrázku; v opačném případě se používá hodnotu alfa zapojil barvu výplně spolu s barvu v obrázku.

    > [!IMPORTANT]
    > Tento krok, společně s výběr barvy v předchozím kroku, zajistí, že základní bitová kopie je připravená pro cílovou texturu "terč", který se vykreslí. Když je na obrázku vyplněna průhledný černý –, a proto je černá ohraničení cíle – bude existovat žádné třepící artefakty kolem cíl.

6. Na panelu nástrojů editoru obrázků **Elipsa** nástroj.

7. Neprůhledný černý nastavte barvu popředí. Nastavte hodnoty **R**, **G**, a **B** vlastností `0` a hodnota **A** vlastnost `255`.

8. Nastavte barvu pozadí na bílou úplně neprůhledné. V **vlastnosti** okno v **barvy** skupiny vlastností, vyberte **pozadí**. Nastavte hodnoty **R**, **G**, **B**, a **A** vlastností `255`.

9. Nastavte šířku obrysu elipsy. V **vlastnosti** okno v **vzhled** skupiny vlastnost, nastavte hodnotu **šířka** vlastnost `8`.

10. Ujistěte se, že je povolená vyhlazení. V **vlastnosti** okno v **vzhled** vlastnost skupině, ujistěte se, že **Vyhladit** je nastavena.

11. Použití **Elipsa** nástroj, nakreslete kruh z pixel souřadnice `(3, 3)` pixel koordinovat `(508, 508)`. Chcete-li nakreslit kruh snadněji, můžete stisknutím a podržením **Shift** klíče při kreslení.

    > [!NOTE]
    > Pixel souřadnice aktuální pozici ukazatele myši se zobrazí ve stavovém řádku sady Visual Studio.

12. Změna barvy pozadí. Nastavte **R** k `44`, **G** k `165`, **B** k `211`, a **A** k `255`.

13. Jiné kruh čerpat pixel souřadnice `(64, 64)` pixel koordinovat `(448, 448)`.

14. Změna barvy pozadí zpět na úplně neprůhledná bílou. Nastavte **R**, **G**, **B**, a **A** k `255`.

15. Jiné kruh čerpat pixel souřadnice `(128, 128)` pixel koordinovat `(384, 384)`.

16. Změna barvy pozadí. Nastavte **R** k `255`, **G** a **B** k `64`, a **A** k `255`.

17. Jiné kruh čerpat pixel souřadnice `(192, 192)` pixel koordinovat `(320, 320)`.

Cílové textury "terč" byla dokončena. Tady je posledním obrázku, s průhlednost.

![Kompletní "terč" cílovou texturu](../designers/media/gfx_image_demo_bullseye.png)

V dalším kroku můžete vygenerovat úrovně MIP této textury. Informace najdete v tématu [postupy: vytvoření a úprava úrovní MIP](../designers/how-to-create-and-modify-mip-levels.md).

## <a name="see-also"></a>Viz také:

- [Editor obrázků](../designers/image-editor.md)