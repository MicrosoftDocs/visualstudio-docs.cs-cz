---
title: 'Postupy: Vytvoření základní textury | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a19cd0b68927effc32b0480fdeb7286be8ad8dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664578"
---
# <a name="how-to-create-a-basic-texture"></a>Postupy: Vytvoření základní textury
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument ukazuje, jak pomocí editoru obrázků vytvořit základní texturu.

 Tento dokument znázorňuje tyto aktivity:

- Nastavení velikosti textury

- Nastavení barev popředí a pozadí

- Používání alfa kanálu (transparentnost)

- Používání nástrojů **vyplnit** a **tři tečky**

- Nastavení vlastností nástroje

## <a name="creating-a-basic-texture"></a>Vytvoření základní textury
 Editor obrázků můžete použít k vytvoření a úpravě obrázků a textur pro vaši hru nebo aplikaci.

 Následující kroky ukazují, jak vytvořit texturu, která představuje cíl "Bullseye". Až budete hotovi, textura by měla vypadat jako na následujícím obrázku. Pro lepší znázornění průhlednosti v textuře byl Editor obrázků nakonfigurován tak, aby používal zelený a monitorový vzor k zobrazení.

 ![Cíl "Bullseye" s transparentností zobrazený zeleně](../designers/media/digit-bullseye-texture-in-editor.png "Číslice-Bullseye-textura in-Editor")

 Než začnete, ujistěte se, že se zobrazilo okno **vlastnosti** . Pomocí okna **vlastnosti** můžete nastavit velikost obrázku, změnit vlastnosti nástroje a určit barvy při práci.

#### <a name="to-create-a-bullseye-target-texture"></a>Chcete-li vytvořit cílovou texturu "Bullseye"

1. Vytvořte texturu, se kterou chcete pracovat. Informace o tom, jak přidat texturu do projektu, naleznete v části Začínáme v [editoru obrázků](../designers/image-editor.md).

2. Nastavte velikost obrázku na 512x512 pixelů. V okně **vlastnosti** nastavte hodnoty vlastnosti **Šířka** a **Výška** na `512` .

3. Na panelu nástrojů Editor obrázků vyberte nástroj **Fill** Tool. V okně **vlastnosti** se nyní zobrazí vlastnosti nástroje **Fill** spolu s vlastnostmi obrázku.

4. Nastavte barvu popředí na plně transparentní černou. V okně **vlastnosti** ve skupině vlastnost **barvy** vyberte tlačítko **popředí**. Nastavte hodnoty vlastností **R**, **G**, **B**a a vedle výběru **A** barvy na `0` .

5. Na panelu nástrojů Editor obrázků zvolte nástroj **Fill** , stiskněte a podržte klávesu SHIFT a vyberte libovolný bod v obrázku. Použití klávesy SHIFT způsobí, že hodnota alfa barvy výplně nahradí barvu v obrázku. v opačném případě se hodnota alfa používá k prolnutí barvy výplně spolu s barvou v obrázku.

   > [!IMPORTANT]
   > Tento krok společně s výběrem barvy v předchozím kroku zajistí, že se bude připravit základní obrázek pro cílovou texturu "Bullseye", kterou nakreslíte. Když je obrázek vyplněn průhledným černým a vzhledem k tomu, že ohraničením cíle je černé – k cíli nebudou žádné žádné artefakty s aliasy.

6. Na panelu nástrojů Editor obrázků vyberte nástroj **Elipsa** .

7. Nastavte barvu popředí na plně neprůhlednou černou. Nastavte hodnoty vlastností **R**, **G**a **B** na `0` a hodnotu vlastnosti **na** `255` .

8. Nastaví barvu pozadí na plně neprůhlednou bílou. V okně **vlastnosti** ve skupině vlastnost **barvy** vyberte možnost **pozadí**. Nastavte hodnoty vlastností **R**, **G**, **B**a a na **A** `255` .

9. Nastaví šířku obrysu elipsy. V okně **vlastnosti** ve skupině vlastnost **vzhled** nastavte hodnotu vlastnosti **Width** na `8` .

10. Ujistěte se, že je povolená ochrana proti aliasům. V okně **vlastnosti** ve skupině vlastností **vzhled** se ujistěte, že je nastavena vlastnost **anti-alias** .

11. Pomocí nástroje **Elipsa** nakreslete kružnici z souřadnice pixelu `(3, 3)` na souřadnici pixel `(508, 508)` . Chcete-li nakreslit kruh snadněji, můžete stisknout a podržet klávesu SHIFT při kreslení.

    > [!NOTE]
    > Souřadnice obrazového bodu aktuálního umístění ukazatele se zobrazí ve [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] stavovém řádku.

12. Změní barvu pozadí. Nastavte **R** na `44` , **G** na `165` , **B** na `211` a a **A** na `255` .

13. Nakreslete další kružnici z souřadnice pixelu `(64, 64)` na souřadnici pixelů `(448, 448)` .

14. Změňte barvu pozadí zpátky na zcela neprůhlednou bílou. Nastavte **R**, **G**, **B** **a a na** `255` .

15. Nakreslete další kružnici z souřadnice pixelu `(128, 128)` na souřadnici pixelů `(384, 384)` .

16. Změní barvu pozadí. Nastavte **R** na `255` , **G** a **B** na `64` a **A** `255` .

17. Nakreslete další kružnici z souřadnice pixelu `(192, 192)` na souřadnici pixelů `(320, 320)` .

    Cílová textura "Bullseye" je dokončena. Tady je finální obrázek, který je zobrazený s průhledností.

    ![Kompletní textura cíle "Bullseye"](../designers/media/gfx-image-demo-bullseye.png "gfx_image_demo_bullseye")

    V dalším kroku můžete vygenerovat úrovně MIP pro tuto texturu. Informace najdete v tématu [Postup: vytváření a úpravy úrovní MIP](../designers/how-to-create-and-modify-mip-levels.md).

## <a name="see-also"></a>Viz také
 [Editor obrázků](../designers/image-editor.md)
