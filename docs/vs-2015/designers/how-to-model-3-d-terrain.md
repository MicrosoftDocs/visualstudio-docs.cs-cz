---
title: 'Postupy: modelování 3D terénu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ab202ed97ce2056313eb661d51d7150bb9689829
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664415"
---
# <a name="how-to-model-3-d-terrain"></a>Postupy: Modelování 3D terénu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument ukazuje, jak použít Editor modelů k vytvoření 3D modelu trojrozměrného terénu.

 Tento dokument znázorňuje tyto aktivity:

- Přidání objektů do scény

- Výběr ploch a bodů

- Překládání výběrů

- Použití nástroje **rozdělit obličej**

- Orámování objektu na návrhové ploše

## <a name="creating-a-3-d-terrain-model"></a>Vytvoření 3D modelu terénu
 3D terén můžete vytvořit rozdělením roviny, aby se vytvořily další plošky, a pak bude manipulováno s vrcholy, abyste mohli vytvářet zajímavé funkce terénu.

 Až budete hotovi, model by měl vypadat takto:

 ![3&#45;D scény zobrazující model terénu](../designers/media/digit-terrain-model.png "Číslice-terén-model")

 Než začnete, ujistěte se, že se zobrazilo okno **vlastnosti** a **Sada nástrojů** .

#### <a name="to-create-a-3-d-terrain-model"></a>Vytvoření 3D modelu terénu

1. Vytvořte 3D model pro práci s. Informace o tom, jak přidat model do projektu, naleznete v části Začínáme v [editoru modelů](../designers/model-editor.md).

2. Přidejte rovinu do scény. V **sadě nástrojů**v části **tvary**vyberte **rovina** a přesuňte ji na návrhovou plochu.

   > [!TIP]
   > Chcete-li nastavit objekt roviny tak, aby lépe fungoval, můžete ho orámovat na návrhové ploše. V režimu **výběru** vyberte objekt rovina a pak na panelu nástrojů editoru modelů zvolte tlačítko **objekt rámce** .

3. Zadejte režim výběru obličeje. Na panelu nástrojů editoru modelů zvolte **možnost vybrat obličej**.

4. Rozdělit rovinu V režimu výběru plochy vyberte rovinu, která se má aktivovat pro výběr, a pak ji znovu vyberte, abyste vybrali jenom svoji plošku. Na panelu nástrojů editoru modelů vyberte **rozdělit plochu**. Tím přidáte nové vrcholy do roviny, které ji rozdělí do čtyř oddílů s rovnoměrné velikosti.

5. Vytvořte další dílčí dělení. Když je vybraná možnost nové plošky, klikněte na **rozdělit obličej** ještě dvakrát. Tím se vytvoří celkem 64 ploch. Vytvořením dalších dílčích dělení můžete přidělit terénu ještě více podrobností.

6. Zadejte režim výběru bodu. Na panelu nástrojů editoru modelů zvolte **možnost vybrat bod**.

7. Úpravou bodu vytvořte funkci terénu. V režimu výběru bodu vyberte jeden z bodů a pak na panelu nástrojů editoru modelů zvolte nástroj pro **Překlad** . Pole, které představuje bod, se zobrazí na návrhové ploše. Pomocí zelené šipky můžete přesunout pole a tím upravit výšku bodu. Opakujte tento krok pro různé body pro vytváření zajímavých funkcí terénu.

   > [!TIP]
   > Můžete vybrat několik bodů najednou a upravit je jednotným způsobem.

   Model terénu je dokončený. Zde je konečný model znovu s aplikovaným Phongova stínováním:

   ![3&#45;D scény zobrazující model terénu](../designers/media/digit-terrain-model.png "Číslice-terén-model")

   Tento model terénu lze použít k předvedení efektu přechodu, který je popsán v tématu [Postupy: vytvoření shaderu přechodu na základě geometrie](../designers/how-to-create-a-geometry-based-gradient-shader.md).

## <a name="see-also"></a>Viz také
 [Editor modelů](../designers/model-editor.md)
