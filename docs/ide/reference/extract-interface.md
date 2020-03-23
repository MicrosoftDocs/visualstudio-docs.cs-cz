---
title: Extrahovat refaktoring rozhraní
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595667"
---
# <a name="extract-an-interface-refactoring"></a>Extrahovat refaktoring rozhraní

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje vytvořit rozhraní pomocí existujících členů z třídy, struktury nebo rozhraní.

**Kdy:** Máte členy ve třídě, struktuře nebo rozhraní, které by mohly být zděděny jinými třídami, strukturami nebo rozhraními.

**Proč:** Rozhraní jsou skvělé konstrukce pro objektově orientované návrhy. Představte si, že třídy pro různá zvířata (Pes, Kočka, Pták), které by mohly mít všechny společné metody, jako je jíst, pít, spát. Použití rozhraní, jako je IAnimal by umožnilo pes, kočka a pták mít společný "podpis" pro tyto metody.

## <a name="extract-an-interface-refactoring"></a>Extrahovat refaktoring rozhraní

1. Umístěte kurzor do názvu třídy.

   - C#:

       ![Zvýrazněný kód - C #](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód – Visual Basic](media/extractinterface-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stiskněte **kombinaci kláves Ctrl+R**a potom **kombinaci kláves Ctrl+I**. (Klávesová zkratka se může lišit podle vybraného profilu.)
      - Stiskněte **klávesu Ctrl**+**.** aktivujte nabídku **Rychlé akce a Refaktoringy** a z místního okna Náhled vyberte **Extrahovat rozhraní.**
   - **Myš**
      - Vyberte **možnost Upravit > refaktorovat rozhraní > extrahovat**.
      - Klikněte pravým tlačítkem myši na název třídy, vyberte nabídku **Rychlé akce a Refaktoringy** a z vyskakovacího okna Náhled vyberte **Extrahovat rozhraní.**

3. V dialogovém okně **Extrahovat rozhraní,** které se objeví, zadejte požadované informace:

   ![extrahování rozhraní](media/extractinterface-dialog-same-file.png)

   | Pole | Popis |
   | - | - |
   | **Nový název rozhraní** | Název rozhraní, které má být vytvořeno. Název bude ve výchozím nastavení i Název*třídy*, kde *Název třídy* je název třídy, kterou jste vybrali výše. |
   | **Nový název souboru** | Název generovaného souboru, který bude obsahovat rozhraní. Stejně jako u názvu rozhraní bude tento název ve výchozím nastavení nastaven na I*ClassName*, kde *Název třídy* je název třídy, kterou jste vybrali výše. Můžete také vybrat možnost **Přidat do aktuálního souboru**. |
   | **Vyberte veřejné členy, aby vytvořili rozhraní** | Položky extrahovat do rozhraní. Můžete si vybrat tolik, kolik budete chtít. |

4. Vyberte **OK**.

   Rozhraní je vytvořeno v souboru zadaného názvu. Kromě toho třída, kterou jste vybrali implementuje toto rozhraní.

   - C#:

      ![Výsledná třída - C #](media/extractinterface-class-cs.png)

      ![Výsledné rozhraní - C #](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Výsledná třída – visual basic](media/extractinterface-class-vb.png)

      ![Výsledné rozhraní – visual basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipy pro vývojáře rozhraní .NET](../csharp-developer-productivity.md)
