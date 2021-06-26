---
title: Zobrazení struktury kódu pomocí oken nástrojů
description: Naučte se používat Zobrazení tříd nástrojů, hierarchii volání, Prohlížeč objektů a definice kódu (pouze C++) k prohlédnutí tříd a jejich členů v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/19/2019
ms.topic: reference
f1_keywords:
- vs.documentoutline.window
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 41c11025e22c1288387862fa138b35efbbca8557
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924952"
---
# <a name="view-the-structure-of-code-by-using-different-tool-windows"></a>Zobrazení struktury kódu pomocí různých oken nástrojů

Můžete prozkoumávat třídy a jejich členy v aplikaci Visual Studio pomocí různých oken nástrojů, včetně **zobrazení tříd**, **hierarchie volání**, **Prohlížeč objektů** a **definice kódu** (pouze C++). Tyto nástroje mohou kontrolovat kód v projektech aplikace Visual Studio, komponentách .NET, komponentách COM, dynamických knihovnách (DLL) a knihovnách typů (TLB).

Můžete také použít **Průzkumník řešení** pro procházení typů a členů v projektech, hledání symbolů, zobrazení hierarchie volání metody, hledání odkazů na symboly a další, aniž byste museli přepínat mezi několika okny nástrojů.

Pokud máte edici Visual Studio Enterprise, můžete použít *mapy kódu* k vizualizaci struktury kódu a jeho závislostí v rámci celého řešení. Další informace najdete v tématu [Mapování závislostí pomocí map kódu](../modeling/map-dependencies-across-your-solutions.md).

## <a name="class-view-visual-basic-c-c"></a>Zobrazení tříd (Visual Basic, C#, C++)

**Zobrazení tříd** se zobrazuje jako součást **Průzkumník řešení** a jako samostatné okno. **Zobrazení tříd** zobrazí prvky aplikace. V horním podokně se zobrazí obory názvů, typy, rozhraní, výčty a třídy a v dolním podokně se zobrazí členové, kteří patří k typu vybranému v horním podokně. Pomocí tohoto okna můžete přejít na definice členů ve zdrojovém kódu (nebo v **Prohlížeč objektů** , pokud je prvek definován mimo vaše řešení).

Není nutné kompilovat projekt, aby bylo možné zobrazit jeho prvky v **zobrazení tříd**. Okno je aktualizováno při úpravách kódu v projektu.

Do projektu můžete přidat kód tak, že vyberete uzel projektu a kliknete na tlačítko **Přidat** a otevřete dialogové okno **Přidat novou položku** . Kód se přidá do samostatného souboru.

Pokud je váš projekt vrácen se změnami do správy zdrojového kódu, každý **zobrazení tříd** element zobrazí ikonu, která označuje stav zdrojového kódu souboru. Běžné příkazy pro řízení zdrojového kódu, jako je **rezervace**, **vrácení se změnami** a **získání nejnovější verze** , jsou také k dispozici v místní nabídce prvku.

### <a name="class-view-toolbar"></a>Panel nástrojů Zobrazení tříd

Panel nástrojů **zobrazení tříd** obsahuje následující příkazy:

|Název|Description|
|-|-|
|**Nová složka**|Vytvoří virtuální složku nebo podsložku, ve které můžete uspořádat často používané prvky. Jsou uloženy v souboru aktivního řešení (*. suo*). Po přejmenování nebo odstranění elementu v kódu se může zobrazit ve virtuální složce jako chybový uzel. Chcete-li tento problém vyřešit, odstraňte chybový uzel. Pokud jste přejmenovali element, můžete jej přesunout z hierarchie projektu do složky znovu.|
|**Zpět**|Přejde k dříve vybrané položce.|
|**Forward**|Přejde na další vybranou položku.|
|**Zobrazení diagramu tříd** (pouze projekty spravovaného kódu)|Bude k dispozici, když v **zobrazení tříd** vyberete obor názvů nebo typ. Když je vybrán obor názvů, diagram třídy zobrazí všechny typy v něm. Když je vybrán typ, diagram třídy zobrazí pouze tento typ.|

### <a name="class-view-settings"></a>Nastavení Zobrazení tříd

Tlačítko **zobrazení tříd nastavení** na panelu nástrojů má následující nastavení:

