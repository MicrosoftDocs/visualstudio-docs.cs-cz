---
title: Zobrazení struktury kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.documentoutline.window
- vs.objectbrowser
- vs.classview
- VS.CodeDefinitionView
- VS.CodeDefinitionWindow
- vs.componentpicker
- vs.callbrowser
helpviewer_keywords:
- document outline window.
- Visual Studio, object browser
- Visual Studio, code definition window
- call hierarchy
- Visual Studio, document outline window
- code definition window
- Visual Studio, class view
- Visual Studio, call hierarchy window
- class view
- object browser
ms.assetid: e6064f58-5ad9-4f05-8c3f-12e994b6583f
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1a860fbb88bb15786fad5fdf277f8f65b245056b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545012"
---
# <a name="viewing-the-structure-of-code"></a>Zobrazení struktury kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete prozkoumávat objekty a členy v projektech sady Visual Studio a objekty a členy v komponentách .NET Framework, komponenty COM, dynamické knihovny (DLL) a knihovny typů (TLB).

 Následující části tohoto dokumentu popisují různá okna struktury kódu.

 [Zobrazení tříd (Visual Basic, C#, C++)](#BKMK_ClassView)

 [Hierarchie volání (Visual Basic, C#, C++)](#BKMK_CallHierarchy)

 [prohlížeč objektů](#BKMK_ObjectBrowser)

 [Okno Definice kódu (C#, C++)](#BKMK_CodeDefinition)

 Můžete také použít **Průzkumník řešení** pro procházení typů a členů v projektech, hledání symbolů, zobrazení hierarchie volání metody, hledání odkazů na symboly a další, aniž byste museli přepínat mezi několika dříve uvedenými okny nástrojů.

 Pokud máte Visual Studio Enterprise můžete použít mapy kódu k vizualizaci struktury kódu a jeho závislostí v celém řešení a přejít k podrobnostem o částech kódu, které vás zajímají. Další informace najdete v tématu [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md).

> [!NOTE]
> Edice sady Visual Studio a nastavení, které používáte, mohou ovlivnit funkce v integrovaném vývojovém prostředí. Můžou se lišit od těch popsaných v tomto tématu.

## <a name="class-view-visual-basic-c-c"></a><a name="BKMK_ClassView"></a>Zobrazení tříd (Visual Basic, C#, C++)
 **Zobrazení tříd** se zobrazuje jako součást **Průzkumník řešení** a v samostatném okně. Okno **zobrazení tříd** zobrazí prvky aplikace. V horním podokně se zobrazí obory názvů, typy, rozhraní, výčty a třídy a v dolním podokně se zobrazí členové, kteří patří k typu vybranému v horním podokně. Pomocí tohoto okna můžete přejít na definice členů ve zdrojovém kódu (nebo v **Prohlížeč objektů** , pokud je prvek definován mimo vaše řešení).

 Není nutné kompilovat projekt, aby bylo možné zobrazit jeho prvky v **zobrazení tříd**. Okno je aktualizováno při úpravách kódu v projektu.

 Do projektu můžete přidat kód tak, že vyberete uzel projektu a kliknete na tlačítko **Přidat** a otevřete dialogové okno **Přidat novou položku** . Kód se přidá do samostatného souboru.

 Pokud je váš projekt vrácen se změnami do správy zdrojového kódu, každý **zobrazení tříd** element zobrazí ikonu, která označuje stav zdrojového kódu souboru. Běžné příkazy pro řízení zdrojového kódu, jako je **rezervace**, **vrácení se změnami**a **získání nejnovější verze** , jsou také k dispozici v místní nabídce prvku.

### <a name="class-view-toolbar"></a>Panel nástrojů Zobrazení tříd
 Panel nástrojů Zobrazení tříd obsahuje následující příkazy.

|Příkaz|Popis|
|-|-|
|**Nová složka**|Vytvoří virtuální složku nebo podsložku, ve které můžete uspořádat často používané prvky. Jsou uloženy v souboru aktivního řešení (. suo). Po přejmenování nebo odstranění elementu v kódu se může zobrazit ve virtuální složce jako chybový uzel. Chcete-li tento problém vyřešit, odstraňte chybový uzel. Pokud jste přejmenovali element, můžete jej přesunout z hierarchie projektu do složky znovu.|
|**Zpět**|Přejde k dříve vybrané položce.|
|**Forward**|Přejde na další vybranou položku.|
|**Zobrazení diagramu tříd** (pouze projekty spravovaného kódu)|Bude k dispozici, když v **zobrazení tříd**vyberete obor názvů nebo typ. Když je vybrán obor názvů, diagram třídy zobrazí všechny typy v něm. Když je vybrán typ, diagram třídy zobrazí pouze tento typ.|

### <a name="class-view-settings"></a>Nastavení Zobrazení tříd
 Tlačítko **zobrazení tříd nastavení** na panelu nástrojů má následující nastavení.

|Name|Popis|
|-|-|
|**Zobrazit základní typy**|Zobrazí se základní typy.|
|**Zobrazit odvozené typy**|Zobrazí se odvozené typy.|
|**Zobrazit skryté typy a členy**|Skryté typy a členy (nejsou určené pro použití klienty) se zobrazují v světle šedého textu.|
|**Zobrazit veřejné členy**|Zobrazí se veřejné členy.|
|**Zobrazit chráněné členy**|Zobrazí se chránění členové.|
|**Zobrazit soukromé členy**|Zobrazí se privátní členové.|
|**Zobrazit ostatní členy**|Zobrazí se další druhy členů, včetně interních členů (nebo přítele v Visual Basic).|
|**Zobrazit zděděné členy**|Jsou zobrazeny zděděné členy.|
|**Zobrazit metody rozšíření**|Jsou zobrazeny rozšiřující metody.|

### <a name="class-view-shortcut-menu"></a>Místní nabídka Zobrazení tříd
 Místní nabídka v **zobrazení tříd** může obsahovat následující příkazy v závislosti na typu vybraného projektu.

|Příkaz|Popis|
|-|-|
|**Přejít k definici**|Vyhledá definici prvku ve zdrojovém kódu nebo v **Prohlížeč objektů**, pokud element není definován v otevřeném projektu.|
|**Procházet definici**|Zobrazí vybranou položku v **Prohlížeč objektů**.|
|**Najít všechny odkazy**|Vyhledá aktuálně vybranou položku objektu a zobrazí výsledky v okně **hledání výsledků** .|
|**Filtrovat podle typu** (jenom spravovaný kód)|Zobrazí pouze vybraný typ nebo obor názvů. Filtr můžete odebrat tak, že kliknete na tlačítko **Vymazat hledání** (X) vedle pole **Najít** .|
|**Kopií**|Zkopíruje plně kvalifikovaný název položky.|
|**Seřadit abecedně**|Zobrazí seznam typů a členů abecedně podle názvu.|
|**Seřadit podle typu člena**|Seznam typů a členů v pořadí podle typu (takové třídy předcházejí rozhraní, rozhraní před delegáty a metody předcházejí vlastností).|
|**Seřadit podle přístupu ke členům**|Zobrazí seznam typů a členů v pořadí podle typu přístupu, jako je například Public nebo Private.|
|**Seskupit podle typu člena**|Seřadí typy a členy do skupin podle typu objektu.|
|**Přejít k deklaraci** (jenom kód C++)|Zobrazí deklaraci typu nebo člena ve zdrojovém kódu, pokud je k dispozici.|
|**Přejít k definici**|Zobrazí definici typu nebo členu ve zdrojovém kódu, pokud je k dispozici.|
|**Přejít na odkaz**|Zobrazí odkaz na typ nebo člen ve zdrojovém kódu, pokud je k dispozici.|
|**Zobrazit hierarchii volání**|Zobrazí vybranou metodu v okně **hierarchie volání** .|

## <a name="call-hierarchy-visual-basic-c-c"></a><a name="BKMK_CallHierarchy"></a>Hierarchie volání (Visual Basic, C#, C++)
 Okno **hierarchie volání** ukazuje, kde je volána daná metoda (nebo vlastnost nebo konstruktor), a uvádí metody, které jsou volány z této metody. Můžete zobrazit více úrovní grafu volání, který ukazuje vztahy volající/volaný mezi metodami v zadaném oboru.

 Můžete zobrazit okno **hierarchie volání** výběrem metody (nebo vlastnosti nebo konstruktoru) a následným výběrem možnosti **Zobrazit hierarchii tříd** v místní nabídce. Zobrazení by mělo vypadat podobně jako na následujícím obrázku.

 ![Otevřít hierarchii volání více uzlů](../ide/media/multiplenodes.png "MultipleNodes") Okno hierarchie volání

 Pomocí rozevíracího seznamu na panelu nástrojů můžete zadat rozsah hierarchie: řešení, aktuální projekt nebo aktuální dokument.

 V hlavním podokně se zobrazí volání a z metody a v podokně **volat weby** se zobrazí umístění vybraného volání. Pro členy, kteří jsou virtuální nebo abstraktní, se zobrazí uzel **název metody přepsání** . Pro členy rozhraní se zobrazí uzel **implementující název metody** .

 Okno **hierarchie volání** nenalezne odkazy na skupiny metod, které obsahují místo, kde je metoda přidána jako obslužná rutina události nebo je přiřazena delegátovi. K vyhledání těchto odkazů použijte příkaz **Najít všechny odkazy** .

 Místní nabídka v okně **hierarchie volání** obsahuje následující příkazy.

|Příkaz|Popis|
|-|-|
|**Přidat jako nový kořen**|Přidá vybraný uzel jako nový kořenový uzel.|
|**Odebrat kořen**|Odebere vybraný kořenový uzel z podokna zobrazení stromu.|
|**Přejít k definici**|Přejde k původní definici metody.|
|**Najít všechny odkazy**|Najde v projektu všechny odkazy na vybranou metodu.|
|**Kopií**|Zkopíruje vybraný uzel (ale ne jeho dílčí uzly).|
|**Aktualizovat**|Aktualizuje informace.|

## <a name="object-browser"></a><a name="BKMK_ObjectBrowser"></a>Prohlížeč objektů
 **Prohlížeč objektů** zobrazí popisy kódu v projektech.

 Můžete filtrovat, co chcete zobrazit v **Prohlížeč objektů**. Pomocí rozevíracího seznamu v horní části okna si můžete vybrat z následujících možností:

- Jakékoli .NET Framework

- Silverlight

- Aktivní řešení

- Vlastní sada komponent

  Vlastní komponenty mohou zahrnovat spustitelné soubory spravovaného kódu, sestavení knihoven, knihovny typů a soubory. ocx. Není možné přidat vlastní součásti C++. Vlastní nastavení se ukládají v adresáři aplikace Visual Studio User,%APPDATA%\Roaming\Microsoft\VisualStudio\11.0\ObjBrowEX.dat.

  V levém podokně **Prohlížeč objektů** se zobrazují fyzické kontejnery, jako jsou .NET Framework a komponenty com. Můžete rozbalit uzly kontejneru a zobrazit tak obory názvů, které obsahují, a poté rozšířit obory názvů tak, aby zobrazovaly typy, které obsahují. Když vyberete typ, jeho členové (například vlastnosti a metody) jsou uvedeny v pravém podokně. V pravém dolním podokně se zobrazí podrobné informace o vybrané položce.

  Konkrétní položku můžete vyhledat pomocí **vyhledávacího** pole v horní části okna. Při hledání se nerozlišují malá a velká písmena. Výsledky hledání se zobrazí v levém podokně. Hledání vymažete tak, že kliknete na tlačítko **Vymazat vyhledávání** (X) vedle pole **hledání** .

  **Prohlížeč objektů** sleduje výběry, které jste provedli, a můžete přecházet mezi jednotlivými výběry pomocí tlačítek **vpřed** a **zpět** na panelu nástrojů.

  Můžete použít **Prohlížeč objektů** pro přidání odkazu na sestavení do otevřeného řešení tak, že vyberete položku (sestavení, obor názvů, typ nebo člen) a kliknete na tlačítko **Přidat odkaz** na panelu nástrojů.

### <a name="object-browser-settings"></a>Nastavení Prohlížeč objektů
 Pomocí tlačítka **Prohlížeč objektů nastavení** na panelu nástrojů můžete zadat jedno z následujících zobrazení.

|Name|Popis|
|-|-|
|**Zobrazit obory názvů**|Zobrazuje obory názvů místo fyzických kontejnerů v levém podokně. Obory názvů uložené ve více fyzických kontejnerech jsou sloučeny.|
|**Zobrazit kontejnery**|Zobrazí v levém podokně fyzické kontejnery, nikoli obory názvů. **Zobrazit obory názvů** a **kontejnery zobrazení** se vzájemně exkluzivním nastavením.|
|**Zobrazit základní typy**|Zobrazí základní typy.|
|**Zobrazit odvozené typy**|Zobrazí odvozené typy.|
|**Zobrazit skryté typy a členy**|Zobrazí skryté typy a členy (nejsou určeny pro klienty), v světle šedého textu.|
|**Zobrazit veřejné členy**|Zobrazí veřejné členy.|
|**Zobrazit chráněné členy**|Zobrazí chráněné členy.|
|**Zobrazit soukromé členy**|Zobrazí soukromé členy.|
|**Zobrazit ostatní členy**|Zobrazí další typy členů, včetně interních členů (nebo přítele v Visual Basic).|
|**Zobrazit zděděné členy**|Zobrazí zděděné členy.|
|**Zobrazit metody rozšíření**|Zobrazí metody rozšíření.|

### <a name="object-browser-shortcut-menu-commands"></a>Příkazy místní nabídky Prohlížeč objektů
 Místní nabídka v **Prohlížeč objektů** může obsahovat následující příkazy v závislosti na typu vybrané položky.

|Příkaz|Popis|
|-|-|
|**Procházet definici**|Zobrazuje primární uzel pro vybranou položku.|
|**Najít všechny odkazy**|Vyhledá aktuálně vybranou položku objektu a zobrazí výsledky v okně **hledání výsledků** .|
|**Filtrovat podle typu**|Zobrazí pouze vybraný typ nebo obor názvů. Filtr můžete odebrat tak, že kliknete na tlačítko **Vymazat hledání** .|
|**Kopií**|Zkopíruje plně kvalifikovaný název položky.|
|**Odebrat**|Pokud je oborem vlastní sada komponent, aplikace Odebere vybranou komponentu z oboru.|
|**Seřadit abecedně**|Zobrazí seznam typů a členů abecedně podle názvu.|
|**Seřadit podle typu objektu**|Seznam typů a členů v pořadí podle typu (takové třídy předcházejí rozhraní, rozhraní před delegáty a metody předcházejí vlastností).|
|**Seřadit podle přístupu k objektům**|Zobrazí seznam typů a členů v pořadí podle typu přístupu, jako je například Public nebo Private.|
|**Seskupit podle typu objektu**|Seřadí typy a členy do skupin podle typu objektu.|
|**Přejít k deklaraci** (jenom projekty C++)|Zobrazí deklaraci typu nebo člena ve zdrojovém kódu, pokud je k dispozici.|
|**Přejít k definici**|Zobrazí definici typu nebo členu ve zdrojovém kódu, pokud je k dispozici.|
|**Přejít na odkaz**|Zobrazí odkaz na typ nebo člen ve zdrojovém kódu, pokud je k dispozici.|
|**Zobrazit hierarchii volání**|Zobrazí vybranou metodu v okně **hierarchie volání** .|

## <a name="code-definition-window-c-c"></a><a name="BKMK_CodeDefinition"></a>Okno Definice kódu (C#, C++)
 V okně **definice kódu** se zobrazí definice vybraného typu nebo členu v aktivním projektu. Typ nebo člen může být vybrán v editoru kódu nebo v okně zobrazení kódu.

 I když je toto okno jen pro čtení, můžete v něm nastavit zarážky nebo záložky. Chcete-li změnit zobrazenou definici, v místní nabídce vyberte možnost **Upravit definici** . Tím se otevře zdrojový soubor v editoru kódu a přesune se kurzor na řádek, kde začíná definice.

### <a name="code-definition-shortcut-menu"></a>Místní nabídka definice kódu
 Místní nabídka v okně **definice kódu** může obsahovat následující příkazy v závislosti na programovacím jazyce.

|Příkaz|Popis|
|-|-|
|**Vytvořit testy jednotek**|Vytvoří testy jednotek pro vybraný prvek.|
|**Generovat sekvenční diagram**|Když je vybrána metoda, vygeneruje sekvenční diagram.|
|**Vytvoření privátního přístupového objektu**|Pokud je v řešení přítomen test jednotek, vygeneruje metodu, kterou test používá pro přístup k kódu.|
|**Přejít k definici**|Najde definici (nebo definice) pro částečné třídy a zobrazí je v okně **výsledků hledání** .|
|**Najít všechny odkazy**|Najde odkazy na typ nebo člena v řešení.|
|**Zobrazit hierarchii volání**|Zobrazí metodu v okně **hierarchie volání** .|
|**Zobrazit volající testy**|Pokud v projektu existují testy jednotek, zobrazí testy, které volají vybraný kód.|
|**Spustit testy volání**|Pokud v projektu existují testy jednotek, spustí testy pro vybraný kód.|
|**Bodu**|Vloží zarážku (nebo zarážka s trasováním).|
|**Spustit ke kurzoru**|Spustí program v režimu ladění do umístění kurzoru.|
|**Kopií**|Zkopíruje vybraný řádek.|
|**Sbalování**|Standardní příkazy pro sbalení.|
|**Upravit definici**|Přesune kurzor do definice v okně Code (kód).|
|**Zvolit kódování**|Otevře okno **kódování** , aby bylo možné nastavit kódování souboru.|

### <a name="document-outline-window"></a>Okno Osnova dokumentu
 Můžete použít okno **Osnova dokumentu** ve spojení s zobrazeními návrháře, jako je například Návrhář pro stránku XAML nebo Návrhář formuláře Windows nebo se stránkami HTML. V tomto okně se zobrazí prvky ve stromovém zobrazení, takže můžete zobrazit logickou strukturu formuláře nebo stránky a vyhledat ovládací prvky, které jsou hluboko vložené nebo skryté.

## <a name="see-also"></a>Viz také
 [Ikony Zobrazení tříd a Prohlížeč objektů](../ide/class-view-and-object-browser-icons.md)
