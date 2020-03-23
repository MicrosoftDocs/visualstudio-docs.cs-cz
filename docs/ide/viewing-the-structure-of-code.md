---
title: Zobrazení třídy, hierarchie volání, prohlížeč objektů, okno definice kódu
ms.date: 09/19/2019
ms.topic: reference
f1_keywords:
- vs.documentoutline.window
- vs.objectbrowser
- vs.classview
- VS.CodeDefinitionView
- VS.CodeDefinitionWindow
- vs.componentpicker
- vs.callbrowser
helpviewer_keywords:
- document outline window
- Visual Studio, object browser
- call hierarchy
- Visual Studio, document outline window
- code definition window [Visual Studio]
- Visual Studio, class view
- Visual Studio, call hierarchy window
- class view
- object browser
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b73a4660c9e0dad66ceb73c04852601765174264
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303055"
---
# <a name="view-the-structure-of-code-using-different-tool-windows"></a>Zobrazení struktury kódu pomocí různých oken nástrojů

Třídy a jejich členy můžete prozkoumat v sadě Visual Studio pomocí různých oken nástrojů, včetně **zobrazení tříd ,** **hierarchie volání**, prohlížeče **objektů**a **definice kódu** (pouze c++). Tato okna nástrojů mohou zkoumat kód v projektech sady Visual Studio, součástech .NET, součástech modelu COM, knihovnách dynamických spojů (DLL) a knihovnách typů (TLB).

**Pomocí Průzkumníka řešení** můžete také procházet typy a členy v projektech, vyhledávat symboly, zobrazit hierarchii volání metody, vyhledávat odkazy na symboly a další, aniž byste museli přepínat mezi více okny nástrojů.

Pokud máte Visual Studio Enterprise edition, můžete použít *mapy kódu* k vizualizaci struktury kódu a jeho závislostí v celém řešení. Další informace naleznete v tématu [Mapování závislostí s mapami kódu](../modeling/map-dependencies-across-your-solutions.md).

## <a name="class-view-visual-basic-c-c"></a>Zobrazení třídy (Visual Basic, C#, C++)

**Zobrazení tříd** je zobrazeno jako součást **Průzkumníka řešení** a jako samostatné okno. **Zobrazení tříd** zobrazuje prvky aplikace. V horním podokně se zobrazí obory názvů, typy, rozhraní, výčty a třídy a v dolním podokně se zobrazí členové, kteří patří k typu vybranému v horním podokně. Pomocí tohoto okna můžete přesunout do definice členů ve zdrojovém kódu (nebo v **prohlížeči objektů,** pokud je prvek definován mimo vaše řešení).

Není třeba zkompilovat projekt pro zobrazení jeho prvků v **zobrazení třídy**. Okno se aktualizuje při úpravě kódu v projektu.

Kód můžete do projektu přidat tak, že vyberete uzel projektu a kliknutím na tlačítko **Přidat** otevřete dialogové okno **Přidat novou položku.** Kód je přidán do samostatného souboru.

Pokud je projekt se změnami do správy zdrojového kódu, každý prvek **zobrazení tříd** zobrazí ikonu, která označuje stav zdrojového kódu souboru. V místní nabídce prvku jsou k dispozici také běžné příkazy pro správu zdrojového kódu, například **Rezervovat**, **Vrátit se změnami**a získat nejnovější **verzi.**

### <a name="class-view-toolbar"></a>Panel nástrojů Zobrazení tříd

Panel nástrojů **Zobrazení tříd** obsahuje následující příkazy:

|||
|-|-|
|**Nová složka**|Vytvoří virtuální složku nebo podsložku, do které můžete uspořádat často používané prvky. Jsou uloženy v aktivním souboru řešení (*.suo*). Po přejmenování nebo odstranění prvku v kódu se může zobrazit ve virtuální složce jako uzel chyby. Chcete-li tento problém vyřešit, odstraňte uzel chyby. Pokud jste prvek přejmenovali, můžete jej znovu přesunout z hierarchie projektu do složky.|
|**Zpět**|Přejde na dříve vybranou položku.|
|**Forward**|Přejde na další vybranou položku.|
|**Zobrazit diagram tříd** (pouze projekty spravovaného kódu)|Bude k dispozici, když vyberete obor názvů nebo typ v **zobrazení třídy**. Pokud je vybrán obor názvů, diagram třídy zobrazuje všechny typy v něm. Je-li vybrán typ, diagram třídy zobrazí pouze tento typ.|

### <a name="class-view-settings"></a>Nastavení zobrazení tříd