|Název|Description|
|-|-|
|**Zobrazit základní typy**|Zobrazí se základní typy.|
|**Zobrazit odkazy projektu**|Zobrazí se odkazy na projekt.|
|**Zobrazit skryté typy a členy**|Skryté typy a členy (nejsou určené pro použití klienty) se zobrazují v světle šedého textu.|
|**Zobrazit veřejné členy**|Zobrazí se veřejné členy.|
|**Zobrazit chráněné členy**|Zobrazí se chránění členové.|
|**Zobrazit soukromé členy**|Zobrazí se privátní členové.|
|**Zobrazit ostatní členy**|Zobrazí se další druhy členů, včetně interních členů (nebo přítele v Visual Basic).|
|**Zobrazit zděděné členy**|Jsou zobrazeny zděděné členy.|

### <a name="class-view-shortcut-menu"></a>Místní nabídka Zobrazení tříd

Místní nabídka (nebo kliknutí pravým tlačítkem myši) v **zobrazení tříd** může obsahovat následující příkazy v závislosti na zvoleném typu projektu:

|Název|Description|
|-|-|
|**Přejít k definici**|Vyhledá definici prvku ve zdrojovém kódu nebo v **Prohlížeč objektů**, pokud element není definován v otevřeném projektu.|
|**Procházet definici**|Zobrazí vybranou položku v **Prohlížeč objektů**.|
|**Najít všechny odkazy**|Vyhledá aktuálně vybranou položku objektu a zobrazí výsledky v okně **hledání výsledků** .|
|**Filtrovat podle typu** (jenom spravovaný kód)|Zobrazí pouze vybraný typ nebo obor názvů. Filtr můžete odebrat tak, že kliknete na tlačítko **Vymazat hledání** (**X**) vedle pole **Najít** .|
|**Kopírovat**|Zkopíruje plně kvalifikovaný název položky.|
|**Seřadit abecedně**|Zobrazí seznam typů a členů abecedně podle názvu.|
|**Seřadit podle typu člena**|Seznam typů a členů v pořadí podle typu (takové třídy předcházejí rozhraní, rozhraní před delegáty a metody předcházejí vlastností).|
|**Seřadit podle přístupu ke členům**|Zobrazí seznam typů a členů v pořadí podle typu přístupu, jako je například Public nebo Private.|
|**Seskupit podle typu člena**|Seřadí typy a členy do skupin podle typu objektu.|
|**Přejít k deklaraci** (jenom kód C++)|Zobrazí deklaraci typu nebo člena ve zdrojovém kódu, pokud je k dispozici.|
|**Přejít k definici**|Zobrazí definici typu nebo členu ve zdrojovém kódu, pokud je k dispozici.|
|**Přejít na odkaz**|Zobrazí odkaz na typ nebo člen ve zdrojovém kódu, pokud je k dispozici.|
|**Zobrazit hierarchii volání**|Zobrazí vybranou metodu v okně **hierarchie volání** .|

## <a name="call-hierarchy-window-visual-basic-c-c"></a>Okno hierarchie volání (Visual Basic, C#, C++)

Okno **hierarchie volání** ukazuje, kde je volána daná metoda nebo vlastnost. Také uvádí metody, které jsou volány z dané metody. Můžete zobrazit více úrovní grafu volání, který ukazuje vztahy volající volaný mezi metodami v zadaném oboru.

Můžete zobrazit okno **hierarchie volání** výběrem metody (nebo vlastnosti nebo konstruktoru) v editoru a následným výběrem možnosti **Zobrazit hierarchii volání** v místní nabídce. Zobrazení by mělo vypadat jako na následujícím obrázku:

![Okno hierarchie volání v aplikaci Visual Studio](../ide/media/multiplenodes.png)

Pomocí rozevíracího seznamu na panelu nástrojů můžete zadat rozsah hierarchie: řešení, aktuální projekt nebo aktuální dokument.

V hlavním podokně se zobrazí volání a z metody a v podokně **volat weby** se zobrazí umístění vybraného volání. Pro členy, kteří jsou virtuální nebo abstraktní, se zobrazí uzel **název metody přepsání** . Pro členy rozhraní se zobrazí uzel **implementující název metody** .

Okno **hierarchie volání** nenalezne odkazy na skupiny metod, které obsahují místo, kde je metoda přidána jako obslužná rutina události nebo je přiřazena delegátovi. K vyhledání těchto odkazů použijte příkaz **Najít všechny** odkazy.

Místní nabídka v okně **Hierarchie volání** obsahuje následující příkazy:

|Název|Description|
|-|-|
|**Přidat jako nový kořen**|Přidá vybraný uzel jako nový kořenový uzel.|
|**Odebrání kořenového adresáře**|Odebere vybraný kořenový uzel z podokna stromového zobrazení.|
|**Přejít k definici**|Přejde na původní definici metody.|
|**Najít všechny odkazy**|Vyhledá v projektu všechny odkazy na vybranou metodu.|
|**Kopírovat**|Zkopíruje vybraný uzel (ale ne jeho dílčí uzly).|
|**Aktualizovat**|Aktualizuje informace.|

## <a name="object-browser"></a><a name="BKMK_ObjectBrowser"></a> Prohlížeč objektů

V **okně Prohlížeče** objektů se zobrazí popisy kódu v projektech.

Součásti, které chcete zobrazit, můžete filtrovat pomocí rozevíracího seznamu v horní části okna. Vlastní komponenty mohou zahrnovat spustitelné soubory spravovaného kódu, sestavení knihoven, knihovny typů a *soubory .ocx.* Vlastní komponenty jazyka C++ není možné přidat.

::: moniker range="vs-2017"

Vlastní nastavení se ukládají v adresáři aplikace uživatele Visual Studio, *%APPDATA%\Microsoft\VisualStudio\15.0\ObjBrowEX.dat.*

::: moniker-end

::: moniker range=">=vs-2019"

Vlastní nastavení se ukládají v adresáři aplikace uživatele Visual Studio, *%APPDATA%\Microsoft\VisualStudio\16.0\ObjBrowEX.dat.*

::: moniker-end

V levém podokně Prohlížeče **objektů se** zobrazují sestavení. Můžete rozbalit sestavení a zobrazit obory názvů, které obsahují, a poté rozbalit obory názvů, aby se zobrazí typy, které obsahují. Když vyberete typ, jeho členy (například vlastnosti a metody) se zobrazí v pravém podokně. V pravém dolním podokně se zobrazí podrobné informace o vybrané položce.

Konkrétní položku můžete vyhledat pomocí **vyhledávacího** pole v horní části okna. Při hledání se malá a velká písmena nerozlišovat. Výsledky hledání se zobrazí v levém podokně. Pokud chcete hledání vymazat, zvolte **tlačítko Vymazat hledání** (**X**) vedle **vyhledávacího** pole.

Prohlížeč **objektů sleduje** výběry, které jste provedli, a můžete mezi  nimi  procházet pomocí tlačítek Vpřed a Zpět na panelu nástrojů.

Prohlížeč objektů  můžete použít k přidání odkazu na sestavení do otevřeného řešení tak, že vyberete  položku (sestavení, obor názvů, typ nebo člen) a zvolíte tlačítko Přidat odkaz na panelu nástrojů.

### <a name="object-browser-settings"></a>Nastavení prohlížeče objektů

Pomocí tlačítka **Nastavení prohlížeče objektů** na panelu nástrojů můžete zadat jedno z následujících zobrazení:

|Název|Description|
|-|-|
|**Zobrazení oborů názvů**|Zobrazí v levém podokně obory názvů místo fyzických kontejnerů. Sloučí se obory názvů uložené ve více fyzických kontejnerech.|
|**Zobrazení kontejnerů**|V levém podokně se zobrazí fyzické kontejnery místo oborů názvů. **Zobrazení oborů názvů** **a kontejnerů zobrazení** se vzájemně vylučují.|
|**Zobrazení základních typů**|Zobrazí základní typy.|
|**Zobrazení skrytých typů a členů**|Zobrazí skryté typy a členy (nezamýšlené pro klienty) ve světle šedém textu.|
|**Zobrazit veřejné členy**|Zobrazí veřejné členy.|
|**Zobrazení chráněných členů**|Zobrazí chráněné členy.|
|**Zobrazit soukromé členy**|Zobrazí privátní členy.|
|**Zobrazit ostatní členy**|Zobrazí další typy členů, včetně interních členů (nebo přátel v Visual Basic členů).|
|**Zobrazení zděděných členů**|Zobrazí zděděné členy.|
|**Zobrazení rozšiřujících metod**|Zobrazí rozšiřující metody.|

### <a name="object-browser-shortcut-menu-commands"></a>Příkazy místní nabídky prohlížeče objektů

Místní nabídka (nebo kliknutí pravým tlačítkem) v **Prohlížeči** objektů může obsahovat následující příkazy v závislosti na typu vybrané položky:

