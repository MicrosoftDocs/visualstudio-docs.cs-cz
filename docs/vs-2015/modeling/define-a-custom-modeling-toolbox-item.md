---
title: Definování vlastní položky sady nástrojů pro modelování | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dcb562eb76e13b5dcb16532ed808b2447de0d6c8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778407"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>Definování vlastní položky sady nástrojů pro modelování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K usnadnění vytváření elementu nebo skupiny prvků podle vzoru, který často používáte, můžete přidat nové nástroje do panelu nástrojů modelování diagramů v sadě Visual Studio. Tyto položky panelu nástrojů ostatním uživatelům aplikace Visual Studio můžete distribuovat.  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Vlastní nástroj vytvoří jednu nebo více nových prvků v diagramu. Například může vytvořit vlastní nástroj k vytváření prvků, jako jsou tyto:  
  
-   Balíček spojené s profil .NET a třída s atributem stereotyp ".NET".  
  
-   Dvojice propojené přidružení k reprezentaci vzor pozorovatel třídy.  
  
> [!NOTE]
>  Tato metoda slouží k vytvoření nástroje pro element. To znamená můžete vytvořit nástroje, které můžete přetáhnout z panelu nástrojů do diagramu. Nelze vytvořit konektor nástroje.  
  
##  <a name="DefineTool"></a> Definování vlastního nástroje modelování  
  
#### <a name="to-define-a-custom-modeling-tool"></a>Chcete-li definovat vlastní modelování nástroj  
  
1.  Vytvoření diagramu UML, který obsahuje prvek nebo skupiny prvků.  
  
    -   Tyto prvky mohou mít vztahy mezi nimi a může mít pomocné prvky, jako jsou porty, atributy, operace nebo kódy PIN.  
  
2.  Diagram pomocí názvu, který chcete přiřadit nový nástroj uložte. Na **souboru** nabídky, použijte **uložit... Jako**.  
  
3.  Pomocí Průzkumníka Windows, zkopírujte soubory dvě diagramu do následující složky nebo jakoukoli podsložku:  
  
     *YourDocuments* **položky panelu nástrojů Tools\Custom \Visual Studio\Architecture**  
  
    -   Pokud ještě neexistuje, vytvořte tuto složku. Možná budete muset vytvořit i **nástroje pro architekturu** a **vlastní položky sady nástrojů**.  
  
    -   Zkopírujte oba soubory diagramu, jeden s názvem, který končí "... **diagram**"a druhý s názvem, který končí"... **diagram.layout**"  
  
    -   Můžete vytvořit libovolný počet vlastních nástrojů, jak potřebujete. Použijte pouze jeden diagram pro jednotlivé nástroje.  
  
