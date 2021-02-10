---
title: 'Postupy: Vytváření řešení jazyka specifického pro doménu'
description: Naučte se vytvořit jazyk specifický pro doménu (DSL) pomocí specializovaného řešení sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5d04366c908494386edc9921129db27df0ead4f7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941408"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Postupy: Vytváření řešení jazyka specifického pro doménu
Jazyk specifický pro doménu (DSL) se vytvoří pomocí specializovaného řešení sady Visual Studio.

## <a name="prerequisites"></a>Požadavky

Než budete moct tento postup spustit, nainstalujte tyto komponenty:

- Visual Studio
- Sada Visual Studio SDK (nainstalovaná jako součást úlohy **vývoje rozšíření pro Visual Studio** )
- Sada SDK pro modelování (instalována jako součást sady Visual Studio)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="creating-a-domain-specific-language-solution"></a>Vytvoření řešení Domain-Specific jazyka

1. Spusťte Průvodce DSL vytvořením nového projektu **Návrháře jazyka specifického pro doménu** .

   > [!NOTE]
   > Název, který si zvolíte pro projekt, by měl být platný identifikátor jazyka Visual C#, protože může být použit pro generování kódu.

   ::: moniker range="vs-2017"

   ![Dialog vytvořit DSL](../modeling/media/create_dsldialog.png)

   ::: moniker-end

2. Vyberte šablonu DSL.

    Na stránce **Vybrat možnosti jazyka Domain-Specific** vyberte jednu z šablon řešení, jako je například **Minimální jazyk**. Vyberte šablonu, která je podobná DSL, kterou chcete vytvořit.

    Další informace o šablonách řešení naleznete v tématu [Volba šablony řešení Domain-Specific jazyka](../modeling/choosing-a-domain-specific-language-solution-template.md).

3. Na stránce **Přípona souboru** zadejte příponu filename. Měl by být jedinečný v počítači a na všech počítačích, na které chcete nainstalovat DSL. Měla by se zobrazit zpráva **žádné aplikace ani editory sady Visual Studio nepoužívají toto rozšíření**.

   - Pokud jste v předchozích experimentálních DSL použili příponu názvu souboru, která nebyla plně nainstalovaná, můžete je vymazat pomocí nástroje pro **obnovení experimentální instance** , který lze najít v nabídce sady Visual Studio SDK.

   - Pokud je v počítači plně nainstalovaná jiná přípona sady Visual Studio, která tuto příponu souboru používá, zvažte její odinstalaci. V nabídce **nástroje** klikněte na **Správce rozšíření**.

4. Zkontrolujte a v případě potřeby upravte pole na zbývajících stránkách průvodce. Až budete s nastavením spokojeni, klikněte na **Dokončit**. Další informace o nastaveních najdete na [stránce průvodce návrháře DSL](#settings).

    Průvodce vytvoří řešení, které má dva projekty s názvem **DSL** a **DslPackage**.

   > [!NOTE]
   > Pokud se zobrazí zpráva upozorňující, že nespouštíte textové šablony z nedůvěryhodných zdrojů, klikněte na tlačítko **OK**. Tuto zprávu můžete nastavit tak, aby se nezobrazovala znovu.

## <a name="the-dsl-designer-wizard-pages"></a><a name="settings"></a> Stránky průvodce návrháře DSL
 Z jejich výchozích hodnot můžete nechat některá z těchto polí beze změny. Ujistěte se však, že jste nastavili pole Přípona souboru.

### <a name="solution-settings-page"></a>Stránka nastavení řešení
 **Jakou šablonu chcete pro konkrétní jazyk domény založit?**
Vyberte šablonu, která je podobná DSL, kterou chcete vytvořit. Různé šablony poskytují pohodlný počáteční bod. Když vyberete šablonu řešení, Průvodce zobrazí popis. Další informace o šablonách řešení naleznete v tématu [Volba šablony řešení Domain-Specific jazyka](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **Jak chcete pojmenovat jazyk specifický pro doménu?**
Ve výchozím nastavení se jedná o název řešení. Z této hodnoty je vygenerován kód. Musí být platný jako název třídy jazyka C#.

### <a name="file-extension-page"></a>Stránka s příponou souboru
 **Jakou příponu mají soubory modelu používat?**
Zadejte novou příponu souboru.

 Ověřte, že tato přípona souboru ještě není zaregistrovaná pro použití v tomto počítači, a to následujícím způsobem:

 Podívejte **se na jiné nástroje a aplikace zaregistrované pro zpracování tohoto rozšíření**. Pokud se zobrazí zpráva **žádné aplikace nebo editory sady Visual Studio nepoužívají toto rozšíření**, můžete použít tuto příponu souboru.

 Pokud se zobrazí seznam nástrojů nebo balíčků, měli byste provést jednu z následujících akcí:

- Zadejte jinou příponu souboru.

     \- ani

- Resetovat experimentální instanci sady Visual Studio. Tím zrušíte registraci všech dříve vytvořených DSL. V nabídce **Start** klikněte na **všechny programy**, **Microsoft Visual Studio 2010 SDK**, **nástroje** a pak **na experimentální instanci Microsoft Visual Studio 2010 obnovte**. Můžete znovu sestavit jakýkoli jiný DSL, který chcete znovu použít.

     \- ani

- Pokud je rozšíření sady Visual Studio, které používá tuto příponu souboru, v počítači plně nainstalováno, odinstalujte ho. V nabídce **nástroje** klikněte na **Správce rozšíření**.

### <a name="product-settings-page"></a>Stránka nastavení produktu
 **Jaký je název produktu, ke kterému patří nový jazyk specifický pro doménu?**
Použije se výchozí název DSL.

 Tato hodnota se používá v Průzkumníkovi Windows (nebo v Průzkumníku souborů) k popisu souborů, které mají tuto příponu souboru.

 **Jaký je název společnosti, do které produkt patří?**
Název vaší společnosti.

 Tato hodnota se začlení do vlastností AssemblyInfo vašeho balíčku DSL.

 **Jaký je kořenový obor názvů pro projekty v tomto řešení?**
Tento název se použije jako název složený z názvu vaší společnosti a produktu.

### <a name="signing-page"></a>stránka Podepisování
 **Vytvořit soubor klíče se silným názvem** Výchozí možnost je vytvořit nový klíč pro podepsání vašeho sestavení DSL.

 **Použít existující klíč se silným názvem** Tuto možnost použijte, pokud chcete své DSL integrovat s jiným sestavením.

 Další informace o silných názvech naleznete v tématu [vytváření a používání Strong-Namedch sestavení](/dotnet/standard/assembly/create-use-strong-named).

## <a name="see-also"></a>Viz také

- [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)
- [Glosář Nástroje DSL](/previous-versions/bb126564(v=vs.100))