|Název|Description|
|-|-|
|**Definice procházení**|Zobrazuje primární uzel pro vybranou položku.|
|**Najít všechny odkazy**|Vyhledá aktuálně vybranou položku objektu a zobrazí výsledky v **okně Najít** výsledky.|
|**Filtrovat na typ**|Zobrazí pouze vybraný typ nebo obor názvů. Filtr můžete odebrat výběrem tlačítka **Vymazat** hledání.|
|**Kopírovat**|Zkopíruje plně kvalifikovaný název položky.|
|**Odebrat**|Pokud je oborem sada vlastních komponent, odebere vybranou komponentu z oboru.|
|**Seřadit abecedně**|Vypíše typy a členy abecedně podle názvu.|
|**Seřadit podle typu objektu**|Vypíše typy a členy v pořadí podle typu (tak, aby třídy předcházely rozhraním, rozhraním předcházely delegátům a metody předcházely vlastnostem).|
|**Řazení podle přístupu k objektům**|Vypíše typy a členy v pořadí podle typu přístupu, například veřejné nebo soukromé.|
|**Seskupit podle typu objektu**|Seřadí typy a členy do skupin podle typu objektu.|
|**Přejít na deklaraci** (pouze projekty C++)|Zobrazí deklaraci typu nebo členu ve zdrojovém kódu, pokud je k dispozici.|
|**Přejít k definici**|Zobrazí definici typu nebo členu ve zdrojovém kódu, pokud je k dispozici.|
|**Přejít na referenční informace**|Zobrazí odkaz na typ nebo člen ve zdrojovém kódu, pokud je k dispozici.|
|**Zobrazení hierarchie volání**|Zobrazí vybranou metodu v **okně Hierarchie** volání.|

## <a name="code-definition-window-c"></a>okno Definice kódu (C++)

V **okně Definice** kódu se zobrazí definice vybraného typu nebo člena C++ v aktivním projektu. Typ nebo člen lze vybrat v editoru kódu nebo v okně zobrazení kódu.

I když je toto okno jen pro čtení, můžete v tomto okně nastavit zarážky nebo záložky. Pokud chcete upravit zobrazenou definici, zvolte **v** místní nabídce Upravit definici. Tím se zdrojový soubor otevře v editoru kódu a přesune se kurzor na řádek, kde začíná definice.

> [!NOTE]
> Počínaje Visual Studio 2015 lze okno **Definice kódu** použít pouze s kódem C++.

### <a name="code-definition-shortcut-menu"></a>Místní nabídka definice kódu

Místní nabídka (nebo kliknutí pravým tlačítkem) v **okně Definice kódu** může obsahovat následující příkazy:

|Název|Description|
|-|-|
|**Rychlé akce a refaktoringy**||
|**Přejmenovat**||
|**Generování grafu zahrnutých souborů**||
|**Náhled definice**||
|**Přejít k definici**|Vyhledá definici (nebo definice pro částečné třídy) a zobrazí je v **okně Najít** výsledky.|
|**Přejít na deklaraci**||
|**Najít všechny odkazy**|Vyhledá odkazy na typ nebo člen v řešení.|
|**Zobrazení hierarchie volání**|Zobrazí metodu v **okně Hierarchie** volání.|
|**Přepnout hlavičku / soubor kódu**||
|**Spouštění testů**|Pokud jsou v projektu testy jednotek, spustí testy pro vybraný kód.|
|**Ladění testů**||
|**Zarážka**|Vloží zarážku (nebo trasovací bod).|
|**Spuštění na kurzor**|Spustí program v režimu ladění do umístění kurzoru.|
|**Fragment kódu**||
|**Vyjmutí,** **kopírování,** **vložení**||
|**Poznámka**||
|**Sbalování**|Standardní příkazy osnovy.|
|**Prohledat**||
|**Upravit definici**|Přesune kurzor na definici v okně kódu.|
|**Volba kódování**|Otevře **okno Kódování,** abyste mohli nastavit kódování souboru.|

## <a name="document-outline-window"></a>Okno Osnova dokumentu

Okno Osnova dokumentu můžete **použít** ve spojení se zobrazeními návrháře, například návrhářem pro stránku XAML nebo návrhářem formulářů Windows nebo se stránkami HTML. Toto okno zobrazí prvky ve stromovém zobrazení, abyste mohli zobrazit logickou strukturu formuláře nebo stránky a najít ovládací prvky, které jsou hluboko vložené nebo skryté.

## <a name="see-also"></a>Viz také

- [Ikony zobrazení tříd a prohlížeče objektů](../ide/class-view-and-object-browser-icons.md)