4.  (Volitelné) Vytvoření **.tbxinfo** sdílené, jak je popsáno v [jak definovat vlastnosti vlastního nástroje](#tbxinfo)a přidejte ho do stejného adresáře. To umožňuje definovat panelu nástrojů ikonu, popisek a tak dále.  
  
    -   Jediný **.tbxinfo** soubor lze použít k definování několika nástrojů. Může odkazovat na diagramu soubory, které jsou v podsložkách.  
  
5.  Restartujte sadu Visual Studio. Další nástroje se zobrazí na panelu nástrojů pro příslušný typ diagramu.  
  
### <a name="what-the-custom-tool-will-replicate"></a>Co bude replikovat Custom Tool  
 Vlastní nástroj bude replikovat většinu funkcí zdrojového diagramu:  
  
- Názvy. Když je vytvořena položka ze sady nástrojů, číslo se přidá na konec názvu v případě potřeby, aby se zabránilo duplicitní názvy ve stejném oboru názvů.  
  
- Barvy, velikost a tvary  
  
- Balíček profilů a stereotypů  
  
- Hodnoty vlastností, jako je například je abstraktní  
  
- Propojené pracovní položky  
  
- Násobnosti a další vlastnosti relace  
  
- Relativní umístění obrazce.  
  
  Tyto funkce se nezachová v vlastního nástroje:  
  
- Jednoduché obrazce. Toto jsou tvary, které nesouvisí s prvky modelu, že lze nakreslit na některé druhy diagramů.  
  
- Konektor směrování. Pokud ručně směrování konektory směrování se nezachová při nástroj se používá. Pozice některé vnořeným obrazcům, jako je například porty, nejsou zachovány vzhledem k jejich vlastníky.  
  
##  <a name="tbxinfo"></a> Definování vlastnosti vlastního nástroje  
 Informace o panelu nástrojů (**.tbxinfo**) soubor umožňuje zadat název panelu nástrojů, ikonu, popisek, karty a klíčové slovo pro jeden nebo více vlastních nástrojů nápovědy. Přiřadit libovolný název, jako například **MyTools.tbxinfo**.  
  
 Obecný tvar souboru je následující:  
  
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
  
 Hodnota položky může být buď:  
  
- Jak je znázorněno v příkladu `<bmp fileName="…"/>` ikony sady nástrojů a `<value>string</value>` u jiných položek.  
  
  \- nebo –  
  
- `<resource fileName="Resources.dll"`  
  
   `baseName="Observer.resources" id="Observer.tabname" />`  
  
   V takovém případě zadáte zkompilovaném sestavení, ve kterém byl zkompilován řetězcové hodnoty jako prostředky.  
  
  Přidat `<customToolboxItem>` uzel pro každou položku sady nástrojů, které chcete definovat.  
  
  Uzly v **.tbxinfo** souboru jsou následující. Neexistuje výchozí hodnota pro každý uzel.  
  
|Název uzlu|definuje|  
|---------------|-------------|  
|displayName|Název položky panelu nástrojů.|  
|tabName|Na kartě panelu nástrojů, ve kterém se má položka zobrazit. Můžete zadat název standardní kartě pro tento typ schématu, nebo odlišný název.|  
|obrázek|Umístění rastrový obrázek (**.bmp**) soubor, který musí mít výšku a šířku 16 a barevnou hloubku 24 bitů.|  
|f1Keyword|Klíčové slovo, která vyhledává téma nápovědy.|  
|Popis tlačítka|Popis pro tento nástroj.|  
  
 Můžete upravit soubor rastrového obrázku v sadě Visual Studio a nastavit jeho výšku a šířku na 16 v okně Vlastnosti.  
  
> [!NOTE]
>  Pokud začnete používat soubor .tbxinfo po pomocí diagramu soubory sami, můžete zjistit, že sada nástrojů obsahuje původní a nové verze položku sady nástrojů. To může také dojít, pokud název souboru diagramu bylo zadáno chybně v souboru .tbxinfo. Pokud k tomu dojde, v místní nabídce na panelu nástrojů zvolte **resetování nástrojů**. Položky vlastního panelu nástrojů zmizí. Restartujte Visual Studio a správné vlastní položky se zobrazí.  
  
##  <a name="Extension"></a> Jak se bude distribuovat položky panelu nástrojů v rozšíření sady Visual Studio  
 Můžete distribuovat položky panelu nástrojů na jiné [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uživatelů podle jejich balení do rozšíření aplikace Visual Studio (VSIX). Příkazy, profily a další rozšíření můžete zabalit do stejného souboru VSIX. Další informace najdete v tématu [nasazení rozšíření sady Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160780).  
  
 Obvyklým způsobem k sestavení rozšíření sady Visual Studio je použití šablony projektu VSIX. Chcete-li to provést, musíte mít nainstalovaný [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>Chcete-li přidat položku sady nástrojů do rozšíření aplikace Visual Studio  
  
1.  [Vytvoření a otestování jeden nebo více vlastních nástrojů](#DefineTool).  
  
2.  [Vytvořte soubor .tbxinfo](#tbxinfo) , která odkazuje na nástroje.  
  
3.  Otevřete existující projekt rozšíření Visual Studio.  
  
     \- nebo –  
  
     Definujte nový projekt rozšíření Visual Studio.  
  
    1.  Na **souboru** nabídce zvolte **nový**, **projektu**.  
  
    2.  V **nový projekt** dialogovém okně **nainstalované šablony**, zvolte **Visual C#**, **rozšiřitelnost**, **VSIX projekt**.  
  
4.  Vaše definice panelu nástrojů přidejte do projektu. Zahrnout **.tbxinfo** souborů, souborů diagramu, rastrové soubory a soubory prostředků a ujistěte se, že jsou obsažené ve VSIX.  
  
    -   V Průzkumníku řešení v místní nabídce projektu VSIX zvolte **přidat**, **existující položku**. V dialogovém okně nastavte **objekty typu: všechny soubory**. Vyhledejte soubory, vyberte je všechny a zvolte **přidat**.  
  
        > [!NOTE]
        >  V tomto projektu nemůže otevřít soubory diagramu v editoru modelů.  
  
5.  Nastavte následující vlastnosti všech souborů, které jste právě přidali. Můžete nastavit jejich vlastnosti ve stejnou dobu tak, že je vyberete v Průzkumníku řešení. Dejte pozor, abyste změnit vlastnosti další soubory v projektu.  
  
     **Kopírovat do výstupního adresáře** = **vždy kopírovat**  
  
     **Akce sestavení** = **obsahu**  
  
     **Zahrnout do VSIX** = **true**  
  
6.  Otevřít **source.extension.vsixmanifest**. Otevře se v editoru manifestu rozšíření.  
  
7.  V části **metadat**, zadejte popis vlastního nástroje.  
  
     V části **prostředky**, zvolte **nový** a pak nastavte pole v dialogovém okně následujícím způsobem:  
  
    -   **Typ** = **typ vlastního rozšíření**  
  
    -   Typ = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`  
  
        > [!NOTE]
        >  To však není jednou z možností v rozevíracím seznamu. Je nutné zadat pomocí klávesnice.  
  
    -   **Zdroj** = **soubor v systému souborů**.  
  
    -   **Cesta** = vaše **.tbxinfo** souboru, například **MyTools.tbxinfo**  
  
8.  Sestavte projekt.  
  
9. **Chcete-li ověřit, že toto rozšíření funguje**, stiskněte klávesu F5. Spustí se experimentální instanci sady Visual Studio.  
  
     V experimentální instanci aplikace vytvořte nebo otevřete diagram UML odpovídající typu. Ověřte, že se zobrazí nový nástroj v soupravě nástrojů, a to, že vytvoří prvky správně.  
  
10. **Chcete získat soubor VSIX pro nasazení:** v Průzkumníku Windows otevřete složku **.\bin\Debug** nebo **.\bin\Release** najít **VSIX** souboru. Jedná se [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] souboru rozšíření. Může být nainstalován v počítači a také odeslán ostatním uživatelům aplikace Visual Studio.  
  
#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>Instalace vlastních nástrojů z rozšíření sady Visual Studio  
  
1.  Otevřít `.vsix` souboru v Průzkumníku Windows nebo v sadě Visual Studio.  
  
2.  Zvolte **nainstalovat** v dialogovém okně, které se zobrazí.  
  
3.  Chcete-li odinstalovat nebo dočasně zakázat rozšíření, otevřete **rozšíření a aktualizace** z **nástroje** nabídky.  
  
## <a name="localization"></a>Lokalizace  
 Můžete vytvořit rozšíření, která, pokud je nainstalovaný na jiném počítači, zobrazí nástroj názvy a popisy tlačítek v jazyce, který cílový počítač.  
  
#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>K poskytování verze nástroje ve více než jednom jazyku  
  
1. Vytvořte projekt rozšíření aplikace Visual Studio, který obsahuje jeden nebo více vlastních nástrojů.  
  
    V **.tbxinfo** souboru, použijte metodu soubor prostředků pro definování nástroje `displayName`, nástrojů `tabName`a popisek. Vytvořit soubor prostředků, ve kterém jsou definovány tyto řetězce a zkompilovat do sestavení na ni odkazovat ze souboru tbxinfo.  
  
2. Vytvořte další sestavení, které obsahují soubory prostředků s řetězci v jiných jazycích.  
  
3. Každý další sestavení umístěte do složky, jehož název je jazykovou verzi kódu pro jazyk. Francouzské verze sestavení, například umístíte text do složky s názvem **fr**.  
  
4. Používejte neutrální jazykovou verzi kódu, obvykle dvě písmena, nikoli konkrétní jazykovou verzi jako `fr-CA`. Další informace o kódech jazykových najdete v tématu [CultureInfo.GetCultures metody](http://go.microsoft.com/fwlink/?LinkId=160782), která poskytuje úplný seznam kódů jazykových verzí.  
  
5. Rozšíření sady Visual Studio můžete vytvářet a distribuovat ji.  
  
6. Při rozšíření je nainstalované v jiném počítači, verzi souboru prostředků na místních jazykovou verzi uživatele se automaticky načtou. Pokud jste nezadali verze pro jazykovou verzi uživatele, použije se výchozí prostředky.  
  
   Tuto metodu nelze použít pro instalaci různých verzích diagram prototypu. Názvy elementů a konektory budou stejné v každé instalaci.  
  
## <a name="other-toolbox-operations"></a>Další sady nástrojů operace  
 Obvykle v [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], můžete si přizpůsobit panel nástrojů přejmenování nástroje, jejich přesunutí na různé sady nástrojů karty a jejich odstranění. Ale tyto změny se neuloží pro nástroje pro modelování vlastní vytvořené pomocí postupů popsaných v tomto tématu. Po restartování [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], vlastních nástrojů se znovu zobrazí jejich definované názvy a umístění panelu nástrojů.  
  
 Kromě toho vlastních nástrojů zmizí, pokud provádíte **resetování nástrojů** příkazu. Však bude znovu po restartování [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Definování profilu pro rozšíření UML](../modeling/define-a-profile-to-extend-uml.md)   
 [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definování omezení ověřování pro modely UML](../modeling/define-validation-constraints-for-uml-models.md)



