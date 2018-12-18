---
title: Vytváření a konfigurace členů typů (návrhář tříd)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b93fa4720a6f0de9e2d7a64eb2c820811610297
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938796"
---
# <a name="create-and-configure-type-members-in-class-designer"></a>Vytvoření a konfigurace členů typů v Návrháři tříd

Můžete přidat tyto členy typů pro třídu diagramu a konfigurovat je v **podrobností třídy** okno:

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
> Když přístupové objekty get a set nepotřebují další logiku, můžete deklaraci vlastnosti zestručnit pomocí automaticky implementovaných vlastností (pouze jazyk C#). Chcete-li zobrazit úplný podpis z **Diagram tříd** nabídku zvolte **změnit formát členů** > **zobrazit úplný podpis**. Další informace o automaticky implementovaných vlastnostech naleznete v tématu [implemented Properties](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).

## <a name="common-tasks"></a>Běžné úlohy

|Úloha|Podpůrný obsah|
|----------| - |
|**Začínáme:** předtím, než vytvoříte a nakonfigurujete členy typů, je nutné otevřít **podrobností třídy** okna.|- [Otevření okna podrobností třídy](creating-and-configuring-type-members.md#open-the-class-details-window)<br />- [Poznámky k použití okna podrobností třídy](creating-and-configuring-type-members.md#class-details-usage-notes)<br />- [Zobrazení informací jen pro čtení](creating-and-configuring-type-members.md#display-of-read-only-information)<br />- [Klávesové zkratky klávesnice a myši v diagramu tříd a podrobností třídy okna](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)|
|**Vytvoření a úpravy členů typů:** můžete vytvořit nové členy, měnit členy a přidat parametry k metodě pomocí **podrobností třídy** okna.|- [Vytváření členů](creating-and-configuring-type-members.md#create-members)<br />- [Úpravy členů typů](creating-and-configuring-type-members.md#modify-type-members)<br />- [Přidání parametrů k metodám](creating-and-configuring-type-members.md#add-parameters-to-methods)|

## <a name="open-the-class-details-window"></a>Otevření okna podrobností třídy

Ve výchozím nastavení **podrobností třídy** okno se automaticky zobrazí při otevření nový diagram tříd. Zobrazit [postupy: Přidání diagramů tříd do projektů](how-to-add-class-diagrams-to-projects.md)). Můžete také otevřít **podrobností třídy** okno následujícími způsoby:

- Klikněte pravým tlačítkem na jakékoli třídy v diagramu, chcete-li zobrazit místní nabídku a zvolte **podrobností třídy**.

- Vyberte **zobrazení** > **ostatní Windows** > **podrobností třídy** z řádku nabídek.

## <a name="create-members"></a>Vytváření členů

Člen můžete vytvořit pomocí libovolného z následujících nástrojů:

- **Návrhář tříd**

- **Třída podrobnosti** panel nástrojů okna

- **Třída podrobnosti** okna

> [!NOTE]
> Pomocí postupů v tomto oddíle můžete také vytvořit konstruktory a destruktory. Nezapomínejte, že konstruktory a destruktory jsou zvláštní druhy metod a jako takové se zobrazují v **metody** ve tvarech diagramu třídy a v oddílu **metody** část  **Třída podrobnosti** mřížky okna okno.

> [!NOTE]
> Parametr je jediná entita, kterou můžete přidat k delegátu. Všimněte si, že postup s názvem "Vytvoření členu pomocí **podrobností třídy** panel nástrojů okna ' není platný pro tuto akci.

### <a name="create-a-member-using-class-designer"></a>Vytvoření členu pomocí návrháře tříd

1.  Klikněte pravým tlačítkem na typ, ke kterému chcete přidat člen, přejděte na **přidat**a pak zvolte typ člena, které chcete přidat.

     Vytvoří se nový podpis člena a přidá se k typu. Se klíči přiřadí výchozí název, který můžete změnit v **návrhář tříd**, **podrobností třídy** okna, nebo **vlastnosti** okna.

2.  Volitelně můžete určit další detaily členu, například jeho typ.

### <a name="create-a-member-using-the-class-details-window-toolbar"></a>Vytvoření členu pomocí panelu nástrojů okna podrobností třídy

1.  Na ploše diagramu vyberte typ, ke kterému chcete přidat člen.

     Typ získá fokus a jeho obsah se zobrazí v **podrobností třídy** okna.

2.  V **podrobností třídy** panel nástrojů okna, klikněte na ikonu nahoře a vyberte **nový \<člena >** z rozevíracího seznamu.

     Kurzor se přesune **název** pole na řádek pro typ členu, které chcete přidat. Například, pokud jste klikli na **novou vlastnost**, kurzor se přesune na nový řádek v **vlastnosti** část **podrobností třídy** okna.

3.  Zadejte název členu, který chcete vytvořit, a stiskněte klávesu Enter (nebo jinak přesuňte fokus, například stisknutím klávesy Tab).

     Vytvoří se nový podpis člena a přidá se k typu. Člen nyní existuje v kódu a zobrazí se v **návrhář tříd**, **podrobností třídy** okna a okna Vlastnosti.

4.  Volitelně můžete určit další detaily členu, například jeho typ.

### <a name="create-a-member-using-the-class-details-window"></a>Vytvoření členu pomocí okna podrobností třídy

1.  Na ploše diagramu vyberte typ, ke kterému chcete přidat člen.

     Typ získá fokus a jeho obsah se zobrazí v **podrobností třídy** okna.

2.  V **podrobností třídy** okno, v části, která obsahuje typ členu, které chcete přidat, klikněte na tlačítko  **\<přidat člen >**. Například pokud chcete přidat pole, klikněte na možnost  **\<přidat pole >**.

3.  Zadejte název členu, který chcete vytvořit, a stiskněte klávesu Enter.

     Vytvoří se nový podpis člena a přidá se k typu. Člen nyní existuje v kódu a zobrazí se v **návrhář tříd**, **podrobností třídy** okna a okna Vlastnosti.

4.  Volitelně můžete určit další detaily členu, například jeho typ.

     **Poznámka:** klávesové zkratky můžete také použít k vytváření členů. Další informace najdete v tématu [klávesové zkratky a zkratky myši v diagramu tříd a podrobností třídy okna](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md).

## <a name="modify-type-members"></a>Úpravy členů typů

V Návrháři tříd můžete upravit členy typů, které se zobrazí v diagramu. Můžete upravit členy libovolného typu, které se zobrazí v diagramu třídy a nejsou jen pro čtení. Členy typu změníte úpravou na místě na návrhové ploše, okno Vlastnosti a **podrobností třídy** okna.

Všechny členy zobrazené v **podrobností třídy** okno představují členy typů v diagramu tříd. Existují čtyři typy členů: metody, vlastnosti, pole a události.

Všechny řádky členů jsou zobrazeny pod nadpisy, které je seskupují podle druhu. Například všechny vlastnosti se zobrazí pod nadpisem **vlastnosti**, který lze jako uzel v mřížce rozbalit nebo sbalit.

Každý řádek členu zobrazuje následující prvky:

- **Ikona členu**

     Každý druh členu znázorňuje jeho vlastní ikona. Umístěním kurzoru myši na ikonu členu zobrazíte podpis členu. Kliknutím na ikonu členu nebo na prázdné znaky vlevo od ikony členu vyberete řádek.

- **Název člena**

     **Název** sloupců na řádku členu zobrazí název členu. Tento název se také zobrazí v **název** vlastností v okně Vlastnosti. Tuto buňku můžete použít ke změně názvu jakéhokoli členu, který má oprávnění pro čtení i zápis.

     Pokud **název** sloupec je příliš úzký, aby se zobrazil celý název, umístěním kurzoru myši na název členu zobrazíte celý název.

- **Typ člena**

     **MemberType** buňky používá technologii IntelliSense, které lze vybrat ze seznamu všech typů dostupných v aktuálním projektu nebo v odkazovaných projektech.

- **Modifikátor členu**

     Změňte viditelnost Modifikátor členu na buď `Public` (`public`), `Private` (`private`), `Friend` (`internal`) `Protected` (`protected`), `Protected``Friend` (`protected``internal`), nebo `Default`.

- **\<Přidat člena >**

     Poslední řádek v **podrobností třídy** okno obsahuje text  **\<přidat člen >** v **název** buňky. Pokud na tuto buňku klikněte, můžete vytvořit nový člen. Další informace najdete v tématu [vytváření členů](creating-and-configuring-type-members.md#create-members).

- **Vlastnosti členu v okně Vlastnosti**

     **Podrobností třídy** okno zobrazuje podmnožinu vlastností členů, které jsou zobrazeny v okně Vlastnosti. Změna vlastnosti na jednom místě aktualizuje hodnotu vlastnosti globálně. Aktualizuje se i zobrazení hodnoty členu v jiném umístění.

- **Shrnutí**

     **Souhrnu** buňky uvádí souhrnné informace o členu. Klikněte na tlačítko se třemi tečkami v **Souhrn** buněk k zobrazení nebo upravte informace o **Souhrn**, **návratový typ**, a **poznámky** pro člena .

- **Skrýt**

     Když **skrýt** zaškrtávací políčko zaškrtnuto, člen není zobrazen v typu.

### <a name="to-modify-a-type-member"></a>Změna členu typu

1.  Pomocí Návrháře tříd vyberte typ.

2.  Pokud **podrobností třídy** okno nezobrazí, klikněte na tlačítko **podrobností třídy** okno tlačítko na panelu nástrojů návrhář tříd.

3.  Upravte hodnoty v polích **podrobností třídy** mřížky okna okno. Po každé úpravě stiskněte klávesu ENTER nebo jinak přesuňte fokus z upravovaného pole, například stisknutím klávesy TAB. Úpravy se v kódu projeví okamžitě.

    > [!NOTE]
    > Pokud chcete změnit pouze název členu, můžete to provést úpravou na místě.

## <a name="add-parameters-to-methods"></a>Přidání parametrů k metodám

Přidání parametrů do metody pomocí **podrobností třídy** okna. Parametry lze konfigurovat jako povinné, či volitelné. Zadání hodnoty pro **volitelné výchozí** vlastnost parametru dáte návrháři pokyn, aby vygeneroval kód jako volitelný parametr.

Řádky parametru obsahují následující položky:

- **Jméno**

     **Název** sloupců na řádku parametru zobrazí název parametru. Tento název se také zobrazí v **název** vlastností v okně Vlastnosti. Tuto buňku můžete použít ke změně názvu jakéhokoli parametru, který má oprávnění pro čtení i zápis.

     Odkazuje na název parametru zobrazí název parametru, pokud **název** sloupec je příliš úzký, aby se zobrazil celý název.

- **Typ**

     **Typ parametru** buňky používá technologii IntelliSense, která vám umožní vybrat si ze seznamu všech typů dostupných v aktuálním projektu nebo v odkazovaných projektech.

- **Modifikátor**

     **Modifikátor** buňku na řádku parametru přijímá a zobrazuje nový modifikátor parametru. Pokud chcete zadat nový parametr modifikátoru, pomocí rozevíracího seznamu vyberte z **žádný**, **ref**, **si**, nebo **params** v C# a **ByVal**, **ByRef**, nebo **ParamArray** v jazyce VB.

- **Shrnutí**

     **Souhrn** buňku na řádku parametru umožňuje zadávání komentářů kódu, které se zobrazí v IntelliSense při zadání parametru do editoru kódu.

- **\<Přidat parametr >**

     Poslední řádek parametru členu obsahuje text **<add parameter>** v **název** buňky. Kliknutím na tuto buňku vytvoříte nový parametr. Další informace najdete v tématu [přidání parametru k metodě](creating-and-configuring-type-members.md#add-parameters-to-methods).

**Vlastnosti** stejné vlastnosti parametru, který se zobrazí v okně se zobrazí **podrobností třídy** okna: **název**, **typ**,  **Modifikátor**, **Souhrn**, jakož i **volitelné výchozí** vlastnost. Změnou vlastnosti na jednom místě aktualizujete hodnotu vlastnosti globálně, včetně zobrazení hodnoty v jiném umístění.

> [!NOTE]
> Chcete-li přidat parametr do delegáta, přečtěte si téma [vytváření členů](creating-and-configuring-type-members.md#create-members).

> [!NOTE]
> Ačkoli je destruktor metoda, nemůže mít parametry.

### <a name="to-add-a-parameter-to-a-method"></a>Přidání parametru do metody

1.  Na ploše diagramu klikněte na typ obsahující metodu, ke které chcete přidat parametr.

     Typ získá fokus a jeho obsah se zobrazí v **podrobností třídy** okna.

2.  V **podrobností třídy** okna rozbalte řádek metody, do které chcete přidat parametr.

     Zobrazí se řádek parametru, který obsahuje pouze dvojici závorek a slova  **\<přidat parametr >.**

3.  Klikněte na tlačítko  **\<přidat parametr >**, zadejte název nového parametru a stiskněte klávesu **Enter**.

     Nový parametr se přidá do metody a kódu metody. Zobrazí se v **podrobností třídy** okna a okna Vlastnosti.

4.  Volitelně můžete určit další detaily parametru, například jeho typ.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Přidání volitelného parametru do metody

1.  Na ploše diagramu klikněte na typ obsahující metodu, ke které chcete přidat volitelný parametr.

     Typ získá fokus a jeho obsah se zobrazí v **podrobností třídy** okna.

2.  V **podrobností třídy** okna rozbalte řádek metody, do které chcete přidat volitelný parametr.

     Zobrazí se řádek parametru, který obsahuje pouze dvojici závorek a slova  **\<přidat parametr >.**

3.  Klikněte na tlačítko  **\<přidat parametr >**, zadejte název nového parametru a stiskněte klávesu **Enter**.

     Nový parametr se přidá do metody a kódu metody. Zobrazí se v **podrobností třídy** okna a okna Vlastnosti.

4.  V okně Vlastnosti zadejte hodnotu **volitelné výchozí** vlastnost. Nastavením vlastnosti Volitelné výchozí nastavíte daný parametr na volitelný.

    > [!NOTE]
    > Volitelné parametry musí být posledními parametry v seznamu parametrů.

## <a name="class-details-usage-notes"></a>Poznámky k použití okna podrobností třídy

Mějte prosím na paměti následující tipy pro používání **podrobností třídy** okna.

### <a name="editable-and-non-editable-cells"></a>Editovatelné a needitovatelné buňky

Všechny buňky v **podrobností třídy** okna je možné upravovat s několika výjimkami:

- Celý typ je jen pro čtení, když, například se nachází v odkazovaném sestavení. Při výběru tvaru v Návrháři tříd **podrobností třídy** okno zobrazí jeho detaily ve stavu jen pro čtení.

- V případě indexerů je název jen pro čtení a zbytek (typ, modifikátor, shrnutí) je editovatelný.

- Mají všechny obecné typy parametry jen pro čtení **podrobností třídy** okna. Chcete-li změnit obecný parametr, upravte jeho zdrojový kód.

- Název parametru typu, který je definován na obecném typu, je jen pro čtení.

- Když kód typu je porušen (), **podrobností třídy** okno zobrazí obsah typu jen pro čtení.

### <a name="the-class-details-window-and-source-code"></a>Detaily třídy okna a zdrojový kód

- Zdrojový kód můžete zobrazit kliknutím pravým tlačítkem myši na obrazec **podrobností třídy** okna (nebo návrhář tříd) a potom kliknutím na zobrazení kódu. Otevře se soubor zdrojového kódu a zobrazení se posune na vybraný prvek.

- Změna zdrojového kódu se okamžitě projeví v zobrazení informací podpisu v Návrháři tříd a **podrobností třídy** okna. Pokud **podrobností třídy** okna je v daném okamžiku zavřeno, nové informace se zobrazí při příštím otevření.

- Když kód typu je porušen (), **podrobností třídy** okně se zobrazí obsah typu jen pro čtení.

### <a name="clipboard-functionality-in-the-class-details-window"></a>Funkce schránky v okně podrobností třídy

Můžete kopírovat nebo vyjímat pole či řádky z **podrobností třídy** okno a vložte je do jiného typu. Řádek můžete vyjmout, pouze pokud je jen pro čtení. Po vložení řádku **podrobností třídy** okno nedošlo ke konfliktu přiřadí nový název (odvozený od názvu zkopírovaného řádku).

## <a name="display-of-read-only-information"></a>Zobrazení informací jen pro čtení

Návrhář tříd a **podrobností třídy** okna můžete zobrazit typy (a členy typů) pro následující:

- projekt, který obsahuje diagram třídy

- projekt odkazovaný z projektu, který obsahuje diagram třídy

- sestavení odkazované z projektu, který obsahuje diagram třídy

V posledních dvou případech je odkazovaná entita (typ nebo člen) v diagramu tříd, který ji reprezentuje, jen pro čtení.

Celý projekt nebo jeho části, například jednotlivé soubory, mohou být jen pro čtení. Většina běžných případů, ve kterých projekt nebo jeden z jeho souborů, je jen pro čtení, jsou takové, kdy se projekt nachází v rámci správy zdrojového kódu (a není rezervován), existuje v externím sestavení nebo když operační systém považuje soubory za soubory jen pro čtení.

**Správa zdrojového kódu**

Protože diagram tříd je uložen jako soubor v projektu, je třeba projekt rezervovat, aby bylo možné uložit změny provedené v Návrháři tříd nebo **podrobností třídy** okna.

**Projekty jen pro čtení**

Projekt může být jen pro čtení z jiného důvodu než pro správu zdrojového kódu. Zavírání projektu se zobrazí dialogové okno s dotazem, zda chcete přepsat soubor projektu, zahodit změny (bez uložení) nebo zrušit operaci zavření. Pokud zvolíte přepsání, soubory projektu jsou přepsány a nastaveny pro čtení i zápis. Je přidán nový soubor diagramu tříd.

**Typy jen pro čtení**

Pokud se pokusíte uložit projekt obsahující typ, jehož soubor zdrojového kódu je jen pro čtení, **uložení souboru jen pro čtení** se zobrazí dialogové okno, které nabízí možnost uložit soubor pod novým názvem nebo nové umístění nebo přepsat soubor jen pro čtení . Pokud soubor přepíšete, nová kopie již není jen pro čtení.

Pokud soubor s kódem obsahuje chybu syntaxe, tvary zobrazující kód v daném souboru budou dočasně jen pro čtení, dokud chyba syntaxe nebude opravena. Tvary v tomto stavu zobrazí červený text a červenou ikonu, která zobrazí popisek s textem „Soubor zdrojového kódu obsahuje chybu analýzy“.

Odkazovaný typ (například typ rozhraní .NET Framework), který existuje v rámci jiného uzlu projektu nebo uzlu odkazovaného sestavení, je na návrhové ploše Návrháře tříd uveden jako jen pro čtení. Místní typ, který existuje v projektu, jež chcete otevřít, je pro čtení i zápis a jeho tvar na návrhové ploše Návrháře tříd je takto označen.

Indexery jsou pro čtení i zápis v kódu a **podrobností třídy** okna, ale název indexeru je jen pro čtení.

Částečné metody nelze upravovat pomocí návrháře tříd nebo **podrobností třídy** okno; k úpravám je nutné použít Editor kódu.

Nativní kód C++ nelze upravovat pomocí návrháře tříd nebo **podrobností třídy** okno; je nutné použít Editor kódu pro úpravu nativního kódu C++.

## <a name="see-also"></a>Viz také:

- [Zobrazování typů a vztahů](viewing-types-and-relationships.md)
- [Refaktoring tříd a typů](refactoring-classes-and-types.md)