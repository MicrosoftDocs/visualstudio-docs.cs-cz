---
title: Definovat vlastní položku sady nástrojů pro modelování | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0a038150519ea7a40a52fb1be16ed93045c09eed
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851520"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>Definování vlastní položky sady nástrojů pro modelování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li usnadnit vytváření prvku nebo skupiny prvků podle vzoru, který často používáte, můžete přidat nové nástroje do sady nástrojů diagramů modelování v sadě Visual Studio. Tyto položky sady nástrojů lze distribuovat jiným uživatelům aplikace Visual Studio.

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Vlastní nástroj vytvoří jeden nebo více nových prvků v diagramu. Můžete například vytvořit vlastní nástroj pro vytváření prvků, jako jsou tyto:

- Balíček propojený s profilem .NET a třídu se stereotypem .NET.

- Dvojice tříd propojených přidružením, která představuje vzor pozorovatele.

> [!NOTE]
> Tuto metodu lze použít k vytvoření nástrojů prvku. To znamená, že můžete vytvořit nástroje, které přetáhnete ze sady nástrojů do diagramu. Nemůžete vytvořit nástroje konektoru.

## <a name="DefineTool"></a>Definování vlastního nástroje pro modelování

#### <a name="to-define-a-custom-modeling-tool"></a>Definování vlastního nástroje pro modelování

1. Vytvořte diagram UML, který obsahuje prvek nebo skupinu prvků.

    - Tyto prvky můžou mít vzájemné vztahy mezi nimi a můžou mít dceřiné prvky, jako jsou porty, atributy, operace nebo PIN kódy.

2. Uložte diagram pomocí názvu, který chcete novému nástroji poskytnout. V nabídce **soubor** použijte příkaz **Uložit... Jako**.

3. Pomocí Průzkumníka Windows zkopírujte dva soubory diagramu do následující složky nebo libovolné podsložky:

     **Položky sady nástrojů YourDocuments \Visual Studio\Architecture Tools\Custom**

    - Tuto složku vytvořte, pokud ještě neexistuje. Možná budete muset vytvořit oba **nástroje architektury** i **vlastní prvky panelu nástrojů**.

    - Zkopírujte oba soubory diagramu, jeden s názvem, který končí na... **diagram**a druhý s názvem, který končí... **diagram. Layout**"

    - Můžete vytvořit tolik vlastních nástrojů, kolik chcete. Pro jednotlivé nástroje použijte jeden diagram.

