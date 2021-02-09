---
title: Vytváření a konfigurace členů typů (návrhář tříd)
description: Naučte se, jak přidat členy do typů v diagramu tříd a nakonfigurovat tyto členy v okně podrobností třídy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 897001a5ac10e8a8e1eef96feca4113afa5e1ebf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880564"
---
# <a name="create-and-configure-type-members-in-class-designer"></a>Vytvoření a konfigurace členů typu v Návrhář tříd

Tyto členy můžete přidat do typů v diagramu tříd a nakonfigurovat je v okně **podrobností třídy** :

|**Typ**|**Členy, které může obsahovat**|
|--------------| - |
|Třída|metoda, vlastnost (pro C# a Visual Basic), pole, událost (pro C# a Visual Basic), konstruktor (metoda), konstruktor (metoda), konstanta|
|Výčet|člen|
|Rozhraní|metoda, vlastnost, událost (pro C# a Visual Basic)|
|Abstraktní třída|metoda, vlastnost (pro C# a Visual Basic), pole, událost (pro C# a Visual Basic), konstruktor (metoda), konstruktor (metoda), konstanta|
|Struktura (struktura v jazyce C#)|metoda, vlastnost (pro C# a Visual Basic), pole, událost (pro C# a Visual Basic), konstruktor (metoda), konstanta|
|Delegát|parameter|
|Modul (pouze VB)|metoda, vlastnost, pole, událost, konstruktor, konstanta|

> [!NOTE]
> Když přístupové objekty get a set nepotřebují další logiku, můžete deklaraci vlastnosti zestručnit pomocí automaticky implementovaných vlastností (pouze jazyk C#). Chcete-li zobrazit úplný podpis, z nabídky **Diagram tříd** vyberte možnost **změnit formát členů**  >  **Zobrazit úplný podpis**. Další informace o automaticky implementovaných vlastnostech naleznete v tématu [automaticky implementované vlastnosti](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Podpůrný obsah|
|----------| - |
|**Začínáme:** Předtím, než vytvoříte a nakonfigurujete členy typu, je nutné otevřít okno **podrobností třídy** .|- [Otevření okna podrobností třídy](creating-and-configuring-type-members.md#open-the-class-details-window)<br />- [Poznámky k využití podrobností třídy](creating-and-configuring-type-members.md#class-details-usage-notes)<br />- [Zobrazení informací jen pro čtení](creating-and-configuring-type-members.md#display-of-read-only-information)<br />- [Klávesové zkratky a zkratky myši v diagramu tříd a okně podrobností třídy](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)|
|**Vytvoření a úprava členů typu:** Můžete vytvořit nové členy, upravit členy a přidat parametry do metody pomocí okna **podrobností třídy** .|- [Vytvoření členů](creating-and-configuring-type-members.md#create-members)<br />- [Upravit členy typu](creating-and-configuring-type-members.md#modify-type-members)<br />- [Přidat parametry do metod](creating-and-configuring-type-members.md#add-parameters-to-methods)|

## <a name="open-the-class-details-window"></a>Otevření okna podrobností třídy

Ve výchozím nastavení se okno **podrobností třídy** zobrazí automaticky při otevření nového diagramu třídy. Viz [Postupy: Přidání diagramů tříd do projektů](how-to-add-class-diagrams-to-projects.md)). Okno **podrobností třídy** lze také otevřít následujícími způsoby:

- Kliknutím pravým tlačítkem myši na libovolnou třídu v diagramu zobrazte kontextovou nabídku a pak vyberte **Podrobnosti třídy**.

- V řádku nabídek vyberte možnost **Zobrazit**  >  **Další**  >  **Podrobnosti o třídě** Windows.

## <a name="create-members"></a>Vytvoření členů

Člen můžete vytvořit pomocí libovolného z následujících nástrojů:

- **Návrhář tříd**

- Panel nástrojů okna **podrobností třídy**

- Okno **podrobností třídy**

> [!NOTE]
> Pomocí postupů v tomto oddíle můžete také vytvořit konstruktory a destruktory. Pamatujte na to, že konstruktory a destruktory jsou zvláštní druhy metod a jako takové se zobrazí v oddílu **metody** ve tvarech diagramů tříd a v části **metody** v mřížce okna **podrobností třídy** .

> [!NOTE]
> Parametr je jediná entita, kterou můžete přidat k delegátu. Všimněte si, že procedura s názvem pro vytvoření člena pomocí panelu nástrojů okna **podrobností třídy** není pro tuto akci platná.

### <a name="create-a-member-using-class-designer"></a>Vytvoření člena pomocí Návrhář tříd

1. Klikněte pravým tlačítkem na typ, ke kterému chcete přidat člena, přejděte na **Přidat** a pak vyberte typ člena, který chcete přidat.

     Vytvoří se nový podpis člena a přidá se k typu. Je mu přiřazen výchozí název, který lze změnit v **Návrhář tříd**, v okně **podrobností třídy** nebo v okně **vlastnosti** .

2. Volitelně můžete určit další detaily členu, například jeho typ.

### <a name="create-a-member-using-the-class-details-window-toolbar"></a>Vytvoření členu pomocí panelu nástrojů okna podrobností třídy

1. Na ploše diagramu vyberte typ, ke kterému chcete přidat člen.

     Typ získá fokus a jeho obsah se zobrazí v okně **podrobností třídy** .

2. Na panelu nástrojů okna **podrobností třídy** klikněte na ikonu shora a v rozevíracím seznamu vyberte **nový \<member>** .

     Kurzor se přesune do pole **název** v řádku pro druh člena, který chcete přidat. Například pokud jste klikli na možnost **Nová vlastnost**, kurzor se přesune na nový řádek v oddílu **vlastnosti** okna **podrobností třídy** .

3. Zadejte název členu, který chcete vytvořit, a stiskněte klávesu Enter (nebo jinak přesuňte fokus, například stisknutím klávesy Tab).

     Vytvoří se nový podpis člena a přidá se k typu. Člen nyní existuje v kódu a zobrazí se v **Návrhář tříd**, v okně **podrobností třídy** a v okno Vlastnosti.

4. Volitelně můžete určit další detaily členu, například jeho typ.

### <a name="create-a-member-using-the-class-details-window"></a>Vytvoření člena pomocí okna podrobností třídy

1. Na ploše diagramu vyberte typ, ke kterému chcete přidat člen.

     Typ získá fokus a jeho obsah se zobrazí v okně **podrobností třídy** .

2. V okně **podrobností třídy** v části obsahující druh člena, který chcete přidat, klikněte na **\<add member>** . Například pokud chcete přidat pole, klikněte na **\<add field>** .

3. Zadejte název členu, který chcete vytvořit, a stiskněte klávesu Enter.

     Vytvoří se nový podpis člena a přidá se k typu. Člen nyní existuje v kódu a zobrazí se v **Návrhář tříd**, v okně **podrobností třídy** a v okno Vlastnosti.

4. Volitelně můžete určit další detaily členu, například jeho typ.

    > [!NOTE]
    > K vytvoření členů můžete také použít klávesové zkratky. Další informace naleznete v tématu [klávesové zkratky a zástupci myši v okně diagram tříd a podrobnosti třídy](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md).

## <a name="modify-type-members"></a>Upravit členy typu

V Návrháři tříd můžete upravit členy typů, které se zobrazí v diagramu. Můžete upravit členy libovolného typu, které se zobrazí v diagramu třídy a nejsou jen pro čtení. Členy typu lze upravit pomocí místních úprav na návrhové ploše, okno Vlastnosti a okně **podrobností třídy** .

Všichni členové zobrazení v okně **podrobností třídy** reprezentují členy typů v diagramu tříd. Existují čtyři typy členů: metody, vlastnosti, pole a události.

Všechny řádky členů jsou zobrazeny pod nadpisy, které je seskupují podle druhu. Například všechny vlastnosti se zobrazí pod **vlastnostmi** záhlaví, které mohou být jako uzel v mřížce sbaleny nebo rozbaleny.

Každý řádek členu zobrazuje následující prvky:

- **Ikona člena**

     Každý druh členu znázorňuje jeho vlastní ikona. Najeďte myší na ikonu členu, aby se zobrazil podpis člena. Kliknutím na ikonu členu nebo na prázdné znaky vlevo od ikony členu vyberete řádek.

- **Název členu**

     Sloupec **název** na řádku člena zobrazuje název člena. Tento název se zobrazí také ve vlastnosti **název** v okno Vlastnosti. Tuto buňku můžete použít ke změně názvu jakéhokoli členu, který má oprávnění pro čtení i zápis.

     Pokud je sloupec **název** příliš úzký, aby se zobrazil celý název, nasměrováním myši na název člena zobrazíte celý název.

- **Typ členu**

     Buňka **MemberType** používá technologii IntelliSense, která umožňuje vybrat ze seznamu všech typů dostupných v aktuálním projektu nebo v odkazovaných projektech.

- **Modifikátor členu**

     Změňte modifikátor viditelnosti člena na hodnotu `Public` ( `public` ), `Private` ( `private` ), `Friend` ( `internal` ) () `Protected` `protected` , `Protected Friend` ( `protected internal` ), nebo `Default` .

- **\<add member>**

     Poslední řádek v okně **podrobností třídy** obsahuje text **\<add member>** v buňce **název** . Pokud na tuto buňku klikněte, můžete vytvořit nový člen. Další informace najdete v tématu [Vytvoření členů](creating-and-configuring-type-members.md#create-members).

- **Vlastnosti člena v okno Vlastnosti**

     V okně **podrobností třídy** se zobrazí podmnožina vlastností členů, které jsou zobrazeny v okno Vlastnosti. Změna vlastnosti na jednom místě aktualizuje hodnotu vlastnosti globálně. Aktualizuje se i zobrazení hodnoty členu v jiném umístění.

- **Souhrn**

     Buňka **summary** zpřístupňuje shrnutí informací o členovi. Kliknutím na tlačítko se třemi tečkami v buňce **Souhrn** zobrazíte nebo upravíte informace o **souhrnu**, **návratovém typu** a **komentáři** člena.

- **Skrýt**

     Pokud je zaškrtnuto políčko **Skrýt** , člen se nezobrazí v typu.

### <a name="to-modify-a-type-member"></a>Změna členu typu

1. Pomocí Návrháře tříd vyberte typ.

2. Pokud se okno **podrobností třídy** nezobrazí, klikněte na tlačítko okna **podrobností třídy** na panelu nástrojů návrhář tříd.

3. Upravte hodnoty v polích v mřížce okna **podrobností třídy** . Po každé úpravě stiskněte klávesu ENTER nebo jinak přesuňte fokus z upravovaného pole, například stisknutím klávesy TAB. Úpravy se v kódu projeví okamžitě.

    > [!NOTE]
    > Pokud chcete změnit pouze název členu, můžete to provést úpravou na místě.

## <a name="add-parameters-to-methods"></a>Přidat parametry do metod

Přidejte parametry do metod pomocí okna **podrobností třídy** . Parametry lze konfigurovat jako povinné, či volitelné. Poskytnutí hodnoty pro **volitelnou výchozí** vlastnost parametru instruuje návrháře, aby vygeneroval kód jako volitelný parametr.

Řádky parametru obsahují následující položky:

- **Název**

     Sloupec **název** v řádku parametrů zobrazuje název parametru. Tento název se zobrazí také ve vlastnosti **název** v okno Vlastnosti. Tuto buňku můžete použít ke změně názvu jakéhokoli parametru, který má oprávnění pro čtení i zápis.

     Pokud je sloupec **název** příliš úzký, aby se zobrazil celý název, ukazatel na název parametru zobrazí název parametru.

- **Typ**

     Buňka **typu parametru** používá technologii IntelliSense, která umožňuje vybrat ze seznamu všech typů dostupných v aktuálním projektu nebo v odkazovaných projektech.

- **Upravující**

     Buňka **modifikátoru** v řádku parametrů přijímá a zobrazuje nový modifikátor parametru. Chcete-li zadat nový modifikátor parametru, použijte rozevírací seznam k výběru z **žádného**, **ref**, **out** nebo **params** v jazyce C# a **ByVal**, **ByRef** nebo **ParamArray** v jazyce VB.

- **Souhrn**

     Buňka **summary** v řádku parametrů umožňuje zadání komentářů kódu, které se zobrazí v technologii IntelliSense při zadání parametru do editoru kódu.

- **\<add parameter>**

     Poslední řádek parametru členu obsahuje text<v buňce **název** **Přidat parametr \>** . Kliknutím na tuto buňku vytvoříte nový parametr. Další informace naleznete v tématu [Přidání parametru do metody](creating-and-configuring-type-members.md#add-parameters-to-methods).

V okně **vlastnosti** se zobrazí stejné vlastnosti parametrů, které se zobrazují v okně **podrobností třídy** : **název**, **typ**, **Modifikátor**, **Souhrn** a také **volitelná výchozí** vlastnost. Změnou vlastnosti na jednom místě aktualizujete hodnotu vlastnosti globálně, včetně zobrazení hodnoty v jiném umístění.

> [!NOTE]
> Chcete-li přidat parametr delegáta, přečtěte si téma [Create Members](creating-and-configuring-type-members.md#create-members).

> [!NOTE]
> Ačkoli je destruktor metoda, nemůže mít parametry.

### <a name="to-add-a-parameter-to-a-method"></a>Přidání parametru do metody

1. Na ploše diagramu klikněte na typ obsahující metodu, ke které chcete přidat parametr.

     Typ získá fokus a jeho obsah se zobrazí v okně **podrobností třídy** .

2. V okně **podrobností třídy** rozbalte řádek metody, do které chcete přidat parametr.

     Zobrazí se řádek s odsazeným parametrem obsahující pouze dvojici závorek a slov **\<add parameter> .**

3. Klikněte na **\<add parameter>** , zadejte název nového parametru a stiskněte klávesu **ENTER**.

     Nový parametr je přidán do metody a kódu metody. Zobrazuje se v okně **podrobností třídy** a okno Vlastnosti.

4. Volitelně můžete určit další detaily parametru, například jeho typ.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Přidání volitelného parametru do metody

1. Na ploše diagramu klikněte na typ obsahující metodu, ke které chcete přidat volitelný parametr.

     Typ získá fokus a jeho obsah se zobrazí v okně **podrobností třídy** .

2. V okně **podrobností třídy** rozbalte řádek metody, do které chcete přidat volitelný parametr.

     Zobrazí se řádek s odsazeným parametrem obsahující pouze dvojici závorek a slov **\<add parameter> .**

3. Klikněte na **\<add parameter>** , zadejte název nového parametru a stiskněte klávesu **ENTER**.

     Nový parametr je přidán do metody a kódu metody. Zobrazuje se v okně **podrobností třídy** a okno Vlastnosti.

4. Do okno Vlastnosti zadejte hodnotu pro **volitelnou výchozí** vlastnost. Nastavením vlastnosti Volitelné výchozí nastavíte daný parametr na volitelný.

    > [!NOTE]
    > Volitelné parametry musí být posledními parametry v seznamu parametrů.

## <a name="class-details-usage-notes"></a>Poznámky k využití podrobností třídy

Při používání okna **podrobností třídy** si prosím přečtěte následující tipy.

### <a name="editable-and-non-editable-cells"></a>Editovatelné a needitovatelné buňky

Všechny buňky v okně **podrobností třídy** jsou editovatelné s několika výjimkami:

- Celý typ je jen pro čtení, pokud se například nachází v odkazovaném sestavení. Když vyberete tvar v Návrhář tříd, okno **podrobností třídy** zobrazí jeho podrobnosti ve stavu jen pro čtení.

- V případě indexerů je název jen pro čtení a zbytek (typ, modifikátor, shrnutí) je editovatelný.

- Všechny obecné typy mají v okně **podrobností třídy** parametry jen pro čtení. Chcete-li změnit obecný parametr, upravte jeho zdrojový kód.

- Název parametru typu, který je definován na obecném typu, je jen pro čtení.

- Když je kód typu porušen (nelze jej analyzovat), okno **podrobností třídy** zobrazí obsah typu jen pro čtení.

### <a name="the-class-details-window-and-source-code"></a>Okno podrobností třídy a zdrojový kód

- Můžete zobrazit zdrojový kód tak, že kliknete pravým tlačítkem myši na tvar v okně **podrobností třídy** (nebo Návrhář tříd) a potom kliknete na Zobrazit kód. Otevře se soubor zdrojového kódu a zobrazení se posune na vybraný prvek.

- Změna zdrojového kódu se okamžitě projeví v zobrazení informací o podpisu v okně Návrhář tříd a v okně **podrobností třídy** . Pokud je okno **podrobností třídy** zavřeno v čase, nové informace se zobrazí při příštím otevření.

- Když je kód typu porušen (nelze jej analyzovat), okno **podrobností třídy** zobrazí obsah typu jen pro čtení.

### <a name="clipboard-functionality-in-the-class-details-window"></a>Funkce schránky v okně podrobností třídy

Můžete kopírovat nebo vyjmout pole nebo řádky z okna **podrobností třídy** a vložit je do jiného typu. Řádek můžete vyjmout, pouze pokud je jen pro čtení. Když vložíte řádek, okno **podrobností třídy** přiřadí nový název (odvozený od názvu kopírovaného řádku), aby se předešlo konfliktu.

## <a name="display-of-read-only-information"></a>Zobrazení informací jen pro čtení

Návrhář tříd a okno **podrobností třídy** může zobrazit typy (a členy typů) pro následující:

- projekt, který obsahuje diagram třídy

- projekt odkazovaný z projektu, který obsahuje diagram třídy

- sestavení odkazované z projektu, který obsahuje diagram třídy

V posledních dvou případech je odkazovaná entita (typ nebo člen) v diagramu tříd, který ji reprezentuje, jen pro čtení.

Celý projekt nebo jeho části, například jednotlivé soubory, mohou být jen pro čtení. Většina běžných případů, ve kterých projekt nebo jeden z jeho souborů, je jen pro čtení, jsou takové, kdy se projekt nachází v rámci správy zdrojového kódu (a není rezervován), existuje v externím sestavení nebo když operační systém považuje soubory za soubory jen pro čtení.

**Správa zdrojového kódu**

Vzhledem k tomu, že diagram tříd je uložen jako soubor v projektu, je nutné projekt rezervovat, aby bylo možné uložit všechny změny, které provedete v Návrhář tříd nebo okně **podrobností třídy** .

**Projekty jen pro čtení**

Projekt může být jen pro čtení z jiného důvodu než pro správu zdrojového kódu. Při zavření projektu se zobrazí dialogové okno s dotazem, zda přepsat soubor projektu, zrušit změny (Neukládat) nebo zrušit operaci Zavřít. Pokud zvolíte přepsání, soubory projektu jsou přepsány a nastaveny pro čtení i zápis. Je přidán nový soubor diagramu tříd.

**Typy jen pro čtení**

Pokud se pokusíte uložit projekt obsahující typ, jehož soubor zdrojového kódu je jen pro čtení, zobrazí se dialogové okno **uložit Read-Only soubor** , které vám nabídne možnost Uložit soubor pod novým názvem nebo novým umístěním, nebo přepsat soubor, který je jen pro čtení. Pokud soubor přepíšete, nová kopie již není jen pro čtení.

Pokud soubor s kódem obsahuje chybu syntaxe, tvary zobrazující kód v daném souboru budou dočasně jen pro čtení, dokud chyba syntaxe nebude opravena. Tvary v tomto stavu zobrazí červený text a červenou ikonu, která zobrazí popisek s textem „Soubor zdrojového kódu obsahuje chybu analýzy“.

Odkazovaný typ (například typ .NET), který existuje v jiném uzlu projektu nebo v uzlu odkazovaného sestavení, je uveden na Návrhář tříd návrhové ploše jako jen pro čtení. Místní typ, který existuje v projektu, jež chcete otevřít, je pro čtení i zápis a jeho tvar na návrhové ploše Návrháře tříd je takto označen.

Indexery jsou pro čtení i zápis v kódu a v okně **podrobností třídy** , ale název indexeru je jen pro čtení.

Nemůžete upravit částečné metody pomocí Návrhář tříd nebo okna **podrobností třídy** ; k jejich úpravě je nutné použít Editor kódu.

Nativní kód jazyka C++ nelze upravovat pomocí Návrhář tříd nebo okna **podrobností třídy** . pro úpravu nativního kódu jazyka C++ je nutné použít Editor kódu.

## <a name="see-also"></a>Viz také

- [Zobrazení typů a vztahů](designing-and-viewing-classes-and-types.md)
- [Refaktoring tříd a typů](refactoring-classes-and-types.md)