Tlačítko **Nastavení zobrazení tříd** na panelu nástrojů má následující nastavení:

|||
|-|-|
|**Zobrazit základní typy**|Zobrazí se základní typy.|
|**Zobrazit odkazy na projekt**|Zobrazí se odkazy na projekt.|
|**Zobrazit skryté typy a členy**|Skryté typy a členy (nejsou určeny pro použití klienty) jsou zobrazeny ve světle šedém textu.|
|**Zobrazit veřejné členy**|Zobrazí se veřejné členy.|
|**Zobrazit chráněné členy**|Zobrazí se chráněné členy.|
|**Zobrazit soukromé členy**|Zobrazí se soukromé členy.|
|**Zobrazit ostatní členy**|Zobrazí se další druhy členů, včetně interních (nebo Friend in Visual Basic).|
|**Zobrazit zděděné členy**|Jsou zobrazeny zděděné členy.|

### <a name="class-view-shortcut-menu"></a>Místní nabídka Zobrazení tříd

Nabídka zástupce (nebo klepnutí pravým tlačítkem myši) v **zobrazení tříd** může obsahovat následující příkazy v závislosti na zvoleném druhu projektu:

|||
|-|-|
|**Přejít na definici**|Vyhledá definici prvku ve zdrojovém kódu nebo v **prohlížeči objektů**, pokud prvek není definován v otevřeném projektu.|
|**Procházet definici**|Zobrazí vybranou položku v **prohlížeči objektů**.|
|**Najít všechny odkazy**|Vyhledá aktuálně vybranou položku objektu a zobrazí výsledky v okně **Najít výsledky.**|
|**Filtr ovat na typ** (pouze spravovaný kód)|Zobrazí pouze vybraný typ nebo obor názvů. Filtr můžete odebrat tak, že vedle pole **Najít** vyberete tlačítko **Vymazat hledání** (**X).**|
|**Kopírovat**|Zkopíruje plně kvalifikovaný název položky.|
|**Seřadit abecedně**|Uvádí typy a členy abecedně podle názvu.|
|**Seřadit podle typu člena**|Seznamy typů a členů v pořadí podle typu (například třídy předcházejí rozhraní, rozhraní předcházejí delegáty a metody předcházejí vlastnosti).|
|**Seřadit podle přístupu člena**|Seznam typů a členů v pořadí podle typu přístupu, například veřejné nebo soukromé.|
|**Skupina podle typu člena**|Seřadí typy a členy do skupin podle typu objektu.|
|**Přejít na deklaraci** (pouze kód Jazyka C++)|Zobrazí deklaraci typu nebo člena ve zdrojovém kódu, pokud je k dispozici.|
|**Přejít na definici**|Zobrazí definici typu nebo člena ve zdrojovém kódu, pokud je k dispozici.|
|**Přejít na odkaz**|Zobrazí odkaz na typ nebo člen ve zdrojovém kódu, pokud je k dispozici.|
|**Zobrazit hierarchii volání**|Zobrazí vybranou metodu v okně **Hierarchie volání.**|

## <a name="call-hierarchy-window-visual-basic-c-c"></a>Okno Hierarchie volání (Visual Basic, C#, C++)

Okno **Hierarchie volání** zobrazuje, kde je volána daná metoda nebo vlastnost. Obsahuje také seznam metod, které jsou volány z této metody. Můžete zobrazit více úrovní grafu volání, který zobrazuje vztahy volajícího volaného mezi metodami v zadaném oboru.

Okno **Hierarchie volání** můžete zobrazit tak, že vyberete metodu (nebo vlastnost nebo konstruktor) v editoru a v místní nabídce zvolíte **Zobrazit hierarchii volání.** Displej by se měl podobat následujícímu obrázku:

![Okno Hierarchie volání v sadě Visual Studio](../ide/media/multiplenodes.png)

Pomocí rozevíracího seznamu na panelu nástrojů můžete určit rozsah hierarchie: řešení, aktuální projekt nebo aktuální dokument.

V hlavním podokně se zobrazí volání do a z metody a **podokno Weby volání** zobrazuje umístění vybraného volání. Pro členy, které jsou virtuální nebo abstraktní, se zobrazí uzel **názvu metody Overrides.** Pro členy rozhraní se zobrazí uzel **názvu metody Implements.**

Okno **Hierarchie volání** nenalezne odkazy na skupiny metod, které zahrnují místa, kde je metoda přidána jako obslužná rutina události nebo je přiřazena delegátovi. Chcete-li najít tyto odkazy, použijte **příkaz Najít všechny odkazy.**

