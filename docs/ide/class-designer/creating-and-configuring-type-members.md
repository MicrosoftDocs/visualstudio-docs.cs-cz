---
title: Vytváření a konfigurace členů typů (návrhář tříd)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdetails.method
- vs.classdetails.property
- vs.classdetails.parameter
- vs.classdetails.event
- vs.classdetails.field
helpviewer_keywords:
- Class Designer [Visual Studio], member creation
- type members, modifying in Class Designer
- parameters [ASP.NET Web Services], adding to methods
- type members, configuring
- type members
- members
- type members, creating
- members, creating
- Class Designer [Visual Studio], type members
- read-only information, displaying
- members, configuring
- methods [Visual Studio], adding parameters
- Class Details window
- Class Details window, member creation
ms.assetid: 42af8738-3738-4ca7-82ff-edf573a68f96
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfed51812b034d63f250a56548b88f09a98214fe
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590407"
---
# <a name="create-and-configure-type-members-in-class-designer"></a>Vytvoření a konfigurace členů typu v Návrháři tříd

Tyto členy můžete přidat do typů v diagramu třídy a nakonfigurovat tyto členy v okně **Podrobnosti o třídě:**

|**Typ**|**Členy, které může obsahovat**|
|--------------| - |
|Třída|metoda, vlastnost (pro C# a Visual Basic), pole, událost (pro C# a Visual Basic), konstruktor (metoda), konstruktor (metoda), konstanta|
|Výčet|člen|
|Rozhraní|metoda, vlastnost, událost (pro C# a Visual Basic)|
|Abstraktní třída|metoda, vlastnost (pro C# a Visual Basic), pole, událost (pro C# a Visual Basic), konstruktor (metoda), konstruktor (metoda), konstanta|
|Struktura (struktura v jazyce C#)|metoda, vlastnost (pro C# a Visual Basic), pole, událost (pro C# a Visual Basic), konstruktor (metoda), konstanta|
|Delegát|parametr|
|Modul (pouze VB)|metoda, vlastnost, pole, událost, konstruktor, konstanta|

> [!NOTE]
> Když přístupové objekty get a set nepotřebují další logiku, můžete deklaraci vlastnosti zestručnit pomocí automaticky implementovaných vlastností (pouze jazyk C#). Chcete-li zobrazit úplný podpis, zvolte z nabídky **Diagram třídy** **změnit formát** > členů**zobrazit úplný podpis**. Další informace o automaticky implementovaných vlastnostech naleznete [v tématu Auto-Implemented Properties](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Podpůrný obsah|
|----------| - |
|**Začínáme:** Před vytvořením a konfigurací členů typu je nutné otevřít okno **Podrobnosti o třídě.**|- [Otevření okna Podrobnosti o třídě](creating-and-configuring-type-members.md#open-the-class-details-window)<br />- [Poznámky k použití Podrobnosti o třídě](creating-and-configuring-type-members.md#class-details-usage-notes)<br />- [Zobrazení informací jen pro čtení](creating-and-configuring-type-members.md#display-of-read-only-information)<br />- [Klávesové zkratky a klávesové zkratky myši v okně Diagram třídy a Podrobnosti o třídě](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)|
|**Vytvořit a upravit členy typu:** Můžete vytvořit nové členy, upravit členy a přidat parametry k metodě pomocí okna **Podrobnosti o třídě.**|- [Vytvořit členy](creating-and-configuring-type-members.md#create-members)<br />- [Změnit členy typu](creating-and-configuring-type-members.md#modify-type-members)<br />- [Přidání parametrů k metodám](creating-and-configuring-type-members.md#add-parameters-to-methods)|

## <a name="open-the-class-details-window"></a>Otevření okna Podrobnosti o třídě

Ve výchozím nastavení se okno **Podrobnosti o třídě** zobrazí automaticky při otevření nového diagramu třídy. Viz [Postup: Přidání diagramů tříd do projektů](how-to-add-class-diagrams-to-projects.md)). Okno **Podrobnosti o třídě** můžete také otevřít následujícími způsoby:

- Klepněte pravým tlačítkem myši na libovolnou třídu v diagramu, chcete-li zobrazit místní nabídku a potom vyberte **podrobnosti třídy**.

- Na řádku nabídek vyberte **Zobrazit** > **další podrobnosti o třídě** **systému Windows.** > 

## <a name="create-members"></a>Vytvořit členy

Člen můžete vytvořit pomocí libovolného z následujících nástrojů:

- **Návrhář tříd**

- Panel nástrojů **Podrobnosti** o třídě

- **Okno Podrobnosti o třídě**

> [!NOTE]
> Pomocí postupů v tomto oddíle můžete také vytvořit konstruktory a destruktory. Mějte prosím na paměti, že konstruktory a destruktory jsou speciální druhy metod a jako takové se zobrazují v oddílu **Metody** v obrazcích diagramu třídy a v části **Metody** v mřížce okna **Podrobnosti třídy.**

> [!NOTE]
> Parametr je jediná entita, kterou můžete přidat k delegátu. Všimněte si, že postup s názvem "Vytvořit člena pomocí panelu nástrojů **okna Podrobnosti třídy"** není pro tuto akci platný.

### <a name="create-a-member-using-class-designer"></a>Vytvoření člena pomocí Návrháře tříd

1. Klikněte pravým tlačítkem myši na typ, ke kterému chcete přidat člena, přejděte na **Přidat**a vyberte typ člena, který chcete přidat.

     Vytvoří se nový podpis člena a přidá se k typu. Je uveden výchozí název, který můžete změnit v **Návrháře tříd**, okno **Podrobnosti třídy** nebo v okně **Vlastnosti.**

2. Volitelně můžete určit další detaily členu, například jeho typ.

### <a name="create-a-member-using-the-class-details-window-toolbar"></a>Vytvoření člena pomocí panelu nástrojů okna Podrobnosti o kurzu

1. Na ploše diagramu vyberte typ, ke kterému chcete přidat člen.

     Typ získá fokus a jeho obsah se zobrazí v okně **Podrobnosti třídy.**

2. V pruhu nástrojů **okna Podrobnosti o třídě** klepněte na horní ikonu a vyberte nový ** \<>členů** v rozevíracím seznamu.

     Kurzor se přesune do pole **Název** v řádku pro druh člena, který chcete přidat. Pokud jste například klepnul na tlačítko **Nová vlastnost**, kurzor se přesune na nový řádek v části **Vlastnosti** v okně **Podrobnosti třídy.**

3. Zadejte název členu, který chcete vytvořit, a stiskněte klávesu Enter (nebo jinak přesuňte fokus, například stisknutím klávesy Tab).

     Vytvoří se nový podpis člena a přidá se k typu. Člen nyní existuje v kódu a je zobrazen v **Návrháři tříd**, v okně **Podrobnosti o třídě** a v okně Vlastnosti.

4. Volitelně můžete určit další detaily členu, například jeho typ.

### <a name="create-a-member-using-the-class-details-window"></a>Vytvoření člena pomocí okna Podrobnosti o kurzu

1. Na ploše diagramu vyberte typ, ke kterému chcete přidat člen.

     Typ získá fokus a jeho obsah se zobrazí v okně **Podrobnosti třídy.**

2. V okně **Podrobnosti třídy** klikněte v části obsahující typ člena, který chcete přidat, na ** \<přidat>člena **. Chcete-li například přidat pole, ** \< **klepněte na tlačítko Přidat pole>.

3. Zadejte název členu, který chcete vytvořit, a stiskněte klávesu Enter.

     Vytvoří se nový podpis člena a přidá se k typu. Člen nyní existuje v kódu a je zobrazen v **Návrháři tříd**, v okně **Podrobnosti o třídě** a v okně Vlastnosti.

4. Volitelně můžete určit další detaily členu, například jeho typ.

    > [!NOTE]
    > Členy můžete také vytvořit pomocí klávesových zkratek. Další informace naleznete [v tématu Klávesové zkratky a klávesové zkratky v diagramu třídy a podrobnosti o třídě](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md).

## <a name="modify-type-members"></a>Změnit členy typu

V Návrháři tříd můžete upravit členy typů, které se zobrazí v diagramu. Můžete upravit členy libovolného typu, které se zobrazí v diagramu třídy a nejsou jen pro čtení. Členy textu můžete upravit pomocí úprav na místě na návrhové ploše, okně Vlastnosti a v okně **Podrobnosti třídy.**

Všechny členy zobrazené v okně **Podrobnosti třídy** představují členy typů v diagramu třídy. Existují čtyři typy členů: metody, vlastnosti, pole a události.

Všechny řádky členů jsou zobrazeny pod nadpisy, které je seskupují podle druhu. Například všechny vlastnosti se zobrazí pod nadpisem **Vlastnosti**, který lze jako uzel v mřížce sbalit nebo rozbalit.

Každý řádek členu zobrazuje následující prvky:

- **Ikona člena**

     Každý druh členu znázorňuje jeho vlastní ikona. Namiřte myší na ikonu člena a zobrazte podpis člena. Kliknutím na ikonu členu nebo na prázdné znaky vlevo od ikony členu vyberete řádek.

- **Název člena**

     Ve sloupci **Název** v řádku člena se zobrazí název člena. Tento název se také zobrazí ve vlastnosti **Name** v okně Vlastnosti. Tuto buňku můžete použít ke změně názvu jakéhokoli členu, který má oprávnění pro čtení i zápis.

     Pokud je sloupec **Název** příliš úzký, aby se zobrazil celý název, zobrazí se na název člena najet myší na název člena.

- **Typ členu**

     Buňka **MemberType** používá technologie IntelliSense, která umožňuje vybrat ze seznamu všech typů dostupných v aktuálním projektu nebo odkazovaných projektech.

- **Modifikátor členů**

     Změňte modifikátor viditelnosti `Public` prvku`public` `Private` na`private` `Friend` (`internal` `Protected` ),`protected` `Protected Friend` (`protected internal`( `Default`( ( ( ), nebo .

- **\<přidat členský>**

     Poslední řádek v okně **Podrobnosti třídy** obsahuje text ** \<přidat>členů** v buňce **Name.** Pokud na tuto buňku klikněte, můžete vytvořit nový člen. Další informace naleznete v tématu [Create members](creating-and-configuring-type-members.md#create-members).

- **Vlastnosti členů v okně Vlastnosti**

     Okno **Podrobnosti třídy** zobrazuje podmnožinu vlastností členů, které jsou zobrazeny v okně Vlastnosti. Změna vlastnosti na jednom místě aktualizuje hodnotu vlastnosti globálně. Aktualizuje se i zobrazení hodnoty členu v jiném umístění.

- **Souhrn**

     **Souhrnná** buňka zpřístupňuje souhrn informací o členu. Klepnutím na tři tečky v buňce **Souhrn** zobrazíte nebo upravíte informace o **souhrnu**, **návratovém typu**a **poznámkách** pro člena.

- **Skrýt**

     Když je zaškrtnuto políčko **Skrýt,** člen se v textu nezobrazí.

### <a name="to-modify-a-type-member"></a>Změna členu typu

1. Pomocí Návrháře tříd vyberte typ.

2. Pokud se okno **Podrobnosti o třídě** nezobrazí, klepněte na tlačítko **okna Podrobnosti třídy** na panelu nástrojů Návrhář třídy.

3. Upravte hodnoty v polích mřížky okna **Podrobnosti o třídě.** Po každé úpravě stiskněte klávesu ENTER nebo jinak přesuňte fokus z upravovaného pole, například stisknutím klávesy TAB. Úpravy se v kódu projeví okamžitě.

    > [!NOTE]
    > Pokud chcete změnit pouze název členu, můžete to provést úpravou na místě.

## <a name="add-parameters-to-methods"></a>Přidání parametrů k metodám

Přidejte parametry metod pomocí okna **Podrobnosti o třídě.** Parametry lze konfigurovat jako povinné, či volitelné. Poskytnutí hodnoty **volitelné výchozí** vlastnost parametru pokyn návrháře generovat kód jako volitelný parametr.

Řádky parametru obsahují následující položky:

- **Název**

     Sloupec **Název** v řádku parametru zobrazuje název parametru. Tento název se také zobrazí ve vlastnosti **Name** v okně Vlastnosti. Tuto buňku můžete použít ke změně názvu jakéhokoli parametru, který má oprávnění pro čtení i zápis.

     Když je sloupec Název příliš úzký na název parametru, zobrazí se název parametru, pokud je sloupec **Název** příliš úzký na to, aby zobrazil celý název.

- **Typ**

     Buňka **Typ parametru** používá technologie IntelliSense, která umožňuje vybrat ze seznamu všech typů dostupných v aktuálním projektu nebo odkazovaných projektech.

- **Modifikátor**

     **Modifikační** buňka v řádku parametru přijme a zobrazí nový modifikátor parametru. Chcete-li zadat nový modifikátor parametrů, vyberte pomocí rozevíracího seznamu **možnost Žádný**, **ref**, **out**nebo **params** v c#, A **ByVal**, **ByRef**nebo **ParamArray** ve VB.

- **Souhrn**

     **Souhrnná** buňka v řádku parametrů umožňuje zadávání komentářů kódu, které se zobrazí v aplikaci IntelliSense při zadávání parametru do editoru kódu.

- **\<přidat>parametrů**

     Poslední řádek parametru člena obsahuje text **<parametr\> u** buňky **Name.** Kliknutím na tuto buňku vytvoříte nový parametr. Další informace naleznete v [tématu Přidání parametru do metody](creating-and-configuring-type-members.md#add-parameters-to-methods).

Okno **Vlastnosti** zobrazuje stejné vlastnosti parametrů zobrazené v okně **Podrobnosti třídy:** **Název**, **Typ**, **Modifikátor**, **Souhrn**a vlastnost **Volitelné výchozí.** Změnou vlastnosti na jednom místě aktualizujete hodnotu vlastnosti globálně, včetně zobrazení hodnoty v jiném umístění.

> [!NOTE]
> Pokud chcete přidat parametr delegátovi, [přečtěte](creating-and-configuring-type-members.md#create-members)si informace o vytvoření členů .

> [!NOTE]
> Ačkoli je destruktor metoda, nemůže mít parametry.

### <a name="to-add-a-parameter-to-a-method"></a>Přidání parametru do metody

1. Na ploše diagramu klikněte na typ obsahující metodu, ke které chcete přidat parametr.

     Typ získá fokus a jeho obsah se zobrazí v okně **Podrobnosti třídy.**

2. V okně **Podrobnosti třídy** rozbalte řádek metody, do které chcete přidat parametr.

     Zobrazí se odsazený řádek parametru, který obsahuje pouze dvojici závorek a slova ** \<přidávají parametr>.**

3. Klepněte na ** \<tlačítko Přidat parametr>**, zadejte název nového parametru a stiskněte **Enter**.

     Nový parametr je přidán do metody a kódu metody. Zobrazí se v okně **Podrobnosti o třídě** a v okně Vlastnosti.

4. Volitelně můžete určit další detaily parametru, například jeho typ.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Přidání volitelného parametru do metody

1. Na ploše diagramu klikněte na typ obsahující metodu, ke které chcete přidat volitelný parametr.

     Typ získá fokus a jeho obsah se zobrazí v okně **Podrobnosti třídy.**

2. V okně **Podrobnosti třídy** rozbalte řádek metody, do které chcete přidat volitelný parametr.

     Zobrazí se odsazený řádek parametru, který obsahuje pouze dvojici závorek a slova ** \<přidávají parametr>.**

3. Klepněte na ** \<tlačítko Přidat parametr>**, zadejte název nového parametru a stiskněte **Enter**.

     Nový parametr je přidán do metody a kódu metody. Zobrazí se v okně **Podrobnosti o třídě** a v okně Vlastnosti.

4. V okně Vlastnosti zadejte hodnotu **vlastnosti Volitelné výchozí.** Nastavením vlastnosti Volitelné výchozí nastavíte daný parametr na volitelný.

    > [!NOTE]
    > Volitelné parametry musí být posledními parametry v seznamu parametrů.

## <a name="class-details-usage-notes"></a>Poznámky k použití podrobností o třídě

Vezměte prosím na vědomí následující tipy pro použití okna **Podrobnosti o třídě.**

### <a name="editable-and-non-editable-cells"></a>Editovatelné a needitovatelné buňky

Všechny buňky v okně **Podrobnosti třídy** lze upravovat s několika výjimkami:

- Celý typ je jen pro čtení, když se například nachází v odkazované mši. Když vyberete obrazec v Návrháři tříd, okno **Podrobnosti třídy** zobrazí jeho podrobnosti ve stavu jen pro čtení.

- V případě indexerů je název jen pro čtení a zbytek (typ, modifikátor, shrnutí) je editovatelný.

- Všechny obecné typy mají parametry jen pro čtení v okně **Podrobnosti třídy.** Chcete-li změnit obecný parametr, upravte jeho zdrojový kód.

- Název parametru typu, který je definován na obecném typu, je jen pro čtení.

- Pokud je kód typu přerušený (neanalyzovatelný), zobrazí se v okně **Podrobnosti o třídě** obsah typu jen pro čtení.

### <a name="the-class-details-window-and-source-code"></a>Okno Podrobnosti o třídě a zdrojový kód

- Zdrojový kód můžete zobrazit kliknutím pravým tlačítkem myši na obrazec v okně **Podrobnosti o třídě** (nebo návrháři tříd) a následným kliknutím na Zobrazit kód. Otevře se soubor zdrojového kódu a zobrazení se posune na vybraný prvek.

- Změna zdrojového kódu se okamžitě projeví v zobrazení informací o podpisu v Návrháři tříd a v okně **Podrobnosti o třídě.** Pokud je okno **Podrobnosti třídy** v době zavřeno, nové informace se zobrazí při příštím otevření.

- Pokud je kód typu přerušený (neanalyzovatelný), zobrazí se v okně **Podrobnosti o třídě** obsah typu pouze pro čtení.

### <a name="clipboard-functionality-in-the-class-details-window"></a>Funkce schránky v okně Podrobnosti třídy

Pole nebo řádky můžete zkopírovat nebo vyjmout z okna **Podrobnosti o třídě** a vložit je do jiného typu. Řádek můžete vyjmout, pouze pokud je jen pro čtení. Když vložíte řádek, okno **Podrobnosti třídy** přiřadí nový název (odvozený od názvu zkopírovaného řádku), aby nedošlo ke konfliktu.

## <a name="display-of-read-only-information"></a>Zobrazení informací jen pro čtení

Návrhář třídy a okno **Podrobnosti o třídě** mohou zobrazit typy (a členy typů) pro následující:

- projekt, který obsahuje diagram třídy

- projekt odkazovaný z projektu, který obsahuje diagram třídy

- sestavení odkazované z projektu, který obsahuje diagram třídy

V posledních dvou případech je odkazovaná entita (typ nebo člen) v diagramu tříd, který ji reprezentuje, jen pro čtení.

Celý projekt nebo jeho části, například jednotlivé soubory, mohou být jen pro čtení. Většina běžných případů, ve kterých projekt nebo jeden z jeho souborů, je jen pro čtení, jsou takové, kdy se projekt nachází v rámci správy zdrojového kódu (a není rezervován), existuje v externím sestavení nebo když operační systém považuje soubory za soubory jen pro čtení.

**Řízení zdrojového kódu**

Vzhledem k tomu, že diagram třídy je uložen jako soubor v projektu, je třeba rezervovat projekt, abyste uložili všechny změny provedené v návrháři tříd nebo v okně **Podrobnosti o třídě.**

**Projekty jen pro čtení**

Projekt může být jen pro čtení z jiného důvodu než pro správu zdrojového kódu. Zavření projektu zobrazí dialogové okno s dotazem, zda přepsat soubor projektu, zahodit změny (neukládat) nebo zrušit operaci zavření. Pokud zvolíte přepsání, soubory projektu jsou přepsány a nastaveny pro čtení i zápis. Je přidán nový soubor diagramu tříd.

**Typy jen pro čtení**

Pokud se pokusíte uložit projekt obsahující typ, jehož soubor zdrojového kódu je jen pro čtení, zobrazí se dialogové okno **Uložit soubor jen pro čtení,** které vám umožní uložit soubor pod novým názvem nebo novým umístěním nebo přepsat soubor jen pro čtení. Pokud soubor přepíšete, nová kopie již není jen pro čtení.

Pokud soubor s kódem obsahuje chybu syntaxe, tvary zobrazující kód v daném souboru budou dočasně jen pro čtení, dokud chyba syntaxe nebude opravena. Tvary v tomto stavu zobrazí červený text a červenou ikonu, která zobrazí popisek s textem „Soubor zdrojového kódu obsahuje chybu analýzy“.

Odkazovaný typ (například typ .NET), který existuje pod jiným uzlovým projektem nebo pod odkazovým uzlovým uzřem, je na návrhovém povrchu Návrháře tříd označen jen pro čtení. Místní typ, který existuje v projektu, jež chcete otevřít, je pro čtení i zápis a jeho tvar na návrhové ploše Návrháře tříd je takto označen.

Indexery jsou čtení a zápis v kódu a **podrobnosti třídy** okna, ale název indexeru je jen pro čtení.

Částečné metody nelze upravovat pomocí návrháře tříd nebo okna **Podrobnosti třídy.** k jejich úpravám je nutné použít Editor kódu.

Nativní kód Jazyka C++ nelze upravovat pomocí návrháře tříd nebo okna **Podrobnosti o třídě.** K úpravě nativního kódu jazyka C++ je nutné použít Editor kódu kódu kódu.

## <a name="see-also"></a>Viz také

- [Zobrazení typů a vztahů](designing-and-viewing-classes-and-types.md)
- [Refaktoring tříd a typů](refactoring-classes-and-types.md)
