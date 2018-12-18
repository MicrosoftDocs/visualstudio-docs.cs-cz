---
title: Práce s kódem jazyka Visual C++ (návrhář tříd) | Dokumentace Microsoftu
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
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- Visual C++, Class Designer
- Class Designer, Visual C++ support
- Class Designer, limitations
- Class Designer, tasks in Visual C++
- Visual C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f777c9bdd0cf2ea300d2df8e7cbfbc8900c25c2a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929527"
---
# <a name="working-with-visual-c-code-class-designer"></a>Práce s kódem jazyka Visual C++ (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vizuální návrhová plocha, volá se zobrazí návrhář tříd *diagram tříd* , který obsahuje vizuální reprezentaci prvků kódu ve vašem projektu. Diagramy tříd můžete navrhovat a zobrazovat třídami a ostatními typy v projektu.  
  
 Návrhář tříd podporuje následující prvky kódu jazyka C++:  
  
-   Třídy (se podobá obrazec spravovanou třídu s tím rozdílem, že může mít více vztahů dědičnosti)  
  
-   Anonymní třídy (zobrazí se vygenerovaný název anonymního typu zobrazení tříd)  
  
-   Třída šablony  
  
-   Struktura  
  
-   Výčet  
  
-   (Zobrazí se po zpracování zobrazení makro) – makro  
  
-   Definice TypeDef  
  
> [!NOTE]
>  To však není stejný jako diagram tříd UML, který vytvoříte v projektu modelování. Další informace najdete v tématu [diagramů tříd UML: referenční](../modeling/uml-class-diagrams-reference.md).  
  
## <a name="troubleshooting-type-resolution-and-display-issues"></a>Řešení potíží typu řešení a problémů zobrazení  
  
### <a name="location-of-source-files"></a>Umístění zdrojových souborů  
 Návrhář tříd není udržovat přehled o umístění zdrojových souborů. Proto pokud změníte strukturu projektu nebo přesunout zdrojové soubory v projektu, návrhář tříd může dojít ke ztrátě sledování typu (zejména zdrojového typu definice typu základní třídy a přidružení typů). K chybě může dojít například **je návrhář tříd nemůže zobrazit tento typ**. Pokud tak učiníte, přetáhněte do diagramu tříd znovu a znovu zobrazit přemístění nebo upravila zdrojový kód.  
  
### <a name="update-and-performance-issues"></a>Aktualizace a problémy s výkonem  
 Pro projekty Visual C++ může trvat přibližně 30 – 60 sekund změny ve zdrojovém souboru se zobrazí v diagramu tříd. Toto zpoždění může také způsobit, že návrhář tříd k vyvolání chyby **nenašly se žádné typy ve výběru**. Pokud obdržíte chybu takovou situaci, klikněte na tlačítko **zrušit** v chybové zprávě a vyčkat, než prvek kódu se zobrazí v zobrazení tříd. Až to uděláte, návrhář tříd by mohli pro zobrazení typu.  
  
 Pokud diagram tříd se neaktualizuje se změny provedené v kódu, může být potřeba diagram zavřít a znovu ji spusťte.  
  
### <a name="type-resolution-issues"></a>Typ řešení problémů  
 Návrhář tříd nemusí být možné přeložit typy z následujících důvodů:  
  
