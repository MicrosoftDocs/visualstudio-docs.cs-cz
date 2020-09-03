---
title: Vytváření a konfigurace členů typu (Návrhář tříd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b871c406b0a2b36d1e7f02a070ab1052510ed20b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619236"
---
# <a name="creating-and-configuring-type-members-class-designer"></a>Vytváření a konfigurace členů typů (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tyto členy můžete přidat do typů v diagramu tříd a nakonfigurovat je v okně **podrobností třídy** :

|**Typ**|**Členy, které může obsahovat**|
|--------------|--------------------------------|
|Třída|metoda, vlastnost (pro C# a Visual Basic), pole, událost (pro C# a Visual Basic), konstruktor (metoda), konstruktor (metoda), konstanta|
|Výčet|člen|
|Rozhraní|metoda, vlastnost, událost (pro C# a Visual Basic)|
|Abstraktní třída|metoda, vlastnost (pro C# a Visual Basic), pole, událost (pro C# a Visual Basic), konstruktor (metoda), konstruktor (metoda), konstanta|
|Struktura (struktura v jazyce C#)|metoda, vlastnost (pro C# a Visual Basic), pole, událost (pro C# a Visual Basic), konstruktor (metoda), konstanta|
|Delegát|Parametr|
|Modul (pouze VB)|metoda, vlastnost, pole, událost, konstruktor, konstanta|

> [!NOTE]
> Když přístupové objekty get a set nepotřebují další logiku, můžete deklaraci vlastnosti zestručnit pomocí automaticky implementovaných vlastností (pouze jazyk C#). Chcete-li zobrazit úplný podpis, z nabídky **Diagram tříd** vyberte možnost **změnit formát členů**, **Zobrazit úplný podpis**. Další informace o automaticky implementovaných vlastnostech naleznete v tématu [automaticky implementované vlastnosti](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7).

## <a name="common-tasks"></a>Obecné úlohy

|Úkol|Podpůrný obsah|
|----------|------------------------|
|**Začínáme:** Předtím, než vytvoříte a nakonfigurujete členy typu, je nutné otevřít okno podrobností třídy.|-   [Otevření Okno podrobností třídy](../ide/creating-and-configuring-type-members-class-designer.md#OpenClassDetails)<br />-   [Poznámky k využití podrobností třídy](../ide/creating-and-configuring-type-members-class-designer.md#ClassDetailsUsageNotes)<br />-   [Zobrazení informací jen pro čtení](../ide/creating-and-configuring-type-members-class-designer.md#ReadOnlyInfo)<br />-   [Klávesové zkratky a zkratky myši v diagramu tříd a Okno podrobností třídy (Návrhář tříd)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md)|
|**Vytvoření a úprava členů typu:** Můžete vytvořit nové členy, upravit členy a přidat parametry do metody pomocí okna podrobností třídy.|-   [Vytváření členů](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers)<br />-   [Úprava členů typu](../ide/creating-and-configuring-type-members-class-designer.md#ModifyTypeMembers)<br />-   [Přidávání parametrů do metod](../ide/creating-and-configuring-type-members-class-designer.md#AddMethodParams)|

## <a name="opening-the-class-details-window"></a><a name="OpenClassDetails"></a> Otevření Okno podrobností třídy
 Ve výchozím nastavení se Okno podrobností třídy automaticky zobrazí při otevření nového diagramu třídy (viz [Postup: Přidání diagramů tříd do projektů (návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)). Okno podrobností třídy můžete také otevřít explicitně následujícími způsoby.

#### <a name="to-open-the-class-details-window"></a>Otevření okna podrobností třídy

1. Kliknutím pravým tlačítkem myši na libovolnou třídu v diagramu zobrazte kontextovou nabídku.

2. V místní nabídce klikněte na **okno podrobností třídy**.

   – nebo -

- V nabídce zobrazení přejděte na **Další okna** a pak klikněte na **Podrobnosti třídy**.

## <a name="creating-members"></a><a name="CreateMembers"></a> Vytváření členů
 Člen můžete vytvořit pomocí libovolného z následujících nástrojů:

- Návrhář tříd

- Panel nástrojů okno podrobností třídy

- Okno podrobností třídy

> [!NOTE]
> Pomocí postupů v tomto oddíle můžete také vytvořit konstruktory a destruktory. Pamatujte na to, že konstruktory a destruktory jsou zvláštní druhy metod a jako takové se zobrazí v oddílu **metody** ve tvarech diagramů tříd a v části **metody** v mřížce okna podrobností třídy.

> [!NOTE]
> Parametr je jediná entita, kterou můžete přidat k delegátu. Upozorňujeme, že postup s názvem „Vytvoření členu pomocí panelu nástrojů okna podrobností třídy“ není pro tuto akci platný.

#### <a name="to-create-a-member-using-class-designer"></a>Vytvoření členu pomocí Návrháře třídy

1. Klikněte pravým tlačítkem na typ, ke kterému chcete přidat člena, přejděte na **Přidat**a pak vyberte typ člena, který chcete přidat.

     Vytvoří se nový podpis člena a přidá se k typu. Je mu přiřazen výchozí název, který lze změnit v **Návrhář tříd**, v okně **podrobností třídy** nebo v okně **vlastnosti** .

2. Volitelně můžete určit další detaily členu, například jeho typ.

#### <a name="to-create-a-member-using-the-class-details-window-toolbar"></a>Vytvoření členu pomocí panelu nástrojů okna podrobností třídy

1. Na ploše diagramu vyberte typ, ke kterému chcete přidat člen.

     Typ získá fokus a jeho obsah se zobrazí v okně podrobností třídy.

2. Na panelu nástrojů okna podrobností třídy klikněte na ikonu shora a v rozevíracím seznamu vyberte **nový \<member> ** .

     Kurzor se přesune do pole **název** v řádku pro druh člena, který chcete přidat. Například pokud jste klikli na možnost **Nová vlastnost**, kurzor se přesune na nový řádek v oddílu **vlastnosti** okna podrobností třídy.

3. Zadejte název členu, který chcete vytvořit, a stiskněte klávesu Enter (nebo jinak přesuňte fokus, například stisknutím klávesy Tab).

     Vytvoří se nový podpis člena a přidá se k typu. Člen nyní existuje v kódu a zobrazí se v **Návrhář tříd**, v okně podrobností třídy a v okno Vlastnosti.

4. Volitelně můžete určit další detaily členu, například jeho typ.

#### <a name="to-create-a-member-using-the-class-details-window"></a>Vytvoření členu pomocí okna podrobností třídy

1. Na ploše diagramu vyberte typ, ke kterému chcete přidat člen.

     Typ získá fokus a jeho obsah se zobrazí v okně podrobností třídy.

2. V okně podrobností třídy v části obsahující druh člena, který chcete přidat, klikněte na **\<add member>** . Například pokud chcete přidat pole, klikněte na **\<add field>** .

3. Zadejte název členu, který chcete vytvořit, a stiskněte klávesu Enter.

     Vytvoří se nový podpis člena a přidá se k typu. Člen nyní existuje v kódu a zobrazí se v **Návrhář tříd**, v okně podrobností třídy a v okno Vlastnosti.

4. Volitelně můžete určit další detaily členu, například jeho typ.

     **Poznámka:** K vytvoření členů můžete také použít klávesové zkratky. Další informace naleznete v tématu [klávesové zkratky a zástupci myši v diagramu tříd a okno podrobností třídy (návrhář tříd)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md).

## <a name="modifying-type-members"></a><a name="ModifyTypeMembers"></a> Úprava členů typu
 V Návrháři tříd můžete upravit členy typů, které se zobrazí v diagramu. Můžete upravit členy libovolného typu, které se zobrazí v diagramu třídy a nejsou jen pro čtení. (Viz [zobrazení informací jen pro čtení (návrhář tříd)](https://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).) Členy typu lze upravit pomocí místních úprav na návrhové ploše, okno Vlastnosti a okně podrobností třídy.

 Všechny členy zobrazené v okně podrobností třídy představují členy typů v diagramu třídy. Existují čtyři typy členů: metody, vlastnosti, pole a události.

 Všechny řádky členů jsou zobrazeny pod nadpisy, které je seskupují podle druhu. Například všechny vlastnosti se zobrazí pod **vlastnostmi**záhlaví, které mohou být jako uzel v mřížce sbaleny nebo rozbaleny.

 Každý řádek členu zobrazuje následující prvky:

- **Ikona člena**

     Každý druh členu znázorňuje jeho vlastní ikona. Umístěním kurzoru myši na ikonu členu zobrazíte podpis členu. Kliknutím na ikonu členu nebo na prázdné znaky vlevo od ikony členu vyberete řádek.

- **Název členu**

     Sloupec **název** na řádku člena zobrazuje název člena. Tento název se zobrazí také ve vlastnosti **název** v okno Vlastnosti. Tuto buňku můžete použít ke změně názvu jakéhokoli členu, který má oprávnění pro čtení i zápis.

     Pokud je sloupec **název** příliš úzký, aby se zobrazil celý název, nasměrováním myši na název člena zobrazíte celý název.

- **Typ členu**

     Buňka **MemberType** používá technologii IntelliSense, která umožňuje vybrat ze seznamu všech typů dostupných v aktuálním projektu nebo v odkazovaných projektech.

- **Modifikátor členu**

     Změňte modifikátor viditelnosti člena na hodnotu `Public` ( `public` ), `Private` ( `private` ), `Friend` ( `internal` ) () `Protected` `protected` , `Protected``Friend` ( `protected``internal` ), nebo `Default` .

- **\<add member>**

     Poslední řádek v okně podrobností třídy obsahuje text **\<add member>** v buňce **název** . Pokud na tuto buňku klikněte, můžete vytvořit nový člen. Další informace najdete v tématu [vytváření členů](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).

- **Vlastnosti člena v okno Vlastnosti**

     Okno podrobností třídy zobrazuje podmnožinu vlastností členů, které jsou zobrazeny v okně Vlastnosti. Změna vlastnosti na jednom místě aktualizuje hodnotu vlastnosti globálně. Aktualizuje se i zobrazení hodnoty členu v jiném umístění.

- **Souhrn**

     Buňka **summary** zpřístupňuje shrnutí informací o členovi. Kliknutím na tlačítko se třemi tečkami v buňce **Souhrn** zobrazíte nebo upravíte informace o **souhrnu**, **návratovém typu**a **komentáři** člena.

- **Skrýt**

     Pokud je zaškrtnuto políčko **Skrýt** , člen se nezobrazí v typu.

#### <a name="to-modify-a-type-member"></a>Změna členu typu

1. Pomocí Návrháře tříd vyberte typ.

2. Pokud se okno podrobností třídy nezobrazí, klikněte na panelu nástrojů Návrhář tříd na tlačítko **okno podrobností třídy** .

3. Upravte hodnoty v polích v mřížce okno podrobností třídy. Po každé úpravě stiskněte klávesu ENTER nebo jinak přesuňte fokus z upravovaného pole, například stisknutím klávesy TAB. Úpravy se v kódu projeví okamžitě.

    > [!NOTE]
    > Pokud chcete změnit pouze název členu, můžete to provést úpravou na místě.

## <a name="adding-parameters-to-methods"></a><a name="AddMethodParams"></a> Přidávání parametrů do metod
 Přidání parametrů do metody pomocí okna podrobností třídy. Parametry lze konfigurovat jako povinné, či volitelné. Poskytnutí hodnoty pro **volitelnou výchozí** vlastnost parametru instruuje návrháře, aby vygeneroval kód jako volitelný parametr.

 Řádky parametru obsahují následující položky:

- **Name**

   Sloupec **název** v řádku parametrů zobrazuje název parametru. Tento název se zobrazí také ve vlastnosti **název** v okno Vlastnosti. Tuto buňku můžete použít ke změně názvu jakéhokoli parametru, který má oprávnění pro čtení i zápis.

   Pokud je sloupec **název** příliš úzký, aby se zobrazil celý název, ukazatel na název parametru zobrazí název parametru.

- **Typ**

   Buňka **typu parametru** používá technologii IntelliSense, která umožňuje vybrat ze seznamu všech typů dostupných v aktuálním projektu nebo v odkazovaných projektech.

- **Upravující**

   Buňka **modifikátoru** v řádku parametrů přijímá a zobrazuje nový modifikátor parametru. Chcete-li zadat nový modifikátor parametru, použijte rozevírací seznam k výběru z **žádného**, **ref**, **out**nebo **params** v jazyce C# a **ByVal**, **ByRef**nebo **ParamArray** v jazyce VB.

- **Souhrn**

   Buňka **summary** v řádku parametrů umožňuje zadání komentářů kódu, které se zobrazí v technologii IntelliSense při zadání parametru do editoru kódu.

- **\<add parameter>**

   Poslední řádek parametru členu obsahuje text<v buňce **název** **Přidat parametr \> ** . Kliknutím na tuto buňku vytvoříte nový parametr. Další informace naleznete v tématu [Přidání parametru do metody](../ide/creating-and-configuring-type-members-class-designer.md#HowToAddParameterToMethod).

  **Vlastnosti parametru v okno Vlastnosti**

  Okno Vlastnosti zobrazí stejné vlastnosti parametrů, které se zobrazují v okně podrobností třídy: **název**, **typ**, **Modifikátor**, **Souhrn**a také **volitelná výchozí** vlastnost. Změnou vlastnosti na jednom místě aktualizujete hodnotu vlastnosti globálně, včetně zobrazení hodnoty v jiném umístění.

> [!NOTE]
> Chcete-li přidat parametr delegáta, přečtěte si téma [Vytvoření členů](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).

> [!NOTE]
> Ačkoli je destruktor metoda, nemůže mít parametry.

### <a name="to-add-a-parameter-to-a-method"></a><a name="HowToAddParameterToMethod"></a> Přidání parametru do metody

1. Na ploše diagramu klikněte na typ obsahující metodu, ke které chcete přidat parametr.

     Typ získá fokus a jeho obsah se zobrazí v okně podrobností třídy.

2. V okně podrobností třídy rozbalte řádek metody, do které chcete přidat parametr.

     Zobrazí se řádek s odsazeným parametrem obsahující pouze dvojici závorek a slov ** \<add parameter> .**

3. Klikněte na **\<add parameter>** , zadejte název nového parametru a stiskněte klávesu **ENTER**.

     Nový parametr se přidá do metody a kódu metody. Zobrazí se v okně podrobností třídy a v okně Vlastnosti.

4. Volitelně můžete určit další detaily parametru, například jeho typ.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Přidání volitelného parametru do metody

1. Na ploše diagramu klikněte na typ obsahující metodu, ke které chcete přidat volitelný parametr.

     Typ získá fokus a jeho obsah se zobrazí v okně podrobností třídy.

2. V okně podrobností třídy rozbalte řádek metody, do které chcete přidat volitelný parametr.

     Zobrazí se řádek s odsazeným parametrem obsahující pouze dvojici závorek a slov ** \<add parameter> .**

3. Klikněte na **\<add parameter>** , zadejte název nového parametru a stiskněte klávesu **ENTER**.

     Nový parametr se přidá do metody a kódu metody. Zobrazí se v okně podrobností třídy a v okně Vlastnosti.

4. Do okno Vlastnosti zadejte hodnotu pro **volitelnou výchozí** vlastnost. Nastavením vlastnosti Volitelné výchozí nastavíte daný parametr na volitelný.

    > [!NOTE]
    > Volitelné parametry musí být posledními parametry v seznamu parametrů.

## <a name="class-details-usage-notes"></a><a name="ClassDetailsUsageNotes"></a> Poznámky k využití podrobností třídy
 Při používání okna podrobností třídy mějte prosím na paměti následující tipy.

 **Editovatelné a needitovatelné buňky**

 Všechny buňky v okně podrobností třídy jsou editovatelné, s několika výjimkami:

- Celý typ je jen pro čtení, pokud se například nachází v odkazovaném sestavení (viz [zobrazení informací jen pro čtení (návrhář tříd)](https://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).) Když vyberete tvar v Návrhář tříd, okno podrobností třídy zobrazí jeho podrobnosti ve stavu jen pro čtení.

- V případě indexerů je název jen pro čtení a zbytek (typ, modifikátor, shrnutí) je editovatelný.

- V okně podrobností třídy mají všechny obecné typy parametry jen pro čtení. Chcete-li změnit obecný parametr, upravte jeho zdrojový kód.

- Název parametru typu, který je definován na obecném typu, je jen pro čtení.

- Když je kód typu porušen (nelze jej analyzovat), okno podrobností třídy zobrazí obsah typu jen pro čtení.

  **Okno podrobností třídy a zdrojový kód**

- Kliknutím pravým tlačítkem myši na tvar v okně podrobností třídy (nebo Návrhář tříd) a následným kliknutím na příkaz Zobrazit kód můžete zobrazit zdrojový kód. Otevře se soubor zdrojového kódu a zobrazení se posune na vybraný prvek.

- Změna zdrojového kódu se okamžitě projeví v zobrazení informací podpisu v okně Návrhář třídy a Podrobnosti třídy. Pokud je okno podrobností třídy v daném okamžiku zavřeno, nové informace se zobrazí při příštím otevření okna.

- Když je kód typu porušen (nelze jej analyzovat), okno podrobností třídy zobrazí obsah typu jen pro čtení.

  **Funkce schránky v Okno podrobností třídy**

  Z okna podrobností třídy můžete kopírovat nebo vyjímat pole či řádky a vkládat je do jiného typu. Řádek můžete vyjmout, pouze pokud je jen pro čtení. Po vložení řádku okno podrobností třídy přiřadí nový název (odvozený od názvu zkopírovaného řádku), aby nedošlo ke konfliktu.

## <a name="display-of-read-only-information"></a><a name="ReadOnlyInfo"></a> Zobrazení informací jen pro čtení
 Návrhář tříd a okno podrobností třídy mohou zobrazit typy (a členy typů) pro:

- projekt, který obsahuje diagram třídy

- projekt odkazovaný z projektu, který obsahuje diagram třídy

- sestavení odkazované z projektu, který obsahuje diagram třídy

  V posledních dvou případech je odkazovaná entita (typ nebo člen) v diagramu tříd, který ji reprezentuje, jen pro čtení.

  Celý projekt nebo jeho části, například jednotlivé soubory, mohou být jen pro čtení. Většina běžných případů, ve kterých projekt nebo jeden z jeho souborů, je jen pro čtení, jsou takové, kdy se projekt nachází v rámci správy zdrojového kódu (a není rezervován), existuje v externím sestavení nebo když operační systém považuje soubory za soubory jen pro čtení.

  **Správa zdrojového kódu**

  Protože diagram tříd je uložen jako soubor v projektu, je třeba projekt rezervovat, aby se uložily všechny změny, které provedete v okně Návrhář tříd nebo okně podrobností třídy.

  **Projekty jen pro čtení**

  Projekt může být jen pro čtení z jiného důvodu než pro správu zdrojového kódu. Při zavírání projektu se zobrazí dialogové okno s dotazem, zda chcete přepsat soubor projektu, zahodit změny (bez uložení) nebo zrušit operaci zavření. Pokud zvolíte přepsání, soubory projektu jsou přepsány a nastaveny pro čtení i zápis. Je přidán nový soubor diagramu tříd.

  **Typy jen pro čtení**

  Pokud se pokusíte uložit projekt obsahující typ, jehož soubor zdrojového kódu je jen pro čtení, zobrazí se dialogové okno **uložení souboru jen pro čtení** , které vám umožní soubor uložit pod novým názvem nebo novým umístěním, nebo přepsat soubor, který je jen pro čtení. Pokud soubor přepíšete, nová kopie již není jen pro čtení.

  Pokud soubor s kódem obsahuje chybu syntaxe, tvary zobrazující kód v daném souboru budou dočasně jen pro čtení, dokud chyba syntaxe nebude opravena. Tvary v tomto stavu zobrazí červený text a červenou ikonu, která zobrazí popisek s textem „Soubor zdrojového kódu obsahuje chybu analýzy“.

  Odkazovaný typ (například typ rozhraní .NET Framework), který existuje v rámci jiného uzlu projektu nebo uzlu odkazovaného sestavení, je na návrhové ploše Návrháře tříd uveden jako jen pro čtení. Místní typ, který existuje v projektu, jež chcete otevřít, je pro čtení i zápis a jeho tvar na návrhové ploše Návrháře tříd je takto označen.

  Indexery jsou pro čtení i zápis v kódu a v okně podrobností třídy, ale název indexeru je jen pro čtení.

  Částečné metody nelze upravovat pomocí Návrháře tříd nebo v okně podrobností třídy; k úpravám je nutné použít Editor kódu.

  Nativní kód C++ nelze upravovat pomocí Návrháře tříd nebo v okně podrobností třídy; k úpravám je nutné použít Editor kódu.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Zobrazování typů a vztahů (Návrhář tříd)](../ide/viewing-types-and-relationships-class-designer.md)|Existující typy, členy a vztahy můžete zobrazit v diagramu třídy.|
|[Refaktoring tříd a typů (Návrhář tříd)](../ide/refactoring-classes-and-types-class-designer.md)|Pomocí refaktoringu můžete snadno přejmenovat typ a členy typu. Můžete také přesunovat členy mezi třídami, rozdělit třídu na částečné třídy a implementovat rozhraní.|