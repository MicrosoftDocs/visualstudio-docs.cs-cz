---
title: C# IntelliSense
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- C#, IntelliSense
- IntelliSense [C#]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 41a4dfa2a904f3fdc09671fd5e9afa0f29c2e9f3
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53160137"
---
# <a name="c-intellisense"></a>C# IntelliSense

C# IntelliSense je k dispozici při psaní kódu v editoru a při ladění v [přímý režim](../ide/reference/immediate-window.md) příkazové okno.

## <a name="completion-lists"></a>Seznamy dokončení

Seznamy dokončení technologie IntelliSense v jazyce C# obsahovat tokeny od seznam členů, Dokončit slovo a další. Poskytuje rychlý přístup k:

- Členy typu nebo oboru názvů

- Proměnné, příkazy a funkce na názvy

- Fragmenty kódu

- Klíčová slova jazyka

- Rozšiřující metody

Seznamu dokončení v jazyce C# je také dostatečně inteligentní, aby odfiltrovat irelevantní tokeny a předem vyberte token na základě kontextu. Další informace najdete v tématu [filtrované seznamy dokončení](#filtered-completion-lists).

### <a name="code-snippets-in-completion-lists"></a>Fragmenty kódu do seznamů dokončení

V jazyce C# obsahuje seznam pro doplňování fragmenty kódu můžete snadno vložit předdefinované obsahy kódu do vaší aplikace. Fragmenty kódu se zobrazí v seznamu pro doplňování jako fragment [textovou zkratku](../ide/code-snippets-schema-reference.md#shortcut-element). Další informace o fragmenty kódu, které jsou k dispozici v jazyce C# ve výchozím nastavení najdete v tématu [fragmenty kódu v C#](../ide/visual-csharp-code-snippets.md).

### <a name="language-keywords-in-completion-lists"></a>Klíčová slova jazyka do seznamů dokončení

V jazyce C# také seznam pro doplňování klíčová slova jazyka. Další informace o klíčových slovech jazyka C# najdete v tématu [klíčová slova jazyka C#](/dotnet/csharp/language-reference/keywords/index).

### <a name="extension-methods-in-completion-lists"></a>Rozšiřující metody do seznamů dokončení

Seznamu dokončení v jazyce C# obsahuje rozšiřující metody, které jsou v oboru.

> [!NOTE]
> Seznam pro doplňování se nezobrazí všechny rozšiřující metody pro <xref:System.String> objekty.

Rozšiřující metody použít jinou ikonu než metody instance. Referenční příručka seznamu ikonu, naleznete v tématu [ikony zobrazení třídy a prohlížeče objektů](../ide/class-view-and-object-browser-icons.md). Jsou-li instanci metody a metody rozšíření se stejným názvem v oboru, seznam pro doplňování zobrazí ikona metody rozšíření.

### <a name="filtered-completion-lists"></a>Filtrované seznamy dokončení

Technologie IntelliSense odstraní nepotřebné členy ze seznamu dokončení pomocí filtrů. C# filtry seznamy dokončení, které se zobrazují pro tyto položky:

- **Základní třídy a rozhraní**: Technologie IntelliSense automaticky odebere položky z rozhraní a základní třídy dokončení seznamů v deklaraci třídy base a interface seznamy a seznamy omezení. Například výčty nejsou uvedena v seznamu dokončení pro základní třídy, protože výčty nelze použít jako základní třídy. Dokončení seznamu základních tříd obsahuje pouze rozhraní a obory názvů. Pokud v seznamu vyberte položku a potom zadejte čárku, technologie IntelliSense odebere ze seznamu dokončení základní třídy, protože C# nepodporuje vícenásobnou dědičnost. Stejné chování dochází k dispozici také pro klauzule omezení.

- **Atributy**: Když použijte atribut na typ seznam pro doplňování se vyfiltruje tak, aby seznam obsahuje pouze ty typy, které sestup od obory názvů obsahují typy, jako třeba <xref:System.Attribute>.

- **Klauzule catch**

- **Inicializátory objektu**: V seznamu dokončení se zobrazí pouze členy, které mohou být inicializovány.

- **New – klíčové slovo**: Po zadání `new` a potom stiskněte klávesu **místo**, zobrazí se seznam pro doplňování. Položka je automaticky vybrán v seznamu na základě kontextu ve vašem kódu. Položky jsou automaticky vybrán v seznamu pro doplňování deklarací a návratovými příkazy v metodách.

- **enum – klíčové slovo**: Po stisknutí klávesy **místo** za symbolem rovná přiřazení výčtového typu, zobrazí se seznam pro doplňování. Položka je automaticky vybrán v seznamu na základě kontextu ve vašem kódu. Například jsou automaticky vybrané položky do seznamu dokončení po zadání – klíčové slovo návratový a při deklaraci.

- **jako a operátoři**: Seznam filtrovaný dokončení se zobrazí automaticky po stisknutí klávesy **místo** po zadání `as` nebo `is` – klíčové slovo.

- **Události**: Po zadání klíčového slova `event`, seznam pro doplňování obsahuje pouze typy delegátů.

- **Parametr nápovědy** automaticky řadí do první přetížení metody, která odpovídá parametrům, jak je zadáte. Pokud více přetížení metody jsou k dispozici, můžete nahoru a dolů šipkami přejít na další možné přetížení v seznamu.

### <a name="most-recently-used-members"></a>Naposledy použité členy

Technologie IntelliSense si pamatuje členy, které jste zvolili nedávno v místní nabídce [seznam členů](../ide/using-intellisense.md) pole pro název dokončení automatický objekt. Příště použijete **seznam členů**, naposledy použité členy se zobrazí v horní části. Mezi každou relaci sady Visual Studio se vymaže historii naposledy použité členy.

### <a name="override"></a>override

Po zadání [přepsat](/dotnet/csharp/language-reference/keywords/override) a potom stiskněte klávesu **místo**, technologie IntelliSense zobrazí všechny členy platný základní třídy, které můžete přepsat v rozevíracím seznamu místní nabídky. Zadáte návratový typ metody za `override` vyzve technologie IntelliSense, aby se zobrazily pouze metody, které vracejí stejného typu. Pokud technologie IntelliSense nemůže najít žádná shoda, zobrazí všechny členy základní třídy.

### <a name="ai-enhanced-intellisense"></a>AI Vylepšená technologie IntelliSense

Můžete nainstalovat experimentální [IntelliCode rozšíření](/visualstudio/intellicode/intellicode-visual-studio) pro Visual Studio, která poskytuje rozšířené umělé inteligence seznamy doplňování technologie IntelliSense. Toto rozšíření předpovídá největší pravděpodobností správné rozhraní API pro použití, ne jenom nabízí ten samý abecední seznam členů. Používá aktuální kontext kódu a vzory pro poskytování dynamického seznamu.

## <a name="automatic-code-generation"></a>Automatické generování kódu

### <a name="add-using"></a>Přidat direktivu using

**Přidat direktivu using** operace IntelliSense automaticky přidá požadované `using` směrnici do souboru kódu. Tato funkce umožňuje spravovat vaše zaměřit se na kód zápisu nechcete vyžadující, abyste svou pozornost zaměřili na jiné části kódu.

K zahájení **přidat direktivu using** operace, pozice kurzoru na typu odkaz, který nelze rozpoznat. Například když Vytvořte konzolovou aplikaci a pak přidejte `XmlTextReader` do těla `Main` metody červená vlnovka se zobrazí na daném řádku kódu, protože nelze rozpoznat odkaz na typ. Potom můžete vyvolat **přidat direktivu using** prostřednictvím **rychlé akce**. **Rychlé akce** je viditelná jen když se kurzor na nevázanému typu.

![Přidání pomocí, rychlá akce rozšířené bitové kopie](../ide/media/addusing-quickaction.png)

Klikněte na ikonu žárovky a klikněte na tlačítko **použití System.Xml;** k automatickému přidávání using – direktiva.

### <a name="remove-and-sort-usings"></a>Odebrat a seřadit direktivy using

**Odebrat a seřadit direktivy using** možnost seřadí a odebere `using` a `extern` deklarace bez změny chování zdrojového kódu. V průběhu času může stát zdrojové soubory opakovaném a mohou ztížit čtení kvůli nepotřebné a neuspořádaná `using` direktivy. **Odebrat a seřadit direktivy using** možnost zkomprimuje zdrojový kód tak, že odeberete nepoužívané `using` direktivy a zlepšuje čitelnost tím, že je řazení. Na **upravit** nabídce zvolte **IntelliSense**a klikněte na tlačítko **uspořádat direktivy using**.

### <a name="implement-interface"></a>Implementace rozhraní

Technologie IntelliSense poskytuje možnost, aby vám pomohly implementovat [rozhraní](/dotnet/csharp/language-reference/keywords/interface) při práci v editoru kódu. Za normálních okolností pro implementaci rozhraní správně, musíte vytvořit deklaraci metody pro každého člena rozhraní ve své třídě. Díky technologii IntelliSense, jakmile zadáte název rozhraní v deklaraci třídy **rychlé akce** se zobrazí žárovka. Žárovka nabídne možnost implementovat rozhraní automaticky, pomocí explicitní nebo implicitní pojmenování. V části explicitní názvy provádět deklarace metody název rozhraní. V části implicitní pojmenování, nevyžadují deklarace metody rozhraní, ke kterému patří. Metody rozhraní explicitně pojmenované je přístupný pouze prostřednictvím instance rozhraní a ne prostřednictvím instance třídy. Další informace najdete v tématu [explicitní implementaci rozhraní](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation).

Implementovat rozhraní vygeneruje minimální počet metoda zástupné procedury, které je nutné splnit rozhraní. Pokud základní třída implementuje částí rozhraní, pak tyto zástupné procedury se znova vygeneroval.

### <a name="implement-abstract-base-class"></a>Implementace třídy base abstraktu

Technologie IntelliSense poskytuje možnost, aby vám pomohly implementovat členy abstraktní základní třída automaticky při práci v editoru kódu. Za normálních okolností k implementaci abstraktní členy základní třídy vyžaduje vytvoření nové definice metody pro každou metodu abstraktní základní třída v odvozené třídě. Pomocí IntelliSense po zadání názvu abstraktní základní třídy v deklaraci třídy **rychlé akce** se zobrazí žárovka. Žárovka nabídne možnost pro implementaci metody třídy base automaticky.

Metoda zástupné procedury, které se vygenerovaly **implementace abstraktní třídy Base** funkce jsou modelovány pomocí fragmentu kódu, které jsou definovány v souboru *MethodStub.snippet*. Fragmenty kódu lze měnit. Další informace najdete v tématu [názorný postup: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md).

### <a name="generate-from-usage"></a>Generování před využitím

**Generovat z využití** funkce vám umožní použít třídy a členy před jejich definování. Můžete vygenerovat zástupnou proceduru pro všechny třídy, konstruktor, metoda, vlastnost, pole nebo výčtu, který chcete použít, ale ještě nebyly definovány. Aniž byste museli opustit váš aktuální umístění v kódu můžete vygenerovat nové typy a členy. Tím se minimalizují přerušení pracovního postupu.

V rámci každé nedefinovaný identifikátor se zobrazí červené podtržení vlnovkou. Při umístění ukazatele myši na identifikátor v popisku se zobrazí chybová zpráva. K zobrazení příslušné možnosti, můžete použít jednu z následujících postupů:

- Klikněte na nedefinovaný identifikátor. A **rychlé akce** pod tento identifikátor se zobrazí žárovka. Klikněte na žárovku.

- Klikněte na nedefinovaný identifikátor a potom stiskněte klávesu **Ctrl**+**.** (**Ctrl** + tečka).

- Klikněte pravým tlačítkem na nedefinovaný identifikátor a potom klikněte na tlačítko **rychlé akce a Refaktoringy**.

Možnosti, které se zobrazí následující:

- **Generovat vlastnost**

- **Generovat pole**

- **Generování metody**

- **Generovat třídy**

- **Generovat nový typ** (pro třídy, struktury, rozhraní nebo výčet)

## <a name="generate-event-handlers"></a>Generujte obslužné rutiny událostí

V editoru kódu technologie IntelliSense můžete připojit k pole události metod (obslužné rutiny událostí).

Po zadání `+=` operátor po polem události v *.cs* souboru, technologie IntelliSense zobrazí výzvu s možností stisknutím klávesy **kartu** klíč. To vloží novou instanci třídy delegáta, který odkazuje na metodu zpracování událostí.

![Zavěšení automatické tlačítko nahoru](../ide/media/vxautohookup.gif)

Pokud stisknete **kartu**, technologie IntelliSense automaticky dokončení příkazu pro vás a odkazu na obslužnou rutinu události zobrazuje jako vybraný text v editoru kódu. Dokončete propojení automatické události IntelliSense výzva ke stisknutí klávesy **kartu** klíč znovu pro vytvoření prázdné zástupné procedury pro obslužnou rutinu události.

![Generovat obslužné rutiny události](../ide/media/vxgenerateeventhandler.gif)

> [!NOTE]
> Pokud nový delegát, který je vytvořen pomocí technologie IntelliSense odkazuje na existující obslužné rutiny události, technologie IntelliSense komunikuje tyto informace v popisu. Poté můžete upravit tento odkaz. text je už vybraná v editoru kódu. V opačném případě propojení automatické událost dokončení v tomto okamžiku.

Pokud stisknete **kartu**, technologie IntelliSense tříd stub si metodu se správným podpisem a umístí kurzor do těla obslužné rutiny události.

> [!NOTE]
> Použití **přejít zpět** příkaz **zobrazení** nabídky (**Ctrl**+**-**) se vrátíte k události propojení příkazu.

## <a name="see-also"></a>Viz také:

- [Používání technologie IntelliSense](../ide/using-intellisense.md)
- [Integrované vývojové prostředí sady Visual Studio](../get-started/visual-studio-ide.md)