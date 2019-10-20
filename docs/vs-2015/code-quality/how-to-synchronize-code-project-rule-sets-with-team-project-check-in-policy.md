---
title: 'Postupy: synchronizace sady pravidel projektu kódu se zásadou vrácení se změnami týmového projektu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3c6e7550940f9d2efa5ca228123310f1b861ee76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651603"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>Postupy: Synchronizace sady pravidel projektu kódu se zásadou vracení se změnami týmového projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Synchronizujete nastavení analýzy kódu pro projekty kódu se zásadou vrácení se změnami pro týmový projekt zadáním sady pravidel, která obsahuje alespoň pravidla zadaná v sadě pravidel pro zásadu vrácení se změnami. Váš vedoucí vývojář může informovat o názvu a umístění sady pravidel pro zásadu vrácení se změnami. Pomocí jedné z následujících možností lze zajistit, aby analýza kódu pro projekt používala správnou sadu pravidel:

- Pokud zásada vracení se změnami používá jednu z předdefinovaných sad pravidel společnosti Microsoft, otevřete dialogové okno Vlastnosti pro projekt kódu, zobrazte stránku Analýza kódu a vyberte sadu pravidel na stránce Analýza kódu v nastavení projektu kódu. Standardní sady pravidel společnosti Microsoft jsou automaticky nainstalovány se sadou Visual Studio, jsou nastaveny jen pro čtení a neměly by být upravovány. Pokud se sady pravidel neupravují, pravidla v zásadách a v místních pravidlech se budou zaručit, aby odpovídala.

- Pokud zásada vracení se změnami používá vlastní sadu pravidel, vytvořte místní kopii provedením operace Get v souboru sady pravidel ve správě verzí. Pak zadejte toto místní umístění v nastavení analýzy kódu pro projekt kódu. Je zaručeno, že pravidla budou shodná s tím, zda je sada pravidel pro zásady vracení se změnami v aktuálním stavu.

     Pokud namapujete umístění správy verzí na místní složku, která je ve stejné relaci jako projekt kódu, je umístění pravidla nastaveno pomocí relativní cesty. Relativní cesta zajišťuje, že nastavení projektu kódu pro analýzu kódu lze přesunout do jiných počítačů.

- Přizpůsobení kopie sady pravidel pro zásadu vrácení se změnami pro projekt kódu. Ujistěte se, že nová sada pravidel obsahuje všechna pravidla v zásadách vrácení se změnami a všechna další pravidla, která chcete zahrnout. Musíte se ujistit, že sada pravidel obsahuje všechna pravidla v sadě pravidel pro zásadu vrácení se změnami.

### <a name="to-specify-a-microsoft-standard-rule-set"></a>Určení standardní sady pravidel společnosti Microsoft

1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt kódu a pak klikněte na **vlastnosti**.

2. Klikněte na **Analýza kódu**.

3. V seznamu **Spustit tuto sadu pravidel** klikněte na sadu pravidel zásad vracení se změnami.

### <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Určení sady pravidel zásad pro vlastní vracení se změnami

1. V případě potřeby proveďte operaci získat v souboru sady pravidel, který určuje zásadu vrácení se změnami.

2. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt kódu a pak klikněte na **vlastnosti**.

3. Klikněte na **Analýza kódu**.

4. V seznamu **Spustit tuto sadu pravidel** klikněte na **\<Browse... >** .

5. V dialogovém okně **otevřít** zadejte soubor sady pravidel zásad vracení se změnami.

### <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Vytvoření vlastní sady pravidel pro projekt kódu

1. Použijte jeden z postupů uvedených výše v tomto tématu a vyberte zásadu vrácení se změnami týmového projektu na stránce Analýza kódu v dialogovém okně nastavení projektu.

2. Klikněte na **otevřít**.

3. Přidejte nebo odeberte pravidla pomocí editoru sad pravidel.

     Další informace najdete v tématu [vytváření vlastních sad pravidel](../code-quality/creating-custom-code-analysis-rule-sets.md).

4. Uložte upravenou sadu pravidel do souboru. ruleset v místním počítači nebo na cestu UNC.

5. Otevřete dialogové okno Vlastnosti pro projekt kódu a zobrazte stránku **Analýza kódu** .

6. V seznamu **Spustit tuto sadu pravidel** klikněte na **\<Browse... >** .

7. V dialogovém okně **otevřít** zadejte soubor sady pravidel.
