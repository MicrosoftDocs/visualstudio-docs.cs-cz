---
title: Použití sad pravidel k určování pravidel C++ pro spuštění
ms.date: 04/28/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.native
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 8e25e28c2ff20a628058d5dfa71de0368fbe9249
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72445609"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Pomocí sad pravidel určete C++ pravidla, která se mají spustit.

V sadě Visual Studio můžete vytvořit a upravit vlastní *sadu pravidel* tak, aby splňovala konkrétní požadavky projektu spojené s analýzou kódu. Výchozí sady pravidel jsou uloženy v `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`.

**Visual Studio 2017 verze 15,7 a novější:** Vlastní sady pravidel můžete vytvořit pomocí libovolného textového editoru a použít je v sestavách příkazového řádku bez ohledu na to, jaký systém sestavení používáte. Další informace naleznete v tématu [/analyze: RuleSet](/cpp/build/reference/analyze-code-analysis).

Chcete-li vytvořit C++ vlastní sadu pravidel v sadě Visual Studio, musíC++ být v integrovaném vývojovém prostředí sady Visual Studio otevřený projekt C/Project. Pak otevřete standardní sadu pravidel v editoru sad pravidel a pak přidejte nebo odeberte specifická pravidla a volitelně změňte akci, ke které dojde, když analýza kódu zjistí, že pravidlo bylo porušeno.

Pokud chcete vytvořit novou vlastní sadu pravidel, uložte ji pomocí nového názvu souboru. Vlastní sada pravidel je automaticky přiřazena k projektu.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Vytvoření vlastního pravidla z jedné existující sady pravidel

1. V Průzkumník řešení otevřete místní nabídku pro projekt a poté zvolte možnost **vlastnosti**.

2. Na kartě **vlastnosti** klikněte na možnost **Analýza kódu**.

3. V rozevíracím seznamu **sada pravidel** proveďte jednu z následujících akcí:

   - Vyberte sadu pravidel, kterou chcete upravit.

     \- nebo –

   - Vyberte **\<Procházet... >** k určení existující sady pravidel, která není v seznamu.

4. Zvolením možnosti **otevřít** zobrazte pravidla v editoru sad pravidel.

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Úprava sady pravidel v editoru sad pravidel

- Chcete-li změnit zobrazovaný název sady pravidel, klikněte v nabídce **zobrazení** na příkaz **Vlastnosti okno**. Do pole **název** zadejte zobrazovaný název. Všimněte si, že zobrazovaný název se může lišit od názvu souboru.

- Pokud chcete přidat všechna pravidla skupiny do vlastní sady pravidel, zaškrtněte políčko u dané skupiny. Chcete-li odebrat všechna pravidla skupiny, zrušte zaškrtnutí políčka.

- Chcete-li přidat konkrétní pravidlo do sady vlastních pravidel, zaškrtněte políčko pravidla. Pokud chcete pravidlo ze sady pravidel odebrat, zrušte zaškrtnutí políčka.

- Chcete-li změnit akci povedenou při porušení pravidla při analýze kódu, zvolte pole **Akce** pro pravidlo a pak zvolte jednu z následujících hodnot:

     **Upozornění** – vygeneruje upozornění.

     **Chyba** – vygeneruje chybu.
     
     **Info** – vygeneruje zprávu.

     **None** – zakáže pravidlo. Tato akce je stejná jako odebrání pravidla ze sady pravidel.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Seskupení, filtrování nebo změna polí v editoru sad pravidel pomocí panelu nástrojů editoru sad pravidel

- Chcete-li rozšířit pravidla všech skupin, vyberte možnost **Rozbalit vše**.

- Pokud chcete pravidla sbalit ve všech skupinách, klikněte na **Sbalit vše**.

- Chcete-li změnit pole, podle kterého jsou pravidla seskupena, vyberte pole ze seznamu **Seskupit podle** . Pokud chcete zobrazit Neseskupená pravidla, vyberte **\<žádná >** .

- Chcete-li přidat nebo odebrat pole ve sloupcích pravidla, vyberte možnost **Možnosti sloupců**.

- Pokud chcete skrýt pravidla, která se nevztahují na aktuální řešení, vyberte **Skrýt pravidla, která se nevztahují na aktuální řešení**.

- Chcete-li přepínat mezi zobrazením a skrytím pravidel, kterým je přiřazena akce chyba, vyberte možnost **Zobrazit pravidla, která mohou generovat chyby analýzy kódu**.

- Chcete-li přepínat mezi zobrazením a skrytím pravidel, která jsou přiřazena k akci upozornění, vyberte možnost **Zobrazit pravidla, která mohou generovat upozornění analýzy kódu**.

- Chcete-li přepínat mezi zobrazením a skrytím pravidel, která jsou přiřazena k akci **none** , vyberte možnost **Zobrazit pravidla, která nejsou povolena**.

- Chcete-li přidat nebo odebrat výchozí sady pravidel Microsoft pro aktuální sadu pravidel, vyberte možnost **Přidat nebo odebrat podřízené sady pravidel**.

## <a name="to-create-a-rule-set-in-a-text-editor"></a>Vytvoření sady pravidel v textovém editoru

Můžete vytvořit vlastní sadu pravidel v textovém editoru, uložit ji do libovolného umístění s rozšířením `.ruleset` a použít v s možností kompilátoru [/analyze: RuleSet](/cpp/build/reference/analyze-code-analysis) .

Následující příklad ukazuje soubor základní sady pravidel, který můžete použít jako výchozí bod:

::: moniker range="vs-2017"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

::: moniker range=">=vs-2019"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end