Místní nabídka v okně **Hierarchie volání** obsahuje následující příkazy:

|||
|-|-|
|**Přidat jako nový kořen**|Přidá vybraný uzel jako nový kořenový uzel.|
|**Odebrat kořenový adresář**|Odebere vybraný kořenový uzel z podokna zobrazení stromu.|
|**Přejít k definici**|Přejde na původní definici metody.|
|**Najít všechny odkazy**|Najde v projektu všechny odkazy na vybranou metodu.|
|**Kopírovat**|Zkopíruje vybraný uzel (ale ne jeho poduzly).|
|**Obnovení**|Aktualizuje informace.|

## <a name="object-browser"></a><a name="BKMK_ObjectBrowser"></a>Prohlížeč objektů

V okně **Prohlížeč objektů** se zobrazí popiskódu v projektech.

Součásti, které chcete zobrazit, můžete filtrovat pomocí rozevíracího seznamu v horní části okna. Vlastní součásti mohou zahrnovat spustitelné soubory spravovaného kódu, sestavení knihoven, knihovny typů a soubory *OCX.* Není možné přidat vlastní součásti jazyka C++.

::: moniker range="vs-2017"

Vlastní nastavení jsou uložena v adresáři uživatelských aplikací sady Visual Studio *,,%APPDATA%\Microsoft\VisualStudio\15.0\ObjBrowEX.dat*.

::: moniker-end

::: moniker range=">=vs-2019"

Vlastní nastavení jsou uložena v adresáři uživatelských aplikací sady Visual Studio *,,%APPDATA%\Microsoft\VisualStudio\16.0\ObjBrowEX.dat*.

::: moniker-end

V levém podokně **prohlížeče objektů** se zobrazují sestavení. Můžete rozbalit sestavení a zobrazit obory názvů, které obsahují, a potom rozbalit obory názvů a zobrazit typy, které obsahují. Když vyberete typ, jeho členy (například vlastnosti a metody) jsou uvedeny v pravém podokně. V pravém dolním podokně se zobrazí podrobné informace o vybrané položce.

Určitou položku můžete vyhledat pomocí pole **Hledat** v horní části okna. Hledání nerozlišují malá a velká písmena. Výsledky hledání se zobrazí v levém podokně. Chcete-li hledání vymazat, zvolte tlačítko **Vymazat hledání** (**X**) vedle pole **Hledat.**

**Prohlížeč objektů** sleduje provedené výběry a můžete mezi sebou procházet pomocí tlačítek **Vpřed** a **Zpět** na panelu nástrojů.

Pomocí prohlížeče **objektů** můžete přidat odkaz na sestavení k otevřenému řešení tak, že vyberete položku (sestavení, jmenný prostor, typ nebo člen) a na panelu nástrojů zvolíte tlačítko **Přidat odkaz.**

### <a name="object-browser-settings"></a>Nastavení prohlížeče objektů

Pomocí tlačítka **Nastavení prohlížeče objektů** na panelu nástrojů můžete určit jedno z následujících zobrazení:

|||
|-|-|
|**Zobrazení oborů názvů**|Zobrazí obory názvů spíše než fyzické kontejnery v levém podokně. Obory názvů uložené ve více fyzických kontejnerech jsou sloučeny.|
|**Zobrazit kontejnery**|Zobrazuje fyzické kontejnery spíše než obory názvů v levém podokně. **Zobrazit obory názvů** a **zobrazit kontejnery** jsou vzájemně se vylučující nastavení.|
|**Zobrazit základní typy**|Zobrazí základní typy.|
|**Zobrazit skryté typy a členy**|Zobrazí skryté typy a členy (nejsou určeny pro použití klienty) ve světle šedém textu.|
|**Zobrazit veřejné členy**|Zobrazí veřejné členy.|
|**Zobrazit chráněné členy**|Zobrazí chráněné členy.|
|**Zobrazit soukromé členy**|Zobrazí soukromé členy.|
|**Zobrazit ostatní členy**|Zobrazí další typy členů, včetně interních (nebo Friend in Visual Basic).|
|**Zobrazit zděděné členy**|Zobrazí zděděné členy.|
|**Zobrazit metody rozšíření**|Zobrazí metody rozšíření.|

### <a name="object-browser-shortcut-menu-commands"></a>Příkazy místní nabídky prohlížeče objektů

Nabídka zástupce (nebo klepnutí pravým tlačítkem myši) v **prohlížeči objektů** může obsahovat následující příkazy v závislosti na zvolené položce:

