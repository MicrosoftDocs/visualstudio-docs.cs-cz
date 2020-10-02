---
title: Vytvoření vlastní sady pravidel pro analýzu kódu
ms.date: 11/02/2018
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d498ee0acfdc87f340a3c5c8848680eaed6276d
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658552"
---
# <a name="customize-a-rule-set"></a>Přizpůsobení sady pravidel

Můžete vytvořit vlastní sadu pravidel pro splnění konkrétních potřeb projektu pro analýzu kódu.

## <a name="create-a-custom-rule-set-from-an-existing-rule-set"></a>Vytvoření vlastní sady pravidel z existující sady pravidel

Pokud chcete vytvořit vlastní sadu pravidel, můžete v **editoru sad pravidel**otevřít integrovanou sadu pravidel. Odtud můžete přidat nebo odebrat specifická pravidla a akci, ke které dojde, když je pravidlo porušeno &mdash; , můžete například zobrazit upozornění nebo chybu.

1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a pak vyberte **vlastnosti**.

2. Na stránkách **vlastnosti** vyberte kartu **Analýza kódu** .

::: moniker range="vs-2017"

3. V rozevíracím seznamu **Spustit tuto sadu pravidel** proveďte jednu z následujících akcí:

::: moniker-end

::: moniker range=">=vs-2019"

3. V rozevíracím seznamu **aktivní pravidla** proveďte jednu z následujících akcí:

::: moniker-end

   - Vyberte sadu pravidel, kterou chcete upravit.

     \- ani

   - Tuto možnost vyberte **\<Browse>** , pokud chcete zadat existující sadu pravidel, která není v seznamu.

4. Vyberte **otevřít** a zobrazte pravidla v editoru sad pravidel.

> [!NOTE]
> Pokud máte projekt .NET Core nebo .NET Standard, proces je trochu odlišný, protože není k dispozici žádná karta vlastnost **Analýza kódu** . Použijte postup [Kopírování předdefinované sady pravidel do projektu a nastavte ji jako aktivní sadu pravidel](/dotnet/fundamentals/code-analysis/code-quality-rule-options). Po zkopírování sady pravidel [ji můžete upravit v editoru sad pravidel sady Visual Studio](working-in-the-code-analysis-rule-set-editor.md) otevřením z **Průzkumník řešení**.

## <a name="create-a-new-rule-set"></a>Vytvořit novou sadu pravidel

V dialogovém okně **nový soubor** můžete vytvořit nový soubor sady pravidel:

1. Vyberte **soubor**  >  **Nový**  >  **soubor**nebo stiskněte klávesu **CTRL** + **N**.

2. V dialogovém okně **nový soubor** vyberte na levé straně kategorii **Obecné** a pak vyberte **sadu pravidel nástroje Analýza kódu**.

3. Vyberte **Otevřít**.

   Nový soubor *. ruleset* se otevře v editoru sad pravidel.

## <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Vytvoření vlastní sady pravidel z více sad pravidel

> [!NOTE]
> Následující postup neplatí pro projekty .NET Core, které nemají kartu vlastnost **analýzy kódu** .

1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a pak vyberte **vlastnosti**.

2. Na stránkách **vlastnosti** vyberte kartu **Analýza kódu** .

::: moniker range="vs-2017"

3. Vyberte **\<Choose multiple rule sets>** možnost **Spustit tuto sadu pravidel**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Vyberte **\<Choose multiple rule sets>** z **aktivních pravidel**.

::: moniker-end

4. V dialogovém okně **Přidat nebo odebrat sady pravidel** vyberte sady pravidel, které chcete zahrnout do nové sady pravidel.

   ![Dialogové okno Přidat nebo odebrat sady pravidel](media/add-remove-rule-sets.png)

5. Vyberte **Uložit jako**, zadejte název souboru *. ruleset* a pak vyberte **Save (Uložit**).

   V seznamu **Spustit sadu pravidel** je vybraná nová sada pravidel.

6. Výběrem **otevřít** otevřete novou sadu pravidel v editoru sad pravidel.

## <a name="rule-precedence"></a>Priorita pravidla

- Pokud je stejné pravidlo uvedeno v sadě pravidel v jednom nebo více časech s různými závažnostmi, kompilátor vygeneruje chybu. Například:

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- Pokud je stejné pravidlo uvedeno v sadě *pravidel se stejnou závažností* dvakrát nebo vícekrát, může se v **Seznam chyb**zobrazit následující upozornění:

   **CA0063: nepovedlo se načíst soubor sady pravidel ' \[ Your]. ruleset ' nebo jeden z jeho závislých souborů sady pravidel. Soubor není v souladu se schématem sady pravidel.**

- Pokud sada pravidel obsahuje podřízenou sadu pravidel pomocí tagu **include** a podřízené a nadřazené pravidlo nastaví stejné pravidlo, ale s různou závažností, má přednost i závažnost v nadřazené sadě pravidel. Například:

   ```xml
   <!-- Parent rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Include Path="classlibrary_child.ruleset" Action="Default" />
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" /> <!-- Overrides CA1021 severity from child rule set -->
     </Rules>
   </RuleSet>

   <!-- Child rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules from child" Description="Code analysis rules from child." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

## <a name="name-and-description"></a>Název a popis

Chcete-li změnit zobrazovaný název sady pravidel otevřené v editoru, otevřete okno **vlastnosti** výběrem možnosti **Zobrazit**  >  **okno vlastností** na řádku nabídek. Do pole **název** zadejte zobrazovaný název. Můžete také zadat popis sady pravidel.

## <a name="next-steps"></a>Další kroky

Teď, když máte nastavené pravidlo, je dalším krokem přizpůsobení pravidel přidáním nebo odebráním pravidel nebo úpravou závažnosti porušení pravidel.

> [!div class="nextstepaction"]
> [Úprava pravidel v editoru sad pravidel](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Viz také

- [Postupy: Konfigurace Analýzy kódu pro spravovaný projekt kódu](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Referenční dokumentace sady pravidel nástroje Analýza kódu](../code-quality/rule-set-reference.md)
