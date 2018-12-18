---
title: 'Postupy: Synchronizace sady pravidel projektu kódu se zásadou vrácení se změnami týmového projektu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3769962829f5d0511b684f03ad8682071b48c07b
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281153"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-an-azure-devops-project-check-in-policy"></a>Postupy: synchronizace sad pravidel projektu kódu pomocí zásad vracení se změnami Azure DevOps Project

Synchronizovat nastavení analýzy kódu pro projekty kódu mají zásady vrácení se změnami pro Azure DevOps project tak, že zadáte sadu pravidel, která obsahuje aspoň pravidla, která jsou uvedená v pravidle nastavit zásady vrácení se změnami. Váš vedoucí vývojář může informovat o název a umístění sada pravidel pro zásadu vrácení se změnami. Jeden z následujících možností můžete zajistit, že analýzy kódu pro projekt používá správné sady pravidel:

-   Pokud zásady vrácení se změnami používá jedné sady předdefinovaných pravidel společnosti Microsoft, otevřete dialogové okno Vlastnosti projektu kódu, zobrazení stránky pro analýzu kódu a vyberte pravidlo, nastavte na stránce analýzy kódu v nastavení projektu kódu. Společnost Microsoft sad standardních pravidel jsou automaticky nainstalován se sadou Visual Studio jsou nastaveny na jen pro čtení a by neměla být upravována. Pokud se neupravují sady pravidel, pravidel zásad a nastaví místní pravidlo zaručeno tak, aby odpovídaly.

-   Pokud zásady vrácení se změnami používá vlastní sady pravidel, proveďte operaci načíst v souboru sady pravidel v rámci správy verzí, chcete-li vytvořit místní kopii. V nastavení analýzy kódu pro projekt kódu zadejte tento místní umístění. Pravidla zaručeno splněno, pokud je aktuální pravidlo pro nastavení zásady vrácení se změnami.

     Pokud namapujete umístění ovládacího prvku verze do místní složky, který je ve stejné relaci do kořenového adresáře Azure DevOps project jako kód projektu, umístění pravidla se nastaví pomocí relativní cesty. Relativní cesta se zajistí, že nastavení projektů kód pro analýzu kódu lze přesunout do jiných počítačů.

-   Upravte kopii tohoto pravidla pro nastavení zásady vrácení se změnami pro projekt kódu. Ujistěte se, že nové sady pravidel obsahuje všechna pravidla v zásadách vrácení se změnami a ostatní pravidla, které chcete zahrnout. Ujistěte se, že vaše sada pravidel obsahuje všechna pravidla v pravidle, nastavte pro zásadu vrácení se změnami.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>Chcete-li určit standardních pravidel společnosti Microsoft nastavit

1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt kódu a potom klikněte na tlačítko **vlastnosti**.

2.  Klikněte na tlačítko **analýza kódu**.

3.  V **spustit tuto sadu pravidel** klikněte na možnost zásad vrácení se změnami sadu pravidel.

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Chcete-li určit sadu pravidel vlastních zásad vrácení se změnami

1.  V případě potřeby proveďte operaci načíst v souboru sady pravidel, která určuje zásady vrácení se změnami.

2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt kódu a potom klikněte na tlačítko **vlastnosti**.

3.  Klikněte na tlačítko **analýza kódu**.

4.  V **spustit tuto sadu pravidel** klikněte na možnost  **\<Procházet... >**.

5.  V **otevřít** dialogového okna zadejte soubor sady pravidel zásad vrácení se změnami.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Chcete-li vytvořit vlastní pravidlo nastavte pro projekt kódu

1.  Postupujte podle jednoho z postupů dříve v tomto tématu vyberte zásadu vrácení se změnami z Azure DevOps project na stránce analýzy kódu v dialogovém okně nastavení projektu.

2.  Klikněte na tlačítko **otevřít**.

3.  Přidání nebo odebrání pravidla pomocí [s editorem sad pravidel](../code-quality/working-in-the-code-analysis-rule-set-editor.md).

4.  Uložte upravený pravidlo nastavte soubor .ruleset v místním počítači nebo na cestu UNC.

5.  Otevřete dialogové okno Vlastnosti projektu kódu a zobrazit **analýzy kódu** stránky.

6.  V **spustit tuto sadu pravidel** klikněte na možnost  **\<Procházet... >**.

7.  V **otevřít** dialogového okna zadejte soubor sady pravidel.