---
title: Generovat třídu nebo typ
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 94786ef10e427a0deb4f80471305509124f1638b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595628"
---
# <a name="generate-a-class-or-type-in-visual-studio"></a>Generování třídy nebo typu v sadě Visual Studio

Toto generování kódu se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje okamžitě vygenerovat kód pro třídu nebo typ.

**Kdy:** Zavedete novou třídu nebo typ a chcete správně deklarovat, automaticky.

**Proč:** Před použitím můžete deklarovat třídu nebo typ, ale tato funkce bude generovat třídu nebo typ automaticky.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na čáru, kde je červená vlnovka. Červená vlnovka označuje třídu, která ještě neexistuje.

   - C#:

       ![Zvýrazněný kód C #](media/class-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód VB](media/class-highlight-vb.png)

2. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
   - **Myš**
      - Klikněte pravým tlačítkem myši a vyberte nabídku **Rychlé akce a Refaktoringy.**
      - Najeďte přes červenou vlnovku a klikněte na ![chybová žárovka](media/error-bulb.png) ikona, která se zobrazí.
      - Klikněte na ![chybová žárovka](media/error-bulb.png) se zobrazí na levém okraji, pokud je textový kurzor již na řádku s červenou vlnovkou.

      ![Generovat náhled třídy](media/class-preview-cs.png)

3. V rozevírací nabídce vyberte jednu z možností:

   - Generovat třídu*TypeName*v&mdash;novém souboru Vytvoří třídu s názvem *TypeName* v souboru s názvem *TypeName*.cs/.vb
   - Generovat třídu "&mdash;*TypeName*" Vytvoří v aktuálním souboru třídu s názvem *TypeName.*
   - Generovat vnořenou třídu '*TypeName*'&mdash;Vytvoří třídu s názvem *TypeName* vnořenou uvnitř aktuální třídy.
   - Generovat nový typ... &mdash;Vytvoří novou třídu nebo strukturu se všemi zadanými vlastnostmi.

   > [!TIP]
   > Pomocí odkazu **Náhled změn** v dolní části okna náhledu [zobrazíte všechny změny,](../../ide/preview-changes.md) které budou provedeny před provedením výběru.

4. Pokud jste vybrali položku **Generovat nový typ,** otevře se dialogové okno **Generovat typ.** Nakonfigurujte usnadnění, druh a umístění nového typu.

   ![Generovat typ](media/class-newtype-cs.png)

   Výběr | Popis
   --- | ---
   Access | Nastavte typ, který má *výchozí*, *interní* nebo *veřejný* přístup.
   Druh | To lze nastavit jako *třídu* nebo *strukturu*.
   Name (Název) | Nelze jej změnit a bude se jedná o název, který jste již zadali.
   Project | Pokud existuje více projektů ve vašem řešení, můžete si vybrat, kde chcete třídy/struktury žít.
   Název souboru | Můžete vytvořit nový soubor nebo můžete přidat typ do existujícího souboru.

Třída nebo struktura je vytvořena. Pro C#je také vytvořen konstruktor.

- C#

   ![Generovat výsledek třídy C #](media/class-result-cs.png)

- Visual Basic

   ![Generovat výsledek třídy VB](media/class-result-vb.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
