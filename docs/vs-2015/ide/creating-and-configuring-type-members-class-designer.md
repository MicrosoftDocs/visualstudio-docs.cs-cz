---
title: Vytvoření a konfigurace členů typů (návrhář tříd) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93a112fac274921fe2d1075e1a1b9178c408240c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827971"
---
# <a name="creating-and-configuring-type-members-class-designer"></a>Vytváření a konfigurace členů typů (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete přidat tyto členy typů pro třídu diagramu a konfigurovat je v **podrobností třídy** okno:  
  
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
>  Když přístupové objekty get a set nepotřebují další logiku, můžete deklaraci vlastnosti zestručnit pomocí automaticky implementovaných vlastností (pouze jazyk C#). Chcete-li zobrazit úplný podpis z **Diagram tříd** nabídce zvolte **změnit formát členů**, **zobrazit úplný podpis**. Další informace o automaticky implementovaných vlastnostech naleznete v tématu [implemented Properties](http://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7).  
  
## <a name="common-tasks"></a>Obecné úlohy  
  
|Úloha|Podpůrný obsah|  
|----------|------------------------|  
|**Začínáme:** předtím, než vytvoříte a nakonfigurujete členy typů, je nutné otevřít okno podrobností třídy.|-   [Otevření okna podrobností třídy](../ide/creating-and-configuring-type-members-class-designer.md#OpenClassDetails)<br />-   [Poznámky k použití okna podrobností třídy](../ide/creating-and-configuring-type-members-class-designer.md#ClassDetailsUsageNotes)<br />-   [Zobrazení informací jen pro čtení](../ide/creating-and-configuring-type-members-class-designer.md#ReadOnlyInfo)<br />-   [Klávesové zkratky a zkratky myši v diagramu tříd a okně podrobností třídy (návrhář tříd)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md)|  
|**Vytvoření a úpravy členů typů:** můžete vytvořit nové členy, měnit členy a přidání parametrů do metody pomocí okna podrobností třídy.|-   [Vytváření členů](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers)<br />-   [Změna členů typů](../ide/creating-and-configuring-type-members-class-designer.md#ModifyTypeMembers)<br />-   [Přidávání parametrů k metodám](../ide/creating-and-configuring-type-members-class-designer.md#AddMethodParams)|  
  
##  <a name="OpenClassDetails"></a> Otevření okna podrobností třídy  
 Ve výchozím nastavení, v okně podrobností třídy zobrazí automaticky při otevření nový diagram tříd (viz [postupy: Přidání diagramů tříd do projektů (návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)). Okno podrobností třídy můžete také otevřít explicitně následujícími způsoby.  
  
#### <a name="to-open-the-class-details-window"></a>Otevření okna podrobností třídy  
  
1. Klikněte pravým tlačítkem na jakékoli třídy v diagramu na zobrazení místní nabídky.  
  
2. V místní nabídce klikněte na tlačítko **okno podrobností třídy**.  
  
   – nebo -  
  
-   Přejděte na **ostatní Windows** v nabídce zobrazení a pak klikněte na tlačítko **podrobností třídy**.  
  
##  <a name="CreateMembers"></a> Vytváření členů  
 Člen můžete vytvořit pomocí libovolného z následujících nástrojů:  
  
-   Návrhář tříd  
  
-   Panel nástrojů okno podrobností třídy  
  
-   Okno podrobností třídy  
  
> [!NOTE]
>  Pomocí postupů v tomto oddíle můžete také vytvořit konstruktory a destruktory. Nezapomínejte, že konstruktory a destruktory jsou zvláštní druhy metod a jako takové se zobrazují v **metody** ve tvarech diagramu třídy a v oddílu **metody** sekce třídy V mřížce okno podrobností.  
  
> [!NOTE]
>  Parametr je jediná entita, kterou můžete přidat k delegátu. Upozorňujeme, že postup s názvem „Vytvoření členu pomocí panelu nástrojů okna podrobností třídy“ není pro tuto akci platný.  
  
#### <a name="to-create-a-member-using-class-designer"></a>Vytvoření členu pomocí Návrháře třídy  
  
1.  Klikněte pravým tlačítkem na typ, ke kterému chcete přidat člen, přejděte na **přidat**a pak zvolte typ člena, které chcete přidat.  
  
     Vytvoří se nový podpis člena a přidá se k typu. Se klíči přiřadí výchozí název, který můžete změnit v **návrhář tříd**, **podrobností třídy** okna, nebo **vlastnosti** okna.  
  
2.  Volitelně můžete určit další detaily členu, například jeho typ.  
  
#### <a name="to-create-a-member-using-the-class-details-window-toolbar"></a>Vytvoření členu pomocí panelu nástrojů okna podrobností třídy  
  
1.  Na ploše diagramu vyberte typ, ke kterému chcete přidat člen.  
  
     Typ získá fokus a jeho obsah se zobrazí v okně podrobností třídy.  
  
2.  V panelu nástrojů okna podrobností třídy klikněte na ikonu nahoře a vyberte **nový \<člena >** z rozevíracího seznamu.  
  
     Kurzor se přesune **název** pole na řádek pro typ členu, které chcete přidat. Například, pokud jste klikli na **novou vlastnost**, kurzor se přesune na nový řádek v **vlastnosti** části okna podrobností třídy.  
  
3.  Zadejte název členu, který chcete vytvořit, a stiskněte klávesu Enter (nebo jinak přesuňte fokus, například stisknutím klávesy Tab).  
  
     Vytvoří se nový podpis člena a přidá se k typu. Člen nyní existuje v kódu a zobrazí se v **návrhář tříd**, v okně podrobností třídy nebo v okně Vlastnosti.  
  
4.  Volitelně můžete určit další detaily členu, například jeho typ.  
  
#### <a name="to-create-a-member-using-the-class-details-window"></a>Vytvoření členu pomocí okna podrobností třídy  
  
1.  Na ploše diagramu vyberte typ, ke kterému chcete přidat člen.  
  
     Typ získá fokus a jeho obsah se zobrazí v okně podrobností třídy.  
  
2.  V okně podrobností třídy v oddílu, který obsahuje typ členu, které chcete přidat, klikněte na tlačítko  **\<přidat člen >**. Například pokud chcete přidat pole, klikněte na možnost  **\<přidat pole >**.  
  
3.  Zadejte název členu, který chcete vytvořit, a stiskněte klávesu Enter.  
  
     Vytvoří se nový podpis člena a přidá se k typu. Člen nyní existuje v kódu a zobrazí se v **návrhář tříd**, v okně podrobností třídy nebo v okně Vlastnosti.  
  
4.  Volitelně můžete určit další detaily členu, například jeho typ.  
  
     **Poznámka:** klávesové zkratky můžete také použít k vytváření členů. Další informace najdete v tématu [klávesové zkratky a zkratky myši v diagramu tříd a okně podrobností třídy (návrhář tříd)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md).  
  
##  <a name="ModifyTypeMembers"></a> Změna členů typů  
 V Návrháři tříd můžete upravit členy typů, které se zobrazí v diagramu. Můžete upravit členy libovolného typu, které se zobrazí v diagramu třídy a nejsou jen pro čtení. (Viz [zobrazení informací jen pro čtení (návrhář tříd)](http://msdn.microsoft.com/en-us/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).) Členy typu změníte úpravou na místě na návrhové ploše, v okně Vlastnosti a v okně podrobností třídy  
  
 Všechny členy zobrazené v okně podrobností třídy představují členy typů v diagramu třídy. Existují čtyři typy členů: metody, vlastnosti, pole a události.  
  
 Všechny řádky členů jsou zobrazeny pod nadpisy, které je seskupují podle druhu. Například všechny vlastnosti se zobrazí pod nadpisem **vlastnosti**, který lze jako uzel v mřížce rozbalit nebo sbalit.  
  
 Každý řádek členu zobrazuje následující prvky:  
  
-   **Ikona členu**  
  
     Každý druh členu znázorňuje jeho vlastní ikona. Umístěním kurzoru myši na ikonu členu zobrazíte podpis členu. Kliknutím na ikonu členu nebo na prázdné znaky vlevo od ikony členu vyberete řádek.  
  
-   **Název člena**  
  
     **Název** sloupců na řádku členu zobrazí název členu. Tento název se také zobrazí v **název** vlastností v okně Vlastnosti. Tuto buňku můžete použít ke změně názvu jakéhokoli členu, který má oprávnění pro čtení i zápis.  
  
     Pokud **název** sloupec je příliš úzký, aby se zobrazil celý název, umístěním kurzoru myši na název členu zobrazíte celý název.  
  
-   **Typ člena**  
  
     **MemberType** buňky používá technologii IntelliSense, které lze vybrat ze seznamu všech typů dostupných v aktuálním projektu nebo v odkazovaných projektech.  
  
-   **Modifikátor členu**  
  
     Změňte viditelnost Modifikátor členu na buď `Public` (`public`), `Private` (`private`), `Friend` (`internal`) `Protected` (`protected`), `Protected``Friend` (`protected``internal`), nebo `Default`.  
  
-   **\<Přidat člena >**  
  
     Poslední řádek v okně podrobností třídy obsahuje text  **\<přidat člen >** v **název** buňky. Pokud na tuto buňku klikněte, můžete vytvořit nový člen. Další informace najdete v tématu [vytváření členů](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).  
  
-   **Vlastnosti členu v okně Vlastnosti**  
  
     Okno podrobností třídy zobrazuje podmnožinu vlastností členů, které jsou zobrazeny v okně Vlastnosti. Změna vlastnosti na jednom místě aktualizuje hodnotu vlastnosti globálně. Aktualizuje se i zobrazení hodnoty členu v jiném umístění.  
  
-   **Shrnutí**  
  
     **Souhrnu** buňky uvádí souhrnné informace o členu. Klikněte na tlačítko se třemi tečkami v **Souhrn** buněk k zobrazení nebo upravte informace o **Souhrn**, **návratový typ**, a **poznámky** pro člena .  
  
-   **Skrýt**  
  
     Když **skrýt** zaškrtávací políčko zaškrtnuto, člen není zobrazen v typu.  
  
#### <a name="to-modify-a-type-member"></a>Změna členu typu  
  
1.  Pomocí Návrháře tříd vyberte typ.  
  
2.  Pokud se v okně podrobností třídy nezobrazí, klikněte na tlačítko **okno podrobností třídy** tlačítko na panelu nástrojů návrhář tříd.  
  
3.  Upravte hodnoty v polích v mřížce okno podrobností třídy. Po každé úpravě stiskněte klávesu ENTER nebo jinak přesuňte fokus z upravovaného pole, například stisknutím klávesy TAB. Úpravy se v kódu projeví okamžitě.  
  
    > [!NOTE]
    >  Pokud chcete změnit pouze název členu, můžete to provést úpravou na místě.  
  
##  <a name="AddMethodParams"></a> Přidávání parametrů k metodám  
 Přidání parametrů do metody pomocí okna podrobností třídy. Parametry lze konfigurovat jako povinné, či volitelné. Zadání hodnoty pro **volitelné výchozí** vlastnost parametru dáte návrháři pokyn, aby vygeneroval kód jako volitelný parametr.  
  
 Řádky parametru obsahují následující položky:  
  
- **Jméno**  
  
   **Název** sloupců na řádku parametru zobrazí název parametru. Tento název se také zobrazí v **název** vlastností v okně Vlastnosti. Tuto buňku můžete použít ke změně názvu jakéhokoli parametru, který má oprávnění pro čtení i zápis.  
  
   Odkazuje na název parametru zobrazí název parametru, pokud **název** sloupec je příliš úzký, aby se zobrazil celý název.  
  
- **Typ**  
  
   **Typ parametru** buňky používá technologii Intellisense, která vám umožní vybrat si ze seznamu všech typů dostupných v aktuálním projektu nebo v odkazovaných projektech.  
  
- **Modifikátor**  
  
   **Modifikátor** buňku na řádku parametru přijímá a zobrazuje nový modifikátor parametru. Pokud chcete zadat nový parametr modifikátoru, pomocí rozevíracího seznamu vyberte z **žádný**, **ref**, **si**, nebo **params** v C# a **ByVal**, **ByRef**, nebo **ParamArray** v jazyce VB.  
  
- **Shrnutí**  
  
   **Souhrn** buňku na řádku parametru umožňuje zadávání komentářů kódu, které se zobrazí v IntelliSense při zadání parametru do editoru kódu.  
  
- **\<Přidat parametr >**  
  
   Poslední řádek parametru členu obsahuje text **<add parameter>** v **název** buňky. Kliknutím na tuto buňku vytvoříte nový parametr. Další informace najdete v tématu [přidání parametru k metodě](../ide/creating-and-configuring-type-members-class-designer.md#HowToAddParameterToMethod).  
  
  **Vlastnosti parametru v okně Vlastnosti**  
  
  V okně Vlastnosti zobrazí stejné vlastnosti parametru v okně podrobností třídy: **název**, **typ**, **modifikátor**, **Souhrn**, jakož i **volitelné výchozí** vlastnost. Změnou vlastnosti na jednom místě aktualizujete hodnotu vlastnosti globálně, včetně zobrazení hodnoty v jiném umístění.  
  
> [!NOTE]
>  Chcete-li přidat parametr do delegáta, přečtěte si téma [vytváření členů](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).  
  
> [!NOTE]
>  Ačkoli je destruktor metoda, nemůže mít parametry.  
  
###  <a name="HowToAddParameterToMethod"></a> Přidání parametru k metodě  
  
1.  Na ploše diagramu klikněte na typ obsahující metodu, ke které chcete přidat parametr.  
  
     Typ získá fokus a jeho obsah se zobrazí v okně podrobností třídy.  
  
2.  V okně podrobností třídy rozbalte řádek metody, do které chcete přidat parametr.  
  
     Zobrazí se řádek parametru, který obsahuje pouze dvojici závorek a slova  **\<přidat parametr >.**  
  
3.  Klikněte na tlačítko  **\<přidat parametr >**, zadejte název nového parametru a stiskněte klávesu **Enter**.  
  
     Nový parametr se přidá do metody a kódu metody. Zobrazí se v okně podrobností třídy a v okně Vlastnosti.  
  
4.  Volitelně můžete určit další detaily parametru, například jeho typ.  
  
### <a name="to-add-an-optional-parameter-to-a-method"></a>Přidání volitelného parametru do metody  
  
1.  Na ploše diagramu klikněte na typ obsahující metodu, ke které chcete přidat volitelný parametr.  
  
     Typ získá fokus a jeho obsah se zobrazí v okně podrobností třídy.  
  
2.  V okně podrobností třídy rozbalte řádek metody, do které chcete přidat volitelný parametr.  
  
     Zobrazí se řádek parametru, který obsahuje pouze dvojici závorek a slova  **\<přidat parametr >.**  
  
3.  Klikněte na tlačítko  **\<přidat parametr >**, zadejte název nového parametru a stiskněte klávesu **Enter**.  
  
     Nový parametr se přidá do metody a kódu metody. Zobrazí se v okně podrobností třídy a v okně Vlastnosti.  
  
4.  V okně Vlastnosti zadejte hodnotu **volitelné výchozí** vlastnost. Nastavením vlastnosti Volitelné výchozí nastavíte daný parametr na volitelný.  
  
    > [!NOTE]
    >  Volitelné parametry musí být posledními parametry v seznamu parametrů.  
  
##  <a name="ClassDetailsUsageNotes"></a> Poznámky k použití okna podrobností třídy  
 Při používání okna podrobností třídy mějte prosím na paměti následující tipy.  
  
 **Editovatelné a needitovatelné buňky**  
  
 Všechny buňky v okně podrobností třídy jsou editovatelné, s několika výjimkami:  
  
- Celý typ je jen pro čtení, když, například se nachází v odkazovaném sestavení (viz [zobrazení jen pro čtení informací (návrhář tříd)](http://msdn.microsoft.com/en-us/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).) Při výběru tvaru v Návrháři tříd, okno podrobností třídy zobrazí jeho detaily ve stavu jen pro čtení.  
  
- V případě indexerů je název jen pro čtení a zbytek (typ, modifikátor, shrnutí) je editovatelný.  
  
- V okně podrobností třídy mají všechny obecné typy parametry jen pro čtení. Chcete-li změnit obecný parametr, upravte jeho zdrojový kód.  
  
- Název parametru typu, který je definován na obecném typu, je jen pro čtení.  
  
- Když je kód typu porušen (nelze jej analyzovat), okno podrobností třídy zobrazí obsah typu jen pro čtení.  
  
  **Okno podrobností třídy a zdrojový kód**  
  
- Kliknutím pravým tlačítkem myši na tvar v okně podrobností třídy (nebo Návrhář tříd) a následným kliknutím na příkaz Zobrazit kód můžete zobrazit zdrojový kód. Otevře se soubor zdrojového kódu a zobrazení se posune na vybraný prvek.  
  
- Změna zdrojového kódu se okamžitě projeví v zobrazení informací podpisu v okně Návrhář třídy a Podrobnosti třídy. Pokud je okno podrobností třídy v daném okamžiku zavřeno, nové informace se zobrazí při příštím otevření okna.  
  
- Když je kód typu porušen (nelze jej analyzovat), okno podrobností třídy zobrazí obsah typu jen pro čtení.  
  
  **Funkce schránky v okně podrobností třídy**  
  
  Z okna podrobností třídy můžete kopírovat nebo vyjímat pole či řádky a vkládat je do jiného typu. Řádek můžete vyjmout, pouze pokud je jen pro čtení. Po vložení řádku okno podrobností třídy přiřadí nový název (odvozený od názvu zkopírovaného řádku), aby nedošlo ke konfliktu.  
  
##  <a name="ReadOnlyInfo"></a> Zobrazení informací jen pro čtení  
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
  
  Pokud se pokusíte uložit projekt obsahující typ, jehož soubor zdrojového kódu je jen pro čtení, **uložení souboru jen pro čtení** se zobrazí dialogové okno, které nabízí možnost uložit soubor pod novým názvem nebo nové umístění nebo přepsat soubor jen pro čtení . Pokud soubor přepíšete, nová kopie již není jen pro čtení.  
  
  Pokud soubor s kódem obsahuje chybu syntaxe, tvary zobrazující kód v daném souboru budou dočasně jen pro čtení, dokud chyba syntaxe nebude opravena. Tvary v tomto stavu zobrazí červený text a červenou ikonu, která zobrazí popisek s textem „Soubor zdrojového kódu obsahuje chybu analýzy“.  
  
  Odkazovaný typ (například typ rozhraní .NET Framework), který existuje v rámci jiného uzlu projektu nebo uzlu odkazovaného sestavení, je na návrhové ploše Návrháře tříd uveden jako jen pro čtení. Místní typ, který existuje v projektu, jež chcete otevřít, je pro čtení i zápis a jeho tvar na návrhové ploše Návrháře tříd je takto označen.  
  
  Indexery jsou pro čtení i zápis v kódu a v okně podrobností třídy, ale název indexeru je jen pro čtení.  
  
  Částečné metody nelze upravovat pomocí Návrháře tříd nebo v okně podrobností třídy; k úpravám je nutné použít Editor kódu.  
  
  Nativní kód C++ nelze upravovat pomocí Návrháře tříd nebo v okně podrobností třídy; k úpravám je nutné použít Editor kódu.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Zobrazování typů a vztahů (Návrhář tříd)](../ide/viewing-types-and-relationships-class-designer.md)|Existující typy, členy a vztahy můžete zobrazit v diagramu třídy.|  
|[Refaktoring tříd a typů (Návrhář tříd)](../ide/refactoring-classes-and-types-class-designer.md)|Pomocí refaktoringu můžete snadno přejmenovat typ a členy typu. Můžete také přesunovat členy mezi třídami, rozdělit třídu na částečné třídy a implementovat rozhraní.|