- Typ není v projektu nebo sestavení, který neodkazuje projekt, který obsahuje diagram třídy. Chcete-li opravit tuto chybu, přidejte odkaz na projekt nebo sestavení obsahující typ. Další informace najdete v tématu [NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
- Typ není ve správném oboru, takže ho nejde najít návrhář tříd. Ujistěte se, že kód není chybí `using`, `imports`, nebo `#include` příkazu. Ujistěte se také, že nebyly vyjme typ (nebo související typ) z oboru názvů, ve kterém bylo původně umístěná.  
  
- Typ neexistuje (nebo má zakomentované). Chcete-li tuto chybu opravit, ujistěte se, že nejsou označené jako komentář nebo odstranit typ.  
  
- Typ je umístěn v knihovně odkazuje direktivu #import. Možných řešení je ruční přidání generovaný kód (soubor .tlh) #include – direktiva v souboru hlaviček.  
  
  Chyba se pravděpodobně chcete zobrazit pro řešení problému s typem je **kód nemohl být nalezen jeden nebo více obrazců v diagramu tříd '\<element > "**. Tato chybová zpráva nemusí znamenat, že je váš kód v chybě. Označuje, že jste byli pouze tento návrhář tříd nemůže zobrazit váš kód. Vyzkoušejte následující míry.  
  
- Ujistěte se, že typ existuje. Ujistěte se, že nejsou neúmyslně zakomentované nebo odstranili zdrojový kód.  
  
- Ujistěte se, že návrhář tříd podporuje typ, který jste zadali. Zobrazit [omezení pro prvky kódu C++](#limitations).  
  
- Došlo k pokusu o přeložení typu. Typ může být v projektu nebo sestavení, který neodkazuje projekt, který obsahuje diagram třídy. Chcete-li opravit tuto chybu, přidejte odkaz na projekt nebo sestavení obsahující typ. Další informace najdete v tématu [NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
- Ujistěte se, že typ je ve správném oboru tak, aby ji mohli najít návrhář tříd. Ujistěte se, že kód není chybí `using`, `imports`, nebo `#include` příkazu. Ujistěte se také, že nebyly vyjme typ (nebo související typ) z oboru názvů, ve kterém bylo původně umístěná.  
  
### <a name="troubleshooting-other-error-messages"></a>Řešení potíží s další chybové zprávy  
 Pomoc při řešení problémů s chybami a upozorněními můžete najít na veřejných fórech Microsoft Developer Network (MSDN). Zobrazit [návrháře fórum Visual Studio třídy](http://go.microsoft.com/fwlink/?linkid=160754).  
  
##  <a name="limitations"></a> Omezení pro prvky kódu C++  
  
-   Když se načte projektu Visual C++, funkce návrháře tříd způsobem jen pro čtení. Můžete změnit diagramu tříd, ale nemůžete ukládat změny z diagramu tříd zpět ke zdrojovému kódu.  
  
-   Návrhář tříd podporuje pouze nativní C++ sémantiku. Pro projekty Visual C++, které jsou kompilovány do spravovaného kódu návrhář tříd vizualizovat pouze prvky kódu, které jsou nativní typy. Proto můžete přidat diagramu tříd do projektu, ale návrhář tříd nebude možné vizualizovat prvků, ve kterém `IsManaged` je nastavena na `true` (tzn. typy hodnot a odkazové typy).  
  
-   Návrhář tříd pro projekty Visual C++ čte pouze definici typu. Předpokládejme například, definice typu v souboru hlaviček (.h) a definovat jeho členy v souboru implementace (.cpp). Pokud vyvoláte "Zobrazit Diagram tříd" v souboru implementace (.cpp), nezobrazí nic návrhář tříd. Další příklad – pokud vyvoláte "Zobrazit Diagram tříd" na soubor .cpp, který používá `#include` příkazu zahrnout další soubory, ale neobsahuje žádné definice tříd skutečné, návrhář tříd znovu nezobrazí nic.  
  
-   Soubory IDL (.idl), které definují rozhraní COM a knihoven typů, se nezobrazují v diagramech, pokud jsou kompilovány do nativního kódu C++.  
  
-   Návrhář tříd nepodporuje globální funkce a proměnné.  
  
-   Návrhář tříd nepodporuje sjednocení. Toto je speciální typ třídy, ve kterém je paměť přidělená je pouze množství potřebné pro největší datový člen Evropské unie.  
  
-   Návrhář tříd nezobrazuje základní datové typy, jako `int` a `char`.  
  
-   Návrhář tříd nezobrazuje typy, které jsou definovány mimo aktuální projekt, pokud projekt nemá správné odkazy na tyto typy.  
  
-   Návrhář tříd můžete zobrazit, ale ne vztahy mezi vnořeného typu a ostatními typy vnořené typy.  
  
-   Návrhář tříd nemůže zobrazit typy, které jsou neplatné nebo které jsou odvozeny od typu void.  
  
## <a name="see-also"></a>Viz také  
 [Navrhování a zobrazování tříd a typů](../ide/designing-and-viewing-classes-and-types.md)   
 [Práce s třídami a ostatními typy (návrhář tříd)](../ide/working-with-classes-and-other-types-class-designer.md)   
 [Práce s diagramy tříd (návrhář tříd)](../ide/working-with-class-diagrams-class-designer.md)   
 [Navrhování tříd a typů (návrhář tříd)](../ide/designing-classes-and-types-class-designer.md)   
 [Další informace o chybách návrháře tříd](../ide/additional-information-about-class-designer-errors.md)   
 [Třídy jazyka Visual C++ v Návrháři tříd](../ide/visual-cpp-classes-in-class-designer.md)   
 [Struktury jazyka Visual C++ v Návrháři tříd](../ide/visual-cpp-structures-in-class-designer.md)   
 [Výčty jazyka Visual C++ v Návrháři tříd](../ide/visual-cpp-enumerations-in-class-designer.md)   
 [Definice Typedefs jazyka Visual C++ v Návrháři tříd](../ide/visual-cpp-typedefs-in-class-designer.md)