|||
|-|-|
|**Procházet definici**|Zobrazí primární uzel pro vybranou položku.|
|**Najít všechny odkazy**|Vyhledá aktuálně vybranou položku objektu a zobrazí výsledky v okně **Najít výsledky.**|
|**Filtr pro psaní**|Zobrazí pouze vybraný typ nebo obor názvů. Filtr můžete odebrat výběrem tlačítka **Vymazat hledání.**|
|**Kopírovat**|Zkopíruje plně kvalifikovaný název položky.|
|**Odebrat**|Pokud je obor vlastní sadou součástí, odebere vybranou součást z oboru.|
|**Seřadit abecedně**|Uvádí typy a členy abecedně podle názvu.|
|**Seřadit podle typu objektu**|Seznamy typů a členů v pořadí podle typu (například třídy předcházejí rozhraní, rozhraní předcházejí delegáty a metody předcházejí vlastnosti).|
|**Seřadit podle přístupu k objektům**|Seznam typů a členů v pořadí podle typu přístupu, například veřejné nebo soukromé.|
|**Seskupit podle typu objektu**|Seřadí typy a členy do skupin podle typu objektu.|
|**Přejít na deklaraci** (pouze projekty jazyka C++)|Zobrazí deklaraci typu nebo člena ve zdrojovém kódu, pokud je k dispozici.|
|**Přejít na definici**|Zobrazí definici typu nebo člena ve zdrojovém kódu, pokud je k dispozici.|
|**Přejít na odkaz**|Zobrazí odkaz na typ nebo člen ve zdrojovém kódu, pokud je k dispozici.|
|**Zobrazit hierarchii volání**|Zobrazí vybranou metodu v okně **Hierarchie volání.**|

## <a name="code-definition-window-c"></a>Okno Definice kódu (C++)

Okno **Definice kódu** zobrazuje definici vybraného typu C++ nebo člena v aktivním projektu. Typ nebo člen lze vybrat v editoru kódu nebo v okně zobrazení kódu.

Přestože je toto okno jen pro čtení, můžete v něm nastavit zarážky nebo záložky. Chcete-li upravit zobrazenou definici, zvolte **Upravit definici** v místní nabídce. Tím se otevře zdrojový soubor v editoru kódu a přesune kurzor na řádek, kde začíná definice.

> [!NOTE]
> Počínaje Visual Studio 2015, okno **definice kódu** lze použít pouze s kódem C++.

### <a name="code-definition-shortcut-menu"></a>Místní nabídka Definice kódu

Nabídka zástupce (nebo klepnutí pravým tlačítkem myši) v okně **Definice kódu** může obsahovat následující příkazy:

|||
|-|-|
|**Rychlé akce a refaktoringy**||
|**Přejmenovat**||
|**Generovat graf zahrnutí souborů**||
|**Náhled definice**||
|**Přejít na definici**|Vyhledá definici (nebo definice pro částečné třídy) a zobrazí je v okně **Najít výsledky.**|
|**Přejít na prohlášení**||
|**Najít všechny odkazy**|Vyhledá odkazy na typ nebo člen v řešení.|
|**Zobrazit hierarchii volání**|Zobrazí metodu v okně **Hierarchie volání.**|
|**Přepnout záhlaví / soubor kódu**||
|**Spustit testy**|Pokud jsou testy částí v projektu, spustí testy pro vybraný kód.|
|**Testy ladění**||
|**Zarážka**|Vloží zarážku (nebo trasovací bod).|
|**Spustit na kurzor**|Spustí program v režimu ladění do umístění kurzoru.|
|**Fragment kódu**||
|**Vyjmout,** **kopírovat,** **vložit**||
|**Poznámka**||
|**Sbalování**|Standardní příkazy osnovy.|
|**Prohledat**||
|**Upravit definici**|Přesune textový kurzor na definici v okně kódu.|
|**Zvolte Kódování**|Otevře okno **Kódování,** abyste mohli nastavit kódování pro soubor.|

## <a name="document-outline-window"></a>Okno Osnova dokumentu

Okno **Osnova dokumentu** můžete použít ve spojení se zobrazeními návrháře, například návrháře pro stránku XAML nebo návrháře formulářů systému Windows nebo se stránkami HTML. Toto okno zobrazuje prvky ve stromovém zobrazení, takže můžete zobrazit logickou strukturu formuláře nebo stránky a najít ovládací prvky, které jsou hluboce vložené nebo skryté.

## <a name="see-also"></a>Viz také

- [Ikony zobrazení třídy a prohlížeče objektů](../ide/class-view-and-object-browser-icons.md)
