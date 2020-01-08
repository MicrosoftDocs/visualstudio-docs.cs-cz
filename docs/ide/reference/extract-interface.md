---
title: Rozhraní refaktoring extrahovat
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595667"
---
# <a name="extract-an-interface-refactoring"></a>Rozhraní refaktoring extrahovat

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Umožňuje vytvořit rozhraní pomocí stávajících členů z třídy, struktury nebo rozhraní.

**Když:** Máte členy třídy, struktury nebo rozhraní, které by mohly být děděny jinými třídami, strukturami nebo rozhraními.

**Důvod, proč:** rozhraní jsou skvělé konstrukce pro objektově orientované vzory. Představte si tříd pro různé zvířata (Dog Cat, Bird), které by mohly běžné metody, jako je například Eat nápoje, přejít do režimu spánku. Použití rozhraní jako IAnimal by umožnilo pes, Cat a Bird mají společnou "podpis" pro tyto metody.

## <a name="extract-an-interface-refactoring"></a>Rozhraní refaktoring extrahovat

1. Umístěte kurzor do názvu třídy.

   - C#:

       ![Zvýrazněný kód:C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód – Visual Basic](media/extractinterface-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stisknutím klávesy **Ctrl + R**, pak **Ctrl + I**. (Vaše klávesová zkratka se může lišit v závislosti na vybraném profilu.)
      - Stisknutím klávesy **Ctrl**+ **.** aktivační událost **rychlé akce a Refaktoringy** nabídky a vybereme **extrahování rozhraní** z automaticky otevíraného okna okno náhledu.
   - **Myši**
      - Vyberte **Upravit > Refaktorovat > extrahování rozhraní**.
      - Klikněte pravým tlačítkem na název třídy, vyberte **rychlé akce a Refaktoringy** nabídky a vybereme **extrahování rozhraní** z automaticky otevíraného okna okno náhledu.

3. V **extrahování rozhraní** dialogové okno, která se otevře, zadejte informace o dotaz:

   ![extrahování rozhraní](media/extractinterface-dialog-same-file.png)

   | Pole | Popis |
   | - | - |
   | **Název nového rozhraní** | Název rozhraní, který se má vytvořit. Název bude ve výchozím nastavení nastaven na hodnotu*ClassName*, kde *ClassName* je název třídy, kterou jste vybrali výše. |
   | **Nový název souboru** | Název generovaného souboru, který bude obsahovat rozhraní. Stejně jako u názvu rozhraní bude tento název ve výchozím nastavení nastaven na hodnotu*ClassName*, kde *ClassName* je název třídy, kterou jste vybrali výše. Můžete také vybrat možnost, která se má **Přidat do aktuálního souboru**. |
   | **Vybrat veřejné členy rozhraní** | Položky, které chcete extrahovat do rozhraní. Můžete vybrat libovolný počet podle potřeby. |

4. Vyberte **OK**.

   Rozhraní se vytvoří v souboru zadaný název. Kromě toho, kterou jste vybrali třída implementuje rozhraní.

   - C#:

      ![Výsledná třída –C#](media/extractinterface-class-cs.png)

      ![Výsledné rozhraní –C#](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Výsledná Visual Basic třídy](media/extractinterface-class-vb.png)

      ![Výsledné rozhraní – Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Viz také:

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipy pro vývojáře .NET](../csharp-developer-productivity.md)
