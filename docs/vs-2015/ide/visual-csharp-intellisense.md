---
title: Visual C# IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [J#]
- Visual C#, IntelliSense
- IntelliSense [C#]
ms.assetid: 79ca304d-dc1e-4dc9-a2a6-7808df2e588e
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 36803dfbba7ea6d6d2a869fb94c05105ed4af15d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643338"
---
# <a name="visual-c-intellisense"></a>Visual C# IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual C# IntelliSense je k dispozici při kódování v editoru a při ladění v příkazovém okně [přímo v režimu](../ide/reference/immediate-window.md) .

## <a name="completion-lists"></a>Seznamy dokončení
 Seznamy dokončení IntelliSense v jazyce Visual C# obsahují tokeny ze seznamu členů, kompletních slov a dalších. Poskytuje rychlý přístup k:

- Členy typu nebo oboru názvů,

- Názvy proměnných, příkazů a funkcí

- [Fragmenty kódu](#CodeSnippets),

- [Klíčová slova jazyka](#Keywords),

- [Rozšiřující metody](#ExtensionMethods)

  Seznam pro doplňování C# v nástroji je také dostatečně inteligentní, aby bylo možné filtrovat nedůležité tokeny a předem vybrat token na základě kontextu. Další informace najdete v tématu [Filtrované seznamy dokončení v C# ](../misc/filtered-completion-lists-in-csharp.md) a [předem vybrané položky seznamu dokončení v C# ](../misc/pre-selected-completion-list-items-in-csharp.md).

### <a name="CodeSnippets"></a>Fragmenty kódu v seznamech dokončení
 V vizuálu C#obsahuje seznam pro dokončování fragmenty kódu, které vám pomůžou snadno vkládat předdefinované části kódu do programu. Fragmenty kódu se zobrazí v seznamu pro doplňování jako [Klávesová zkratka fragmentu (fragmenty kódu technologie IntelliSense)](https://msdn.microsoft.com/052cc97a-5c70-42f8-b398-4c3adf670cfa).  Další informace o fragmentech kódu, které jsou ve výchozím nastavení C# k dispozici v jazyce Visual, naleznete v tématu [vizuální C# fragmenty kódu](../ide/visual-csharp-code-snippets.md).

### <a name="Keywords"></a>Klíčová slova jazyka v seznamech dokončení
 V vizuálu C#obsahuje seznam pro doplňování také klíčová slova jazyka. Další informace o C# klíčových slovech jazyka najdete v tématu [ C# klíčová](https://msdn.microsoft.com/library/e929b0f2-4b92-4d37-8060-23d323b098ad)slova.

### <a name="ExtensionMethods"></a>Metody rozšíření v seznamech dokončení
 V vizuálu C#obsahuje seznam pro dokončování rozšiřující metody, které jsou v oboru.

> [!NOTE]
> V seznamu pro doplňování se nezobrazí všechny metody rozšíření pro objekty <xref:System.String>.

 Metody rozšíření používají jinou ikonu než metody instance. Seznam ikon seznamu naleznete v tématu [zobrazení tříd a prohlížeč objektů ikony](../ide/class-view-and-object-browser-icons.md). Pokud metoda instance a metoda rozšíření se stejným názvem jsou v oboru, v seznamu pro doplňování se zobrazí ikona metody rozšíření.

### <a name="filtered-completion-lists"></a>Filtrované seznamy dokončení
 IntelliSense odebere nepotřebné členy ze seznamu pro doplňování pomocí filtrů.

 Vizuální C# filtry zobrazuje seznam dokončení, který se zobrazí pro tyto položky:

- **Rozhraní a základní třídy.** Technologie IntelliSense automaticky odebere položky ze seznamu rozhraní a seznamů doplňování základní třídy v deklaracích třídy Base a seznam rozhraní a seznamy omezení. Například výčty se nezobrazují v seznamu pro doplňování pro základní třídy, protože výčty nelze použít pro základní třídy. Seznam dokončení základních tříd obsahuje pouze rozhraní a obory názvů. Pokud vyberete položku v seznamu a potom zadáte čárku, technologie IntelliSense odebere základní třídy ze seznamu dokončení, protože vizuál C# nepodporuje vícenásobnou dědičnost. Stejné chování se projeví také v klauzulích omezení.

- **Atributy**: když použijete atribut na typ, seznam pro doplňování se vyfiltruje tak, že seznam obsahuje jenom ty typy, které se dokončí od oborů názvů, které obsahují tyto typy, například <xref:System.Attribute>.

- operátory `as` a `is`.

- **Klauzule catch.**

- **Inicializátory objektů:** V seznamu dokončení se zobrazí pouze členové, kteří mohou být inicializováni.

- **New – klíčové slovo**: když zadáte `new` a potom stisknete mezerník, zobrazí se seznam pro doplňování. Položka je automaticky vybrána v seznamu na základě kontextu v kódu. Například položky jsou automaticky vybrány v seznamu pro doplňování pro deklarace a příkazy Return v metodách.

- **operátory as a jsou:** Filtrované seznamy dokončení se zobrazí automaticky po stisknutí klávesy MEZERNÍK po zadání klíčového slova `as` nebo `is`.

- Události: když zadáte klíčové slovo `event`, seznam pro doplňování obsahuje jenom typy delegátů.

- Parametr help se automaticky řadí k prvnímu přetížení metody, které odpovídá parametrům při jejich zadávání. Pokud je k dispozici více přetížení metod, můžete pomocí šipek nahoru a dolů přejít na další možné přetížení v seznamu.

## <a name="most-recently-used-members"></a>Naposledy použité členy
 Technologie IntelliSense pamatuje členy, které jste v poslední době vybrali v rozevíracím [seznamu Členové](../ide/using-intellisense.md) okna pro automatické dokončování názvů objektů. Při příštím použití seznamu členů se v horní části zobrazí naposledy použité členy. Historie naposledy použitých členů je mezi jednotlivými relacemi v integrovaném vývojovém prostředí vymazána.

## <a name="override"></a>override
 Když zadáte [přepsání](https://msdn.microsoft.com/library/dd1907a8-acf8-46d3-80b9-c2ca4febada8) a potom stisknete mezerník, IntelliSense zobrazí všechny platné členy základní třídy, které lze přepsat v rozevíracím seznamu. Po zadání návratového typu metody po `override` se zobrazí výzva IntelliSense, aby zobrazila pouze metody, které vracejí stejný typ. Pokud IntelliSense nenajde žádné shody, zobrazí všechny členy základní třídy.

## <a name="automatic-code-generation"></a>Automatické vytváření kódu

### <a name="add-using"></a>Přidat direktivu using
 Operace přidat pomocí technologie IntelliSense umožňuje zachovat fokus na kód, který píšete, nikoli na to, abyste museli posunout fokus na jinou část kódu.

 Chcete-li zahájit operaci přidat pomocí, umístěte kurzor na odkaz na typ, který nelze přeložit. Například pokud vytvoříte konzolovou aplikaci a poté přidáte `XmlTextReader` do těla metody `Main`, zobrazí se inteligentní značka pod pravým znakem `XmlTextReader`, protože se zobrazí jako odkaz na typ, který nelze přeložit.

 ![Přidat s použitím obrázku inteligentní značky](../ide/media/addusesmart.gif "AddUseSmart")

 Pak můžete vyvolat přidat pomocí výběrem z podnabídky **vyřešit** v nabídce **IntelliSense** nebo v kontextové nabídce nebo vyvoláním metody Add pomocí inteligentní značky. Inteligentní značka je viditelná pouze v případě, že je kurzor umístěn na nebo sousedící s nevázaným typem.

 ![Přidat pomocí rozbaleného obrázku inteligentní značky](../ide/media/addusesmartexp.gif "AddUseSmartExp")

### <a name="organize-usings"></a>Uspořádat direktivy using
 Možnost **organizovat používá** řazení a odebírání `using` a `extern` deklarací, aniž by došlo ke změně chování zdrojového kódu. V průběhu času se zdrojové soubory můžou bloated a obtížně číst z důvodu zbytečných a neuspořádaných `using` direktiv. Možnost **Uspořádat používá** kompaktní zdrojový kód odebráním nepoužívaných direktiv `using` a vylepšuje čitelnost jejich řazením.

 Chcete-li zobrazit dostupné možnosti v integrovaném vývojovém prostředí sady Visual Studio, v nabídce **Upravit** přejděte na možnost **IntelliSense**a pak na položku **uspořádat pomocí**. Rozhraní IDE poskytuje následující možnosti pro uspořádání a odebrání `usings` direktiv:

### <a name="implement-interface"></a>Implementovat rozhraní
 Technologie IntelliSense poskytuje možnost, která vám umožní implementovat [rozhraní](https://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba) při práci v editoru kódu. Obvykle pro správné implementaci rozhraní musíte vytvořit deklaraci metody pro každého člena rozhraní ve vaší třídě. Pomocí technologie IntelliSense po zadání názvu rozhraní v deklaraci třídy se zobrazí inteligentní značka. Inteligentní značka poskytuje možnost automatického nasazení rozhraní pomocí explicitního nebo implicitního pojmenování. V rámci explicitního pojmenování deklarace metod přenese název rozhraní; v rámci implicitního pojmenování deklarace metod neurčuje rozhraní, ke kterému patří. K metodě explicitně pojmenovaného rozhraní lze přistupovat pouze prostřednictvím instance rozhraní a nikoli prostřednictvím instance třídy. Další informace naleznete v tématu [explicitní implementace rozhraní](https://msdn.microsoft.com/library/181c901f-0d4c-4f29-97fc-895079617bf2).

 Implementující rozhraní vygeneruje minimální počet zástupných procedur, které jsou požadovány pro uspokojení rozhraní. Pokud základní třída implementuje části rozhraní, pak tyto zástupné procedury nejsou znovu vygenerovány.

### <a name="implement-abstract-base-class"></a>Implementovat abstraktní základní třídu
 Technologie IntelliSense poskytuje možnost, která vám umožní při práci v editoru kódu automaticky implementovat členy abstraktní základní třídy. Za normálních okolností pro implementaci členů abstraktní základní třídy je nutné vytvořit novou definici metody pro každou metodu abstraktní základní třídy v odvozené třídě. Pomocí technologie IntelliSense po zadání názvu abstraktní základní třídy v deklaraci třídy se zobrazí inteligentní značka. Inteligentní značka poskytuje možnost automaticky implementovat metody základní třídy.

 Metoda zástupných procedur, které jsou generovány funkcí implementovat abstract Base Class, jsou modelovány fragmentem kódu, který je definován v souboru MethodStub. fragment. Fragmenty kódu lze upravovat. Další informace naleznete v tématu [Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md).

### <a name="generate-from-usage"></a>Generovat z využití
 Funkce **Generovat z využití** umožňuje použít třídy a členy před jejich definováním. Můžete vygenerovat zástupnou proceduru pro libovolnou třídu, konstruktor, metodu, vlastnost, pole nebo výčet, které chcete použít, ale ještě nebyly definovány. Můžete generovat nové typy a členy, aniž byste opustili aktuální umístění v kódu. Tím se minimalizuje přerušení pracovního postupu.

 Pod každým nedefinovaným identifikátorem se zobrazí vlnové podtržení. Když umístíte ukazatel myši na identifikátor, zobrazí se v popisu chybová zpráva.

 Chcete-li zobrazit vhodné možnosti, můžete použít jeden z následujících postupů:

- Klikněte na nedefinovaný identifikátor. Pod znakem nejvíce vlevo se zobrazí krátké podtržení. Umístěte ukazatel myši na krátké podtržení a zobrazí se inteligentní značka (ikona). Klikněte na inteligentní značku.

- Klikněte na nedefinovaný identifikátor a potom stiskněte klávesovou zkratku CTRL +. (tečka).

- Klikněte pravým tlačítkem na nedefinovaný identifikátor a pak klikněte na **vygenerovat**.

  Mezi možnosti, které se zobrazí, patří následující:

- **Vygenerovat zástupnou proceduru vlastnosti**

- **Vygenerovat zástupnou proceduru pole**

- **Vygenerovat zástupnou proceduru metody**

- **Generovat třídu**

- **Generovat nový typ** (pro třídu, strukturu, rozhraní nebo výčet)

## <a name="generate-event-handlers"></a>Generovat obslužné rutiny událostí
 V editoru kódu vám IntelliSense může přispět k zapojení metod (obslužných rutin událostí) do polí událostí.

 Když zadáte operátor `+=` po poli události v souboru. cs, IntelliSense vás vyzve k stisknutí klávesy TABULÁTORu. Tím se vloží nová instance delegáta, která odkazuje na metodu, která událost zpracovává.

 ![Automatické zavěšení tlačítka](../ide/media/vxautohookup.gif "vxAutoHookUp")

 Pokud stisknete klávesu TAB, technologie IntelliSense automaticky dokončí příkaz a v editoru kódu zobrazí odkaz na obslužnou rutinu události jako vybraný text. K dokončení automatické služby Event propojení vás IntelliSense vyzve k opětovnému stisknutí klávesy TAB a k vytvoření prázdné zástupné procedury pro obslužnou rutinu události.

 ![Generovat obslužnou rutinu události](../ide/media/vxgenerateeventhandler.gif "vxGenerateEventHandler")

> [!NOTE]
> Pokud nový delegát, který je vytvořen technologií IntelliSense, odkazuje na existující obslužnou rutinu události, technologie IntelliSense tyto informace komunikuje v popisu tlačítka. Pak můžete tento odkaz upravit; text je již vybrán v editoru kódu. V opačném případě je v tuto chvíli dokončená Automatická Event propojení.

 Pokud stisknete klávesu TAB, technologie IntelliSense odblokuje metodu se správným podpisem a umístí kurzor do těla vaší obslužné rutiny události.

> [!NOTE]
> Pomocí příkazu **Navigovat zpět** v nabídce **zobrazení** (CTRL +-) se vraťte do příkazu Event propojení.

 Následující úkol ukazuje, jak technologie IntelliSense automaticky připojí obslužnou rutinu události s názvem `button1_Click` do pole události s názvem `button1.Click`.

## <a name="see-also"></a>Viz také
 [Integrované vývojové prostředí sady Visual Studio](../ide/visual-studio-ide.md)
