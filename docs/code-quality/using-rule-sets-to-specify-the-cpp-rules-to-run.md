---
title: Použití sad pravidel k určování pravidel C++ pro spuštění
ms.date: 04/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: a2bd14e4d052179df8a61dfa4b418f07b0f31e3c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893595"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Použití sad pravidel k určování pravidel C++ pro spuštění

V sadě Visual Studio, můžete vytvořit a upravit vlastní *sada pravidel, která* podle potřeb konkrétního projektu související s analýzou kódu. Výchozí sady pravidel jsou uloženy v `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`.

**Visual Studio 2017 verze 15.7** můžete vytvoření vlastních sad pravidel pomocí libovolného textového editoru a použít je v sestaveních příkazového řádku bez ohledu na to, co sestavovací systém, který používáte. Další informace najdete v tématu [/ analyze: ruleset](/cpp/build/reference/analyze-code-analysis).

K vytvoření vlastní sady v sadě Visual Studio pravidel C++, musí být otevřeny v integrovaném vývojovém prostředí sady Visual Studio projekt C/C++. Potom otevřete sadu standardních pravidel v editoru sad pravidel a pak přidat nebo odebrat konkrétní pravidla a volitelně změnit akce, která nastane, pokud analýza kódu určuje, že pravidlo bylo narušeno.

Chcete-li vytvořit nové vlastní pravidlo nastavte, uložte ho pomocí nového názvu souboru. Sada vlastních pravidel se automaticky přiřadí do projektu.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Chcete-li vytvořit vlastní pravidlo z jednoho stávající sadu pravidel

1. V Průzkumníku řešení otevřete místní nabídku pro projekt a klikněte na tlačítko **vlastnosti**.

2. Na **vlastnosti** kartě **analýzy kódu**.

3. V **sady pravidel** rozevíracího seznamu, proveďte jednu z následujících akcí:

   - Vyberte sadu pravidel, kterou chcete upravit.

     \- nebo –

   - Zvolte  **\<Procházet... >** zadat sadu existujících pravidel, která se nenachází v seznamu.

4. Zvolte **otevřít** zobrazíte pravidla v editoru sad pravidel.

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Chcete-li upravit pravidlo nastavte v editoru sad pravidel

- Chcete-li změnit zobrazovaný název sady pravidel na **zobrazení** nabídce zvolte **okno vlastností**. Zadejte zobrazovaný název v **název** pole. Všimněte si, že zobrazované jméno se může lišit od názvu souboru.

- Chcete-li přidat do vlastní sady pravidel všechna pravidla skupiny, zaškrtněte políčko skupiny. Pokud chcete odebrat všechna pravidla skupiny, zrušte zaškrtnutí políčka.

- Chcete-li přidat konkrétní pravidlo do sady vlastních pravidel, zaškrtněte políčko pravidla. Chcete-li odebrat pravidlo ze sady pravidel, zrušte zaškrtnutí políčka.

- Chcete-li změnit akce provedená v případě porušení pravidla analýzy kódu, zvolte **akce** pole pro pravidlo a pak vyberte jednu z následujících hodnot:

     **Upozornit** – vygeneruje upozornění.

     **Chyba** – vygeneruje chybu.

     **Žádný** – zakáže pravidlo. Tato akce je stejná jako pravidla odebírání sady pravidel.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Do skupiny, filtrování nebo změně polí v editoru sad pravidel pomocí panelu nástrojů editoru sady pravidel

- Chcete-li rozbalit pravidla ve všech skupinách, zvolte **Rozbalit vše**.

- Chcete-li sbalit pravidla ve všech skupinách, zvolte **Sbalit vše**.

- Chcete-li změnit pole, pravidla se seskupují podle, zvolte na pole **Group** seznamu. Chcete-li zobrazit pravidla neseskupené, zvolte  **\<žádný >**.

- Chcete-li přidat nebo odebrat pole ve sloupcích pravidlo, zvolte **možnosti sloupce**.

- Chcete-li skrýt pravidla, která se nevztahují na aktuální řešení, zvolte **skrýt pravidla, která se nevztahují na aktuální řešení**.

- Chcete-li přepnout mezi zobrazení a skrytí pravidla, které jsou přiřazeny akce chyby, zvolte **zobrazit pravidla, která mohou generovat chyby analýzy kódu**.

- Chcete-li přepnout mezi zobrazení a skrytí pravidla, které jsou přiřazeny akce upozornění, zvolte **zobrazit pravidla, která mohou generovat upozornění analýzy kódu**.

- Pro přepínání zobrazení a skrytí pravidla, které jsou přiřazeny **žádný** akce, zvolte **zobrazit pravidla, která nejsou povolena**.

- Chcete-li přidat nebo odebrat Microsoft výchozí pravidlo se nastaví na aktuální sadu pravidel, zvolte **přidat nebo odebrat podřízené sady pravidel**.

## <a name="to-create-a-rule-set-in-a-text-editor"></a>Chcete-li vytvořit pravidlo nastavte v textovém editoru

Můžete vytvořit vlastní sady pravidel v textovém editoru, uložte ho do libovolného umístění s `.ruleset` rozšíření a vztahují se [/ analyze: ruleset](/cpp/build/reference/analyze-code-analysis) – možnost kompilátoru.

Následující příklad ukazuje, že soubor, který můžete použít jako výchozí bod nastavit základní pravidla:

```xml

<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```
