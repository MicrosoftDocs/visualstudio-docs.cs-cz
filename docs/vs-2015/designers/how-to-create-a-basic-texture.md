---
title: 'Postupy: vytvoření základní textury | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2312b82fbcb6f4cd4ed00b288cb87283538cb372
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855830"
---
# <a name="how-to-create-a-basic-texture"></a>Postupy: Vytvoření základní textury
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument ukazuje, jak použít Editor obrázků pro vytvoření základní textury.  
  
 Tento dokument vysvětluje tyto činnosti:  
  
-   Nastavení velikosti pole textury  
  
-   Nastavení barvy popředí a pozadí  
  
-   Prostřednictvím alfa kanálu (transparentnost)  
  
-   Použití **vyplnit** a **Elipsa** nástroje  
  
-   Nastavení vlastnosti nástroje  
  
## <a name="creating-a-basic-texture"></a>Vytvoření základní textury  
 Můžete použít Editor obrázků pro vytvoření a úprava obrazů a textur pro vaše hry nebo aplikace.  
  
 Následující kroky ukazují, jak vytvořit texturu, která představuje cíl "terč". Až skončíte, by měla textura vypadat jako na následujícím obrázku. K předvedení lépe průhlednosti v textuře, Editor obrázků má nakonfigurovaná pro použití vzoru zelené, šachovnicová mřížka zobrazíte.  
  
 ![Cíl "Terč" s transparentnosti zobrazené zeleně](../designers/media/digit-bullseye-texture-in-editor.png "číslice-terč-textury – v editoru")  
  
 Než začnete, ujistěte se, že **vlastnosti** se zobrazí okno. Můžete použít **vlastnosti** okna nastavte velikost obrázku, změňte vlastnosti nástroje a zadat barvy při práci.  
  
#### <a name="to-create-a-bullseye-target-texture"></a>Vytvoření textury cíl "terč"  
  
1. Vytvořte textur pro práci s. Informace o tom, jak přidat do projektu texturu naleznete v části Začínáme v [Editor obrázků](../designers/image-editor.md).  
  
2. Nastavte velikost obrázku na 512 x 512 pixelů. V **vlastnosti** okno, nastavte hodnoty **šířka** a **výška** vlastností `512`.  
  
3. Na panelu nástrojů editoru obrázků **vyplnit** nástroj. **Vlastnosti** okno nyní zobrazuje vlastnosti **vyplnit** spolu s vlastností bitové kopie.  
  
4. Nastavte barvu popředí na zcela průhledný černý. V **vlastnosti** okno v **barvy** skupiny vlastností, vyberte **popředí**. Nastavte hodnoty **R**, **G**, **B**, a **A** vlastnosti vedle výběr barvy tento výběr `0`.  
  
5. Na panelu nástrojů editoru obrázků **vyplnit** nástroj a potom stiskněte a podržte klávesu Shift a vyberte libovolný bod v bitové kopii. Pomocí klávesy Shift způsobí, že alfa hodnota barvy výplně nahradit barvu v obrázku; v opačném případě hodnotu alfa slouží k blend barvu výplně spolu s barvu v obrázku.  
  
   > [!IMPORTANT]
   >  Tento krok, společně s výběr barvy v předchozím kroku, zajistí, že základní bitová kopie je připravená pro cílovou texturu "terč", který se vykreslí. Když je na obrázku vyplněna průhledný černý –, a proto je černá ohraničení cíle – bude existovat žádné třepící artefakty kolem cíl.  
  
6. Na panelu nástrojů editoru obrázků **Elipsa** nástroj.  
  
7. Nastavte barvu popředí zcela neprůhledný černý. Nastavte hodnoty **R**, **G**, a **B** vlastností `0` a hodnota **A** vlastnost `255`.  
  
8. Nastavte barvu pozadí na bílou úplně neprůhledné. V **vlastnosti** okno v **barvy** skupiny vlastností, vyberte **pozadí**. Nastavte hodnoty **R**, **G**, **B**, a **A** vlastností `255`.  
  
9. Nastavte šířku obrysu elipsy. V **vlastnosti** okno v **vzhled** skupiny vlastnost, nastavte hodnotu **šířka** vlastnost `8`.  
  
10. Ujistěte se, že je povolená vyhlazení. V **vlastnosti** okno v **vzhled** vlastnost skupině, ujistěte se, že **Vyhladit** je nastavena.  
  
11. Použití **Elipsa** nástroj, nakreslete kruh z pixel souřadnice `(3, 3)` pixel koordinovat `(508, 508)`. Chcete-li nakreslit kruh další snadno, můžete stisknutím klávesy a podržte klávesu Shift při kreslení.  
  
    > [!NOTE]
    >  Pixel souřadnice aktuální pozici ukazatele myši se zobrazují na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] stavový řádek.  
  
12. Změna barvy pozadí. Nastavte **R** k `44`, **G** k `165`, **B** k `211`, a **A** k `255`.  
  
13. Jiné kruh čerpat pixel souřadnice `(64, 64)` pixel koordinovat `(448, 448)`.  
  
14. Změna barvy pozadí zpět na bílou úplně neprůhledné. Nastavte **R**, **G**, **B**, a **A** k `255`.  
  
15. Jiné kruh čerpat pixel souřadnice `(128, 128)` pixel koordinovat `(384, 384)`.  
  
16. Změna barvy pozadí. Nastavte **R** k `255`, **G** a **B** k `64`, a **A** k `255`.  
  
17. Jiné kruh čerpat pixel souřadnice `(192, 192)` pixel koordinovat `(320, 320)`.  
  
    Cílové textury "terč" byla dokončena. Tady je posledním obrázku, s průhlednost.  
  
    ![Kompletní "terč" cílové textury](../designers/media/gfx-image-demo-bullseye.png "gfx_image_demo_bullseye")  
  
    V dalším kroku můžete vygenerovat úrovně MIP této textury. Informace najdete v tématu [jak: vytvořit a upravit MIP úrovních](../designers/how-to-create-and-modify-mip-levels.md).  
  
## <a name="see-also"></a>Viz také  
 [Editor obrázků](../designers/image-editor.md)