4. Volitelné Vytvořte soubor **. tbxinfo** , jak je popsáno v tématu [jak definovat vlastnosti vlastních nástrojů](#tbxinfo)a přidat ho do stejného adresáře. To vám umožní definovat ikonu panelu nástrojů, popis a tak dále.

    - Jeden soubor **. tbxinfo** lze použít k definování několika nástrojů. Může odkazovat na soubory diagramu, které jsou v podsložkách.

5. Restartujte sadu Visual Studio. Další nástroj se zobrazí v sadě nástrojů pro příslušný typ diagramu.

### <a name="what-the-custom-tool-will-replicate"></a>Jak bude vlastní nástroj replikován
 Vlastní nástroj bude replikovat většinu funkcí zdrojového diagramu:

- Názvy. Při vytvoření položky z panelu nástrojů je číslo přidáno na konec názvu, pokud je to nutné, aby se zabránilo duplicitním názvům ve stejném oboru názvů.

- Barvy, velikosti a tvary

- Stereotypy a profily balíčků

- Hodnoty vlastností, jako je abstraktní

- Propojené pracovní položky

- Násobnosti a další vlastnosti vztahů

- Relativní pozice tvarů.

  Následující funkce se nezachovají ve vlastním nástroji:

- Jednoduché tvary. Jedná se o tvary, které nesouvisí s prvky modelu, které lze nakreslit na některé druhy diagramů.

- Směrování konektoru. Pokud konektory směrujete ručně, směrování se nezachová při použití nástroje. Pozice některých vnořených tvarů, jako jsou porty, nejsou zachovány relativně ke svým vlastníkům.

## <a name="tbxinfo"></a>Jak definovat vlastnosti vlastních nástrojů
 Soubor s informacemi o sadě nástrojů ( **. tbxinfo**) umožňuje zadat název panelu nástrojů, ikonu, popis, kartu a nápovědu pro jeden nebo více vlastních nástrojů. Dejte mu libovolný název, třeba **Moje nástroje. tbxinfo**.

 Obecná forma souboru je následující:

```
<?xml version="1.0" encoding="utf-8" ?>
<customToolboxItems xmlns="http://schemas.microsoft.com/visualstudio/[version]/ArchitectureTools/CustomToolboxItems">
  <customToolboxItem fileName="MyObserverTool.classdiagram">
    <displayName>
       <value>Observer Pattern</value>
    </displayName>
    <tabName>
       <value>UML Class Diagram</value>
    </tabName>
    <image><bmp fileName="ObserverPatternIcon.bmp"/></image>
    <f1Keyword>
      <value>ObserverPatternHelp</value>
    </f1Keyword>
    <tooltip>
       <value>Create a pair of classes</value>
    </tooltip>
  </customToolboxItem>
</customToolboxItems>
```

 Hodnota každé položky může být jedna z těchto hodnot:

- Jak je znázorněno v příkladu, `<bmp fileName="…"/>` pro ikonu panelu nástrojů a `<value>string</value>` pro ostatní položky.

  \- nebo –

- `<resource fileName="Resources.dll"`

   `baseName="Observer.resources" id="Observer.tabname" />`

   V tomto případě zadáte zkompilované sestavení, ve kterém byly řetězcové hodnoty kompilovány jako prostředky.

  Přidejte `<customToolboxItem>` uzel pro každou položku sady nástrojů, kterou chcete definovat.

  Uzly v souboru **. tbxinfo** jsou následující. Pro každý uzel existuje výchozí hodnota.

|Název uzlu|Definuje|
|---------------|-------------|
|displayName|Název položky sady nástrojů|
|tabName|Karta panelu nástrojů, na které se má položka zobrazit Pro tento typ diagramu můžete zadat buď název regulární karty, nebo samostatný název.|
|obrázek|Umístění souboru rastrového obrázku ( **. bmp**), který musí mít výšku a šířku 16 a barevnou hloubku 24 bitů.|
|f1Keyword|Klíčové slovo, které vyhledává téma nápovědy.|
|okna|Popis tlačítka pro tento nástroj|

 Můžete upravit rastrový soubor v sadě Visual Studio a nastavit jeho výšku a šířku na 16 v okno Vlastnosti.

> [!NOTE]
> Pokud začnete používat soubor. tbxinfo po experimentování s použitím souborů diagramu sami, můžete zjistit, že sada nástrojů obsahuje jak starou, tak i nové verze položky sady nástrojů. K tomu může dojít také v případě, že název souboru diagramu byl v souboru. tbxinfo chybně natypový. Pokud k tomu dojde, v místní nabídce panelu nástrojů vyberte **obnovit sadu nástrojů**. Vlastní položky panelu nástrojů zmizí. Restartujte Visual Studio a zobrazí se správné vlastní položky.

## <a name="Extension"></a>Postup distribuce položek panelu nástrojů v rozšíření sady Visual Studio
 Položky panelu nástrojů lze distribuovat jiným [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uživatelům jejich zabalením do rozšíření sady Visual Studio (VSIX). Příkazy, profily a další rozšíření můžete zabalit do stejného souboru VSIX. Další informace najdete v tématu [nasazení rozšíření sady Visual Studio](https://msdn.microsoft.com/library/dd393694(VS.100).aspx).

 Běžný způsob, jak sestavit rozšíření sady Visual Studio, je použít šablonu projektu VSIX. K tomu je potřeba mít nainstalovanou [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].

#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>Přidání položky sady nástrojů do rozšíření aplikace Visual Studio

1. [Vytvoření a otestování jednoho nebo více vlastních nástrojů](#DefineTool).

2. [Vytvořte soubor. tbxinfo](#tbxinfo) , který odkazuje na nástroje.

3. Otevřete existující projekt rozšíření aplikace Visual Studio.

     \- nebo –

     Definujte nový projekt rozšíření sady Visual Studio.

    1. V nabídce **soubor** klikněte na příkaz **Nový**, **projekt**.

    2. V dialogovém okně **Nový projekt** v části **Nainstalované šablony**vyberte možnost **Visual C#** , **rozšiřitelnost**, **projekt VSIX**.

4. Přidejte do projektu definice sady nástrojů. Zahrňte soubor **. tbxinfo** , soubory diagramu, rastrové soubory a všechny soubory prostředků a ujistěte se, že jsou zahrnuty do VSIX.

    - V Průzkumník řešení v místní nabídce projektu VSIX vyberte možnost **Přidat**, **existující položka**. V dialogovém okně nastavte **objekty typu: všechny soubory**. Vyhledejte soubory, vyberte je vše a pak zvolte **Přidat**.

        > [!NOTE]
        > V tomto projektu nelze otevřít soubory diagramu v editoru modelů.

5. Nastavte následující vlastnosti všech souborů, které jste právě přidali. Můžete nastavit jejich vlastnosti současně tak, že je vyberete vše v Průzkumník řešení. Dejte pozor, abyste neměnili vlastnosti ostatních souborů v projektu.

     **Kopírovat do výstupního adresáře** = **Kopírovat vždycky**

     **Akce sestavení** = **Obsah**

     **Zahrnout do VSIX** = **true**

6. Otevřete **source. extension. vsixmanifest**. Otevře se v editoru manifestu rozšíření.

7. V části **metadata**přidejte popis vlastních nástrojů.

     V části **assety**zvolte **nové** a pak nastavte pole v dialogovém okně následujícím způsobem:

    - **Typ** = **vlastní typ rozšíření**

    - Type = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`

        > [!NOTE]
        > Nejedná se o jednu z možností v rozevíracím seznamu. Je nutné zadat ho pomocí klávesnice.

    - **Zdrojový** = **soubor v systému souborů**.

    - **Cesta** = váš soubor **. tbxinfo** , například **Moje nástroje. tbxinfo**

8. Sestavte projekt.

9. **Chcete-li ověřit, zda rozšíření funguje**, stiskněte klávesu F5. Spustí se experimentální instance sady Visual Studio.

     V experimentální instanci vytvořte nebo otevřete diagram UML příslušného typu. Ověřte, zda se nový nástroj zobrazuje v sadě nástrojů a zda správně vytvoří prvky.

10. **Získání souboru VSIX pro nasazení:** V Průzkumníku Windows otevřete složku **.\bin\debug** nebo **.\bin\Release** a vyhledejte soubor **. vsix** . Toto je soubor rozšíření [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Může být nainstalováno do vašeho počítače a také odesílán ostatním uživatelům aplikace Visual Studio.

#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>Instalace vlastních nástrojů z rozšíření sady Visual Studio

1. Otevřete soubor `.vsix` v Průzkumníkovi Windows nebo v aplikaci Visual Studio.

2. V dialogovém okně, které se zobrazí, vyberte **nainstalovat** .

3. Chcete-li odinstalovat nebo dočasně zakázat rozšíření, otevřete **rozšíření a aktualizace** z nabídky **nástroje** .

## <a name="localization"></a>Lokalizace
 Můžete vytvořit rozšíření, které při instalaci na jiný počítač zobrazí názvy nástrojů a popisy tlačítek v jazyce cílového počítače.

#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>Poskytnutí verze nástroje ve více než jednom jazyce

1. Vytvořte projekt rozšíření aplikace Visual Studio, který obsahuje jeden nebo více vlastních nástrojů.

    V souboru **. tbxinfo** použijte metodu souboru prostředků k definování `displayName`nástroje, panelu nástrojů `tabName`a popisu tlačítka. Vytvořte soubor prostředků, ve kterém jsou tyto řetězce definovány, zkompilujte je do sestavení a odkazujte na ni ze souboru tbxinfo.

2. Vytvořte další sestavení, která obsahují soubory prostředků s řetězci v jiných jazycích.

3. Každé další sestavení umístěte do složky, jejíž název je kód jazykové verze pro jazyk. Například vložte francouzskou verzi sestavení do složky s názvem **fr**.

4. Měli byste použít neutrální kód kultury, obvykle dvě písmena, nikoli konkrétní jazykovou verzi, například `fr-CA`. Další informace o kódech kultury naleznete v tématu [CultureInfo. GetCultures](https://msdn.microsoft.com/library/system.globalization.cultureinfo.getcultures(VS.100).aspx), který poskytuje úplný seznam kódů jazykové verze.

5. Sestavte rozšíření sady Visual Studio a distribuujte ho.

6. Pokud je rozšíření nainstalováno v jiném počítači, bude automaticky načtena verze souboru prostředků pro místní jazykovou verzi uživatele. Pokud jste pro jazykovou verzi uživatele nezadali verzi, budou použity výchozí prostředky.

   Tuto metodu nelze použít k instalaci různých verzí diagramu prototypu. Názvy prvků a konektorů budou v každé instalaci stejné.

## <a name="other-toolbox-operations"></a>Jiné operace sady nástrojů
 V [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]je obvykle možné sadu nástrojů přizpůsobit přejmenováním nástrojů, jejich přesunutím na různé karty sady nástrojů a jejich odstraněním. Tyto změny se ale neuchovávají pro vlastní nástroje pro modelování vytvořené pomocí postupů popsaných v tomto tématu. Po restartování [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]se vlastní nástroje znovu zobrazí se svými definovanými názvy a umístěními sady nástrojů.

 I když provedete příkaz **obnovit sadu nástrojů** , vaše vlastní nástroje zmizí. Budou se ale po restartování [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]znovu zobrazovat.

## <a name="see-also"></a>Viz také
 [Rozšiřování modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md) [Definování profilu pro rozšiřování UML](../modeling/define-a-profile-to-extend-uml.md) [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Definování omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md)
