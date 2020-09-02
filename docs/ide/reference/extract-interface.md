---
title: Extrakce refaktoringu rozhraní
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 5055f50d07cf9362c9be1bdc8135e31240a7cc66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595667"
---
# <a name="extract-an-interface-refactoring"></a>Extrakce refaktoringu rozhraní

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Umožňuje vytvořit rozhraní pomocí stávajících členů z třídy, struktury nebo rozhraní.

**Když:** Máte členy třídy, struktury nebo rozhraní, které by mohly být děděny jinými třídami, strukturami nebo rozhraními.

**Proč:** Rozhraní jsou skvělé konstrukce pro objektově orientované návrhy. Představte si, že máte třídy pro různé živočichy (pes, Cat, ptáky), které by měly mít všechny společné metody, jako je například Eat, nápoj, spánek. Použití rozhraní, jako je IAnimal, umožňuje psa, Cat a ptáku mít pro tyto metody společný podpis.

## <a name="extract-an-interface-refactoring"></a>Extrakce refaktoringu rozhraní

1. Umístěte kurzor do názvu třídy.

   - C#:

       ![Zvýrazněný kód-C #](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód – Visual Basic](media/extractinterface-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stiskněte klávesy **CTRL + R**a potom **kombinaci kláves CTRL + I**. (Vaše klávesová zkratka se může lišit v závislosti na vybraném profilu.)
      - Stiskněte klávesu **CTRL** + **.** Chcete-li aktivovat nabídku **rychlé akce a refaktoring** a v okně Náhled vyberte možnost **Extrahovat rozhraní** .
   - **Myš**
      - Vyberte **upravit > refaktorovat > Extrahování rozhraní**.
      - Klikněte pravým tlačítkem myši na název třídy, vyberte nabídku **rychlé akce a refaktoring** a v okně Náhled **rozbalte položku extrahovat rozhraní** .

3. V dialogovém okně **rozbalte rozhraní** , které se zobrazí, zadejte požadované informace:

   ![extrahování rozhraní](media/extractinterface-dialog-same-file.png)

   | Pole | Popis |
   | - | - |
   | **Nový název rozhraní** | Název rozhraní, které se má vytvořit. Název bude ve výchozím nastavení nastaven na hodnotu*ClassName*, kde *ClassName* je název třídy, kterou jste vybrali výše. |
   | **Nový název souboru** | Název generovaného souboru, který bude obsahovat rozhraní. Stejně jako u názvu rozhraní bude tento název ve výchozím nastavení nastaven na hodnotu*ClassName*, kde *ClassName* je název třídy, kterou jste vybrali výše. Můžete také vybrat možnost, která se má **Přidat do aktuálního souboru**. |
   | **Vybrat veřejné členy pro vytvoření rozhraní** | Položky, které mají být extrahovány do rozhraní. Můžete vybrat tolik, kolik chcete. |

4. Vyberte **OK**.

   Rozhraní se vytvoří v souboru zadaného názvu. Kromě toho třída, kterou jste vybrali, implementuje toto rozhraní.

   - C#:

      ![Výsledná třída – C #](media/extractinterface-class-cs.png)

      ![Výsledné rozhraní-C #](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Výsledná Visual Basic třídy](media/extractinterface-class-vb.png)

      ![Výsledné rozhraní – Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipy pro vývojáře na platformě .NET](../csharp-developer-productivity.md)
